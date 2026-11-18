# EX-10: Implementation of Opening and Closing using OpenCV

## Aim

To write a Python program using OpenCV to perform morphological Opening and Closing operations on an image.

### Operations Performed
1. Morphological Opening
2. Morphological Closing

## Software Used

- Anaconda – Python 3.7
- Jupyter Notebook / VS Code
- OpenCV (`cv2`)
- NumPy
- Matplotlib

## Algorithm

**Step 1:** Import the required libraries: OpenCV, NumPy, and Matplotlib.

**Step 2:** Create or load an input image containing foreground objects.

**Step 3:** Display the original image.

**Step 4:** Create a structuring element (kernel) of suitable size.

**Step 5: Opening Operation**
- Apply the Opening operation using the structuring element.
- Opening consists of Erosion followed by Dilation.
- Remove small foreground noises while preserving the shape of larger objects.
- Display the opened image.

**Step 6: Closing Operation**
- Apply the Closing operation using the structuring element.
- Closing consists of Dilation followed by Erosion.
- Fill small holes and gaps within foreground objects.
- Display the closed image.

**Step 7:** Compare the original, opened, and closed images.

## Program

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Create a blank image
image = np.zeros((500, 500, 3), dtype=np.uint8)

# Insert text into the image
font = cv2.FONT_HERSHEY_SIMPLEX
cv2.putText(
    image,
    'IMAGE',
    (100, 250),
    font,
    1,
    (255, 255, 255),
    2,
    cv2.LINE_AA
)

# Create a 3x3 kernel
kernel = np.ones((3, 3), np.uint8)

# Display the original image
plt.subplot(1, 3, 1)
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title("Input Image with Text")
plt.axis('off')

# Morphological Opening
opened_image = cv2.morphologyEx(
    image, cv2.MORPH_OPEN, kernel
)

plt.subplot(1, 3, 2)
plt.imshow(cv2.cvtColor(opened_image, cv2.COLOR_BGR2RGB))
plt.title("Opening Operation")
plt.axis('off')

# Morphological Closing
closed_image = cv2.morphologyEx(
    image, cv2.MORPH_CLOSE, kernel
)

plt.subplot(1, 3, 3)
plt.imshow(cv2.cvtColor(closed_image, cv2.COLOR_BGR2RGB))
plt.title("Closing Operation")
plt.axis('off')

# Display all results
plt.tight_layout()
plt.show()
```

## Output

The following images show the results of the morphological operations.

<img width="938" height="741" alt="image" src="https://github.com/user-attachments/assets/aabd1a3d-7c18-4091-8cc9-300a1a34066d" />


## Result

Thus, the morphological Opening and Closing operations are successfully implemented using OpenCV. Opening removes small foreground noises, while Closing fills small holes and gaps within foreground objects.
