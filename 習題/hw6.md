# 梯度下降法程式可以找任何向量函數的谷底
```
import numpy as np

def df(f, p, k, step=0.01):
    """計算偏導數"""
    p1 = p.copy()
    p1[k] = p[k] + step
    return (f(*p1) - f(*p)) / step

def grad(f, p):
    """計算梯度"""
    gp = [df(f, p, k) for k in range(len(p))]
    return np.array(gp)

def gradient_descent(f, initial_point, learning_rate=0.1, tolerance=1e-6, max_iterations=1000):
    """梯度下降法"""
    p = np.array(initial_point)
    
    for i in range(max_iterations):
        gradient = grad(f, p)
        p = p - learning_rate * gradient

        if np.linalg.norm(gradient) < tolerance:
            break

    return p, f(*p)

def f(x, y, z):
    return x**2 + y**2 + z**2

initial_point = [8, 1, 5]
result = gradient_descent(f, initial_point)

print("最終結果： p =", result[0], "f(p) =", result[1])
```
