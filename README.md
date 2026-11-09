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
    
#####week10###
import numpy as np
import sympy as sp
x_sym, y_sym = sp.symbols('x y')
print("1. Straight line")
print("2. Parabola")
choice = int(input("Enter your choice (ex: 1|2): "))
if choice == 1 or choice == 2:
    n = int(input("Enter number of sample points (n): "))
    x_data = list(map(float, input("Enter x values: ").split()))
    y_data = list(map(float, input("Enter y values: ").split()))
    if len(x_data) != n or len(y_data) != n:
        print("x,y values must be n points")
    elif choice == 1:
        # y = ax + b
        a, b = np.polyfit(x_data, y_data, 1)
        a = round(a, 4)
        b = round(b, 4)
        print("a =", a, "b =", b)
        exp1 = a * x_sym + b
        eq1 = sp.Eq(y_sym, exp1)
        print("The straight line equation:")
        display(eq1)
    else:
        # y = ax^2 + bx + c
        a, b, c = np.polyfit(x_data, y_data, 2)
        a = round(a, 4)
        b = round(b, 4)
        c = round(c, 4)
        print("a =", a, "b =", b, "c =", c)
        exp2 = a * x_sym**2 + b * x_sym + c
        eq2 = sp.Eq(y_sym, exp2)
        print("Parabola")
        display(eq2)
else:
    print("Invalid number")
    ##WEEK12
import matplotlib.pyplot as plt
import numpy as np
n = int(input("Enter sample points (n): "))
x = np.array(list(map(float, input("Enter x values: ").split())))
y = np.array(list(map(float, input("Enter y values: ").split())))
if len(x) != n or len(y) != n:
    print("ERROR: x and y must be same as n")
    exit()
elif np.any(x <= 0) or np.any(y <= 0):
    print("x & y value must be positive")
    exit()
else:
    # Power model: y = a * x^b
    y_log = np.log(y)
    x_log = np.log(x)
    b, log_a = np.polyfit(x_log, y_log, 1)
    a = np.exp(log_a)
    pc = a * x ** b
    # Exponential model: y = a * e^(bx)
    b1, log_a1 = np.polyfit(x, y_log, 1)
    a1 = np.exp(log_a1)
    ec = a1 * np.exp(b1 * x)
    # Plot power and exponential curves
    plt.plot(x, pc, label="Power curve")
    plt.plot(x, ec, label="Exponential")
    plt.grid(True)
    plt.title("Power & Exponential curve")
    plt.xlabel("x values")
    plt.ylabel("y values")
    plt.legend(loc="upper left", facecolor="gray")
    plt.scatter(
        x,
        y,
        marker="o",
        color="red",
        label="given data"
        )
    plt.show()
#week7#
natural growth 
import math
x0 = float(input("Enter initial amount of substance: "))
x1 = float(input("Enter amount of substance after t1: "))
t1 = float(input("Enter time (t1): "))
k = math.log(x1 / x0) / t1
if k < 0:
    print("Natural decay")
elif k > 0:
    print("Natural growth")
else:
    print("Neither growth nor decay")
print("1. Amount of substance")
print("2. Required time")
choice = int(input("Enter choice (1, 2): "))
if choice == 1:
    t2 = float(input("Enter time t2: "))
    x2 = x0 * math.exp(k * t2)
    print(f"Amount of substance after time {t2} is {x2}")
elif choice == 2:
    x2 = float(input("Enter amount of substance at t2: "))
    t2 = math.log(x2 / x0) / k
    print(f"Amount of substance {x2} is reached at time {t2}")
else:
    print("Enter valid choice")
## Newton's law of cooling ##
import math
T0 = float(input("Enter initial temp: "))
T1 = float(input("Enter temp after t1 time: "))
t1 = float(input("Enter time t1: "))
Ts = float(input("Enter surrounding temp (Ts): "))
k = math.log((T0 - Ts) / (T1 - Ts)) / t1
print("1. Find T2")
print("2. Find t2")
print("3. Both")
choice = int(input("Enter choice (1, 2, 3): "))
if choice == 1:
    t2 = float(input("Enter time t2: "))
    T2 = (T0 - Ts) * math.exp(-k * t2) + Ts
    print(f"Temperature of the body after {t2} time is {T2}")
elif choice == 2:
    T2 = float(input("Enter temp of body at t2: "))
    t2 = math.log((T0 - Ts) / (T2 - Ts)) / k
    print(f"Decreasing time of body after t2 time is {t2}")
elif choice == 3:
    t_real = float(input("Enter time to calculate temperature: "))
    T_real = (T0 - Ts) * math.exp(-k * t_real) + Ts
    print(f"Temperature of body after {t_real} time is {T_real}")
    T_cal = float(input("Enter temp of body after t: "))
    t_cal = math.log((T0 - Ts) / (T_cal - Ts)) / k
    print(f"Decreasing time of the body after t_cal is {t_cal}")
else:
    print("You have invalid choice")
