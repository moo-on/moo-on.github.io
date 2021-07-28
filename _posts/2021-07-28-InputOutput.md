---
date: 2021-07-28

title: "Python I/O methods"
excerpt: ""

categories: Python
tags: I/O

toc: true  
toc_sticky: true
toc_label: "contents"
toc_icon : 

last_modified_at : 2021-07-28
---
about I/O in python

## input
- ### basic
    ```python
    a = input() #type to str

    a = input().split() #split based all of space. 5 10 -> ['5', '10']
    
    # map is list element mapping custom function, return map object 
    a = ['5','10']
    a = list(map(int, a)) return [5, 10] 

    # 5\n10 -> [['5'],['10']] split is return to list
    a = [input().split() for _ in range(2)] 

    # 5\n10 -> ['5','10'] rstrip is only remove space
    a = [input().rstrip() for _ in range(2)]
    ```
---