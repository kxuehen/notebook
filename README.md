# projective

import math
import numpy as np
R1=18.384
R2=13.560
x3 = 16.544
x2 = 12.157
y3 = 2.2046
y2 = 10.022

x3_0 = 16.544
x2_0 = 12.157
y3_0 = 2.2046
y2_0 = 10.022
a_R1 = ((x3_0-x2_0)*(x3_0-x2_0)+(y2_0-y3_0)*(y2_0-y3_0))**0.5
theta00= math.asin(0.5*a_R1/R2)*2
print(theta00)

delta = 0.150

for theta in np.linspace(theta00, theta00 + 0.1, 2): 
  x22 = np.linspace(12.157, 12.157 + 0.2,  2)  
  theta0 = (math.pi-theta)*0.5
  a_R1 = math.cos(theta0)*R2*2
  for x2 in x22:
    t0 = math.acos(x2/R1)
    x3 = x2+math.cos(math.pi - theta0 - t0)*a_R1
    O2A = (R1-R2)*x2/R1
    P4O2 = R2**2/(x3 - O2A)
    P4A = P4O2 + O2A 
    x4 = (math.sin(t0 - theta)*R2 - delta)*math.tan(t0 - theta) + x3
    O1A = math.sin(t0)*(R1-R2)
    y1 = R1 - O1A - delta
    y2 = math.sin(t0)*R1 - O1A -delta
    y3 = math.sin(t0 - theta)*R2 -delta
    
    s1 = math.pi*R1**2*(math.asin(x2/R1)/math.pi) - O2A*O1A
    s2 = math.pi*R2**2*theta/(2*math.pi)*2
    s3 = P4O2 * math.sin(t0 - theta)*R2
    s = s1 + s2 + s3
    
    print('t0: %g'% t0) 
    print('theta: %g' % theta)
    print('x2: %g'% x2) 
    print('x3: %g' % x3) 
    print('x4: %g' % x4) 
    print('y1: %g'% y1) 
    print('y2: %g' % y2) 
    print('y3: %g' % y3) 
    print('s: %g' % s)
