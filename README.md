# Parking-Assistance-Using-Homography
Project: ENPM673: Perception for Autonomous Robots

![Picture 1](https://github.com/user-attachments/assets/9e287ccc-4793-49b2-b272-c7349359b008)

* Use concept of homography to create a 360 deg top-view of a vehicle using a number of cameras mounted on the vehicle.
* Show a video with the surrounding of the vehicle while it is reversing to park.

## Accomplishments
* Built a computer vision pipeline using Homography to create a 360 deg top view of a real-world vehicle with 4 cameras (1 front, 1 rear & 2 sides) mounted on it.
* Performed camera calibration, image distortion correction, projective transform, feature detection and image stitching using OpenCV in Python for 1140+ images to obtain a real-time top-view video footage.

## Contributors
* Hamsaavarthan Ravichandar
* Caleb James Myers
* Dillon Michael Miller

## Methodology
### Data Acquisition
* Used 4 Gopros (different models)  mounted on a Jeep Cherokee
  * 2 Side Cameras, a Back Camera, and a Front Camera
* Placed objects around the corner of the car for features
* The cameras did not all share the same frame rate or image size

### Camera Calibration
* From each camera, 15 images of fiducials were taken
  * 6x4 checkerboard
* Camera Calibration gives the cameras intrinsic matrix necessary to undistort the image
* Used OpenCV Functions
<img width="261" alt="Screenshot 2025-04-15 at 6 16 16 PM" src="https://github.com/user-attachments/assets/3b93ac88-a96f-4859-a8c6-f502b0c494a2" />


### Correct Image Distortion
* Ideally we have straight lines for parking lines, but the wide lens of the gopro cameras create significant distortion
* Though not exactly fisheye (>180 degrees), we are able to correct for the distortion from the wide lens
* Correction allows for the parking lines to appear straight 
* Correction was applied for all 1140 images from all 4 cameras
<img width="275" alt="image" src="https://github.com/user-attachments/assets/95c7c23c-f31f-4356-901f-387af0c95d0b" />

### Crop and Resize images
* Re-Oriented and Resize the image to match size of vehicle and relative camera orientation.
* Cropped image to have no black space and to remove the car from the image

### Feature Detection & Image Stitching
* Sift Feature Detection and cv.BFMatcher() was used to match features
* The ‘y’ value of the same feature was used to stitch the two images together.
<img width="395" alt="image" src="https://github.com/user-attachments/assets/cfee409e-b330-4e30-ae38-2a40ab7a928e" />


* Video Creation

