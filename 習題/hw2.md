# power2n 的四種實作方法
## 方法 1

```
n=int(input("輸入數字"))

def power2n(n):
    power2n = 2 ** n
    return power2n
result= power2n(n)
print(result)
```
### 結果
輸入數字11
2048
## 方法 2a：用遞迴

```
n=int(input("輸入數字"))

def power2n(n):
    if n == 0:
        return 1
    else:
        return power2n(n - 1) + power2n(n - 1)
result= power2n(n)
print(result)
```
### 結果

輸入數字15
32768
## 方法2b：用遞迴

```
n=int(input("輸入數字"))

def power2n(n):
    if n == 0:
        return 1
    else:
        return 2 * power2n(n - 1)
result= power2n(n)
print(result)
```
### 結果
輸入數字13
8192
## 方法 3：用遞迴+查表

```
n=int(input("輸入數字"))

def power2n(n,memo={}):
    if n in memo:
        return memo[n]
    
    if n == 0:
        return 1
    elif n == 1:
        return 2
    
    result = 2 * power2n(n - 1, memo)
    memo[n] = result
    return result
result= power2n(n)
print(result)
```
### 結果
輸入數字19
524288

