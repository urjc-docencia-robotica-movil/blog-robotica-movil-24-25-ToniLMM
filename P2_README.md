
## Practice 2: Follow line

This second practice consists of a Formula 1 car that must follow the center of the red line and complete the circuit as quickly as possible. The goal of this exercise is to perform a PID reactive control capable of following the line painted on the racing circuit

### First days

Having already made the code, I have been improving the code and lowering the track times. I have tried many things such as raising the centroid to anticipate the curves in advance, increasing the maximum speed both on straight lines and in curves... However, the behavior did not vary too much so I have left the code as at the beginning with slight changes

### Final version
This final version is a mix of speed and staying on top of the line as much as possible. However, speed is prioritized a little more than going above the line, because minimum times are required in this practice. Even if speed is prioritized, line tracking continues at all times. If it is necessary to be on top of the line all time, the maximum speed can be reduced and the PIDs adjusted, in this way the car can correct its trajectory more efficiently and effectively and make smoother movements.

### Algorithm explanation

This algorithm controls the speed and steering of a vehicle navigating a track, using a camera to detect the path and a PID (Proportional-Integral-Derivative) controller to adjust its movement. It specifically handles straight sections and curves differently by adjusting the linear and angular velocities accordingly. This is divided into 4 blocks:

1. Image Processing:

    The image_filtering function processes an image from the camera, using HSV color filtering to isolate red contours on the track. It calculates the center of the largest red object (red path) and displays a reduced version of the image.

2. Curve Detection:

    The is_curve function checks if the vehicle is on a curve by analyzing the deviation of the detected object's center from the reference center of the image. If the deviation exceeds a threshold, it considers the current position as a curve.

3. Speed Control:

    The speed function uses a PID controller to adjust the linear velocity (V) and angular velocity (W) based on whether the vehicle is on a straight section or a curve. It decreases the velocity when on curves and gradually increases it on straight sections. The angular velocity is controlled by PID, taking into account the position error of the object in the camera's field of view.

4. Main Loop:

    In the main loop, the camera captures an image, processes it to determine the object's center, checks if the vehicle is on a curve, and adjusts the speed (V) and angular velocity (W) accordingly. The vehicle's linear speed increases over time on straight sections but decreases on curves.

Here is the video of the final version working (recording screen final time = 67.82):

https://github.com/user-attachments/assets/6da8bf55-93b4-4801-81fa-78c1ed1dfb86

Without the burden of having to record the screen, the time improves by approximately 5 seconds (final time = 63.20s):

https://github.com/user-attachments/assets/e551b67d-c586-4881-9cb1-4d136058774c

It also has a function implemented that looks for the red line:

[Screencast from 2024-10-13 18-55-27.webm](https://github.com/user-attachments/assets/c5c8a4f1-57cb-44e7-b2b1-d6efc410e620)

### ACKERMAN

The Ackerman model has been difficult to control and with the values ​​that I have tried I have not completely succeeded since the car oscillates a lot, however by changing the parameters and setting Vmax to 15 I have managed to complete the circuit in 160 seconds

https://github.com/user-attachments/assets/44c9a636-3803-4e91-87fd-474604ff8172

## Observations

To date, my best lap has been approximately 56 seconds with changes in the code, however they were tests since the car deviated a lot and the relationship between following the line and going at a good speed was broken. It should also be noted that times may vary due to computer performance.





