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

This code implements a Monte Carlo Localization (MCL) algorithm for a robot using particles to estimate its position on a map.

  1. get_map(): Loads the map image from the provided URL and converts it into a binary map (0 for obstacles, 255 for free space).

  2. initialize_particles_map(size, map_array): Initializes the particles by selecting random positions in free space on the map and assigning random yaw (orientation).

  3. propagate_particles_velocity(particles, dt): Propagates the particles' positions based on a constant velocity and adds noise. The particles' new positions are calculated using basic kinematics.

  4. compute_particle_weights_parallel(particles, laser_data, map_array): Computes the weight of each particle based on how well its virtual laser readings match the real laser data. This is done in parallel using multiprocessing to speed up the computation.

  5. compute_single_particle_weight(particle, laser_data, map_array): Helper function that computes the weight of a single particle by comparing its virtual laser readings to the actual laser data.

  6. resample_particles(particles, weights): Resamples the particles based on their weights using importance sampling, with higher-weight particles having a higher chance of being selected.

  7. parse_laser_data(): Retrieves and processes the laser data by selecting a subset of beams based on LASER_NUM_BEAMS.

  8. virtual_laser_beam(start_x, start_y, end_x, end_y): Performs ray tracing to simulate a laser beam from a starting point to an endpoint. The function returns the point where the laser hits an obstacle, or the endpoint if no obstacle is encountered.

  9. get_virtual_laser(particle, map_array): Simulates laser readings from a given particle's position. It uses the virtual laser beam function for each laser beam and computes the distances to the obstacles in the environment.

  10. estimate_position(particles, weights): Computes the estimated position of the robot by calculating the weighted average of the particles' positions and orientations.

#### Parameters

These have been the parameters used:

INIT_XY_STD = 0.2

INIT_ANGLE_STD = 0.1

PROPAGATION_XY_NOISE_STD = 0.005

PROPAGATION_ANGLE_NOISE_STD = 0.001

LINEAR_VEL = 0.4

ANGULAR_VEL = 0.8

OBSTACLE_VALUE = 0

FREE_VALUE = 255

MAX_LASER_DISTANCE = 10

LASER_NUM_BEAMS = 10

RAYTRACING_SKIP_STEPS = 1

The number of particles can be chosen by the user. In the following videos I have made examples with 100, 300, 500 and 1000 particles

#### Videos

Video 100 particles:


[Screencast from 2025-01-26 17-26-52.webm](https://github.com/user-attachments/assets/d90071a0-db00-406e-a4f6-bb346f2f6133)

Video 300 particles:



https://github.com/user-attachments/assets/0a01ea52-e78b-48c7-bc8d-2c8e646a560e



Video 500 particles:



https://github.com/user-attachments/assets/9aa343e3-820f-4676-a9fb-b67022d10c7b


Video 1000 particles:



[Screencast from 2025-01-26 17-25-16.webm](https://github.com/user-attachments/assets/8d18f1b0-b741-4102-b1cd-7845bd4fc64b)



### Observations

As can be seen from the performance of the videos, the more particles are used in the algorithm, the higher its computational cost will be, which will slow down self-localization.
