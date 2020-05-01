# 프로그래머스  
2018 Kakao Blind Recruitment [1차] 비밀지도

## 1. 문제 정보

- 출처 : 프로그래머스 2018 kakao blind recrutment [1차] 비밀지도

- 난이도 : Level 1

## 2. 문제 해결

- 문제 유형 : 비트 연산 및 단순 반복문

- 코드

```python
    def solution(n, arr1, arr2):
      answer = []
      temp = []
      bit = 1 << n

      for i in range(0, n):
          temp.append(bin(arr1[i] | arr2[i] | bit))

      for i in range(0, n):
          sol = list(temp[i])
          result = []
          for j in range(3, n+3):            
              if sol[j] == '1':
                  result.append('#')
              else :
                  result.append(' ')
          answer.append("".join(result))
    
    return answer
```
