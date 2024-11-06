
## Practice 4: Global Navigation using TeleTaxi

### GOAL

The objective of this practice is to implement the logic of a Gradient Path Planning (GPP) algorithm. Selected a destination, the GPP algorithm is responsible for finding the shortest path to it, avoiding, in the case of this practice, everything that is not road. Once the path has been selected, the logic necessary to follow this path and reach the objective must be implemented in the robot. With this, it is possible for the robot to go to the marked destination autonomously and following the shortest path.

### First days

During these first days I have been playing with the teacher's examples. The second day I started with the cost map

![image](https://github.com/user-attachments/assets/1ec4714f-a61a-46e7-b528-62769ae2cb82)

![image](https://github.com/user-attachments/assets/7a5e9df1-75ba-4471-a9c8-31eda1a35565)

At the moment it makes the entire map (image) but it will be improved so that it only goes to the car to improve performance and not use unnecessary data

