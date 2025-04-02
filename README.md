# Digital Image Processing Project: Object Detection

## Project Overview

This repository contains the code and documentation for a digital image processing project focused on object detection within images. The main approach used for object detection is template matching, with an alternative approach of feature matching also explored. The project includes preprocessing steps to enhance detection accuracy, such as converting images to grayscale, applying Gaussian blur, and using histogram equalization. The results of different attempts and adjustments to the detection process are documented, highlighting the improvements made to achieve accurate detection and visualization of objects.

## Object Detection Process

### Image Preparation
- The original image was split into two parts:
  - **Main Image:** The image where objects need to be detected.
  - **Template Images:** Individual images of the objects to be found within the main image.

### Preprocessing Steps
To improve detection accuracy, the following preprocessing steps were applied to both the main image and template images:
- Converted all images to **grayscale** to simplify processing.
- Applied **Gaussian blur** to reduce noise in the grayscale images.
- Used **histogram equalization** to enhance contrast, making object features more distinguishable.

### Detection Approach: Template Matching
The primary method used was **template matching**, which involved comparing the template images to the main image to locate objects. Below are the steps and iterations:

#### First Attempt
- Set a confidence threshold of **0.7** (detections required a confidence score greater than 0.7 to be valid).
- **Result:** Only **2 out of 12 objects** were detected.
- **Observation:** The threshold was too strict, missing most objects.

#### Second Attempt
- Lowered the confidence threshold to **0.4** to capture more detections.
- **Result:** Successfully detected **12 out of 12 objects**.
- **Issue:** Bounding boxes were not drawn correctly around the detected objects.
  - **Fix:** Adjusted the `visualize` function to use the detection result locations directly, rather than relying on additional details.
- **Observation After Fix:**
  - Objects **4, 5, 6, and 8** were detected incorrectly due to a scale of **0.5**, while other objects were detected at a scale of **0.75**.

#### Final Adjustment
- Modified the scale range, setting the **minimum scale to 0.75**.
- **Result:** All **12 objects** were detected with:
  - Correct scales.
  - Accurate bounding boxes that properly enclosed each object.

### Alternative Approach: Feature Matching
An alternative method, **feature matching**, was briefly explored:
- **Result:** Detected **12 out of 12 objects**.
- **Issue:** Bounding boxes were poorly drawn and did not accurately outline the objects.
- **Decision:** This approach was abandoned in favor of refining template matching, which proved more effective.

## Conclusion
After testing both template matching and feature matching, the **template matching approach** with an adjusted scale range (minimum scale of 0.75) provided the best results. This method successfully detected all 12 objects in the image and visualized them with accurate bounding boxes.

## Instructions for Running the Project

1. Clone the repository and navigate to the project directory.
2. Ensure you have the necessary dependencies installed, such as OpenCV and NumPy.
3. Open the `main.ipynb` file in Jupyter Notebook or any compatible environment.
4. Follow the steps outlined in the notebook to preprocess the images, perform object detection using template matching, and visualize the results.
5. Refer to the `Log.md` file for detailed documentation on the object detection process and the adjustments made to improve accuracy.
