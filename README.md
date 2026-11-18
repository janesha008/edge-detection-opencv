# edge-detection-opencv

## Aim

To perform edge detection using Sobel, Roberts, Prewitt, Laplacian, and Canny edge detectors.

---

## Software Required

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (cv2)  
- NumPy  
- Matplotlib  

---

## ⚙️ Algorithm

### Step 1:
Import all the necessary modules for the program.
```
import cv2
import numpy as np
import matplotlib.pyplot as plt
```

### Step 2:
Load an image using `cv2.imread()`.

### Step 3:
Convert the image to grayscale.
```
filename = list(uploaded.keys())[0]

img = cv2.imread(filename)

img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

plt.imshow(img)
plt.title('Original Image')
plt.axis('off')
plt.show()
```

### Step 4:
Apply **Sobel operator** using OpenCV to detect edges.
```
sobelx = cv2.Sobel(gray, cv2.CV_64F, 1, 0, ksize=3)
sobely = cv2.Sobel(gray, cv2.CV_64F, 0, 1, ksize=3)

sobel = cv2.magnitude(sobelx, sobely)

sobel = cv2.convertScaleAbs(sobel)

plt.imshow(sobel, cmap='gray')
plt.title('Sobel Edge Detection')
plt.axis('off')
plt.show()
```

### Step 5:
Apply **Prewitt operator** using custom kernels.
```
kernelx = np.array([[-1, 0, 1],
                    [-1, 0, 1],
                    [-1, 0, 1]])

kernely = np.array([[-1, -1, -1],
                    [0, 0, 0],
                    [1, 1, 1]])

prewittx = cv2.filter2D(gray, -1, kernelx)
prewitty = cv2.filter2D(gray, -1, kernely)

prewitt = cv2.addWeighted(prewittx, 0.5, prewitty, 0.5, 0)

plt.imshow(prewitt, cmap='gray')
plt.title('Prewitt Edge Detection')
plt.axis('off')
plt.show()
```

### Step 6:
Apply **Roberts operator** using custom kernels.
```
robertsx = np.array([[1, 0],
                     [0, -1]])

robertsy = np.array([[0, 1],
                     [-1, 0]])

rx = cv2.filter2D(gray, cv2.CV_32F, robertsx)
ry = cv2.filter2D(gray, cv2.CV_32F, robertsy)

roberts = cv2.magnitude(rx, ry)

roberts = cv2.convertScaleAbs(roberts)

plt.imshow(roberts, cmap='gray')
plt.title('Roberts Edge Detection')
plt.axis('off')
plt.show()
```

### Step 7:
Apply **Laplacian operator** using OpenCV.
```
laplacian = cv2.Laplacian(gray, cv2.CV_64F)

laplacian = cv2.convertScaleAbs(laplacian)

plt.imshow(laplacian, cmap='gray')
plt.title('Laplacian Edge Detection')
plt.axis('off')
plt.show()
```

### Step 8:
Apply **Canny edge detector** using OpenCV.
```
canny = cv2.Canny(gray, 100, 200)

plt.imshow(canny, cmap='gray')
plt.title('Canny Edge Detection')
plt.axis('off')
plt.show()
```

### Step 9:
Display all edge-detected images for comparison.
```
images = [img, sobel, prewitt, roberts, laplacian, canny]

titles = ['Original Image',
          'Sobel Edge Detection',
          'Prewitt Edge Detection',
          'Roberts Edge Detection',
          'Laplacian Edge Detection',
          'Canny Edge Detection']

plt.figure(figsize=(15, 10))

for i in range(6):
    plt.subplot(2, 3, i+1)

    if i == 0:
        plt.imshow(images[i])
    else:
        plt.imshow(images[i], cmap='gray')

    plt.title(titles[i])
    plt.axis('off')

plt.tight_layout()
plt.show()
```

---

## Developed By

- **Name:** Janesha S
- **Register No:** 212225240056

---

## Output

###  Sobel Edge Detector
- Detects edges in horizontal and vertical directions  
- Produces gradient-based edge map

  <img width="515" height="350" alt="image" src="https://github.com/user-attachments/assets/4264a797-e223-4f61-9af4-60a1991d4b2b" />


###  Prewitt Edge Detector
- Similar to Sobel but simpler kernel  
- Detects directional edges

  <img width="515" height="350" alt="image" src="https://github.com/user-attachments/assets/9367bc4c-6c50-4c63-ac57-e2ebaa16f953" />


###  Roberts Edge Detector
- Detects edges using diagonal gradients  
- Sensitive to noise

  <img width="515" height="350" alt="image" src="https://github.com/user-attachments/assets/38c313dc-cda3-49f1-805f-af5d9cd024fc" />


###  Laplacian Edge Detector
- Detects edges using second-order derivatives  
- Highlights rapid intensity changes

   <img width="515" height="350" alt="image" src="https://github.com/user-attachments/assets/2c4814ff-83db-498b-be0e-bfe9ec540351" />


###  Canny Edge Detector
- Multi-stage edge detection  
- Produces clean and thin edges

  <img width="515" height="350" alt="image" src="https://github.com/user-attachments/assets/d372a1cd-43cb-4c09-af7a-1e0be0c802c3" />

  <img width="1489" height="775" alt="image" src="https://github.com/user-attachments/assets/2ac8cc2d-15a3-4a6f-8a02-c52af541a6d8" />



---

## Result

Thus, edges are successfully detected using Sobel, Prewitt, Roberts, Laplacian, and Canny edge detection techniques. Each method highlights edges differently based on gradient and intensity variations, improving feature extraction and analysis.
