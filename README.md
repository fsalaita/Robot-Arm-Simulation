# Introduction
1. This project displays the equations for the equations for θ1(t) and θ2(t) with the values found for the coefficients (a1, a2, a3) and (b1, b2, b3).
2. Creates a time vector from 0 to 2 sec with 100 points. Utilizing the equations found in part (a) and the equation for x and y, plot the path of the robotic hand from t=0 until t=tf.

## Input Data

clear;

clc;

close all

L1 = 4; L2 = 3;

theta1=[-19 43];

theta2=[44 151];

t = [0 2];

x = [6.5 0];

y = [0 2];

tf=t(2);

A=[tf^3 tf^4 tf^5;3*tf^2 4*tf^3 5*tf^4;6*tf 12*tf^2 20*tf^3];

theta1_in=[theta1(2) - theta1(1);0;0];

a=A\theta1_in;

theta2_in=[theta2(2) - theta2(1);0;0];

b=A\theta2_in;

## Coefficients for robotic arm motion

disp(' a1 a2 a3')

disp(a')

disp(' b1 b2 b3')

disp(b')

 a1 a2 a3
 
 77.5000 -58.1250 11.6250
 
 b1 b2 b3
 
 133.7500 -100.3125 20.0625
 

## Plot arm angles vs time

t=linspace(0,2,100);

ftheta1 = theta1(1) + a(1)*t.^3 + a(2)*t.^4 + a(3)*t.^5;

plot(t,ftheta1,'linewidth',2);

grid

xlabel('t');ylabel('\theta_1(t)')

title('Shoulder to upper arm angle')

ftheta2 = theta2(1) + b(1)*t.^3 + b(2)*t.^4 + b(3)*t.^5;

figure()

plot(t,ftheta2,'linewidth',2);

grid

xlabel('t');ylabel('\theta_2(t)')

title('Elbow to forearm angle')

figure()

![image](https://github.com/fsalaita/RobotArmSimulation/assets/146680465/046a34ed-1eb8-4101-95dc-c519cea64fb8)

![image](https://github.com/fsalaita/RobotArmSimulation/assets/146680465/1ab98242-bc5a-4407-942d-4ee5a69cbd20)

## Plot hand trajectory

fx=L1*cos(ftheta1*pi/180) + L2*cos((ftheta1 + ftheta2)*pi/180);

fy=L1*sin(ftheta1*pi/180) + L2*sin((ftheta1 + ftheta2)*pi/180);

plot(fx,fy,'linewidth',2);

grid

xlabel('x');ylabel('y')

title('Trajectory of Robotic Arm Hand')

![image](https://github.com/fsalaita/RobotArmSimulation/assets/146680465/3b598d35-5c99-4a07-a431-e29bdf289c9d)


