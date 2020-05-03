# 프로그래머스
2018 kakao blind recruitment [1차] 뉴스 클러스터링

## 1. 문제 정보

- 출처 : 프로그래머스 2018 kakao blind recruitment [1차] 뉴스 클러스터링

- 난이도 : Level 2

## 2. 문제 해결

- 문제 유형 : 문자열, 집합, 사전 다루기

- 코드

```python
def solution(str1, str2):
    answer = 0
    
    str1 = list(str1.lower())
    str2 = list(str2.lower())
    set1 = set()
    set2 = set()
    dic1 = {}
    dic2 = {}
    sum = 0
    
    i = 1
    while i < len(str1):
        if 'a' <= str1[i-1] and str1[i-1] <= 'z':
            if 'a' <= str1[i] and str1[i] <= 'z':
                value = str1[i-1] + str1[i]
                sum = sum + 1
                if value in set1:
                    dic1[value] = dic1[value] + 1
                else :
                    set1.add(str1[i-1] + str1[i])
                    dic1[value] = 1
                i = i+1
            else :
                i = i + 2
        else :
            i = i + 1
    i = 1
    while i < len(str2):
        if 'a' <= str2[i-1] and str2[i-1] <= 'z':
            if 'a' <= str2[i] and str2[i] <= 'z':
                value = str2[i-1] + str2[i]
                sum = sum + 1
                if value in set2:
                    dic2[value] = dic2[value] + 1
                else :
                    set2.add(str2[i-1] + str2[i])
                    dic2[value] = 1
                i = i+1
            else :
                i = i + 1
        else :
            i = i + 1
    
    inter_set = set1 & set2
    sum_inter = 0
    for i in inter_set:
        if dic1[i] < dic2[i]:
            sum = sum - dic1[i]
            sum_inter = sum_inter + dic1[i]
        else :
            sum = sum - dic2[i]
            sum_inter = sum_inter + dic2[i]
    if sum == 0:
        answer = 65536
    elif sum_inter == 0:
        answer = 0
    else :
        answer = int((sum_inter / sum) * 65536)
    
    return answer
```
