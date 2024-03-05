# import numpy as np
from scipy.integrate import odeint
import matplotlib.pyplot as plt

# Function that returns dy/dt
def model(y, t):
    y0, y1 = y
    dydt = [y1, 2*y1 - y0]  # y'' - 2y' + y = 0
    return dydt

# Initial condition
y0 = [0, 1]  # y(0) = 0, y'(0) = 1

# Time points
t = np.linspace(0, 10, 100)

# Solve the differential equation
y = odeint(model, y0, t)

# Plot the solution
plt.figure()
plt.plot(t, y[:, 0], 'b', label='y(t)')
plt.plot(t, y[:, 1], 'g', label="y'(t)")
plt.xlabel('Time')
plt.ylabel('Solution')
plt.title('Solution of Second Order Differential Equation')
plt.legend(loc='best')
plt.grid()
plt.show()
