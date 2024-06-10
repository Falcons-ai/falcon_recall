
<div id="top"></div>
<div align="center">

[![Generic badge](https://img.shields.io/badge/FALCONS.AI-Computer_Vision-red.svg)](https://shields.io/)
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Jupyter Notebook](https://img.shields.io/badge/jupyter-%23FA0F00.svg?style=for-the-badge&logo=jupyter&logoColor=white)
![Microsoft](https://img.shields.io/badge/Microsoft-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)


</div>


<!-- PROJECT LOGO -->
<br />
<div align="center">
    <img src="assets/fai_gradient_logo.png" alt="Logo" >
</div>




# Falcon Recall w/ Microsoft PHI3

## Overview

This project includes a function called `run_recall` that captures the current screen, compares it with the last captured screenshot, and processes it based on whether the screenshots are different. If the screenshots are different, the new image is saved and described using a PHI3 Vision model; otherwise, the duplicate screenshot is deleted.

## Features

1. **Screen Capture**: Captures the entire screen using the Pillow library.
2. **Image Comparison**: Compares the newly captured screenshot with the last modified screenshot in the recall directory to detect differences.
3. **Image Saving**: Saves the screenshot with a timestamped filename to avoid overwriting.
4. **Image Description**: If the images are different, it generates a description of the new image using the PHI3 Vision model and logs the description.
5. **Duplicate Handling**: Deletes the new screenshot if it is identical to the previous one to prevent duplicate storage.

## Dependencies

- Python 3.x
- Pillow
- PHI3 Vision model (assumed to be a custom or third-party module)

## How It Works

1. **Get Last Modified Image**: The function retrieves the last modified `.png` file from the recall directory.
2. **Capture Screenshot**: The entire screen is captured using `ImageGrab.grab()` from the Pillow library.
3. **Generate Timestamp**: A timestamp is generated using the current date and time to create a unique filename.
4. **Save Screenshot**: The screenshot is saved with the timestamped filename in the recall directory.
5. **Compare Images**: The newly saved screenshot is compared with the last modified image.
    - If the images are different:
        - Generate an image description using the PHI3 Vision model.
        - Save the image path and description to a log file.
        - Close the screenshot to release resources.
        - Print "Run normal" to indicate normal operation.
    - If the images are the same:
        - Delete the new screenshot to avoid storing duplicates.
6. **Return Filename**: The function returns the filename of the saved screenshot.

## Usage

- Ensure all dependencies are installed.
- Implement or provide access to the PHI3 Vision model and ensure it is correctly integrated.
- Call the `run_recall` function to capture the screen and process the image as described.

## Directory Structure

- The project expects a `recall` directory where screenshots are saved and compared.
- Log files with image descriptions are stored as specified by the `save_image_description` function.

## Important Notes

- The function assumes the existence of helper functions: `get_last_png_written`, `get_next_versioned_filename`, `are_images_different`, `Image_desc`, and `save_image_description`.
- Error handling and edge cases (e.g., no previous images in the directory) should be managed for robust functionality.
- Ensure appropriate permissions for reading and writing files in the specified directories.

## Disclaimer

**Privacy Notice**: The `run_recall` function captures the entire screen, including any sensitive or personal information displayed at the time of capture. Users should exercise discretion and be aware of privacy implications while Falcon-Recall is running. It is advised to close any sensitive documents or applications before running this function to avoid unintentional exposure of confidential information. Falcons.ai nor any of the staff there at, are not responsible for any privacy breaches or data leaks that may occur as a result of using this code base.
