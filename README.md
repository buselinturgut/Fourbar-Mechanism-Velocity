# Fourbar-Mechanism-Velocity


clc;clear all;
a= 250;
b= 353.75;
c= 280;
d= 650;
w=2;

theta = degtorad(330);
k1= d/a;
k2= d/c;
k3= (a^2-b^2+c^2+d^2)/(2*a*c);
k4= d/b;
k5= (-c^2+d^2+a^2+b^2)/(2*a*b);

mod = -1;

A= cos(theta)-k1-k2*cos(theta)+k3;
B= -2*sin(theta);
C= k1- (k2+1)*cos(theta)+k3;

theta4=  radtodeg(2*atan((-B+mod*sqrt(B^2-4*A*C))/(2*A)));

D= -cos(theta)+k1-k4*cos(theta)+k5;
E= 2*sin(theta);
F= -k1+(-k4+1)*cos(theta)+k5;

theta3= radtodeg(2*atan((-E-mod*sqrt(E^2-4*D*F))/(2*D)));

M = [-b*sin(degtorad(theta3)),c*sin(degtorad(theta4));-b*cos(degtorad(theta3)),c*cos(degtorad(theta4))];
M1 = [a*w*sin(theta);a*w*cos(theta)];
M2 = inv(M)*M1;
