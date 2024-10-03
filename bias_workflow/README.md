# Bioimage analysis workflow – a primer

Short intro here

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
The background in this image has a different "scale" compared to the rice grains. We can estimate the background using Gaussian blurring.

```python
from skimage.filters import gaussian

g_filt = gaussian(img,sigma=10 preserve_range=True)
```

#### Task 3.2: Determine the Best Sigma Value for Background Estimation

Experiment with different sigma values and discuss the results. Try to estimate the sigma that gives the best approximation of the uneven background.

```python
stackview.interact(gaussian, img)
```
After determining the best sigma, subtract the background from the original image to correct for uneven illumination.

## Segmentation – Second Attempt
Now that we’ve improved the image quality, let’s try global segmentation again.

### Exercise 4: Segment the Background-Corrected Image

#### Task 4.1: Check Background Correction
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



Material based on this book: https://github.com/CamachoDejay/MyFavouriteBIAStool_NEUBIAS/blob/main/Example.ipynb