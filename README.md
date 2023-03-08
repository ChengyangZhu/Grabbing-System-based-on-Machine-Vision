# Grabbing-System-based-on-Machine-Vision
Robotic arm grabbing system based on machine vision (SIFT algorithm)


https://user-images.githubusercontent.com/113228076/212432220-dfa0abeb-46c4-41f9-b467-53284290c0d5.mp4

#Image Transformation and Calibration
There are multiple coordinate systems in a robot system, so the unification of coordinate systems is critical, which determines whether the robot system can successfully achieve grabbing. In vision-based robot system, the input information is the image captured by the camera, which is two-dimensional. The purpose of image transformation is to convert the captured two-dimensional information into the coordinates of objects in world coordinate system, which is three-dimensional. To achieved image transformation, camera intrinsic calibration and hand-eye calibration are indispensable, and the details are presented in this chapter. Since the camera used in this project is unable to provide depth information, so deriving the depth information is critical, which is achieved by EPnP algorithm. The image process is finished in Python 3.7 environment, with support of OpenCV libraries. 
