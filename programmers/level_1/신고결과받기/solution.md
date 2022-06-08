### solution.py

```python
def solution(id_list, report, k):
    # 변수 생성
    answer = []     # 최종 답 
    temp = []       # 임시 공간
    
    # id_list에 대응되는 공간 생성
    for _ in range(len(id_list)):
        temp.append([])
        answer.append(0)
    
    # 각각의 id를 신고한 다른 id들의 리스트 생성 
    for r in report:
        a, b = r.split()        # string 타입의 신고데이터를 분리 시켜줌
        idx = id_list.index(b)  # 신고당한 b의 id_list에서의 index를 구함
        if a not in temp[idx]:  # 중복 방지
            temp[idx].append(a) 
            # id_list에 대응되는 공간(temp[index])에 b를 신고한 a를 리스트에 추가함 
    
    # temp안의 리스트를 조회
    # 조건에 맞는 index를 구하고 id_list에 대응하는 공간(answer)의 해당 index에 +1을 해줌
    for m in range(len(temp)):
        if len(temp[m]) >= k:           # 신고당한 횟수가 k번 이상인 경우만 진행
            for n in temp[m]:           # 신고한 id 조회
                i = id_list.index(n)    # 신고한 id의 id_list에서의 index 구함
                answer[i] += 1          # 그에 대응하는 answer의 index에 1을 더해줌 
    
    return answer
```



- for 문을 여러 번 사용했더니 '시간초과' 발생
- 시간복잡도를 최소화하는 방향으로 진행