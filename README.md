# Blog Robótica Móvil 2024-2025
This will be Toni's Mobile Robotics blog, where the status of the practices, their news, progress, errors and solutions will be reported.

# Index

* [Index][Ind]
* [Practice 1][p1]

[Ind]: https://github.com/urjc-docencia-robotica-movil/blog-robotica-movil-24-25-ToniLMM/blob/main/README.md/#index
[p1]: https://github.com/urjc-docencia-robotica-movil/blog-robotica-movil-24-25-ToniLMM/blob/main/README.md/#practice-1-basic-vacuum-cleaner

## Practice 1: Basic Vacuum Cleaner

### Day 1
Today I implemented the code structure that I had already made and ran it to see if it still worked. Changes will be made to this code to improve its efficiency and apply improvements
![Screenshot from 2024-09-16 10-15-19](https://github.com/user-attachments/assets/3d073f8d-0234-4de1-a126-09db35507f13)

## Final algorithm

The robot follows a finite state machine (FSM) model to decide its behavior based on sensor inputs and time-based triggers. It transitions between four states:

  - SPIRAL: Moves in a gradually increasing outward spiral.
  - FORWARD: Moves straight ahead at a set speed.
  - TURN: Randomly rotates in place by a random angle.
  - BACK: Moves backward briefly to avoid obstacles.

Here is the diagram of the states used and their transitions:

![image](https://github.com/user-attachments/assets/60d67063-7475-407d-8950-44ebb9b6ab55)


It begins in the SPIRAL state, moving in a widening spiral while gradually increasing speed. After a set time, it transitions to BACK, moving backward for a brief period to avoid obstacles. The robot then switches to TURN, where it rotates by a random angle. Once the turn is complete, it randomly decides to either return to SPIRAL (40% probability) or move FORWARD (60% probability) in a straight line. If an obstacle is detected while moving FORWARD, the robot transitions back to BACK, and the cycle repeats.

