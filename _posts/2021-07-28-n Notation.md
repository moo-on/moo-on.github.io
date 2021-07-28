---
date: 2021-07-28

title: "N Notation For Python"
excerpt: "about binary, decimal, octal and hex conversion for Python "

categories: Python
tags: notation, binary, octal, decimal, hex

toc: true  
toc_sticky: true
toc_label: "contents"


last_modified_at : 2021-07-28
---
about binary, decimal, octal and hex conversion for Python 

파이썬으로 2진법 8진법 10진법 16진법 변환,
<span style = "color:blue;">[korean version](https://puffy-juice-530.notion.site/Math-7cad080debfe428a8fc8efb465b6084b)</span>


## Notation


- ### binary and decimal conversion  
  
    binary → decimal     : The multiplier of 2 increases by one

    $1010101(2) -> 2^6 + 2^4 + 2^2 + 2^0 = 64 + 16 + 4 +1 = 85$

    decimal → binary : Divide by 2 each time 
    85  
    = (42)*2 + 1 = 85  
    = (21)*2 + 0 = 42  
    = (10)*2 + 1 = 21  
    = (5)*2 + 0 = 10  
    = (2)*2 + 1 =5  
    =(1)*2 + 0 = 2  
    =(0)*2 + 1 = 1  
    → 1010101

    ```python
    #2->10

    def binary_to_decimal(binary):
        decimal = 0
        temp = list(str(binary))
        length = len(temp)
        for i, e in enumerate(temp):
            if e == '1': decimal += 2**(length -1 - i)
        return int(decimal)

    #10->2
    def decimal_to_binary(decimal):
        temp = deque()
        q,r = divmod(int(decimal), 2)
        temp.appendleft(r)
        while q != 0:
            q,r = divmod(q, 2)
            temp.appendleft(r)
        binary = ''.join(list(map(str, temp)))
        return str(binary)
    ```

- ### binary and hex conversion

    binary → hex

    $$
    1110011011(2) -> 0011/1001/1011$$

    $$2^1+2^0/2^3+2^0/2^3+2^1+2^0 = 
    3/9/11 =0x39B$$

    hex → binary

    $$0x39B → 3/9/B$$

    $$11/1001/1011$$

    ```python
    #2->16
    def binary_to_hexadecimal(binary):
        binary = list(str(binary))
        for _ in range(4 - len(binary)%4):
            binary.insert(0, 0) 
        answer = deque()
        t = 0
        temp = 0
        while binary:
            n = int(binary.pop())
            if n == 1:
                temp += 2**t
            t+=1
            if t = 4:
                if temp >=10:
                    temp += 55
                    answer.appendleft(chr(temp))
                else:answer.appendleft(str(temp))
                t = 0
                temp = 0
        answer.appendleft('0x')
        answer = ''.join(answer)
        return str(answer)

    #16->2
    def hexadecimal_to_binary(hexadecimal):
        answer = []
        temp = list(hexadecimal[2:])
        for e in temp:
            if e.isalpha(): n = ord(e) - 55
            else: n = int(e)
            n = str(decimal_to_binary(n))
            while len(n) != 4:
                n=''.join(['0', n])
            answer.append(n)
        answer = ''.join(answer)
        answer = answer.lstrip('0')
        return str(n)
    ```

- ### decimal and hex conversion

    decimal → hex

    10 = A  
    11 = B  
    12 = C  
    13 = D  
    14 = E  
    15 = F  

    127
    = (7)*16 + 15
    = (0)*16 + 7
    → 0x7F  
  
    hex -> decimal

    $$7F -> 16^1*7 +16^0*15 = 112 + 15 =127$$

    ```python
    #10->16
    def decimal_to_hexadecimal(decimal):
        answer = []
        temp = deque()
        q,r = divmod(int(decimal), 16)
        temp.appendleft(r)

        while q != 0:
            q,r = divmod(q, 2)
            temp.appendleft(r)
        for e in temp:
            if e >=10:
                    e += 55
                    answer.appendleft(chr(e))
            else:answer.appendleft(str(e))
            
        answer.appendleft('0x')
        hexadecimal = ''.join(answer)
        return str(hexadecimal)
        
    #16->10
    def hexadecimal_to_decimal(hexadecimal):
        answer = 0
        hexa = list(hexadecimal[2:].upper())
        length = len(hexa)
        for i,e in enumerate(hexa):
            if e.isalpha(): answer += (ord(e)-55)*(16**(length-1-i))
            else: answer += (16**(length-1-i))*int(e)
        return int(answer)
    ```