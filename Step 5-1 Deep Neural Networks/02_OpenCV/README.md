# OpenCV with Python
***

## **Introduction**

OpenCV is an open source library which is supported by multiple platforms including Windows, Linux, and MacOS, and is available for use in multiple other languages as well; however, it is most commonly used in Python for Machine Learning applications, specifically in the Computer Vision domain.


Apart from its cross-platform support and availability in multiple other computer languages, which allows applications developed in it to be used on different systems, OpenCV is also, in comparison to other such libraries, fairly efficient in terms of computations, as it uses vector operations for most of its functions.

## **Installation**
**Note**: Since we are going to use OpenCV in the Python language, it is an implicit requirement that you already have Python (version 3) installed on your workstation. Depending upon your OS, execute one of the following commands to install OpenCV library on your system:


**Windows**

```
$ pip install opencv-python
```


**MacOS**

```
$brew install opencv3 --with-contrib --with-python3
```

**Linux**

```
$ sudo apt-get install libopencv-dev python-opencv
```

To check if your installation was successful or not, run the following command in either a Python shell, or your command prompt/ terminal:

```
import cv2
```

If you do not get an error on importing `cv2` then it was installed correctly.


## **Basic Image Operations**
Now that we have installed OpenCV on our workstations, let's get our hands dirty with some of the functionalities that OpenCV offers.

## **Display an Image**
Displaying an image using OpenCV is a two-step process; first, we have to load it, and then we can display it. Both operations are done in sequence using different functions.

To display an image, we need to know two things:

1.   Image Path (both absolute and relative paths work)
2.   Read Mode (read, write, etc.)

The function we'll use for reading/loading an image is **`cv2.imread()`**, which has two variations. First one is **`IMREAD_GRAYSCALE`**, which as the name suggests, converts the image to grayscale before reading it. The second one is **`IMREAD_UNCHANGED`**, which loads the image without cutting out the alpha channel. The default is **`IMREAD_COLOR`**, which simply reads the colored image using the RGB channels only.

Let's code an example:

```
import cv2
my_bike = cv2.imread('bike.png')
```

This will load the image of a bike from the file system and store it in the my_bike variable for further operations.

Let's now display the image we just read. It can be done by the **`cv2.imshow()`** function.

```
cv2.imshow('my_bike', my_bike)
```

The first parameter to the **`imshow()`** function is the string name that you want to display on the image window. The second parameter is the image handler we created using the **`cv2.imread()`** function.

The **`waitKey`** command will wait for you to press a key before it moves on to the next command. This is useful so that the program will continue to display your image until a key is pressed, otherwise it will be displayed for a split second and then quickly disappear once the program has stopped executing.

## **Arithmetic Operations on Images**

Arithmetic operations on images refer to adding, subtracting, multiplying, or dividing multiple images to generate a new image which is an arithmetic combination of the input images. Image arithmetics has a lot of applications, like adding a watermark to an image, creating a blended combination of two images, applying different types of image filters, etc.

While there are many operations you can perform, we will only be showing two examples here, as this will then allow you to apply the concept to other arithmetic operations available in OpenCV. The first example will be the addition of two images, and the second example will be blending two images.

Let's code these two examples:

## **Adding Images**

```
import cv2

# Read in the two images
image_1 = cv2.imread('bike.jpg')
image_2 = cv2.imread('car.jpg')

# Sum the two image arrays for all channels
result = cv2.add(image_1, image_2)

cv2.imshow('result', result)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

The **`waitKey`** command will wait for you to press a key before it moves on to the next command. This is useful so that the program will continue to display your image until a key is pressed, otherwise it will be displayed for a split second and then quickly disappear once the program has stopped executing.

## **Blending Images**

Blending images is similar to image addition, except each image's contribution to the new resulting image can be controlled. Basically, if we want one image to be more focused, and the other one to be more faint when they get merged, we will go with blending, instead of simple addition.

Images are added as per the equation below:

```
g(x) = (1 - a)f(x) + af1(x)
```

Lets code it to clarify further:

```
import cv2

# Read in the two images
image_1 = cv2.imread('bike.jpg')
image_2 = cv2.imread('car.jpg')

result = cv2.addWeighted(image_1, 0.9, image_2, 0.1)

cv2.imshow('result', result)
cv2.waitKey(0)        # Wait for the user to press a key before continuing
cv2.destroyAllWindows()

```

The sum of the weights given to the addWeighted function should be equal to 1.0. You can also give a scalar value at the end, which would be added to all the pixel values of the resultant image.

## **Image Smoothing**

Image smoothing is a very helpful feature, which is mostly performed before the images are passed on to a machine learning model. It is mostly done to remove noise/high-frequency elements from images by passing the image through a low-pass filter. There are many filters, including box filter (averaging filter), median filter, mode filter, Gaussian filter, and many more; however, to understand image smoothing and how to do it using OpenCV, we will only cover the box filter.

Let's say you have an image of 10x10, and you want to pass it through a 3x3 box/averaging filter, how would you do it?

You'll start with the top left of the image, place your 3x3 filter there, and replace the central element with the average of all 9 elements. This was the first step, now you will move your filter one step to the right, and repeat the same process until you have covered the whole image. An example of 10x10 image, and 3x3 averaging filter are shown below for your reference:

<br>
<img src="https://i.imgur.com/I96ztFo.png"> <br>

Now that we have discussed how it works, lets try and see how we can apply different filters on our image using OpenCV; please read the comments thoroughly to know which line of code is used for which filter:

```
import cv2

# Load the original image
original_image = cv2.imread('my_bike.png')

# Filter by passing image through 3x3 averaging filter
average_image = cv2.blur(original_image,(3,3))

# Apply 3x3 gaussian filter on the original image
gaussian_image = cv2.GaussianBlur((original_image,(3,3),0))

# Apply 3x3 median filter on the original image
median_image = cv2.medianBlur(original_image,3)
```

Note: You can view the resulting images by using the following additional code:

```
import matplotlib.pyplot as plt

plt.imshow(average_image)
plt.show()
```

<br>

## **Image Transformations**
Image transformation is the last, but one of the most important topics that we are going to cover with OpenCV. It has a lot of applications, but one of the most common ones nowadays is in Machine Learning for Data Augmentation, i.e. when you have a shortage of dataset, you augment/transform the currently available images to make them different from your existing dataset. This effectively increases your dataset size and might help in improving your model accuracy.

The list of possible transformations is a long one, including scaling, affine, rotation, translation, etc. We will only cover two of them using OpenCV to get a general idea; however, OpenCV provides supporting functions for a wide range of them. Let's start with scaling.



## **Scaling**
To put it in simple words, scaling is basically just resizing your image, i.e. either making it bigger or smaller. **`resize`** is the function used for scaling the images in OpenCV. Resizing has three types: **`INTER_CUBIC`**, **`INTER_LINEAR`**, and **`INTER_AREA`**. Let's code an example using these functions for scaling; please read through the code, comments, and descriptions carefully as they will explain what exactly is going on in the code:

```
import cv2
import numpy as np
import matplotlib.pyplot as plt

image = cv2.imread('my_bike.jpg')

# Scale up/expand both width and height by factor of 2
result_1 = cv2.resize(image, None, fx=2, fy=2, interpolation=cv2.INTER_CUBIC)

# Scale down/shrink both width and height by factor of 2
result_2 = cv2.resize(image, None, fx=2, fy=2, interpolation=cv2.INTER_AREA)

# Display the resulting images
plt.imshow(result_1)
plt.imshow(result_2)
plt.show()
```

Here in the **`resize`** function, the **`fx`** parameter in represents the scale factor for width, **fy** represents the scale factor height, and **`interpolation`** specifies the function to be used for scaling (shrinking or expansion).

## **Rotation**

Rotation allows us to move an image about the axis for a certain specified angle.

Before we learn how to rotate our images using code, we should know that there is a **`rotation matrix`** that is used for performing this transformation; we will not go in details of that, as OpenCV makes it very simple for us to calculate that matrix using a single function call. You will see that in the code below:

```
import cv2
import matplotlib.pyplot as plt

# Load the image of a bike
image = cv2.imread('my_bike.jpg',0)

# Rows and columns
r, c = image.shape

matrix = cv2.getRotationMatrix2D((cols/2,rows/2), 180, 1)
result = cv2.warpAffine(image,matrix,(c,r))

# Display resulting rotation
plt.imshow(result)
plt.show()
```

In the **`getRotationMatrix2D`** function, 180 specifies the degree by which the image should be rotated, 1 is the scaling factor, the function call would return the rotation matrix in the **`matrix`** variable.

The **warpAffine** function call uses the matrix we calculated from the previous method to rotate the image according to our specifications.

<br>

## Image Filters

Image filters are used to reduce the amount of noise in an image and to enhance the edges in an image. There are two types of noise that can be present in an image: **`speckle noise`** and **`salt-and-pepper noise`**. **`Speck noise`** is the noise that occurs during image acquisition **`while salt-and-pepper noise`** (which refers to sparsely occurring white and black pixels) is caused by sudden disturbances in an image signal. Enhancing the edges of an image can help a model detect the features of an image.

For Python, the **Open-CV** and **PIL packages** allow you to apply several digital filters. Applying a digital filter involves taking the convolution of an image with a kernel (a small matrix). A kernal is an n x n square matrix were n is an odd number. 

### 1. Mean Filter

The mean filter is used to blur an image in order to remove noise. It involves determining the mean of the pixel values within a n x n kernel. The pixel intensity of the center element is then replaced by the mean. This eliminates some of the noise in the image and smooths the edges of the image. The blur function from the Open-CV library can be used to apply a mean filter to an image.

When dealing with color images it is first necessary to convert from RGB to HSV (hue, saturation, value, also known as HSB or hue, saturation, brightness) since the dimensions of RGB are dependent on one another where as the three dimensions in HSV are independent of one another (this allows us to apply filters to each of the three dimensions separately.)

The following is a python implementation of a mean filter:

```

import numpy as np
import cv2
from matplotlib import pyplot as plt
from PIL import Image, ImageFilter
%matplotlib inline

image = cv2.imread('Trump.JPG') # reads the image
image = cv2.cvtColor(image, cv2.COLOR_BGR2HSV) # convert to HSV
 
new_image = cv2.blur(image,(9, 9)) # 9*9 the dimension of the x and y axis of the kernal.

plt.figure(figsize=(11,6))

plt.subplot(121), plt.imshow(cv2.cvtColor(image, cv2.COLOR_HSV2RGB)),plt.title('Original')
plt.xticks([]), plt.yticks([])

plt.subplot(122), plt.imshow(cv2.cvtColor(new_image, cv2.COLOR_HSV2RGB)),plt.title('Mean filter')
plt.xticks([]), plt.yticks([])
plt.show()

```

### 2. Gaussian Filter
The Gaussian Filter is similar to the mean filter however it involves a weighted average of the surrounding pixels and has a parameter sigma. The kernel represents a discrete approximation of a Gaussian distribution. While the Gaussian filter blurs the edges of an image (like the mean filter) it does a better job of preserving edges than a similarly sized mean filter. 

The `GaussianBlur` function from the `Open-CV` package can be used to implement a Gaussian filter. The function allows you to specify the shape of the kernel. You can also specify the the standard deviation for the x and y directions separately. If only one sigma value is specified then it is considered the sigma value for both the x and y directions.

```
#Gaussian Filter
new_image = cv2.GaussianBlur(image, (9, 9),0)
plt.figure(figsize=(11,6))

plt.subplot(121), plt.imshow(cv2.cvtColor(image, cv2.COLOR_HSV2RGB)),plt.title('Original')
plt.xticks([]), plt.yticks([])

plt.subplot(122), plt.imshow(cv2.cvtColor(new_image, cv2.COLOR_HSV2RGB)),plt.title('Gaussian Filter')
plt.xticks([]), plt.yticks([])
plt.show()
```

### 3. Median Filter

The median filter calculates the median of the pixel intensities that surround the center pixel in a n x n kernel. The median then replaces the pixel intensity of the center pixel. The median filter does a better job of removing **salt and pepper noise** than the mean and Gaussian filters. The median filter preserves the edges of an image but it does not deal with speckle noise. 

The `medianBlur` function from the `Open-CV` library can be used to implement a median filter.

```
new_image = cv2.medianBlur(image, 9)
plt.figure(figsize=(11,6))
plt.subplot(121), plt.imshow(cv2.cvtColor(image, cv2.COLOR_HSV2RGB)),plt.title('Original')
plt.xticks([]), plt.yticks([])
plt.subplot(122), plt.imshow(cv2.cvtColor(new_image, cv2.COLOR_HSV2RGB)),plt.title('Median Filter')
plt.xticks([]), plt.yticks([])
plt.show()
```
#### 4. Laplacian Filter
The Laplacian of an image highlights the areas of rapid changes in intensity and can thus be used for edge detection. If we let `I(x,y)` represent the intensities of an image then the Laplacian of the image is given by the following formula:

$$L(x,y) = \frac{\partial^2 I}{\partial x^2} + \frac{\partial^2 I}{\partial y^2} $$

The discrete approximation of the Laplacian at a specific pixel can be determined by taking the weighted mean of the pixel intensities in a small neighborhood of the pixel. The following figure shows two kernels which represent two different ways of approximating the Laplacian.

<img src="https://i.imgur.com/R0U8Z0W.png" width="400" class="left"> <br>

Since the Laplacian filter detects the edges of an image it can be used along with a Gaussian filter in order to first remove speckle noise and then to highlight the edges of an image. This method is referred to as the Lapalcian of Gaussian filtering. 

The `Laplacian` function from the `Open-CV` library can be used to find the Laplacian of an image.

```

new_image = cv2.Laplacian(image2,cv2.CV_64F)

plt.figure(figsize=(11,6))
plt.subplot(131), plt.imshow(image2, cmap='gray'),plt.title('Original')
plt.xticks([]), plt.yticks([])

plt.subplot(132), plt.imshow(new_image, cmap='gray'),plt.title('Laplacian')
plt.xticks([]), plt.yticks([])

plt.show()

```
### 5. Unsharp Filter

The `Unsharp filter` can be used to enhance the edges of an image. The `ImageFilter.Unsharpmask` function from the PIL package applys an unsharp filter to an image (the image first needs to be converted to a PIL Image object.) `The ImageFilter.Unsharpmask` function has three parameters. The `radius` parameter specifies how many neighboring pixels around edges get affected. The `percentage` parameter specifies how much darker or lighter the edges become. The third parameter `threshold` defines how far apart adjacent tonal values have to be before the filter does anything.

```
image2 = Image.fromarray(image2.astype('uint8'))
new_image = image2.filter(ImageFilter.UnsharpMask(radius=2, percent=150))

plt.figure(figsize=(11,6))
plt.subplot(121),plt.imshow(image2, cmap = 'gray')
plt.title('Input Image'), plt.xticks([]), plt.yticks([])
plt.subplot(122),plt.imshow(new_image, cmap = 'gray')
plt.title('Unsharp Filter'), plt.xticks([]), plt.yticks([])
plt.show()
```

There is always a trade off between removing noise and preserving the edges of an image. In order to remove the `speckle noise` in an image a blurring filter needs to be applied which in turn blurs the edges of the image. If you want to retain the edges of an image the only noise that you can remove is the `salt-and-pepper noise`.


OpenCV is a library available in multiple languages and is mostly used in conjunction with NumPy, SciPy and Matplotlib, as we saw in some of the examples above, as well. Some of its functions are the same as in Matlab, and it also supports vectorized operations, hence increasing computational efficiency.
