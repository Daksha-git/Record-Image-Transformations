# Exp-4--Record-Image-Transformations
# IMAGE-TRANSFORMATIONS

## Aim

To perform image transformations such as Translation, Scaling, Shearing, Reflection, Rotation, and Cropping using OpenCV and Python.

## Software Required

- Anaconda - Python 3.7
- OpenCV
- NumPy
- Matplotlib

## Algorithm

### Step 1
Import all the necessary modules.

### Step 2
Choose an image and save it as `filename.jpg` or `bird.png`.

### Step 3
Use `cv2.imread()` to read the image.

### Step 4
Use `cv2.warpPerspective(image, M, (cols, rows))` to translate the image.

### Step 5
Use `cv2.warpPerspective(image, M, (cols2, rows2))` to scale the image.

### Step 6
Apply shearing, reflection, and rotation by defining the appropriate transformation matrices.

### Step 7
Crop a specific region of the image and save the cropped image.

## Program

**Developed By:** DAKSHA C

**Register Number:** 212224230048


## i) Image Translation

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 1: Load the image
image = cv2.imread('my_photo.jpg')  # Load the image from file

# Display the original image
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))  # Convert BGR to RGB for correct display
plt.title("Original Image")  
plt.axis('off')

# Step 2: Image Translation
tx, ty = 100, 50  # Translation factors (shift by 100 pixels horizontally and 50 vertically)
M_translation = np.float32([[1, 0, tx], [0, 1, ty]])  # Translation matrix: 
# [1, 0, tx] - Horizontal shift by tx
# [0, 1, ty] - Vertical shift by ty
translated_image = cv2.warpAffine(image, M_translation, (image.shape[1], image.shape[0]))

plt.imshow(cv2.cvtColor(translated_image, cv2.COLOR_BGR2RGB))  # Display the translated image
plt.title("Translated Image")  
plt.axis('off')
```

## ii) Image Scaling

```python
# Step 3: Image Scaling
fx, fy = 5.0, 2.0  # Scaling factors (1.5x scaling for both width and height)
scaled_image = cv2.resize(image, None, fx=fx, fy=fy, interpolation=cv2.INTER_LINEAR)
# resize: Resize the image by scaling factors fx, fy
# INTER_LINEAR: Uses bilinear interpolation for resizing

plt.imshow(cv2.cvtColor(scaled_image, cv2.COLOR_BGR2RGB))  # Display the scaled image
plt.title("Scaled Image")  # Set title
plt.axis('off')
```

## iii) Image Shearing

```python
# Step 4: Image Shearing
shear_matrix = np.float32([[1, 0.5, 0], [0.5, 1, 0]])  # Shearing matrix
# The matrix shears the image by a factor of 0.5 in both x and y directions
# [1, 0.5, 0] - Shear along the x-axis (horizontal)
# [0.5, 1, 0] - Shear along the y-axis (vertical)
sheared_image = cv2.warpAffine(image, shear_matrix, (image.shape[1], image.shape[0]))

plt.imshow(cv2.cvtColor(sheared_image, cv2.COLOR_BGR2RGB))  # Display the sheared image
plt.title("Sheared Image")  # Set title
plt.axis('off')
```

## iv) Image Reflection

```python
# Step 5: Image Reflection
reflected_image = cv2.flip(image, 2)  # Flip the image horizontally (1 means horizontal flip)
# flip: 1 means horizontal flip, 0 would be vertical flip, -1 would flip both axes

plt.imshow(cv2.cvtColor(reflected_image, cv2.COLOR_BGR2RGB))  # Display the reflected image
plt.title("Reflected Image")  # Set title
plt.axis('off')
```

## v) Image Rotation

```python
# Step 6: Image Rotation
(height, width) = image.shape[:2]  # Get the image height and width
angle = 45  # Rotation angle in degrees (rotate by 45 degrees)
center = (width // 2, height // 2)  # Set the center of rotation to the image center
M_rotation = cv2.getRotationMatrix2D(center, angle, 1)  # Get the rotation matrix
# getRotationMatrix2D: Takes the center of rotation, angle, and scale factor (1 means no scaling)
rotated_image = cv2.warpAffine(image, M_rotation, (width, height))  # Apply rotation

plt.imshow(cv2.cvtColor(rotated_image, cv2.COLOR_BGR2RGB))  # Display the rotated image
plt.title("Rotated Image")  # Set title
plt.axis('off')
```

## vi) Image Cropping

```python
# Step 7: Image Cropping
x, y, w, h = 100, 100, 200, 150  # Define the top-left corner (x, y) and the width (w) and height (h) of the crop
# Cropping the image from coordinates (x, y) to (x+w, y+h)
cropped_image = image[y:y+h, x:x+w]
# The crop is performed by slicing the image array in the y and x directions

plt.imshow(cv2.cvtColor(cropped_image, cv2.COLOR_BGR2RGB))  # Display the cropped image
plt.title("Cropped Image")  # Set title
plt.axis('off')
```

## Output
### i) Input Iamge

<img width="270" height="471" alt="Screenshot 2026-11-14 204337" src="https://github.com/user-attachments/assets/2461e095-6f40-432a-b44a-7fbb098dea13" />



### ii) Image Translation


<img width="262" height="462" alt="Screenshot 2026-11-14 204410" src="https://github.com/user-attachments/assets/0680d064-13d1-4ea1-ad22-2b73c1dc2041" />




### iii) Image Scaling


<img width="581" height="450" alt="Screenshot 2026-11-14 204443" src="https://github.com/user-attachments/assets/09ed6ee8-5eda-42eb-a4a9-2470976bb153" />

### iv) Image Shearing

<img width="282" height="465" alt="Screenshot 2026-11-14 204604" src="https://github.com/user-attachments/assets/987f572e-ca8c-44fd-834a-7e422755df9a" />



### v) Image Reflection


<img width="278" height="467" alt="Screenshot 2026-11-14 204609" src="https://github.com/user-attachments/assets/b9a8df26-7b00-4fd2-9cd8-13e62c83dd12" />


### vi) Image Rotation


<img width="292" height="471" alt="Screenshot 2026-11-14 204614" src="https://github.com/user-attachments/assets/e0c46b4f-45d2-4632-b66a-068a5031b879" />


### vii) Image Cropping


<img width="600" height="460" alt="Screenshot 2026-11-14 204620" src="https://github.com/user-attachments/assets/80349757-8e69-4806-803a-4f42ceebdc23" />



## Result

Thus, different image transformations such as Translation, Scaling, Shearing, Reflection, Rotation, and Cropping were performed using OpenCV and Python programming.
