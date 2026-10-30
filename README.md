# Ex. No: 03 Histogram Processing
# NAME : Alageshwari V
# REG NO : 212224240010

## Aim

To perform histogram equalization on grayscale and color images using OpenCV and Matplotlib to improve the contrast and visual clarity of the images.


## Procedure

### **Part 1: Histogram Equalization for Grayscale Images**

1. **Import Libraries:** Import the necessary libraries (`cv2`, `numpy`, and `matplotlib.pyplot`).
2. **Load the Image:** Read the input image in grayscale mode (`cv2.IMREAD_GRAYSCALE`).
3. **Display Original Image:** Plot and display the original grayscale image using `plt.imshow()`.
4. **Plot Original Histogram:** Compute and plot the pixel intensity distribution (histogram) of the original grayscale image using `plt.hist()`.
5. **Apply Equalization:** Enhance the contrast of the grayscale image using OpenCV's histogram equalization function (`cv2.equalizeHist()`).
6. **Display Equalized Results:** Plot the histogram and display the equalized image to observe the improvement in contrast.

### **Part 2: Histogram Equalization for Color Images**

1. **Load Color Image:** Read the input image in color mode (`cv2.IMREAD_COLOR`).
2. **Convert Color Space:** Convert the image from the BGR color space to the HSV color space using `cv2.cvtColor()`.
3. **Equalize the Value Channel:** Extract the Value ($V$) channel (which represents brightness/intensity) from the HSV image and apply histogram equalization specifically to it, preserving the color information.
4. **Convert Back to BGR:** Merge the channels and convert the HSV image back to the BGR color space.
5. **Visualize and Compare:**
* Display both the original color image and the equalized color image side by side using subplots.
* Plot and compare the histograms of the original and equalized color images.
  
## Code:
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
img = cv2.imread('photo.png', cv2.IMREAD_GRAYSCALE)
plt.imshow(img, cmap='gray')
plt.title('Original Image')
plt.show()
plt.hist(img.ravel(),256,range = [0, 256]);
plt.title('Original Image')
plt.show()
img_eq = cv2.equalizeHist(img)
plt.hist(img_eq.ravel(), 256, range = [0, 256])
plt.title('Equalized Histogram')
plt.imshow(img_eq, cmap='gray')
plt.title('Original Image')
plt.show()
img = cv2.imread('photo.png', cv2.IMREAD_COLOR)
img_hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)
img_hsv[:,:,2] = cv2.equalizeHist(img_hsv[:, :, 2])
img_eq = cv2.cvtColor(img_hsv, cv2.COLOR_HSV2BGR)
plt.imshow(img_eq[:,:,::-1]); plt.title('Equalized Image');plt.show()
plt.hist(img_eq.ravel(),256,range = [0, 256]); plt.title('Histogram Equalized');plt.show()
plt.figure(figsize = (20,10))
plt.subplot(221); plt.imshow(img[:, :, ::-1]); plt.title('Original Color Image')
plt.subplot(222); plt.imshow(img_eq[:, :, ::-1]); plt.title('Equalized Image')
plt.show()
plt.figure(figsize = [15,4])
plt.subplot(121); plt.hist(img.ravel(),256,range = [0, 256]); plt.title('Original Image')
plt.subplot(122); plt.hist(img_eq.ravel(),256,range = [0, 256]); plt.title('Histogram Equalized')
```

## Output:


<img width="457" height="542" alt="image" src="https://github.com/user-attachments/assets/0446cca8-40e9-4b52-85f2-e1f620f121b7" />
<img width="767" height="551" alt="image" src="https://github.com/user-attachments/assets/3b499ca8-de6e-4a30-b69c-18bc03cb1287" />
<img width="766" height="572" alt="image" src="https://github.com/user-attachments/assets/d423f60c-fbe6-404c-955b-d83a03257b41" />
<img width="480" height="547" alt="image" src="https://github.com/user-attachments/assets/b15a3863-64d9-4013-880a-4c894e0ba763" />
<img width="498" height="543" alt="image" src="https://github.com/user-attachments/assets/86b0ded2-2f77-47c5-8f80-a810fc2c0261" />
<img width="733" height="546" alt="image" src="https://github.com/user-attachments/assets/3540efc9-0119-4b0f-a2f2-7aa0d6ce1516" />
<img width="1337" height="475" alt="image" src="https://github.com/user-attachments/assets/3ff4684a-f89a-4011-b6c6-bd968dd29941" />
<img width="1347" height="440" alt="image" src="https://github.com/user-attachments/assets/e58d7210-9770-4e01-b002-f0c86e68c4ac" />

## Result:

Thus, the histogram processing of the given image was successfully performed using OpenCV, and the pixel intensity distribution was displayed and analyzed.
