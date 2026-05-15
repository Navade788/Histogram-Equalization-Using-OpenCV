# Histogram Equalization Using OpenCV (Grayscale & Color Images)

---

## Aim

To write a Python program using OpenCV to perform histogram equalization on both grayscale and color images to enhance image contrast and brightness.

The program performs the following operations:

- Read and display a grayscale image  
- Plot histogram of the grayscale image  
- Apply histogram equalization on grayscale image  
- Read and display a color image  
- Plot histogram of B, G, R channels  
- Convert image to HSV color space  
- Apply histogram equalization on the Value (V) channel  
- Convert the enhanced image back to BGR format  
- Display original and enhanced images with histograms  

---

## Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  
- NumPy  
- Matplotlib  

---

## Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the image `parrot.jpg` in grayscale format.

### Step 3:
Display the grayscale image and plot its histogram.

### Step 4:
Apply histogram equalization using `cv2.equalizeHist()` to enhance contrast.

### Step 5:
Display original grayscale image, its histogram, enhanced image, and its histogram using a 2 × 2 grid.

### Step 6:
Read the same image in color format.

### Step 7:
Split the image into B, G, R channels and plot their histograms.

### Step 8:
Convert the image from BGR to HSV color space.

### Step 9:
Apply histogram equalization on the V (Value) channel.

### Step 10:
Merge the channels and convert the image back to BGR format.

### Step 11:
Display original color image, histogram, enhanced image, and enhanced histogram using a 2 × 2 grid.

---

## Program

### Developed By:
**Name:** S.NAVADEEP  

### Register No: 212224230180
____________________________  

### Import required libraries
```
import cv2
import numpy as np
import matplotlib.pyplot as plt
```
### Read the image in grayscale format
```
img=cv2.imread("parrot.jpg",0)
```
### Display the grayscale image.
```
plt.imshow(img,cmap='gray')
plt.title("Gray Scale Image")
plt.axis("off")
```
### Plot the histogram of the grayscale image
```
plt.hist(img.ravel(),256,range=[0,256])
plt.title("Original Image")
plt.show()
```
### Perform histogram equalization
```
eq_hist=cv2.equalizeHist(img)
```
### Display [1] the Original Image (Gray Image) and its Histogram, and [2] the Enhanced Image and its Histogram using a 2×2 layout in Matplotlib.
```
plt.figure(figsize=(10,8))

plt.subplot(2,2,1)
plt.imshow(img,cmap='gray')
plt.title("Original Image")
plt.axis("off")

plt.subplot(2,2,2)
plt.hist(img.ravel(),256,range=[0,256])
plt.title("Original Histogram")

plt.subplot(2,2,3)
plt.imshow(eq_hist,cmap='gray')
plt.title("Equalized Image")
plt.axis("off")

plt.subplot(2,2,4)
plt.hist(eq_hist.ravel(),256,range=[0,256])
plt.title("Equalized Histogram")

plt.show()
```
### Read the colorgiven parrot.jpg image.
```
img_clr=plt.imread("parrot.jpg")
plt.imshow(img_clr[:,:,::-1])
plt.title("Original Colour Image")
plt.axis("off")
plt.show()
```
### Plot the histogram of colour image
```
color = ('b','g','r')

for i,col in enumerate(color):
    hist = cv2.calcHist([img_clr],[i],None,[256],[0,256])
    plt.plot(hist,color=col)

plt.title("Histogram of Original Image")
plt.xlabel("Pixel Intensity")
plt.ylabel("Frequency")
plt.show()
```
### Convert to HSV.
```
hsv_img = cv2.cvtColor(img_clr, cv2.COLOR_BGR2HSV)
plt.imshow(hsv_img)
```
### Perform histogram equalization
```
h,s,v = cv2.split(hsv_img)
v_eq = cv2.equalizeHist(v)
```
### Convert back to BGR format
```
hsv_eq = cv2.merge((h,s,v_eq))
enh_img = cv2.cvtColor(hsv_eq, cv2.COLOR_HSV2BGR)
```
### Display
```
plt.figure(figsize=(10,8))


# Original Image

plt.subplot(2,2,1)
plt.imshow(img_clr[:,:,::-1])
plt.title("Original Image")
plt.axis("off")


# Original Histogram

plt.subplot(2,2,2)
plt.hist(img_clr.ravel(),256,[0,256])
plt.title("Original Histogram")

# Enhanced Image
plt.subplot(2,2,3)
plt.imshow(enh_img[:,:,::-1])
plt.title("Enhanced Image")
plt.axis("off")

# Enhanced Histogram
plt.subplot(2,2,4)
plt.hist(enh_img.ravel(),256,[0,256])
plt.title("Enhanced Histogram")

plt.show()
```
##  Output

### Grayscale Histogram Equalization

- Original grayscale image is displayed  
- Histogram of original grayscale image is plotted  
- Enhanced image after histogram equalization is displayed  
- Histogram of enhanced grayscale image shows improved contrast  

### Color Image Histogram Equalization

- Original color image is displayed  
- Histogram of B, G, R channels is plotted  
- Enhanced image after HSV-based equalization is displayed  
- Histogram of enhanced image shows better intensity distribution  

---

## Result

Thus, histogram equalization is successfully performed on both grayscale and color images using OpenCV. The contrast and brightness of the images are significantly improved, enhancing visual quality and feature visibility.
