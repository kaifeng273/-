# 列舉所有排列的程式
```
n=int(input("輸入數字"))

def print_permutation(arr):
    print("".join(map(str, arr)))

def backtrack(arr, used, n, N):
    if n == N:
        print_permutation(arr)
        return

    for i in range(N):
        if not used[i]:
            used[i] = True
            arr[n] = i
            backtrack(arr, used, n + 1, N)
            used[i] = False

def enumerate_permutations(N):
    a = [0] * N
    used = [False] * N
    backtrack(a, used, 0, N)
result = n  
enumerate_permutations(result)
```
## 結果
輸入數字3
012
021
102
120
201
210
