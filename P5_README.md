## Practice 5: MonteCarlo laser-based robot localization

### GOAL

The aim of this practical is to develop a localization algorithm based on the particle filter using the robot’s laser.

### First days

During the first few days I was trying out the examples that the teacher gave us. In these first tests the algorithm generated the particles near the position of the robot. That's why the first change was to spread out all the initialized particles.

Before:

![image](https://github.com/user-attachments/assets/be134b4a-b3d2-492f-a1f1-b73edade4292)

After:

![image](https://github.com/user-attachments/assets/b9a1d542-fa06-4d3e-9ed4-7890c848eebf)



### Final algorithm

Video 100 particles:


[Screencast from 2025-01-26 17-26-52.webm](https://github.com/user-attachments/assets/d90071a0-db00-406e-a4f6-bb346f2f6133)

Video 300 particles:



https://github.com/user-attachments/assets/0a01ea52-e78b-48c7-bc8d-2c8e646a560e



Video 500 particles:



https://github.com/user-attachments/assets/9aa343e3-820f-4676-a9fb-b67022d10c7b


Video 1000 particles:



[Screencast from 2025-01-26 17-25-16.webm](https://github.com/user-attachments/assets/8d18f1b0-b741-4102-b1cd-7845bd4fc64b)



### Observations
