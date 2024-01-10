# 使用爬山演算法程式使其可以找任何向量函數的山頂
```
import random

def neighbor(f, p, h=0.01):   
    return [x + random.uniform(-h, h) for x in p], f(p)

def hillClimbing(f, p, h=0.01):
    failCount = 0
    
    while failCount < 10000:
        f_now = f(*p)
        p1, f1 = neighbor(f, p, h)
        
        if f1 >= f_now:
            f_now = f1
            p = p1
            print('p =', p, 'f(p) =', f_now)
            failCount = 0
        else:
            failCount += 1
    
    return p, f_now

def f(x, y, z):
    return -1 * (x**2 + y**2 + z**2)

result = hillClimbing(f, [2, 1, 3])
print("最終結果： p =", result[0], "f(p) =", result[1])

```
