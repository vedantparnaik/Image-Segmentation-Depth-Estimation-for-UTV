# Image Segmentation with Depth Estimation

## Overview
This project focuses on image segmentation using depth maps obtained from LIDAR data and camera images. By leveraging both 2D dense depth maps and original images, the application achieves object segmentation while also estimating the depth of segmented objects.  
   
### Key Features   
- Uses classical computer vision techniques for depth completion and image segmentation.
- Does not require neural networks, making it efficient and faster on CPUs.
- Superimposes depth images onto original images for enhanced segmentation.

## Project Structure
- `depth_completion.py`: Runs the depth completion process using the `ip_basic` algorithm, generating dense depth maps.
- `segment.py`: Takes the original image and the completed depth image, blends them, and performs segmentation using Mean-shift clustering.
- Output: The segmented images with depth overlay are saved in the output folder.

## Approach
### Depth Completion
The project utilizes a modified version of the `ip_basic` algorithm for depth completion. This involves several steps:
1. **Depth Inversion**: Inverts KITTI depth maps.
2. **Custom Kernel Dilation**: Fills empty pixels using a custom dilation kernel.
3. **Small and Large Hole Filling**: Fills remaining gaps using dilation and extrapolation techniques.
4. **Blur Operations**: Applies median and Gaussian blur to smooth out the depth map.

### Segmentation
After obtaining the completed depth map, the `segment.py` script performs:
1. **Mean-shift Segmentation** on the original image.
2. **Overlay of Depth and Original Image**: Combines the depth image with the original image.
3. **Superimposed Segmentation**: Performs segmentation on the blended image for enhanced results.

## Tech Stack
- **Programming Language**: Python
- **Libraries**:
  - OpenCV
  - PIL
  - NumPy
  - Scikit-image
  - Matplotlib

## Installation
### Prerequisites
- Python 3.8 or higher
- `pip` for package installation

### Setup
1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd <repository-name>
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Usage
1. Run the depth completion script:
   ```bash
   python depth_completion.py
   ```
   - This will create an output folder with the completed depth images.

2. Run the segmentation script:
   ```bash
   python segment.py
   ```
   - The segmented images will be saved in the output folder.

## Dataset
- The project uses the KITTI Vision Benchmark Depth Completion Dataset, which includes:
  - Annotated depth maps (14 GB)
  - Raw LIDAR scans (5 GB)

## Results
- The project successfully achieves smooth segmentation with depth estimation.
- Superimposed images show clear boundaries and reduced noise compared to traditional segmentation methods.

## Known Issues
- The project currently relies on classical image processing techniques, which may not perform well in highly complex scenes.
- Sparse depth maps can lead to inaccuracies in the segmentation results.

## Future Enhancements
- Incorporate spatial 3D metrics to establish relationships between segmented objects (e.g., using Haversine or Minkowski distance).
- Explore GPU acceleration for faster processing on larger datasets.

## Contributing
Contributions are welcome! Please open an issue or submit a pull request for any enhancements or bug fixes.

## License
This project is licensed under the MIT License.

## Contact
For any queries, feel free to reach out to:
- Vedant Parnaik - [LinkedIn](https://www.linkedin.com/in/vedantparnaik/)
- Advait Raman Samudralwar - [LinkedIn](your-linkedin-url)

---
