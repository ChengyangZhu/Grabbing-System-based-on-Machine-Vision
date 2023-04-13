# Grabbing System based on Machine Vision
Robotic arm grabbing system based on machine vision (SIFT algorithm)

https://user-images.githubusercontent.com/113228076/212432220-dfa0abeb-46c4-41f9-b467-53284290c0d5.mp4

## Robotics Kinematics
The MDH table of the robotic arm
| No. of Joints  | $α_{n-1}$ | $a_{n-1}$ | $θ_n$ | $d_n$ | minimum angle | maximum angle |
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| 1 | 0  | 0 | $θ_1$ | 127| -100 | 160 |
| 2 | -π/2  | 29.7 | $θ_2$ | 0 | -120 | -20 |
| 3 | 0  | 108 | $θ_3$ | 0 | -170 | 60 |
| 4 | -π/2  | 20 | $θ_4$ | 169 | -350 | 350 |
| 5 | π/2  | 0 | $θ_5$ | 0 | -115 | 126 |
| 6 | π/2  | 0 | $θ_6$ | -24.8 | -360 | 360 |

### Trajectory Planning
<p align="center">
  <img width="600" height="300" src="https://user-images.githubusercontent.com/113228076/231647773-9b9da653-9803-4ca1-bea6-d16ccbb78b26.jpg">
</p>

## Image Transformation and Calibration
There are multiple coordinate systems in a robot system, so the unification of coordinate systems is critical, which determines whether the robot system can successfully achieve grabbing. In vision-based robot system, the input information is the image captured by the camera, which is two-dimensional. The purpose of image transformation is to convert the captured two-dimensional information into the coordinates of objects in world coordinate system, which is three-dimensional. To achieved image transformation, camera intrinsic calibration and hand-eye calibration are indispensable. Since the camera used in this project is unable to provide depth information, so deriving the depth information is critical, which is achieved by EPnP algorithm. The image process is finished in Python 3.7 environment, with support of OpenCV libraries. 

### Image Transformation
The projection relationship is shown in the following figure.

<p align="center">
  <img width="600" height="300" src="https://user-images.githubusercontent.com/113228076/223846542-7a62bcda-1884-47a8-8204-5e3735c4f53a.jpg">
</p>

The coordinates in image plane, is part of the camera coordinate system, and the key difference is the z-axis coordinate, which is also called depth information. The transformation matrix between the pixel plane and the camera coordinate system is called intrinsic parameters, ${\left\lbrack \matrix{f_x & 0 & c_x \cr 0 & f_y & c_y \cr 0 & 0 & 1} \right\rbrack}$.\
where: $f_x$ and $f_y$ are the scale factors between the image plane and pixel plane\
       $c_x$ and $c_y$ are the pixel offset between the image plane and pixel plane\
After calibration, the intrinsic matrix is ${\left\lbrack \matrix{625.5708 & 0 & 321.6519 \cr 0 & 625.9031 & 231.1601 \cr 0 & 0 & 1} \right\rbrack}$.
