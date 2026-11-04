# EXP 04 - Record-Image Transformations
## NAME: RAGASUDHA R
## REG NO: 212224230215
## AIM
To perform various image transformations such as translation, scaling, shearing, reflection, rotation, and cropping using OpenCV in Python.
## PROCEDURE
1. Import the required libraries such as OpenCV, NumPy, and Matplotlib.
2. Load the input image using cv2.imread() and display the original image.
3. Perform image translation by shifting the image horizontally and vertically.
4. Perform image scaling and shearing to change the size and shape of the image.
5. Apply image reflection using the cv2.flip() function.
6. Perform image rotation using a rotation matrix and display the rotated image.
7. Crop the required portion of the image using array slicing and display the cropped image.
## CODE
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
# Step 1: Load the image
image = cv2.imread('photo.jpeg')  # Load the image from file
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
# Step 3: Image Scaling
fx, fy = 5.0, 2.0  # Scaling factors (1.5x scaling for both width and height)
scaled_image = cv2.resize(image, None, fx=fx, fy=fy, interpolation=cv2.INTER_LINEAR)
# resize: Resize the image by scaling factors fx, fy
# INTER_LINEAR: Uses bilinear interpolation for resizing
plt.imshow(cv2.cvtColor(scaled_image, cv2.COLOR_BGR2RGB))  # Display the scaled image
plt.title("Scaled Image")  # Set title
plt.axis('off')
# Step 4: Image Shearing
shear_matrix = np.float32([[1, 0.5, 0], [0.5, 1, 0]])  # Shearing matrix
# The matrix shears the image by a factor of 0.5 in both x and y directions
# [1, 0.5, 0] - Shear along the x-axis (horizontal)
# [0.5, 1, 0] - Shear along the y-axis (vertical)
sheared_image = cv2.warpAffine(image, shear_matrix, (image.shape[1], image.shape[0]))
plt.imshow(cv2.cvtColor(sheared_image, cv2.COLOR_BGR2RGB))  # Display the sheared image
plt.title("Sheared Image")  # Set title
plt.axis('off')
# Step 5: Image Reflection
reflected_image = cv2.flip(image, 2)  # Flip the image horizontally (1 means horizontal flip)
# flip: 1 means horizontal flip, 0 would be vertical flip, -1 would flip both axes
plt.imshow(cv2.cvtColor(reflected_image, cv2.COLOR_BGR2RGB))  # Display the reflected image
plt.title("Reflected Image")  # Set title
plt.axis('off')
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
# Step 7: Image Cropping
x, y, w, h = 210, 300, 750, 950  # Define the top-left corner (x, y) and the width (w) and height (h) of the crop
# Cropping the image from coordinates (x, y) to (x+w, y+h)
cropped_image = image[y:y+h, x:x+w]
# The crop is performed by slicing the image array in the y and x directions
plt.imshow(cv2.cvtColor(cropped_image, cv2.COLOR_BGR2RGB))  # Display the cropped image
plt.title("Cropped Image")  # Set title
plt.axis('off')
```
## OUTPUT
<img width="911" height="556" alt="image" src="https://github.com/user-attachments/assets/7faa752b-8988-4e2d-9fbd-ed248532b45a" />
<img width="910" height="562" alt="image" src="https://github.com/user-attachments/assets/85ac8b46-b48e-4a21-8f1b-0837741a929f" />
<img width="907" height="400" alt="image" src="https://github.com/user-attachments/assets/31acee94-4eec-4ff8-a3cb-463d2b8ab4da" />
<img width="966" height="562" alt="image" src="https://github.com/user-attachments/assets/832861a3-e4c6-41c3-9c43-af8aca1998d1" />
<img width="972" height="561" alt="image" src="https://github.com/user-attachments/assets/0544b20e-2966-4bc8-ab6c-2fa85683d1eb" />
<img width="1111" height="561" alt="image" src="https://github.com/user-attachments/assets/1091fe20-372b-4ed5-97c4-4c57ec73dd4a" />
<img width="1037" height="557" alt="image" src="https://github.com/user-attachments/assets/488089eb-be9e-4e68-97c3-d7d4b6eff736" />

## RESULT
Thus, various image transformations such as translation, scaling, shearing, reflection, rotation, and cropping were successfully implemented using OpenCV and Python.
