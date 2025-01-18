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

### Observations