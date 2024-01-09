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

# 在區間 [0, 3] 中求解方程式
a = -1000
b = 1001
result = solve_equation_bisection(a, b)

if result is not None:
    print(f"方程式的根為: {result}")
else:
    print("無法在給定區間內找到解。")

```

## 迭代法2.

```

```
## 迭代法3.
```

```
