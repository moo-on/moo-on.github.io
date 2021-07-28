---
date: 2021-07-28

title: "Python Dictionary and Set Methods"
excerpt: "about Dictionary and Set that Python bulit-in types"

categories: Python
tags: dictionary, set

toc: true  
toc_sticky: true
toc_label: "contents"
toc_icon : 

last_modified_at : 2021-07-28
---
about Dictionary and Set that Python bulit-in types

## Dictionary

- ### methods
    ```python
    d.values()
    d.keys()
    d.items()
    ```

- ### basic
    ```python
    key in d # if key in d, return True

    list(d) # return d keys

    d[key] = value # set d[key] to value

    d.pop(key[,default]) #if default set, when key not in dic, return default
    d.popitem()

    setdefault(key[,default]) #if key return value, else return default

    for k,v in d.items(): 

    ```

- sort

    ```python
    #sorted by key
    sorted(dic.keys()[,reverse = False]) #return keys list
    sorted(dic.items()) #return items list

    #vsorted by lambda
    sorted(dic.items(), key = lambda x:x[1])

    #sorted by key's length
    sorted(dic.items(), key = lamda x:len(x[0])
    ```

- defaultdict

    ```python
    from collections import defaultdict

    dic = defaultdict(int)

    dic['a'] -> dic['a'] = 0
    ```
---

## Set

- ### methods
    ```python
    set.add(x)

    set.remove(x)
    set.discard(x) #remove method is if not in x , return ValueError
    ```
---