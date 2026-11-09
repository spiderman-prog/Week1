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
    
###week 6##
import sympy as sp
x, y = sp.symbols('x y')
M = sp.sympify(input("Enter M: "))
N = sp.sympify(input("Enter N: "))
dMy = sp.diff(M, y)
dNx = sp.diff(N, x)
def solve_exact(M, N):
    F = sp.integrate(M, x)
    G = sp.integrate(N - sp.diff(F, y), y)
    return sp.simplify(F + G)
# Check whether the given differential equation is exact
if sp.simplify(dMy - dNx) == 0:
    print("The given differential equation is Exact")
    print("Soln :", solve_exact(M, N), "= C")
else:
    u = None
    u_type = None
    # Homogeneous differential equation integrating factor
    if sp.simplify(sp.diff(M / (M * x + N * y), y) -
                   sp.diff(N / (M * x + N * y), x)) == 0:
        u = sp.simplify(1 / (M * x + N * y))
        u_type = "The integrating factor is 1/(Mx + Ny)"
    if u is None:
        mu = sp.simplify(1 / (M * x - N * y))
        if sp.simplify(sp.diff(mu * M, y) -
                       sp.diff(mu * N, x)) == 0:
            u = mu
            u_type = "The integrating factor is 1/(Mx - Ny)"
    if u is None:
        F = sp.simplify((dMy - dNx) / N)
        if not F.has(y):
            u = sp.exp(sp.integrate(F, x))
            u_type = "The integrating factor is x-dependent"
    if u is None:
        G = sp.simplify((dNx - dMy) / M)
        if not G.has(x):
            u = sp.exp(sp.integrate(G, y))
            u_type = "The integrating factor is y-dependent"
    if u is not None:
        u = sp.simplify(u)
        print("IF Type =", u_type)
        print("Integrating Factor =", u)
        print("Soln :", solve_exact(u * M, u * N), "= C")
    else:
        print("The given differential equation does not have an integrating factor")

#week5 ###
import numpy as np
import sympy as sp
x, y, z = sp.symbols('x y z')
A = []
B = []
n = int(input("Enter number of unknowns: "))
for i in range(n):
    eq = input(f"Enter equation {i+1}: ")
    lhs, rhs = eq.split("=")
    lhs = sp.sympify(lhs)
    rhs = float(rhs)
    A.append
    lhs.coeff(x),
        lhs.coeff(y),
        lhs.coeff(z)
    ])
    B.append(rhs)
A =np.array(A, dtype=float)
B =np.array(B, dtype=float)
for i in range(n):
    diagonal = abs(A[i][i])
    non_diagonal = sum(
        abs(A[i][j])
        for j in range(n)
        if j != i
    )
    if diagonal <= non_diagonal:
        print("The given system of equations is not diagonally dominant")
        exit()
else:
    print("The given system of equations is diagonally dominant")

# Initial approximation
X = np.zeros(n)
# Gauss-Seidel iteration
for itr in range(300):
    X_old = X.copy()
    for i in range(n):
        s = 0
        for j in range(n):
            if j != i:
                s += A[i][j] * X[j]
        X[i] = (B[i] - s) / A[i][i]
    # Check convergence
    if np.max(np.abs(X - X_old)) < 0.0001:
        break
else:
    print("Solution does not converge")
    exit()
# Print solution
print("\nSolution")
print("x =", X[0])
if n > 1:
    print("y =", X[1])
if n > 2:
    print("z =", X[2])
##week 1 # 

import numpy as np
r = int(input("Enter no. of rows: "))
c = int(input("Enter no. of columns: "))
A= np.zeros((r, c))
print("Enter the elements of matrix A:")
for i in range(r):
    for j in range(c):
        A[i][j] = float(input(f"A[{i+1}][{j+1}] = "))
eigenvalues, eigenvectors = np.linalg.eig(A)
print("\nEigen values:")
print(eigenvalues)
print("\nEigen vectors:")
print(eigenvectors)
#week2#

import sympy as sp
x = sp.symbols("x")
y = sp.Function("y")(x)
order = int(input("Enter order of the DE: "))
coeff = []
for i in range(order + 1):
    coeff.append(float(input(f"Enter coefficient of y^{order-i}: ")))
lhs = sum(
    coeff[i] * sp.diff(y, x, order - i)
    for i in range(order + 1)
)
rhs = sp.sympify(input("Enter RHS of the DE: "))
eq = sp.Eq(lhs, rhs)
sp.pprint(eq)
print("The general solution of given ODE:")
solution = sp.dsolve(eq, y)
sp.pprint(solution)

#week 3#
def f(x):
    return x**3 - x - 2
def df(x):
    return 3 * x**2
x = float(input("Enter initial point: "))
tol = float(input("Enter tolerance: "))
iteration = 1
max_iterations = 100
while iteration <= max_iterations:
    if df(x) == 0:
        print("Derivative is zero. Solution cannot be found.")
        break
    x_new = x - (f(x) / df(x))
    print(f"Iteration {iteration}: {x_new:.4f}")
    if abs(x_new - x) < tol or abs(f(x_new)) < tol:
        print("Approximate root is:", round(x_new, 4))
        break
    x = x_new
    iteration += 1
else:
    print("Solution does not converge.")
##week 5 ##
import sympy as sp
x = sp.symbols('x')
y = sp.Function('y')(x)
order = int(input("Enter order of the DE: "))
coeff = []
for i in range(order + 1):
    coeff.append(float(input(f"Enter coefficient of y[{order-i}]: ")))
lhs = sum(coeff[i] * sp.diff(y, x, order-i)
          for i in range(order + 1))
rhs = sp.sympify(input("Enter rhs of the DE: "))
eq = sp.Eq(lhs, rhs)
display(eq)
print("The general solution of given ODE:")
solution = sp.dsolve(eq, y)
display(solution)
#week 4##
x = y = z = 0
tol = float(input("Enter tolerance level: "))
for i in range(50):
    x_old, y_old, z_old = x, y, z
    x = (12 - y_old - z_old) / 10
    y = (13 - 2*x_old - z_old) / 10
    z = (14 - 2*x_old - 2*y_old) / 10
    print(f"Iteration {i+1}: x={x:.4f}, y={y:.4f}, z={z:.4f}")
    if (abs(x_old - x) < tol and
        abs(y_old - y) < tol and
        abs(z_old - z) < tol):
        break
print("\nSolutions of the system of equations:")
print("x =", round(x, 4))
print("y =", round(y, 4))
print("z =", round(z, 4))
