# 프로그래머스
2018 kakao blind recrutment [1차] 다트게임

## 1. 문제 정보

- 출처 : 프로그래머스 2018 kakao blind recrutment [1차] 다트게임

- 난이도 : Level 1

## 2. 문제 해결

- 문제 유형 : 문자열 치환

- 코드

```python
def solution(dartResult):
    answer = 0

    input_str = dartResult
    input_str = input_str.replace("S",",")
    input_str = input_str.replace("D",",")
    input_str = input_str.replace("T",",")
    input_str = input_str.replace("*","")
    input_str = input_str.replace("#","")    
    input_str = input_str.split(',')

    num = []
    num.append(int(input_str[0]))
    num.append(int(input_str[1]))
    num.append(int(input_str[2]))

    index = 0
    for i in list(dartResult):
        if i == 'S':
            num[index] = num[index]
            index = index + 1
        elif i == 'D':
            num[index] = num[index]*num[index]
            index = index + 1
        elif i == 'T':
            num[index] = num[index]*num[index]*num[index]
            index = index + 1
        elif i == '*':
            if index == 1:
                num[index - 1] = num[index - 1] * 2
            else :
                num[index - 1] = num[index - 1] * 2
                num[index - 2] = num[index - 2] * 2
        elif i == '#':
            num[index - 1] = num[index - 1] * -1

        answer = num[0] + num[1] + num[2]
    return answer
```
