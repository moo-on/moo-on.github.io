---
date: 2021-07-28

title: "Python String Methods"
excerpt: ""

categories: Python
tags: python method

toc: true  
toc_sticky: true
toc_label: "contents"
toc_icon : 

last_modified_at : 2021-07-28
---
about String that Python bulit-in types

## String

- ### methods
    ```python
    str.count(sub,start,end)
    str.endswith(suffix,[start,end])
    str.startswith(suffix,[start,end])

    str.find(sub,[start,end])
    str.rfind(sub, [start,end]) # start looking from right, no exist return -1
    str.rindex(sub, [start,end]) # no exist return value error, 

    str.isalnum() #alphabet or numeric
    str.isalpha() #alphabet
    str.isdigit() #numberic shape ex)3^2
    str.isdecimal() #possible to conversion Integer
    str.isnumeric() #all of type ex)三
    str.isascii() #exists as ASCII
    str.isidentifier() #if identifier
    str.islower() #
    str.isupper() #
    str.isprintable() #
    str.isspace() #
    str.istitle() #
   

    str.join(iterable)

    str.replace(old, new, [count])
    str.maketrans(s1,s2)
    str.translate(table)

    str.partition(sep) #return tuple that include sep
    str.rpartition(sep) 
    str.split(sep=None, maxsplit=-1)
    str.rsplit(sep=None, maxsplit=-1) #return list that not include sep, 
    str.splitlines()

    str.lstrip("ab") # aaabbccd -> ccd
    str.strip("ab") #remove left,right

    str.swapcase() #changes lower or upper 
    str.title() #first alphabet is upper
    str.upper() #all of alphabet is upper

    str.ljust(width, [fillchar]) #padding fillchar until width after left align
    str.rjust(width, [fillchar])
    str.center(width, [fillchar])
    str.zfill(width) #prepend zero until width

    str.encode()
    ```

- ### formating
    ```python
    str = "ex"
    f"example, {str}."
    f"3+5={3+5}"
    ```
---