# Robotic-System
#Code for optimization
% pos = [L2*cosdd(th(1))*cosdd(th(2)) + L3*cosdd(th(1))*cosdd(th(2))*cosdd(th(3)) - L3*cosdd(th(1))*sindd(th(2))*sindd(th(3))
%  L2*cosdd(th(2))*sindd(th(1)) + L3*cosdd(th(2))*cosdd(th(3))*sindd(th(1)) - L3*sindd(th(1))*sindd(th(2))*sindd(th(3))
%                             L2*sindd(th(2)) + L3*cosdd(th(2))*sindd(th(3)) + L3*cosdd(th(3))*sindd(th(2))];
pos=[L2*cosd(th(1))*cosd(th(2)) + L3*cosd(th(1))*cosd(th(2))*cosd(th(3)) - L3*cosd(th(1))*sind(th(2))*sind(th(3))
 L2*cosd(th(2))*sind(th(1)) + L3*cosd(th(2))*cosd(th(3))*sind(th(1)) - L3*sind(th(1))*sind(th(2))*sind(th(3))
                       L1 - L2*sind(th(2)) - L3*cosd(th(2))*sind(th(3)) - L3*cosd(th(3))*sind(th(2))]
fmin=sqrt((X-pos(1))^2 + (Y-pos(2))^2 + (Z-pos(3))^2 )     
end
#Code for object detection through colour 

tic
clear all;
clc;
l1 = 8.5;
l2= 18.5;
l3 = 17.5; 
nl =3;

X = input('X-coordinate-: ');
Y = input('Y-coordinate-: ');
Z = input('Z-coordinate-: ');
ang =zeros(1,nl);

A = [];
b = [];
Aeq = [];
beq = [];

lb = [0, 0, 0];
ub = [180,180,180];
  [ang1,fval,exitflag,output]=fmincon(@(th) calfun(th,X,Y,Z,nl,l1,l2,l3),ang,A,b,Aeq,beq,lb,ub)
%  [ang1,fval,exitflag,output] = fminsearch(@(th)calfun(th,X,Y,Z,nl,l1,l2,l3),ang,optimset('MaxIter',20000000,'MaxFunEvals',20000000));
th=ang1


