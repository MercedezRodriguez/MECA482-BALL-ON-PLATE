# MECA482 BALL ON PLATE
Group: Maria Rodriguez, Anthony McKinney, Catherine Crichton, David Nguiffo, Aiden Williams


## 1. INTRODUCTION
###### Our Ball ON PLate system consists of plate, touch screen and servo motor. The Touch screen is placed over the plate and our goal is to balance a freely rolling ball in a specific position OR to move it in a trajectory on the plate with the least possible error and smallest settling time achieved for the dynamics of the real time system.  A linear mathematical model of the system is derived to find the relationship between input and output and MATLAB is used to evaluate the closed loop system response and determine the PID parameters. 
## 2. MODELING
##### Our Ball and Plate system is shown below labeled Figure 1.
![Alt Text](https://user-images.githubusercontent.com/75716205/102707421-9daad400-424f-11eb-8677-3b076ca3c2f3.png)
##  3. Equations
###### The system was modeled with the assumption that the kinetic energy of he plate is negligible and that the servo-motors controlling motion in the x-z and y-z planes are uncoupled. Throught he force balanced Equation in the direction normal to the plate, a governing equation was derived below. (Equation 1.)
![Alt Text](https://github.com/MercedezRodriguez/MECA482-BALL-ON-PLATE/issues/2#issue-771535796)

The angle of the servo-motor ( thetamax) and the angle of the plate (Phi x) and through the following equations can be related: 


 
