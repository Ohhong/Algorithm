# 프로그래머스
2018 kakao blind recruitment [1차] 프렌즈4블록

## 1. 문제 정보

- 출처 : 프로그래머스 2018 kakao blind recruitment [1차] 프렌즈4블록

- 난이도 : Level 2

## 2. 문제 해결

- 문제 유형 : 튜플, 집합 다루기

- 코드

```python
def solution(m, n, board):
    answer = 0
    s = set()
    for i in range(0, m) :
        board[i] = list(board[i])
        
    while True:
        for i in range(0, m - 1):
            for j in range(0, n - 1):
                if board[i][j] != '0' and board[i][j] == board[i+1][j] and board[i][j] == board[i][j+1] and board[i][j] == board[i+1][j+1]:
                    s.add((i,j))
                    s.add((i+1,j))
                    s.add((i,j+1))
                    s.add((i+1, j+1))
        if len(s) == 0 :
            break
        else :
            answer = answer + len(s)
            for i in s:
                board[i[0]][i[1]] = '0'
            s.clear()
            
            for j in range(0, n):
                l = []
                num = 0
                for i in range(0, m):
                    if board[i][j] != '0':
                        l.append(board[i][j])
                    else :
                        num = num + 1
                index = 0
                for i in range(num, m):
                    board[i][j] = l[index]
                    index = index + 1
                for i in range(0, num):
                    board[i][j] = '0'
                    
    return answer
```
