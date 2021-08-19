# GSoC'21 RoboComp project: Simultaneous path planning and following using Model Predictive Control (SPAF)

19th August, 2021

# Differential Robot
Many mobile robot use differential drive mechanism in their motion. By definition, it consists of two wheels mounted on a common axis, where each wheel must rotate about a point lying on it know as the Instantaneous Center of Curvature (ICC), and each wheel can be driven independently in a direction. The equations of the velocity for each side (right and left) can be described as follows: 

<img src="https://latex.codecogs.com/gif.latex?\bg_white&space;v_r&space;=&space;w&space;(R&space;&plus;&space;l/2)" /> and 
<img src="https://latex.codecogs.com/gif.latex?\bg_white&space;v_l&space;=&space;w&space;(R&space;-&space;l/2)" />

Knowing that "w" is the angular velocity, "R" the signed distance from the ICC to the midpoint between the wheels, and finally "l" is the distance between the centers of the two wheels.

In order to switch between the omni-directionnal wheeled robot and the differential robot, a flag was added. It sets the lower and upper bounds of a a velocity of a certain direction (i.e, X-direction) to satisfy the mecanum wheeled's inverse kinematic model. The idea is simply assume that we have two wheels instead of four, and equating the right side with the left one as by the differential mode's definition explained earlier. 

```python
# TODO: revert the old function for point stabilzation
controlMPC = self.controller.compute(initialState, 
                                    X_COEFFS, 
                                    Y_COEFFS, 
                                    isDifferential=True)
```
# The Simulation
By giving the robot a point " PUT A POINT" as a target to compare the motion between differential mode and omni-directional mode.
1. **Differential Mode:**
![diff_mode](ADD VIDEO IN ASSETS)

2. **Omni-directionnal Mode:**
![omni_mode](ADD VIDEO IN ASSETS)
