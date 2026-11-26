# Detect-the-lines-using-Hough-Transform
### Name : Priya B
### Reg no : 212224230208
## Aim
To detect straight lines in an input image using the Hough Line Transform technique in OpenCV and draw the detected lines on the original image.

## Software Used

 Anaconda – Python 3.7
 
Jupyter Notebook / VS Code

OpenCV (cv2)

NumPy

Matplotlib

## Algorithm

1.Import the required libraries: OpenCV (cv2), NumPy (numpy), and Matplotlib (matplotlib.pyplot).

2.Read the input image using the cv2.imread() function.

3.Convert the input image into a grayscale image using cv2.cvtColor().

4.Display both the original image and the grayscale image.

5.Apply the Canny Edge Detection algorithm using cv2.Canny() to identify the edges in the image.

6.Display the detected edges.

7.Apply the Probabilistic Hough Line Transform using cv2.HoughLinesP() to detect straight lines and obtain their coordinates.

8.Use a for loop to extract the coordinates (x1, y1, x2, y2) of each detected line.

9.Draw the detected lines in green on the original image using cv2.line().

10.Display the final output image containing the detected lines.

## Program
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 2: Load the image using imread() from cv2 module
image = cv2.imread('pic2.jpeg')  # Replace 'image.jpg' with your image path

# Step 3: Convert the image to grayscale
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

# Input image and grayscale image
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))  # Convert image to RGB for displaying
plt.title("Input Image")
plt.axis('off')

plt.imshow(gray_image, cmap='gray')
plt.title("Grayscale Image")
plt.axis('off')

# Step 4: Using Canny operator from cv2, detect the edges of the image
edges = cv2.Canny(gray_image, 50, 150)  # Canny edge detection with threshold values 50 and 150


# Canny Edge Detector output
plt.imshow(edges, cmap='gray')
plt.title("Canny Edge Detector")
plt.axis('off')

# Step 5: Using the HoughLinesP(), detect line coordinates for every point in the image
# The parameters of HoughLinesP are: image, resolution, threshold, minLineLength, maxLineGap
lines = cv2.HoughLinesP(edges, 1, np.pi / 180, 100, minLineLength=50, maxLineGap=10)

# Step 6: Using a for loop, draw the lines on the original image using the detected coordinates
# The lines variable contains the endpoints of the detected lines
for line in lines:
    x1, y1, x2, y2 = line  # Unpacking the line coordinates
    cv2.line(image, (x1, y1), (x2, y2), (0, 255, 0), 2)  # Draw green lines with thickness of 2
    
# Display the result of Hough Transform (Image with lines)
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))  # Image with lines drawn
plt.title("Result of Hough Transform")
plt.axis('off')
```

## Output

<img width="266" height="353" alt="image" src="https://github.com/user-attachments/assets/3e2126e3-e50b-45cc-bde4-af6027c5dc7c" />

<img width="267" height="350" alt="image" src="https://github.com/user-attachments/assets/a3a7dfb4-4927-4a48-a4a9-d31524c76ba0" />

<img width="276" height="345" alt="image" src="https://github.com/user-attachments/assets/d37b235b-82d6-4f8a-ad39-5817138b35a4" />

<img width="272" height="351" alt="image" src="https://github.com/user-attachments/assets/20811d36-e7e4-40ad-805c-4793f4361615" />

## Result
Thus, straight lines in the input image were successfully detected using the Probabilistic Hough Line Transform (HoughLinesP()) in OpenCV. The detected lines were drawn in green on the original image and the output was displayed successfully.
