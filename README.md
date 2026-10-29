# Image_Smoothing_and_Sharpening_Using_OpenCV

## Aim

To write a Python program using OpenCV to apply different smoothing filters (Averaging, Weighted Averaging, Gaussian, Median) and sharpening filters (Laplacian Kernel and Laplacian Operator) for image enhancement, and display each result separately along with the original image for comparison.

---

## The program performs the following operations:

- Read and display an input image  
- Apply Averaging filter  
- Apply Weighted Averaging filter  
- Apply Gaussian filter  
- Apply Median filter  
- Apply Laplacian sharpening using kernel  
- Apply Laplacian operator  
- Display all outputs for comparison  

---

##  Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (cv2)  
- NumPy  
- Matplotlib  

---

##  Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image (e.g., `image.jpg`).

### Step 3:
Convert the image from BGR to RGB format for display.

### Step 4:
Apply Averaging Filter using `cv2.blur()`.

### Step 5:
Apply Weighted Averaging Filter using a custom kernel with `cv2.filter2D()`.

### Step 6:
Apply Gaussian Filter using `cv2.GaussianBlur()`.

### Step 7:
Apply Median Filter using `cv2.medianBlur()`.

### Step 8:
Apply Laplacian Sharpening using Kernel with `cv2.filter2D()`.

### Step 9:
Convert image to grayscale and apply Laplacian Operator using `cv2.Laplacian()`.

### Step 10:
Display all filtered images using a grid layout for comparison.

---

##  Developed By

- **Name:** DEEPAKKUMAR S 
- **Register No:** 212225230042

## program

```
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 1: Read the input image
img = cv2.imread("bird.png")

if img is None:
    print("Error: Image not found!")
    exit()

# Step 2: Convert BGR to RGB
rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# Step 3: Apply Averaging Filter
average = cv2.blur(rgb, (5, 5))

# Step 4: Apply Weighted Averaging Filter
kernel = np.array([[1, 2, 1],
                   [2, 4, 2],
                   [1, 2, 1]], dtype=np.float32) / 16

weighted = cv2.filter2D(rgb, -1, kernel)

# Step 5: Apply Gaussian Filter
gaussian = cv2.GaussianBlur(rgb, (5, 5), 0)

# Step 6: Apply Median Filter
median = cv2.medianBlur(rgb, 5)

# Step 7: Apply Laplacian Sharpening using Kernel
lap_kernel = np.array([[0, -1, 0],
                       [-1, 5, -1],
                       [0, -1, 0]])

sharpened = cv2.filter2D(rgb, -1, lap_kernel)

# Step 8: Convert to Grayscale and Apply Laplacian Operator
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
laplacian = cv2.Laplacian(gray, cv2.CV_64F)
laplacian = cv2.convertScaleAbs(laplacian)

# Step 9: Display all images in a grid
images = [
    (rgb, "Original Image"),
    (average, "Averaging Filter"),
    (weighted, "Weighted Averaging"),
    (gaussian, "Gaussian Filter"),
    (median, "Median Filter"),
    (sharpened, "Laplacian Sharpening"),
    (laplacian, "Laplacian Operator")
]

plt.figure(figsize=(14, 10))

for i, (image, title) in enumerate(images):
    plt.subplot(3, 3, i + 1)
    plt.imshow(image, cmap='gray' if len(image.shape) == 2 else None)
    plt.title(title)
    plt.axis('off')

plt.tight_layout()
plt.show()
```

##  Output
<img width="1150" height="896" alt="image" src="https://github.com/user-attachments/assets/cdf7c8e8-1fa2-45c0-9b19-48a27e6c4b74" />


### Smoothing Filters

- Averaging filter produces blurred image  
- Weighted averaging provides smoother result with less distortion  
- Gaussian filter preserves edges better while reducing noise  
- Median filter removes salt-and-pepper noise effectively  

###  Sharpening Filters

- Laplacian kernel enhances edges and fine details  
- Laplacian operator detects edges clearly in grayscale  

---

##  Result

Thus, smoothing filters and sharpening filters are successfully implemented using OpenCV.

The smoothing filters reduce noise and improve image quality, while sharpening filters enhance edges and details for better feature extraction.
