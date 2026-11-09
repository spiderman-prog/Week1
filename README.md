# Week11
import numpy as np
import sympy as sp
x, y = sp.symbols('x y')
n = int(input("Enter no. of sample points: "))
x_data = list(map(float, input("Enter x values: ").split()))
y_data = list(map(float, input("Enter y values: ").split()))
if len(x_data) != n or len(y_data) != n:
    print("ERROR: Number of x and y values must be equal to n")
    exit()
print("1. Exponential curve")
print("2. Power curve")
choice = int(input("Enter your choice [1/2]: "))
if choice == 1:
    # y = a * e^(b*x)
    Y = np.log(y_data)
    b, A = np.polyfit(x_data, Y, 1)
    a = np.exp(A)
    a = round(a, 4)
    b = round(b, 4)
    print(f"a = {a}, b = {b}")
    print("The exponential curve:")
    e_curve = sp.Eq(y, a * sp.exp(b * x))
    print(e_curve)
elif choice == 2:
    # y = a * x^b
    Y = np.log(y_data)
    X = np.log(x_data)
    b, A = np.polyfit(X, Y, 1)
    a = np.exp(A)
    a = round(a, 4)
    b = round(b, 4)
    print(f"a = {a}, b = {b}")
    print("The power curve:")
    p_curve = sp.Eq(y, a * x**b)
    print(p_curve)
else:
    print("Invalid choice")
