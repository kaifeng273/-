# 求解方程式 x^2 - 3x + 1 = 0
## 暴力法
```
def findAn():
    for x in range(-1000, 1001):
        aw_result = x**2 - 3*x + 1
        if abs(aw_result) == 0:
            return x
    return None

result = findAn()

if result is not None:
    print(f"方程的解為 x = {result}")
else:
    print("未找到解")

```
## 迭代法(二分法)

```
def equation(x):
    return x**2 - 3*x + 1

def solve_equation_bisection(a, b, tolerance=1e-6, max_iterations=1000):
    if equation(a) * equation(b) > 0:
        print("在給定區間內找不到解。")
        return None

    iteration = 0
    while (b - a) / 2 > tolerance and iteration < max_iterations:
        midpoint = (a + b) / 2
        if equation(midpoint) == 0:
            return midpoint
        elif equation(midpoint) * equation(a) < 0:
            b = midpoint
        else:
            a = midpoint
        iteration += 1

    return (a + b) / 2

# 在區間 [-1000,1001] 中求解方程式
a = -1000
b = 1001
result = solve_equation_bisection(a, b)

if result is not None:
    print(f"方程式的根為: {result}")
else:
    print("無法在給定區間內找到解。")

```

## 迭代法(牛頓法)

```
def f(x):
    return x**2 - 3*x + 1

def df(x):
    return 2*x - 3

def newton_method(initial_guess, tolerance=1e-6, max_iterations=100):
    x = initial_guess
    iteration = 0

    while abs(f(x)) > tolerance and iteration < max_iterations:
        x = x - f(x) / df(x)
        iteration += 1

    if abs(f(x)) <= tolerance:
        return x
    else:
        raise Exception("Newton's method did not converge")

# 使用牛頓法求解方程式
solution = newton_method(initial_guess=0.0)
print(f" 方程式的根為: {solution:.6f}")

```
## 迭代法
```

f1 = lambda x: (x*x + 1) / 3
f2 = lambda x: 3 - (1/x)
f3 = lambda x: (x-3)*(x+1) + 4

x1 = x2 = x3 = 1

for i in range(20):
    x1, x2, x3 = f1(x1), f2(x2), f3(x3)
    print('第', i+1, '次迭代結果：x1:', x1, 'x2:', x2, 'x3:', x3)

equation_result = x1*x1 - 3*x1 + 1
print('x^2 - 3x + 1 的值:', equation_result)


```
