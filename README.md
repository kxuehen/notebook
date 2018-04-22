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


for theta in np.linspace(theta00, theta00+0.4, 10):
  x22 = np.linspace(10.7667, 10.7667,  1)
  theta0 = (math.pi-theta)*0.5
  a_R1 = math.cos(theta0)*R2*2
  for x2 in x22:
    t0 = math.acos(x2/R1)
    x3 = x2+math.cos(math.pi - theta0 - t0)*a_R1
    O2A = (R1-R2)*x2/R1
    P4O2 = R2**2/(x3 - O2A)
    P4A = P4O2 + O2A
    print('t0: %g'% t0)
    print('theta: %g' % theta)
    print('x2: %g'% x2)
    print('x3: %g' % x3)
    print('x4: %g' % P4A)

