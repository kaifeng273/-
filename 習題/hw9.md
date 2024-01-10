# 《狼、羊、甘藍菜》過河的問題
```
objs = ["人", "狼", "羊", "菜"]
state = [0, 0, 0, 0]

def neighbors(s):
    side = s[0]
    next_states = []
    check_add(next_states, move(s, 0))
    for i in range(1, len(s)):
        if s[i] == side:
            check_add(next_states, move(s, i))
    return next_states

def check_add(next_states, s):
    if not is_dead(s):
        next_states.append(s)

def is_dead(s):
    if s[1] == s[2] and s[1] != s[0]:  # 狼吃羊
        return True
    if s[2] == s[3] and s[2] != s[0]:  # 羊吃菜
        return True
    return False

# 人帶著 obj 移到另一邊
def move(s, obj):
    new_s = s.copy()
    side = s[0]
    another_side = 1 - side
    new_s[0] = another_side
    new_s[obj] = another_side
    return new_s

visited_map = {}

def visited(s):
    str_key = ''.join(map(str, s))
    return str_key in visited_map

def is_success(s):
    return all(value == 1 for value in s)

def state2str(s):
    return ' '.join([objs[i] + str(s[i]) for i in range(len(s))])

path = []

def print_path(path):
    for state in path:
        print(state2str(state))

def dfs(s):
    if visited(s):
        return
    path.append(s)
    if is_success(s):
        print("Success!")
        print_path(path)
        return
    visited_map[''.join(map(str, s))] = True
    neighbors_list = neighbors(s)
    for neighbor in neighbors_list:
        dfs(neighbor)
    path.pop()

dfs(state)
```
