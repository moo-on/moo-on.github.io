---
date: 2021-07-28

title: "Python List Methods"
excerpt: ""

categories: Python
tags: list

toc: true  
toc_sticky: true
toc_label: "contents"
toc_icon : 

last_modified_at : 2021-07-28
---
about list that Python bulit-in types

## List


- ### methods

    ```python
    del list[:]

    list.reverse()

    list.append(x)
    list.extend(x)
    list.insert(i, x)

    list.remove(x)
    list.pop(i)

    list.sort()
    list.reverse()

    list.copy() #SHALLOW, deep copy -> deepcopy.copy(list) or use for loop
    list.clear()

    #deque is useful in timecomplexity
    import deque
    deque.appendleft(x) # list O(N), deque O(1)
    deque.popleft()
    ```
---