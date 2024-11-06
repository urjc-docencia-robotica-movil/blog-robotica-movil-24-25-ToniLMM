## Practice 3: Local navigation with VFF 

The objective of this practice is to implement the logic of the VFF navigation algorithm.

Navigation using VFF (Virtual Force Field), consists of:

  - Each object in the environment generates a repulsive force towards the robot.

  - Destiny generates an attractive force in the robot.

This makes it possible for the robot to go towards the target, distancing itself of the obstacles, so that their address is the vector sum of all the forces.

### First days

Already having a code, I had to tweak it since the platform has changed things compared to last year. On the other hand, when seeing how it works, local minimums have appeared which I have had to solve by adding the 'escape_local_minimum()' function.

### Final algorithm

This algorithm implements a VFF navigation, combining attractive and repulsive forces to guide the car toward a target while avoiding obstacles. This is divided into 6 blocks:

1. Relative Coordinates:

   First, the code converts the target's absolute coordinates into relative coordinates based on the robot's position and orientation. This makes it easier to calculate the attractive force toward the target from the robot's perspective.

2. Attractive Force:

   Using the relative coordinates, an attractive force towards the target is calculated. This force has a capped magnitude (maximum of 2) to prevent the robot from accelerating too quickly as it approaches the target.

3. Repulsive Force:

   Using laser sensor data, the code generates a repulsive force that acts in the opposite direction of detected obstacles. This force helps the robot avoid obstacles in its path.

4. Escaping Local Minimum:

   If the robot gets stuck (moving very little over a defined time), it enters an "escape" mode, which makes it move forward and turn slightly to to free itself from local minimum.

5. Calculating and Applying Velocities:

   Finally, the combined attractive and repulsive forces determine the robot's linear and angular velocities. Limits are applied to prevent sharp turns, and the calculated velocities are sent to the robot through the HAL module.

6. Visualization:

    The code uses the GUI module to display the attractive, repulsive, and resulting forces, along with the local target. This helps monitor the robot’s behavior in real time.

Here is the video of the final version working:

https://github.com/user-attachments/assets/93bd2596-064f-410d-9abe-5df805e947bf

### Observations

During the first days I found 2 local minimums (the attractive and repulsive force cancel each other, giving a resulting vector of 0), which I solved with 'escape_local_minimum()' function. This function is very simple, it is activated when it detects that the car has not traveled more than 5 meters in 5 seconds (because it is stopped or moving too slowly), therefore when it is activated the car advances and turns slightly for 3 seconds, which which causes the forces to no longer cancel each other out and the algorithm to work again.

This solution works due to the characteristics of this circuit, however with other conditions this function could be modified so that it followed the right wall until it left the local minimum, all of this depends on the case.

[Screencast from 2024-10-25 11-19-01.webm](https://github.com/user-attachments/assets/6e562e4a-1f1b-4b2f-b2eb-ce4d6e454456)

