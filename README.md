# image_segmentation

# Image Segmentation using OpenCV and Skimage

## Overview
This project applies **image segmentation** techniques using **OpenCV** and **skimage** to analyze and extract meaningful regions from images.

## Features
- **Threshold-based segmentation**: Converts grayscale images into binary images.
- **Region-based segmentation**: Identifies connected components using `skimage.measure.label()`.
- **Edge-based segmentation**: Uses **Canny edge detection** to highlight object boundaries.
- **Visualization**: Displays segmentation results using Matplotlib.

## Dependencies
Ensure you have the following installed:

```bash
pip install opencv-python numpy matplotlib scikit-image
```

## How to Run
1. **Load an image**: Reads the input image in grayscale.
2. **Apply segmentation techniques**:
   - Threshold-based segmentation
   - Region-based segmentation
   - Edge-based segmentation
3. **Visualize results**: Uses Matplotlib to display the segmented images.

### Example Usage
```python
import cv2
import matplotlib.pyplot as plt
from skimage.measure import label

# Load Image
image_path = "path/to/image.jpg"  # Replace with the actual image path
image = cv2.imread(image_path, cv2.IMREAD_GRAYSCALE)
if image is None:
    raise FileNotFoundError("Image not found. Please check the path.")

# Threshold-based Segmentation
_, thresholded_image = cv2.threshold(image, 127, 255, cv2.THRESH_BINARY)

# Region-based Segmentation
labeled_image = label(thresholded_image)

# Edge-based Segmentation
edges = cv2.Canny(image, 100, 200)

# Display Results
fig, axes = plt.subplots(1, 3, figsize=(15, 5))
axes[0].imshow(thresholded_image, cmap='gray')
axes[0].set_title("Thresholded Image")
axes[1].imshow(labeled_image, cmap='nipy_spectral')
axes[1].set_title("Region-based Segmentation")
axes[2].imshow(edges, cmap='gray')
axes[2].set_title("Edge-based Segmentation")

for ax in axes:
    ax.axis("off")
plt.show()
```

## Expected Output
The script will display:
- The **original image** converted to a binary mask.
- The **segmented regions** using label-based segmentation.
- The **edges** detected using the Canny filter.

![Screenshot 2025-03-27 003637](https://github.com/user-attachments/assets/b7c275ae-f605-406a-ba0b-caec5ca3949e)




## Notes
- Ensure the **image path** is correctly set before running the script.
- Adjust the **threshold values** for better segmentation results.
- The Canny edge detector parameters can be fine-tuned for different edge strengths.

## License
This project is open-source and available under the MIT License.

