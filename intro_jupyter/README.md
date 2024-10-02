# Introduction to Jupyter and Python for Bioimage Analysis

## Opening Jupyter Lab in the BAND Environment:

The BAND team has pre-installed Jupyter Lab on the virtual machines you are using. We will use this setup to get started quickly. In the next session, we will cover how to install and configure Jupyter Lab on your own virtual machines and, later, on your personal devices.

Once you open Jupyter Lab, you will notice that a kernel has been prepared specifically for this course. Don’t worry too much about understanding what a "kernel" is at this stage. You can think of it as a self-contained installation of Python along with the necessary Python packages that we will use throughout the course. We will cover the topic of kernels in more detail before lunch.

1. Go to *Applications*
2. Go to *Programming*
3. Select *JupyterLab*

## Jupyter Lab Web Interface Overview

When you open Jupyter Lab, you will be greeted by its web-based interface, which is organized into several key areas:

1. **Main Work Area**
   - This is the central part of the interface where you will do most of your work. Here, you can open multiple documents or notebooks side by side in a tabbed or split view.
   - Each tab can contain notebooks, text files, terminals, or other applications like a file viewer.

2. **File Browser (Left Sidebar)**
   - The left sidebar contains the **File Browser**, which shows all the files and folders in your working directory.
   - You can navigate through your files, open existing notebooks, or create new ones. Other tabs in this sidebar include a list of running terminals, kernels, and other useful tools.

3. **Launcher (Main Menu)**
   - When you first open Jupyter Lab, you’ll see the **Launcher** in the main work area. It allows you to quickly create new notebooks, text files, or terminals.
   - From here, you can select the type of notebook or console to open, with the option to choose different programming environments (kernels).

4. **Top Menu Bar**
   - The **Menu Bar** at the top provides access to standard menu options like File, Edit, View, Run, and more.
   - You can use it to save your work, manage kernel settings, or change the layout of the interface.

5. **Command Palette**
   - The **Command Palette** can be opened by clicking on the `Command Palette` option in the left sidebar or by pressing `Ctrl + Shift + C`.
   - It provides quick access to Jupyter Lab’s commands, including opening files, managing extensions, or running specific tasks.

6. **Kernel Status**
   - The kernel status is displayed in the top right of the interface. It shows the state of the active kernel for your notebook.
   - If a notebook is running, you will see a circle indicator (⚫️ means idle, 🔵 means busy).

In the upcoming sessions, we will explore each of these areas and learn how to navigate the interface efficiently. Don’t worry if it seems overwhelming at first; you will get familiar with it quickly as we go along.

## Create Your Own Jupyter Notebook

Now it’s time to create your own Jupyter Notebook. Follow these steps:

1. Navigate to the appropriate folder using the **File Browser** on the left sidebar.
2. Open the **Launcher** by clicking on the "+" symbol in the main work area or from the top menu (File > New Launcher).
3. Under the **Notebook** section, click on the appropriate kernel, which in this case is "EuBi Course."

To enable tab completion for file paths, it's a good idea to save your notebook early on. You can give it any name you prefer. For example, you could name it `test-book.ipynb`.

Once saved, you are ready to start working in your own Jupyter Notebook!

## Exercise: Understanding Jupyter Cell Types

In Jupyter notebooks, there are two primary cell types: **Code Cells** and **Markdown Cells**. In this exercise, we will create one of each.

### Step 1: Create a Code Cell

1. In your notebook, ensure the current cell is a **code cell** (the default).
2. In this cell, type a simple arithmetic operation. For example:

    ```python
    # This is a code cell
    5 + 7
    ```

3. Run the cell by pressing `Ctrl + Enter`.

You should see the result of the operation, `12`, displayed below the cell.

### Step 2: Create a Markdown Cell

1. Now, create a new cell by clicking the `+` button on the toolbar or by pressing `B` (with the current cell selected).
2. Change this new cell type to **Markdown** by either:
   - Clicking on the dropdown in the toolbar (it says "Code" by default) and selecting "Markdown."
   - Pressing `M` while the cell is selected. (`Y`: selects for "code", `M`: selects for "Markdown")

3. In this markdown cell, type a heading and some formatted text. For example:

    ```markdown
    # This is a Markdown Cell

    You can write text in **bold**, *italic*, and create lists:
    
    - Item 1
    - Item 2
    - Item 3
    ```

4. Run the markdown cell by pressing `Ctrl + Enter`.

You should now see a nicely formatted heading and list.

### Recap

- **Code Cells**: Used for writing and executing code (e.g., Python).
- **Markdown Cells**: Used for writing formatted text, explanations, and documentation.

Try switching between code and markdown cells in your notebook to get familiar with both!


## Exercise: Hello World and Basic Programming Concepts

In this exercise, we will learn the basics of variables, strings, and print statements in Python. We'll also practice running and rerunning cells in Jupyter to see how the output changes dynamically.

### Step 1: Create a Hello World Program

1. In a new **code cell**, type the following code to print "Hello, World!":

    ```python
    # This is a code cell
    print("Hello, World!")
    ```

2. Run the cell by pressing `Shift + Enter`.

   - When you press `Shift + Enter`, it will execute the current cell and automatically create a new cell below it. This is a quick way to run code and immediately continue working.
   - You should see the text `Hello, World!` displayed below the cell as the output.

### Step 2: Understanding Variables and Strings

1. In the next **code cell**, create a variable to store the string "World" and print it. Type the following:

    ```python
    # Assigning a string to a variable
    message = "World"
    print("Hello,", message)
    ```

2. Run the cell by pressing `Shift + Enter`. The output should now be:

    ```
    Hello, World
    ```

3. Variables store values that can be used later in the program. In this case, `message` stores the string `"World"` and is used in the `print` statement.

### Step 3: Dynamic Programming – Modifying and Rerunning Cells

1. Change the value of the `message` variable to a different string. For example:

    ```python
    message = "Jupyter"
    print("Hello,", message)
    ```

2. Rerun the cell by pressing `Shift + Enter`. You should now see:

    ```
    Hello, Jupyter
    ```

3. This demonstrates how you can change the contents of a cell and rerun it to see the new output.

### Step 4: String Concatenation in the print() Statement

1. In Python, you can combine (or concatenate) strings together in a `print()` statement. Let’s see an example. In a new code cell, type:

    ```python
    greeting = "Hello"
    subject = "Jupyter"
    print(greeting + " " + subject + "!")
    ```

2. Run the cell by pressing `Shift + Enter`.

    The output should display:

    ```
    Hello Jupyter!
    ```

3. Here’s what is happening:
   - The `+` symbol is used to concatenate (combine) multiple strings together.
   - We are combining the string stored in `greeting` with a space `" "` and then the string stored in `subject`, followed by an exclamation mark `"!"`.
   - This method of combining strings is useful when you want to dynamically build strings using variables.

### Recap

- **Variables**: Store values like strings, numbers, etc., and can be reused in the program.
- **Strings**: Text enclosed in quotes (e.g., `"Hello, World!"`).
- **String Concatenation**: The process of combining strings using the `+` symbol.
- **print()**: A function used to display output in Python.
- **Running Cells**: You can run a cell by pressing `Shift + Enter`. This executes the code and creates a new cell below for continued work. Changing and rerunning cells shows dynamic behavior.

Feel free to experiment by changing the variables and running the cells again!


## Exercise: Arithmetic, Variables, NumPy, and Formatted Strings

In this exercise, we will explore:
- Simple arithmetic operations
- Checking variable types
- Introduction to `f-strings`
- Using NumPy to calculate the mean and standard deviation of a one-dimensional array (vector)
- Using `f-strings` to print formatted messages

### Step 1: Simple Arithmetic and Checking Variable Types

1. Create a new **code cell** and type the following code to perform some basic arithmetic and check variable types:

    ```python
    # Basic arithmetic
    a = 10
    b = 3
    
    # Performing arithmetic operations
    addition = a + b
    subtraction = a - b
    multiplication = a * b
    division = a / b  # This will result in a float

    # Checking variable types
    print(type(addition))      # Check the type of 'addition'
    print(type(division))      # Check the type of 'division'
    ```

2. Run the cell using `Shift + Enter`.

    You should see the types of the results printed below the cell. The output should show:
    
    ```
    <class 'int'>
    <class 'float'>
    ```

    - `addition` is of type `int` because it results from adding two integers.
    - `division` is of type `float` because division always returns a floating-point number in Python.

### Step 2: Introduction to `f-Strings`

1. Next, let’s introduce `f-strings`. An `f-string` allows you to embed expressions inside string literals, using curly braces `{}`.

2. Modify the previous cell to print the results using an `f-string`:

    ```python
    # Using f-strings to format the output
    print(f"Addition: {addition}")
    print(f"Division: {division}")
    ```

3. Run the cell again. You should now see the formatted output:

    ```
    Addition: 13
    Division: 3.3333333333333335
    ```

   - The `f` before the string allows you to embed variables directly into the string by placing them inside curly braces `{}`.
   - This is a convenient way to format output in Python.

### Step 3: Variables with Integers and Floats

1. Now, let’s further explore variables with different types. Create a new code cell and add the following:

    ```python
    # Integer variable
    int_var = 5

    # Float variable
    float_var = 5.0

    # Print their types
    print(f"The type of int_var is: {type(int_var)}")
    print(f"The type of float_var is: {type(float_var)}")
    ```

2. Run the cell. The output will show:

    ```
    The type of int_var is: <class 'int'>
    The type of float_var is: <class 'float'>
    ```

### Step 4: Using NumPy for Mean and Standard Deviation

1. First, ensure you have NumPy available by importing it in a new **code cell**:

    ```python
    # Import NumPy
    import numpy as np
    ```

2. Create a one-dimensional NumPy array (vector) and calculate the mean and standard deviation:

    ```python
    # Creating a 1D array (vector)
    data = np.array([10, 12, 23, 23, 16, 25, 30, 18])

    # Calculate mean and standard deviation
    mean_val = np.mean(data)
    std_val = np.std(data)

    print(f"Mean: {mean_val}")
    print(f"Standard Deviation: {std_val}")
    ```

3. Run the cell to see the mean and standard deviation printed.

### Step 5: Using f-Strings for Formatted Output

1. Now, let’s use `f-strings` to display the mean and standard deviation in a formatted message. In a new **code cell**, type the following:

    ```python
    # Print a formatted message using f-strings
    print(f"The mean value is {mean_val:.2f} ± {std_val:.2f}")
    ```

2. Run the cell. The output should display the mean and standard deviation rounded to two decimal places, in the format:

    ```
    The mean value is 19.63 ± 6.37
    ```

### Recap

- **Arithmetic Operations**: You learned basic arithmetic like addition, subtraction, multiplication, and division.
- **Checking Variable Types**: Use `print(type(variable))` to check whether a variable is an integer, float, etc.
- **f-Strings**: Formatted strings allow you to insert variables into strings for clear output.
- **NumPy**: We used NumPy to calculate the mean and standard deviation of a one-dimensional array (vector).

Feel free to experiment by changing the array values and rerunning the cells to see how the mean and standard deviation change!


## Exercise: Handling File Paths, Reading Images, and Plotting with Matplotlib

In this exercise, we will:
1. Introduce how to handle file paths using `Path` from the `pathlib` module.
2. Use `skimage.io` to read an image into a NumPy array.
3. Visualize the image using `matplotlib`.

### Step 1: Handling File Paths with `Path`

In Python, it's important to handle file paths correctly, especially when working with different operating systems. The `Path` class from the `pathlib` module provides an easy way to handle file system paths.

1. Create a new **code cell** and type the following:

    ```python
    # Import Path from pathlib
    from pathlib import Path

    # Define the path to the image file
    tif_path = Path("./data/blobs.tif")

    # Check if the file exists at the given path
    print(tif_path.exists())
    ```

2. Run the cell using `Shift + Enter`.

    If the image file exists at the specified path, it will return `True`. Otherwise, it will return `False`. If the file doesn’t exist, make sure to adjust the path to the correct location.

### Step 2: Reading Images Using `skimage.io`

Now that we’ve handled the file path, let’s read the image file into a NumPy array using `skimage.io`.

1. Create a new **code cell** and type the following code to read the image:

    ```python
    # Import skimage.io to read the image
    import skimage.io as skio

    # Read the image using imread() function
    img = skio.imread(tif_path)

    # Check the shape of the image (height, width)
    print(f"The image has shape: {img.shape}")
    ```

2. Run the cell.

    You should see the shape of the image printed below the cell, for example:

    ```
    The image has shape: (254, 256)
    ```

   - The `imread()` function reads the image into a NumPy array (also known as a matrix).
   - The shape tells us the dimensions of the image, where the first value is the height and the second is the width.

### Step 3: Visualizing the Image with `matplotlib`

Now that we have loaded the image into a NumPy array, let's visualize it using `matplotlib`.

1. Create a new **code cell** and type the following code:

    ```python
    # Import matplotlib.pyplot for plotting
    import matplotlib.pyplot as plt

    # Plot the image using imshow()
    plt.imshow(img, cmap="gray")

    # Add a title to the plot
    plt.title("Image Visualization")

    # Show the plot
    plt.show()
    ```

2. Run the cell.

    You should see a grayscale image of the array displayed in the output.

   - `imshow()` displays the image, and `cmap="gray"` ensures it is shown in grayscale.
   - `plt.show()` is used to render the plot.



### Step 4: Recap

- **Path Handling**: We used `Path` from the `pathlib` module to handle file paths and check if the file exists.
- **Reading Images**: The `skimage.io.imread()` function was used to read the image into a NumPy array, which represents the image as a matrix of pixel values.
- **Visualizing Images**: We used `matplotlib` to visualize the image with `plt.imshow()` and set the colormap to grayscale.

Feel free to experiment by using different images and paths to see how the process works with various file formats!


## Exercise: Calculating Parameters from an Image

In this exercise, we will:
1. Calculate basic parameters from an image, such as the number of pixels, minimum, maximum, and mean intensity values.
2. Check the data type of the image using NumPy.
3. Print the results using `f-strings`.

### Step 1: Load the Image

1. First, let’s load the image file into a NumPy array using `skimage.io`. Create a new **code cell** and type the following:

    ```python
    # Import Path from pathlib and skimage.io for image reading
    from pathlib import Path
    import skimage.io as skio
    import matplotlib.pyplot as plt

    # Define the path to the image file
    cell_path = Path("./data/public-repos/AC16_Rep1_18d24h_HNRNPC488_NUP594_04_SIR_THR_ALN-1_c-3.tif")

    # Read the image
    img = skio.imread(cell_path, plugin="tifffile")

    # Display the image using matplotlib
    plt.imshow(img, cmap="gray")
    plt.title("Cell Image")
    plt.show()
    ```

2. Run the cell to visualize the image.

### Step 2: Calculate the Number of Pixels

1. Next, calculate the total number of pixels in the image using the `.size` attribute of the NumPy array.

    ```python
    # Calculate the number of pixels in the image
    num_pixels = img.size
    print(f"the sape of the iamge is: {img.shape}")
    print(f"Total number of pixels: {num_pixels}")
    ```

2. Run the cell. This will print the total number of pixels in the image.

### Step 3: Calculate Min, Max, and Mean Intensity Values

1. In a new **code cell**, calculate the minimum, maximum, and mean intensity values of the image using NumPy functions:

    ```python
    # Calculate minimum, maximum, and mean intensity values
    min_val = img.min()
    max_val = img.max()
    mean_val = img.mean()

    # Print the results using f-strings
    print(f"Minimum intensity: {min_val}")
    print(f"Maximum intensity: {max_val}")
    print(f"Mean intensity: {mean_val:.2f}")
    ```

2. Run the cell. You will see the intensity statistics printed:

    ```
    Minimum intensity: <min_val>
    Maximum intensity: <max_val>
    Mean intensity: <mean_val>
    ```

    - The `mean_val` is rounded to two decimal places using `.2f` for better readability.

### Step 4: Determine the Data Type of the Image

1. The image data is stored as a NumPy array, and each pixel has a specific data type. To check the data type of the array, use the `.dtype` attribute.

    ```python
    # Check the data type of the image
    dtype = img.dtype
    print(f"Data type of the image: {dtype}")
    ```

2. Run the cell. You will see the data type of the image printed (for example, `uint16` for unsigned 16-bit integers).

### Step 5: Recap

- **Number of Pixels**: The `.size` attribute of a NumPy array gives the total number of elements (pixels) in the array.
- **Min, Max, Mean Intensity**: The `.min()`, `.max()`, and `.mean()` functions provide basic statistical measures of the image pixel intensities.
- **Data Type**: The `.dtype` attribute shows the data type of the array, such as `uint8` or `uint16`.
- **f-Strings**: Used to format output, including variables, into strings for clear reporting of results.

Feel free to experiment by loading different images and calculating their parameters!

## Exercise: Extracting Information from File Names and Storing in a DataFrame

In this exercise, you will:
1. Iterate over a list of `.tif` files and filter them based on channel information (`c_info`) or time information (`time_info`).
2. Create a function to extract the `c_info` (channel) and `time_info` (time under insult) from the file name using simple `if-elif` statements.
3. Store the file paths and the extracted information in a `pandas` DataFrame for further analysis.


### Step 1: Iterating Over Files and Filtering Based on `c_info` or `time_info`

1. **Iterate over the files in a folder** and filter only the files that:
   - Have a `.tif` extension.
   - Start with a specific channel (e.g., `C1`) or contain specific time information (e.g., `37d`).

   ```python
   from pathlib import Path

   # Define the path to the data folder
   data_folder = Path("./data/public-repos/")

   # List comprehension to iterate over files and check for .tif extension
   tif_files = [file for file in data_folder.iterdir() if file.suffix == '.tif']

   # Print all .tif file names
   for tif_file in tif_files:
       print(tif_file.name)

   # Now filter the files by channel (e.g., C1) or time (e.g., 37d)
   c1_files = [file for file in tif_files if file.name.startswith("C1")]
   time_37d_files = [file for file in tif_files if "37d" in file.name]

   # Print the filtered file names
   print("\nFiltered by channel (C1):")
   for file in c1_files:
       print(file.name)

   print("\nFiltered by time (37d):")
   for file in time_37d_files:
       print(file.name)


### Step 2: Creating a Function to Extract c_info and time_info
1. **Create a function that will extract the c_info and time_info from the file name using if-elif statements.**

    ```python
    def get_tif_info(file_path):
        # Ensure the file is a .tif file
        assert file_path.suffix == '.tif', 'File must be a .tif image'

        # Extract the channel info (C1, C2, C3)
        if file_path.name.startswith("C1"):
            c_info = "C1"
        elif file_path.name.startswith("C2"):
            c_info = "C2"
        elif file_path.name.startswith("C3"):
            c_info = "C3"
        else:
            c_info = "Unknown"

        # Extract the time info (37d, 28d24h, 18d24h)
        if "37d" in file_path.name:
            time_info = "37d"
        elif "28d24h" in file_path.name:
            time_info = "28d24h"
        elif "18d24h" in file_path.name:
            time_info = "18d24h"
        else:
            time_info = "Unknown"

        return c_info, time_info
    # Example usage of the function
    file_path = Path("./data/public-repos/C1-AC16_Rep1_37d_HNRNPC488_NUP594_09_SIR_THR_ALN-1_c.tif")
    c_info, time_info = get_tif_info(file_path)
    print(f"Channel: {c_info}, Time: {time_info}")
    ```
    
Test the function on a few files to ensure it works as expected.

### Step 3: Storing the Information in a pandas DataFrame
1. Now that you have the c_info and time_info extracted for each file, create a pandas DataFrame to store this information along with the file path.

    ```python
    import pandas as pd

    # Create a list to store the data
    data = []

    # Iterate over all .tif files and extract info
    for file in tif_files:
        c_info, time_info = get_tif_info(file)
        # Append the information as a dictionary to the list
        data.append({"file_path": file, "c_info": c_info, "time_info": time_info})

    # Create a pandas DataFrame from the list of dictionaries
    df = pd.DataFrame(data)

    # Display the DataFrame
    print(df)
    ```

2. The DataFrame will contain the following columns:

    * file_path: The full path to the file.
    * c_info: The channel information (C1, C2, C3).
    * time_info: The time under insult (37d, 28d24h, 18d24h).

### Step 4: Recap
- **Iteration:** You used Path.iterdir() and list comprehensions to iterate over files in a folder and filter them by channel and time.
- **Function:** You created a simple function to extract c_info and time_info from the file name.
- **DataFrame:** You used pandas to store the extracted information in a DataFrame, which can be used for further analysis.


# Return to main course page
https://github.com/CCI-GU-Sweden/eRImote-python-BIAS-Gtb
