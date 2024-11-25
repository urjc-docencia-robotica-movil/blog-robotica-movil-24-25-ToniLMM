
## Practice 4: Global Navigation using TeleTaxi

### GOAL

The objective of this practice is to implement the logic of a Gradient Path Planning (GPP) algorithm. Selected a destination, the GPP algorithm is responsible for finding the shortest path to it, avoiding, in the case of this practice, everything that is not road. Once the path has been selected, the logic necessary to follow this path and reach the objective must be implemented in the robot. With this, it is possible for the robot to go to the marked destination autonomously and following the shortest path.

### First days

During these first days I have been playing with the teacher's examples. The second day I started with the cost map

![image](https://github.com/user-attachments/assets/1ec4714f-a61a-46e7-b528-62769ae2cb82)

![image](https://github.com/user-attachments/assets/7a5e9df1-75ba-4471-a9c8-31eda1a35565)

At the moment it makes the entire map (image) but it will be improved so that it only goes to the car to improve performance and not use unnecessary data

### Final algorithm

1. Map Initialization:
   
   The city map is loaded as a 2D numpy array from an image file. The map is processed to distinguish accessible (white) areas from obstacles (black), and a cost grid is initialized to store computed path costs.

2. Gradient Cost Calculation:
   
   The calculate_cost_gradient function computes a wavefront-based cost gradient starting from the target location. It propagates costs outward, marking obstacles and expanding their influence after the gradient calculation. This ensures paths are planned around obstacles. The process uses a breadth-first search with priority for lower costs.

3. Obstacle Expansion:
   
   The expand_obstacles function enlarges obstacles within a specified radius, making them less likely to be traversed by the robot during pathfinding.

4. Path Extraction:
   
   The path_extraction function derives the shortest path from the robot's current position to the target by following the cost gradient. It uses a greedy approach, always selecting the next step with the lowest cost.

5. Robot Movement:
    
   The move_robot function guides the robot along the extracted path. It uses real-time pose data to calculate the distance and orientation to the next waypoint and adjusts linear and angular velocities accordingly. The robot stops when it reaches the goal.

6. Main Loop:
    
   The main loop continuously updates the robot's position and listens for a new target input from the GUI. When a target is selected, the system recalculates the cost gradient and path, and commands the robot to navigate toward the goal.

Here are a few videos of the final version working:

[Screencast from 2024-11-25 14-18-27.webm](https://github.com/user-attachments/assets/cae32769-540e-4523-aa2b-92ccde926b4a)

[Screencast from 2024-11-25 14-30-08.webm](https://github.com/user-attachments/assets/d47c7c6d-402d-4c59-8593-785abed87592)

[Screencast from 2024-11-25 14-34-23.webm](https://github.com/user-attachments/assets/7324cada-5f21-4d44-9feb-6adf54474a2e)

[Screencast from 2024-11-25 14-37-13.webm](https://github.com/user-attachments/assets/e8e58190-b4d6-4d0e-b89b-589b6a40f3b2)

[Screencast from 2024-11-25 14-41-03.webm](https://github.com/user-attachments/assets/f247cc05-ceef-4fee-b46c-52310205b679)
