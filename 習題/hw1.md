# 費氏數列的迴圈版

```
n=int(input("輸入數字"))

def fibonacci(n):
    if n <= 0:
        return "請輸入正整數"
    elif n == 1:
        return 1
    elif n == 2:
        return 1
    else:
        a, b = 1, 1
        for _ in range(n - 2):
            a, b = b, a + b
        return b



result = fibonacci(n)
print(result)

```
