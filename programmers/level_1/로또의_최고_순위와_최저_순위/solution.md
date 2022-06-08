### solution.py

```python
def solution(lottos, win_nums):
    rank = [6, 6, 5, 4, 3, 2, 1]
    zero_cnt = 0
    win_cnt = 0
    
    for l in lottos:
        if l in win_nums:
            win_cnt += 1
        elif l == 0:
            zero_cnt += 1
            
    return [rank[win_cnt + zero_cnt], rank[win_cnt]]
```



- 당첨 가능한 최고 순위(win_cnt)와 최저 순위(zero_cnt)을 따로 계산하여 쉽게 해결 가능