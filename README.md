# Histogram-Equalization-Using-OpenCV

## AIM
To write a Python program using OpenCV to perform histogram equalization on both grayscale and color images to enhance image contrast and brightness.

The program performs the following operations:

Read and display a grayscale image
Plot histogram of the grayscale image
Apply histogram equalization on grayscale image
Read and display a color image
Plot histogram of B, G, R channels
Convert image to HSV color space
Apply histogram equalization on the Value (V) channel
Convert the enhanced image back to BGR format
Display original and enhanced images with histograms

## Software Used
• Anaconda – Python 3.7
• Jupyter Notebook / VS Code
• OpenCV (cv2)
• NumPy
• Matplotlib

## Algorithm
Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

Step 2:
Read the image parrot.jpg in grayscale format.

Step 3:
Display the grayscale image and plot its histogram.

Step 4:
Apply histogram equalization using cv2.equalizeHist() to enhance contrast.

Step 5:
Display original grayscale image, its histogram, enhanced image, and its histogram using a 2 × 2 grid.

Step 6:
Read the same image in color format.

Step 7:
Split the image into B, G, R channels and plot their histograms.

Step 8:
Convert the image from BGR to HSV color space.

Step 9:
Apply histogram equalization on the V (Value) channel.

Step 10:
Merge the channels and convert the image back to BGR format.

Step 11:
Display original color image, histogram, enhanced image, and enhanced histogram using a 2 × 2 grid.

## Program
## Developed By: KRUTHIKA R
## Register No: 212225240075

## Loads porsche.jpg in grayscale
```
import cv2
import numpy as np
import matplotlib.pyplot as plt
image_path = r"C:\Users\kruthika\OneDrive\Dev\courses\College\DIPT.ipynb\porsche.jpg"
gray = cv2.imread(image_path, cv2.IMREAD_GRAYSCALE)
print(type(gray))
print(gray is None)
```
## Enhanced grayscale image
```
enhanced = cv2.equalizeHist(gray)

plt.imshow(enhanced, cmap='gray')
plt.title("Enhanced Grayscale Image")
plt.axis('off')
plt.show()
```
## Image Enhancement and Histogram Comparison using Matplotlib
```
plt.figure(figsize=(10, 8))
plt.subplot(2, 2, 1)
plt.imshow(gray, cmap='gray')
plt.title("Original Grayscale Image")
plt.axis('off')
plt.subplot(2, 2, 2)
plt.hist(gray.ravel(), bins=256, range=(0, 256))
plt.title("Original Histogram")
plt.subplot(2, 2, 3)
plt.imshow(enhanced, cmap='gray')
plt.title("Enhanced Grayscale Image")
plt.axis('off')
plt.subplot(2, 2, 4)
plt.hist(enhanced.ravel(), bins=256, range=(0, 256))
plt.title("Enhanced Histogram")
plt.tight_layout()
plt.show()
```

## Reading and Displaying an Original Colour Image using OpenCV
```
color = cv2.imread(image_path)
if color is not None:
    color_rgb = cv2.cvtColor(color, cv2.COLOR_BGR2RGB)
    plt.imshow(color_rgb)
    plt.title("Original Colour Image")
    plt.axis('off')
    plt.show()
else:
    print("Image not found!")
```
## Splitting and Displaying RGB Colour Channels using OpenCV
```
b, g, r = cv2.split(color)
plt.figure(figsize=(12, 4))
plt.subplot(1, 3, 1)
plt.imshow(b, cmap='gray')
plt.title("Blue Channel")
plt.axis('off')
plt.subplot(1, 3, 2)
plt.imshow(g, cmap='gray')
plt.title("Green Channel")
plt.axis('off')
plt.subplot(1, 3, 3)
plt.imshow(r, cmap='gray')
plt.title("Red Channel")
plt.axis('off')
plt.tight_layout()
plt.show()
```
## Histogram Analysis of Individual Colour Channels (RGB)
```
plt.figure(figsize=(12, 4))
plt.subplot(1, 3, 1)
plt.hist(b.ravel(), bins=256, range=(0, 256), color='blue')
plt.title("Blue Histogram")
plt.subplot(1, 3, 2)
plt.hist(g.ravel(), bins=256, range=(0, 256), color='green')
plt.title("Green Histogram")
plt.subplot(1, 3, 3)
plt.hist(r.ravel(), bins=256, range=(0, 256), color='red')
plt.title("Red Histogram")
plt.tight_layout()
plt.show()
```
## HSV Colour Space Conversion and Value Channel Histogram Equalization
```
hsv = cv2.cvtColor(color, cv2.COLOR_BGR2HSV)
h, s, v = cv2.split(hsv)
print("HSV conversion completed successfully!")
v_eq = cv2.equalizeHist(v)
plt.imshow(v_eq, cmap='gray')
plt.title("Equalized V Channel")
plt.axis('off')
plt.show()
```
## Colour Image Enhancement using HSV Colour Space
```
hsv_eq = cv2.merge((h, s, v_eq))
enhanced_color = cv2.cvtColor(hsv_eq, cv2.COLOR_HSV2BGR)
print("Colour image enhancement completed!")
```
## Comparison of Original and Enhanced Colour Images with Histograms
```
plt.figure(figsize=(10, 8))

plt.subplot(2, 2, 1)
plt.imshow(cv2.cvtColor(color, cv2.COLOR_BGR2RGB))
plt.title("Original Colour Image")
plt.axis('off')

plt.subplot(2, 2, 2)
plt.hist(color.ravel(), bins=256, range=(0, 256))
plt.title("Original Colour Histogram")

plt.subplot(2, 2, 3)
plt.imshow(cv2.cvtColor(enhanced_color, cv2.COLOR_BGR2RGB))
plt.title("Enhanced Colour Image")
plt.axis('off')

plt.subplot(2, 2, 4)
plt.hist(enhanced_color.ravel(), bins=256, range=(0, 256))
plt.title("Enhanced Colour Histogram")

plt.tight_layout()
plt.show()
```

## OUTPUT 
<img width="1032" height="437" alt="image" src="https://github.com/user-attachments/assets/93906230-7140-49d4-9e7c-a8753f9f3b30" />
<img width="366" height="458" alt="image" src="https://github.com/user-attachments/assets/0264a8a0-00a8-4e28-bc05-8ab09b6c0353" />
<img width="946" height="788" alt="image" src="https://github.com/user-attachments/assets/b0c1c0db-30e9-461c-be49-6911d85e7cc6" />
<img width="326" height="410" alt="image" src="https://github.com/user-attachments/assets/2d04b575-8314-4fd7-b2f6-f1f0a36daf7a" />
<img width="1132" height="395" alt="image" src="https://github.com/user-attachments/assets/7f0d9530-ed74-41ec-99d3-a07a786406c5" />
<img width="1088" height="362" alt="image" src="https://github.com/user-attachments/assets/aee8dd82-c538-4359-9a57-47e68f7c71bc" />
<img width="312" height="406" alt="image" src="https://github.com/user-attachments/assets/2ec6f5c2-ee9d-4b8a-8074-66f332ea3dfa" />
<img width="891" height="782" alt="image" src="https://github.com/user-attachments/assets/6a1a1cb1-bb8b-4c51-87f4-efa95c703f93" />


## RESULT
Thus, histogram equalization is successfully performed on both grayscale and color images using OpenCV. The contrast and brightness of the images are significantly improved, enhancing visual quality and feature visibility.
