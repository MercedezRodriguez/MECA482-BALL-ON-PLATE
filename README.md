

# MECA482 BALL ON PLATE
##### Group: Maria Rodriguez, Anthony McKinney, Catherine Crichton, David Nguiffo, Aiden Williams


## 1. INTRODUCTION
###### The **Ball on Plate** project is a system that consists of a ball balanced on a sensored plate. The plate tilts according to the position of the ball. Two servo-motors with linkage arms attached to the plate control its tilt angle as can be seen in Fig. 1. The two servo-motors are uncoupled, meaning that one servo-motor controls motion in the x-z-plane while another controls motion in the y-z-plane. Coppelia Sim, connected to MatLab and Simulink, will simulate the mathematical model of the entire system. The control algorithm tests the system to ensure that it meets the requirements. The system’s basic patterns must be able to conduct are to move a ball in a square at the four corner points of the plate, move the ball in a triangle, and move the ball in a circle. It must also stabilize itself and bring the ball back to the center origin of the plate when it is knocked off balance 
https://github.com/MercedezRodriguez/MECA482-BALL-ON-PLATE/issues/21#issue-771876357
## 2. MODELING
##### Our Ball and Plate system is shown below labeled Figure 1.
![Alt Text](https://user-images.githubusercontent.com/75716205/102710637-84625180-4268-11eb-9796-e548042e480f.png)
##  3. Equations
###### The system was modeled with the assumption that the kinetic energy of he plate is negligible and that the servo-motors controlling motion in the x-z and y-z planes are uncoupled. Throught he force balanced Equation in the direction normal to the plate, a governing equation was derived below. (Equation 1.)
![Alt Text](https://user-images.githubusercontent.com/75716205/102708141-9090e380-4255-11eb-8bba-21f7c3c5faf1.png)

###### The angle of the servo-motor ( thetamax) and the angle of the plate (Phi x) and through the following equations can be related: 
![Alt Text](https://user-images.githubusercontent.com/75716205/102708206-1ca30b00-4256-11eb-8ff4-88eaf7a5370f.png)


###### Now we take th LaPlace transform of both Eq. 1 and Eq. 2:

![Alt Text](https://user-images.githubusercontent.com/75716205/102708241-65f35a80-4256-11eb-8e8b-797b9aeff15e.png)






###### With **small angle aproximation** Eq3.  was linearized with the assumption that **sin(theta)max=thetam,x**:


![Alt Text](https://user-images.githubusercontent.com/75716205/102708237-5411b780-4256-11eb-8052-bbe4c2386c3f.png)




###### Now with Eq. 4, our **Transfer Function** can be found: 



![Alt Text](https://user-images.githubusercontent.com/75716205/102708250-77d4fd80-4256-11eb-8e24-d4c33654f7e8.png)

## 4. Contoller Design and Simulations
## 4a. Controller
###### The root locus control method was implemented to control the ball-on-plate system. The
###### Root Locus method was selected due to its ease of implementation and its ability to predict the
###### performance of the entire system.The initial assumptions for the system were that it needed to have a settling time less than or equal to three seconds and less than a 5% overshoot. Using the settling time equation (Eq. 7) and the percent overshoot equation (Eq. 8) the values for the damping ratio and natural frequency of the system were found to be ζ = 0.7 and ωn = 1.9 Hz.

###### Our design was created with the criteria of 
###### - 3 seconds settling time
###### - 5% Overshoot
###### The root locus control method was implemented to control the ball-on-plate system. The Root Locus method was selected due to its ease of implementation and its ability to predict the performance of the entire system. Using the equations for Settling Time(Eq. 6) and Percent Overshoot (Eq. 7)

![Alt Text](https://user-images.githubusercontent.com/75716205/102709193-eddc6300-425c-11eb-8a0c-d714d8978f9d.png)


##### The pole locations with acceptable percent overshoot and settling time can be visualized in the figure below. Poles, where the percent overshoot is less than 5%, are located in the area between the 0.7 lines. Poles with a settling time less than 3 seconds are located in the area inside of the curved line. The green and blue lines fall on the imaginary axis but not inside any of the areas of interest. The root locus can be adjusted into an area of stability by utilizing either a lead or lag compensator. A lead compensator would increase the stability and speed of response while a lag compensator would reduce the amount of error in a system. Stability and response time are important factors in the ball-on-plate model so a lead compensator was selected for this project.

###### From the equations above we obtained a Settling time and natural frequency of:

![Alt Text](https://user-images.githubusercontent.com/75716205/102709371-ed44cc00-425e-11eb-9cf0-27d8d65ff037.png)

###### We used **Root Locus** to design our controller, we used **Matlab** to show us the roots and poles of our transfer function. Below is the sgrid function + rlocus function 

![Alt Text](https://user-images.githubusercontent.com/75716205/102709492-0306c100-4260-11eb-9d7f-77d91a802dd3.png)


###### Note the green and blue lines fall on the imaginary axis but not inside the area of interest. To correct this, a ** Lead/Lag** compensator was introduced. To give s the resuts below: 

![Alt Text](https://user-images.githubusercontent.com/75716205/102709692-8674e200-4261-11eb-947a-1d3166693541.png)

###### Using an iterative process to determine values, placing a zero of 0.01 and a pole of 5 into the lead compensator yielded the results in Fig. 5. The lead compensator function is:


![Alt Text](https://user-images.githubusercontent.com/75716205/102710303-495f1e80-4266-11eb-80d2-cb2d5615d97d.png)

###### Where the magnitude of z0 (0.01) is less than p0 (5). A gain value, K, was determined fromEq. 9 for the system for use in Simulink.
###### The control system is a closed-loop, meaning it is critical to identify the poles and zeros. The root locus focuses on how the roots of the system change with a variation of its parameters. The root locus is incorporated with the feedback system on the s-plane. Fig. 6 was generated in MatLab and calculated the gain, poles, damping, percent overshoot, and frequency. The selected point, gain, and resulting poles can be seen in Fig. 7. The gain is the relationship between the magnitude of input and the magnitude of the output when the system is at a steady state. The poles and zeros refer to the transfer function frequency and are used to determine whether or not the system is stable. The damping ratio refers to how much the system oscillates. A damping ratio of 0.967 means that the system absorbs 96.7% of the frequency due to vibration and shock energy. The percent overshoot is in reference to how much the output exceeds its final steady-state value. It is best to have a low percent overshoot value to prevent errors in the system’s data or performance.




![Alt Text](https://user-images.githubusercontent.com/75716205/102710560-ee2e2b80-4267-11eb-92dd-8854d94f0cd3.png)



## 4b. Simulink
###### Simulink is used to create a mathematical model of the ball is utilized to test the lead compensator. Below is our Simulink Block Diagram. The Simulink model's purpose is to take the current position of the ball and give an output of the expected position of the ball. 

![Alt Text](https://user-images.githubusercontent.com/75716205/102742938-1458d780-430b-11eb-9638-ffd6b13ee43b.png)










## 4c. Coppelia and Matlab
###### Coppelia is used to create simulaions via Simulin Models . Below is our code used in Coppelia , which is how Matlab gets the coordiates of where the ball is located on the plate. Below are figures of how Coppelia and Matlab communicate as well as our Joint Test Code.
###### Joint Test
![Alt Test](https://user-images.githubusercontent.com/75716205/102741758-0f465900-4308-11eb-933a-1315435ad527.png)
![Alt Text](https://user-images.githubusercontent.com/75716205/102742096-f0949200-4308-11eb-982f-379485984fb1.png)
![Alt Text](https://user-images.githubusercontent.com/75716205/102742148-15890500-4309-11eb-9ba4-56d4cf3014e2.png)

###### Coppelia Code
![Alt Text](https://user-images.githubusercontent.com/75716205/102742538-fc348880-4309-11eb-87c4-1029f11d5937.png)
![Alt Text](https://user-images.githubusercontent.com/75716205/102742589-1a9a8400-430a-11eb-86ab-77dd726bf1e9.png)

## Summary
###### Our system still requires several adjustments,but our servo motors  are working correctly as expected. 
###### Below is the Final Report 
https://github.com/MercedezRodriguez/MECA482-BALL-ON-PLATE/issues/23#issue-771903116













 
