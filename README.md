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
![Screenshot from 2024-09-25 19-58-23](https://github.com/user-attachments/assets/1262813c-2042-4e55-b4f0-0b177d0507b7)

## Final algorithm

The robot follows a finite state machine (FSM) model to decide its behavior based on sensor inputs and time-based triggers. It transitions between four states:

  - SPIRAL: Moves in a gradually increasing outward spiral.
  - FORWARD: Moves straight ahead at a set speed.
  - TURN: Randomly rotates in place by a random angle.
  - BACK: Moves backward briefly to avoid obstacles.

Here is the diagram of the states used and their transitions:

![image](https://github.com/user-attachments/assets/3ae03de2-53a2-4353-8c16-a12b69de8e6c)



It begins in the SPIRAL state, moving in a widening spiral while gradually increasing speed. After an obstacle is detected, it transitions to BACK, moving backward for a brief period to avoid obstacles. The robot then switches to TURN, where it rotates by a random angle. Once the turn is complete, it randomly decides to either return to SPIRAL (30% probability) or move FORWARD (70% probability) in a straight line. If an obstacle is detected while moving FORWARD, the robot transitions back to BACK, and the cycle repeats.

Here are some videos of the algorithm working:
These videos are at x4 speed

https://github.com/user-attachments/assets/e94a9eff-d04a-4e3b-9253-38ae4391ef70

https://github.com/user-attachments/assets/6f952e10-9143-47c6-83b3-df8b4b8999bc


## Observations

In the red zones, once the robot enters, it will be difficult to exit since they are areas with limited space and it will take a while to exit since the TURN turns are random.
On the other hand, if the robot enters green areas, it gets stuck since the space between the leg of the table and the sofa is the same size as that of the robot vacuum cleaner.

![image](https://github.com/user-attachments/assets/5003e394-62b4-4238-96cb-7bdc1a48f7c2)


