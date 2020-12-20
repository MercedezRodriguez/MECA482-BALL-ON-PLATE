

# MECA482 BALL ON PLATE
##### Group: Maria Rodriguez, Anthony McKinney, Catherine Crichton, David Nguiffo, Aiden Williams


## 1. INTRODUCTION
###### Our Ball On PLate system consists of plate, touch screen and servo motor. The Touch screen is placed over the plate and our goal is to balance a freely rolling ball in a specific position OR to move it in a trajectory on the plate with the least possible error and smallest settling time achieved for the dynamics of the real time system.  A linear mathematical model of the system is derived to find the relationship between input and output and MATLAB is used to evaluate the closed loop system response and determine the PID parameters. 
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
###### Our design was created with the criteria of 
###### - 3 seconds settling time
###### - 5% Overshoot
###### The root locus control method was implemented to control the ball-on-plate system. The Root Locus method was selected due to its ease of implementation and its ability to predict the performance of the entire system. Using the equations for Settling Time(Eq. 6) and Percent Overshoot (Eq. 7)

![Alt Text](https://user-images.githubusercontent.com/75716205/102709193-eddc6300-425c-11eb-8a0c-d714d8978f9d.png)



###### From the equations above we obtained a Settling time and naatral frequency of:

![Alt Text](https://user-images.githubusercontent.com/75716205/102709371-ed44cc00-425e-11eb-9cf0-27d8d65ff037.png)

###### We used **Root Locus** to design our controller, we used **Matlab** to show us the roots and poles of our transfer function. Below is the sgrid function + rlocus function 

![Alt Text](https://user-images.githubusercontent.com/75716205/102709492-0306c100-4260-11eb-9d7f-77d91a802dd3.png)


###### Note the green and blue lines fall on the imaginaryaxis but no inside the area of interest. To correct this, a ** Lead/Lag** compensator was introduced. To give s the resuts below: 

![Alt Text](https://user-images.githubusercontent.com/75716205/102709692-8674e200-4261-11eb-947a-1d3166693541.png)




![Alt Text](https://user-images.githubusercontent.com/75716205/102710303-495f1e80-4266-11eb-80d2-cb2d5615d97d.png)




###### This is a **closed loop system**, therfore locating the poles and zeros is essential.The gain helped provide power, and is the relationship between;
###### -the magnitude of input
###### -magnitude of the output when the system is at a steady state.
###### The poles and zeros refer to the frequency of the TF. They are used to determine whether or not the system is stable. 
###### The zeros are calculated by setting the numerator to zero and solving for the s-variable. And the poles are calculated the same way except are in the denominator of the transfer function


![Alt Text](https://user-images.githubusercontent.com/75716205/102710560-ee2e2b80-4267-11eb-92dd-8854d94f0cd3.png)



## 4b. Simulink














## 4c. Coppelia and Simulink
















 
