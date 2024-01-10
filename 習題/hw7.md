# 梯度下降法程式改用 micrograd 的反傳遞算法算梯度
```
import micrograd as mg

def df(f, p, k):
    p1 = [mg.Tensor(x) for x in p]
    p1[k] = p[k] + step
    return (f(*p1) - f(*p)) / step

def grad(f, p):
    gp = [df(f, p, k) for k in range(len(p))]
    return gp

def gradient_descent(f, initial_point, learning_rate=0.1, tolerance=1e-6, max_iterations=1000):
    p = [mg.Tensor(x) for x in initial_point]
    
    for i in range(max_iterations):
        gradient = grad(f, p)
        for k in range(len(p)):
            p[k].data -= learning_rate * gradient[k].data

        if max(abs(g.data) for g in gradient) < tolerance:
            break

    return [g.data for g in p], f(*p)

def f(x, y, z):
    return x**2 + y**2 + z**2

step = 0.01
initial_point = [2.0, 1.0, 3.0]
result = gradient_descent(f, initial_point)

print("最終結果： p =", result[0], "f(p) =", result[1])
```
