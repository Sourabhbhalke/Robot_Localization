# Robot Localization with Particle Filters
https://www.youtube.com/watch?v=eTF_eHrCTTE&ab_channel=Sourabh.in.Germany
## Overview

This project demonstrates a robot localization system using particle filters, leveraging computer vision (CV2) and NumPy. The objective is to accurately locate a robot within a terrain map by implementing a particle filter algorithm to estimate the robot's position based on noisy sensor data.

## Project Components

1. **Map and Coordinate System:**
   - **Map:** A grayscale image where pixel intensity represents terrain height. Loaded using OpenCV (`cv2.imread`).
   - **Coordinate System:** The origin `(0, 0)` is at the top-left corner of the image. The map height is given by `map(Y, X)`.

2. **Particle Filter Algorithm:**
   - **Particle Initialization:** Particles are initialized randomly across the map with random orientations.
   - **Motion Model:** The robot's movement incorporates Gaussian noise to simulate real-world uncertainties in forward movement and turning.
   - **Sensor Model:** The robot's sensor readings are simulated with noise, where the elevation at `(x, y)` coordinates is compared to sensor measurements.
   - **Weight Computation:** Particle weights are computed based on the error between the particle's predicted sensor readings and the actual sensor data.
   - **Resampling:** Particles are resampled based on computed weights to focus on more probable states.
   - **Noise Addition:** Additional Gaussian noise is added to particles to maintain diversity and prevent degeneracy.

3. **Key Functions:**
   - `get_input()`: Reads keyboard input to control robot movement.
   - `move_robot()`: Applies motion to the robot with noise.
   - `move_particles()`: Moves particles based on the robot's movement.
   - `sense()`: Simulates sensor readings with optional noise.
   - `compute_weights()`: Calculates particle weights based on sensor readings.
   - `resample()`: Resamples particles based on computed weights.
   - `add_noise()`: Adds noise to particles to ensure diversity.
   - `display()`: Visualizes the map, robot position, and particles.

## Setup and Usage

1. **Dependencies:**
   - Python 3.x
   - NumPy
   - OpenCV (`cv2`)

2. **Execution:**
   - Ensure the map image (`map.png`) is in the project directory.
   - Run the script using a Python environment that includes the required dependencies.
   - Use arrow keys for control:
     - Up arrow: Move forward.
     - Right arrow: Turn right.
     - Left arrow: Turn left.
     - ESC: Stop and exit.

3. **Visualizations:**
   - The map, robot position, and particle cloud are visualized using OpenCV's `imshow` function.

## Technical Details

- **Particle Filter:** A Monte Carlo method to estimate the state of a system through a set of weighted samples (particles).
- **Gaussian Noise:** Introduced to simulate real-world uncertainties in robot movement and sensor readings, controlled by parameters `SIGMA_STEP` and `SIGMA_SENSOR`.
- **Resampling:** Prevents particle degeneration by concentrating on high-probability states.
- **Noise Addition:** Ensures particles remain diverse and avoid clustering.

## Note

This project demonstrates the fundamental principles of particle filters in robot localization and can be extended or integrated into more complex systems involving real-world sensors and robotics.

