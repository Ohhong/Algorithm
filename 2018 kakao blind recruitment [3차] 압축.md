# 프로그래머스
2018 kakao blind recruitment [3차] 압축

## 1. 문제 정보

- 출처 : 프로그래머스 2018 kakao blind recruitment [3차] 압축

- 난이도 : Level 2

## 2. 문제 해결

- 문제 유형 : 딕셔너리 사용

- 코드

```python
def solution(msg):
    answer = []
    dic = {}
    i = 1
    for j in 'ABCDEFGHIJKLMNOPQRSTUVWXYZ':
        dic[j] = i
        i = i + 1
    
    index = 27
    i = 0

    while i < len(msg):
        if i+1 == len(msg):
            answer.append(dic[msg[i]])
            break
        else:
            result = dic[msg[i]]
            temp = msg[i] + msg[i+1]
            while True:
                if temp in dic.keys():
                    result = dic[temp]
                    if i+2 == len(msg):
                        i = len(msg)
                        break
                    temp = temp + msg[i+2]
                    i = i + 1
                else:
                    break
            answer.append(result)
            dic[temp] = index
            index = index + 1
            i = i+ 1
            
    
    return answer
```
