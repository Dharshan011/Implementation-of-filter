# Implementation-of-filter
## Aim:
To implement filters for smoothing and sharpening the images in the spatial domain.

## Software Required:
Anaconda - Python 3.7

## Algorithm:
### Step 1: 
Import necessary libraries (cv2, NumPy, Matplotlib) for image loading, filtering, and visualization.

### Step 2: 
Load the image using cv2.imread() and convert it to RGB format using cv2.cvtColor() for proper display in Matplotlib.

### Step 3: 
Apply different filters:
1. Averaging Filter: Define an averaging kernel using np.ones() and apply it to the image using cv2.filter2D().
2. Weighted Averaging Filter: Define a weighted kernel (e.g., 3x3 Gaussian-like) and apply it with cv2.filter2D().
3. Gaussian Filter: Use cv2.GaussianBlur() to apply Gaussian blur.
4. Median Filter: Use cv2.medianBlur() to reduce noise.
5. Laplacian Operator: Use cv2.Laplacian() to apply edge detection.
    
### Step 4: 
Display each filtered image using plt.subplot() and plt.imshow() for side-by-side comparison of the original and processed images.

### Step 5: 
Save or show the images using plt.show() after applying each filter to visualize the effects of smoothing and sharpening.

## Program:
### Developed By   : DHARSHAN V
### Register Number: 212222230031
```
import cv2
import matplotlib.pyplot as plt
import numpy as np
image1 = cv2.imread("dog.jpg")
image2 = cv2.cvtColor(image1, cv2.COLOR_BGR2RGB)
plt.figure(figsize=(10, 8))
plt.subplot(1, 2, 1)
plt.imshow(image2)
plt.title("Original Image")
plt.axis("off")
```
![Screenshot 2024-10-03 154049](https://github.com/user-attachments/assets/c04ab73d-0a34-40e1-9e1c-2eb7cb2956de)


### 1. Smoothing Filters

i) Using Averaging Filter
```
kernel = np.ones((11, 11), np.float32) / 121
averaging_image = cv2.filter2D(image2, -1, kernel)
plt.figure(figsize=(10, 8))
plt.subplot(1, 2, 2)
plt.imshow(averaging_image)
plt.title("Averaging Filter Image")
plt.axis("off")
plt.show()

```
![Screenshot 2024-10-03 154055](https://github.com/user-attachments/assets/fc184f1d-af23-4484-9e9f-b46067eb1e73)




ii) Using Weighted Averaging Filter
```Python
kernel1 = np.array([[1, 2, 1],
                    [2, 4, 2],
                    [1, 2, 1]]) / 16

weighted_average_image = cv2.filter2D(image2, -1, kernel1)
plt.figure(figsize=(10, 8))
plt.subplot(1, 2, 2)
plt.imshow(weighted_average_image)
plt.title("Weighted Average Filter Image")
plt.axis("off")
plt.show()

```

![Screenshot 2024-10-03 154059](https://github.com/user-attachments/assets/0d1fb6f6-df6f-4ada-a1bf-f60aa69e3685)


iii) Using Minimum Filter
```Python
min_filter = cv2.erode(image1, np.ones((5, 5), np.uint8))
min_filter_rgb = cv2.cvtColor(min_filter, cv2.COLOR_BGR2RGB)
plt.imshow(min_filter_rgb)
plt.title("Minimum Filter")
plt.show()
```

![Screenshot 2024-10-03 154114](https://github.com/user-attachments/assets/c0d390aa-2d6c-4f32-911d-ae30cda695e8)



iv) Using Maximum Filter
```
max_filter = cv2.dilate(image1, np.ones((5, 5), np.uint8))
max_filter_rgb = cv2.cvtColor(max_filter, cv2.COLOR_BGR2RGB)
plt.imshow(max_filter_rgb)
plt.title("Maximum Filter")
plt.show()
```



![Screenshot 2024-10-03 154119](https://github.com/user-attachments/assets/453ece39-e0e1-4988-9b61-f21cd49b19f6)


v) Using Median Filter
```
median_filter = cv2.medianBlur(image1, 5)
median_filter_rgb = cv2.cvtColor(median_filter, cv2.COLOR_BGR2RGB)
plt.imshow(median_filter_rgb)
plt.title("Median Filter")
plt.show()
```



![Screenshot 2024-10-03 154124](https://github.com/user-attachments/assets/93e0c340-5bce-423f-9377-7689101896c8)


### 2. Sharpening Filters
i) Using Laplacian Linear Kernal
```
sharpened_image = cv2.filter2D(image1, -1, kernel1)
plt.figure(figsize=(10, 8))
plt.subplot(1, 2, 2)
plt.imshow(sharpened_image)
plt.title("Sharpened Image (Laplacian Kernel)")
plt.axis("off")
plt.show()
```



![Screenshot 2024-10-03 154128](https://github.com/user-attachments/assets/704b1b27-6f3a-401b-baf6-0c886598875a)


ii) Using Laplacian Operator
```
laplacian = cv2.Laplacian(image1, cv2.CV_64F)
plt.figure(figsize=(10, 8))
plt.subplot(1, 2, 2)
plt.imshow(laplacian, cmap='gray')
plt.title("Laplacian Operator Image")
plt.axis("off")
plt.show()
```


![Screenshot 2024-10-03 154132](https://github.com/user-attachments/assets/b629b0ff-c2e0-4a3e-bf29-ce7cd9e09d9f)

## Result:
Thus the filters are designed for smoothing and sharpening the images in the spatial domain.
