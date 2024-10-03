# Bioimage analysis workflow – a primer

In this session, we will introduce the essential steps in constructing a bioimage analysis workflow. We will explore some of the most common processes involved, focusing on the task of quantifying the area distribution of rice grains. This hands-on approach will help you understand key concepts and techniques used in bioimage analysis.

## Basic Scheme of a Bioimage Analysis (BIAS) Workflow

1. **Image Import and Metadata Management**: We will keep this section brief, as it was covered in detail during the previous session.
2. **Image Pre-Processing**: The aim is to enhance features of interest, reduce background noise, and remove unwanted imaging artifacts.
3. **Image Segmentation**: This involves differentiating the foreground (objects of interest) from the background.
4. **Segmentation Post-Processing**: Refining segmented objects, often using prior knowledge about the sample.
5. **Connected Component Labeling**: Transitioning from segmentation to identifying individual objects. As we will discuss tomorrow, some segmentation methods already handle this step.
6. **Quantification of the Objects**: This can include morphological features or intensity-based measurements.


## Image Input – TIFF Example

Let’s load a TIFF image and display it:

```python
import skimage.io as skio
from pathlib import Path
import matplotlib.pyplot as plt

img_path = Path('./data/MathWorksInc/rice.tif')
img = skio.imread(img_path, plugin="tifffile")
plt.imshow(img, cmap="gray")
```

### Exercise 1: Image Quality Assessment
In pairs, discuss whether this image is easy or difficult to segment. Identify any issues, and we will discuss them together as a group.

Feel free to explore the image further with this interactive tool:

```python
import stackview
stackview.picker(img)
```

## Segmentation – First Attempt
Let’s try to segment the image using a simple global thresholding method. We will explore both manual and automated threshold value estimation.

### Excercise 2: Segmentation
#### Task 2.1: Manual segmentation 
Now that you have explored the image values with the picker tool, choose a reasonable threshold value. All pixels above or below this value can be classified as "rice" (foreground) or background.

```python
th_val = 100
bw = img > th_val
plt.imshow(bw, cmap="gray")
```

#### Task 2.2: Automated Segmentation (Otsu's Method).
Otsu’s method works by finding the threshold value that minimizes the intra-class variance (i.e., the variance within each of the two groups: foreground and background).

```python
from skimage.filters import threshold_otsu

th_val = threshold_otsu(img)
bw_otsu = img > th_val
plt.imshow(bw_otsu)
```

#### Task 2.3: Assess the Segmentation Quality
Try the following command to compare the original image and the segmented version:

```python
stackview.curtain(img, bw_otsu)
```
Discuss the results in pairs

## Image Pre-Processing
We will try to "improve" the image quality to make segmentation easier.

### Exercise 3: Estimation of Uneven Illumination (Background)

#### Task 3.1: Gaussian Filtering – A Versatile Tool
The background in this image has a different "scale" compared to the rice grains. We can estimate the background using Gaussian blurring. Try different sigma values, any ideas on how we can estimate the background?

```python
from skimage.filters import gaussian

g_filt = gaussian(img,sigma=your_value_here, preserve_range=True)
stackview.insight(g_filt)
```

#### Task 3.2: Determine the Best Sigma Value for Background Estimation

To experiment with different sigma values we will use the nice "interact" functionality of stackview. Try to estimate the sigma that gives the best approximation of the uneven background.

```python
stackview.interact(gaussian, img)
```
After determining the best sigma, subtract the background from the original image to correct for uneven illumination.

## Segmentation – Second Attempt
Now that we’ve improved the image quality, let’s try global segmentation again.

### Exercise 4: Segment the Background-Corrected Image

#### Task 4.1: Check Background Correction
You can use ```stackview.curtain``` to compare the images
```python
img_bg = gaussian(img,sigma=your_value_here,preserve_range=True)
img_nobg = img - img_bg
stackview.curtain(img, img_nobg)
```

#### Task 4.2: Segment the Background-Corrected Image

```python
th_val = threshold_otsu(img_nobg)
print(f'The value is: {th_val}')
bw_otsu = img_nobg > th_val
stackview.curtain(img, bw_otsu)
```

## Connected Component Analysis

Now that we have a segmentation strategy we are satisfied with, the next step is to transition from a foreground/background image to an "object-based" image. Our goal is to identify each rice grain as an individual object with a unique identifier. To achieve this, we can use the connected components labeling algorithm.

```python
# Run connected component analysis
from skimage.measure import label

lbl = label(bw_otsu)
stackview.switch([img, bw_otsu, lbl])
```

### Exercise 5: Segmentation/Labeling Post-Processing

Let us consider the task at hand: quantifying the area distribution of the rice grains. To achieve this, we first need to create an image with well-separated objects. Please discuss the following questions in pairs:

* Are there any objects that were incorrectly segmented?
* What happens at the borders of the image?

#### Task 5.1: Separate Touching Objects – Watershed

This quote from the [skimage documentation](https://scikit-image.org/docs/stable/auto_examples/segmentation/plot_watershed.html) provides a basic understanding of the watershed algorithm. We won't dive into the full details at this stage:

> Starting from user-defined markers, the watershed algorithm treats pixels values as a local topography (elevation). The algorithm floods basins from the markers until basins attributed to different markers meet on watershed lines. In many cases, markers are chosen as local minima of the image, from which basins are flooded.
![watershed example from skimage](https://scikit-image.org/docs/stable/_images/sphx_glr_plot_watershed_001.png)

In our case, since the objects have well-defined shapes and are nearly separated, we can use a small trick to achieve separation:

1. **Shrink the objects slightly** so they become separated from one another.
2. **Use the shrunken image as markers**.
3. **Apply the watershed algorithm** to recover the original objects.

**Note:** The methods described below may also have the "side effect" of removing small objects.

##### Option 1: Erosion
```python
from skimage.morphology import isotropic_erosion
from scipy import ndimage as ndi

eroded_bw = isotropic_erosion(bw_otsu, radius=4)
markers = label(eroded_bw)
distance = ndi.distance_transform_edt(bw_otsu)
ws_lbl = watershed(-distance, markers, mask=bw_otsu)

stackview.switch([img, distance, ws_lbl])
```
The risk with this method is that excessive erosion can cause large objects to break into smaller ones or even disappear entirely.

##### Option 2: Binary Opening

Morphological opening is a process that involves an erosion followed by a dilation. However, it is easier to understand by seeing it in action. Below is an [image from Wikipedia](https://en.wikipedia.org/wiki/Opening_(morphology)) that illustrates the process:

![binary openning](https://upload.wikimedia.org/wikipedia/commons/c/c1/Opening.png)

```python
from skimage.morphology import binary_opening, disk
from scipy import ndimage as ndi

eroded_bw = isotropic_erosion(bw_otsu, radius=2)
round_edges = binary_opening(eroded_bw, footprint=disk(4))
markers = label(round_edges)
distance = ndi.distance_transform_edt(bw_otsu)

ws_lbl = watershed(-distance, markers, mask=bw_otsu)

stackview.switch([img, round_edges, ws_lbl])
```

#### Task 5.2: Removing Objects That Are Incomplete (Touching the Borders)

In this task, we will remove objects that are incomplete or touching the borders of the image.

```python
from skimage.segmentation import clear_border
from skimage.color import label2rgb

# Remove objects touching the image borders
full_rice_lbl = clear_border(ws_lbl)

# Overlay the labeled objects on the original image
overlay = label2rgb(full_rice_lbl, image=img, bg_label=0)
plt.imshow(overlay)
```

## Quantification

Now, we will extract properties from the identified objects in the image and store them in a `pandas` DataFrame for further analysis.

```python
import pandas as pd
from skimage.measure import regionprops_table

# Define the properties to quantify
properties = ['label', 'area', 'eccentricity', 'intensity_mean']

# Generate a table of properties for each labeled object
table = regionprops_table(label_image=full_rice_lbl,
                          intensity_image=img,
                          properties=properties)

# Convert the result into a pandas DataFrame
table = pd.DataFrame(table)
table.head()
```

Now that we have the desired properties in a table, we can save this data and create some basic statistics or plots.

```python
# Save the data to a CSV file
table.to_csv('rice_size.csv', index=False)

# Create a histogram of the object areas
table.hist(column='area', figsize=(4, 4))
```


Material based on this book: https://github.com/CamachoDejay/MyFavouriteBIAStool_NEUBIAS/blob/main/Example.ipynb