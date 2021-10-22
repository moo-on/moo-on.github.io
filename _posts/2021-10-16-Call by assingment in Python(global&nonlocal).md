---
date: 2021-10-16

title: "Call by assingment in Python and global & nonlocal"
excerpt: "about the Call by assingment in Python and global & nonlocal"

categories: Python
tags: python, algorithm

toc: true  
toc_sticky: true
toc_label: "contents"
toc_icon : 

last_modified_at : 2021-10-17
---

## **Call By Assignment**

- Python 의 특징 ( Call By Object Reference 라고도 불린다.)
- immutable 자료형에는 Call By Value 와 같은 결과(int, string, tuple...)
- mutable 자료형에는 Call By Reference 와 같은 결과(list, dict...)

## **Call By Value**

- 변수를 선언하면, 그 변수에 특정 메모리를 할당 후 값을 입력
- Stack Frame 내부의 변수와 외부의 변수는 메모리 주소가 다르기 때문에 간섭불가능

### Call by value 예제

```python
n = 10

def test():
	n = 20
	return
    
test()
print(n)

#  결과: 10
```

![https://user-images.githubusercontent.com/70089259/137614050-3ae9d263-93f3-42e4-abe8-50eb425de5fd.png](https://user-images.githubusercontent.com/70089259/137614050-3ae9d263-93f3-42e4-abe8-50eb425de5fd.png)

 global variable n = 10 선언 후,

함수 내에서 n을 다시 할당한다면 stack frame 내부 n은 새로운 참조를 한다, 전역변수 n과는 독립된 관계가 된다. 

![https://user-images.githubusercontent.com/70089259/137614045-93e06f80-e4c5-4f17-b464-efd69a78efa0.png](https://user-images.githubusercontent.com/70089259/137614045-93e06f80-e4c5-4f17-b464-efd69a78efa0.png)

이후 함수가 종료 후 stack frame이 사라지면서 전역변수만 그대로 남겨둔다.

## **Call By Reference**

- 포인터를 통하여 선언된 변수의 메모리 주소 자체에 접근
- Stack Frame 사라져도 변수에 간섭가능

### Call by reference 예제

```python
lst = []

def func():
    lst.append(4)
    return

func()
print(lst)

#  결과: [4]
```

![https://user-images.githubusercontent.com/70089259/137614296-7696bf18-91db-459f-b5be-4f4be5f3633e.png](https://user-images.githubusercontent.com/70089259/137614296-7696bf18-91db-459f-b5be-4f4be5f3633e.png)

list자료형과는 같은 참조 값을 가지기에 그대로 남아있다.

*주의 할점은 새롭게 할당 할 경우 새로운 참조 값을 가진다.*

```python
lst = []

def func():
    lst = []
    lst.append(4)
    return

func()
print(lst)

#  결과: []
```

이미 존재하는 객체를 불러와서 수행하는 연산이 아닌, 할당 등에는 메모리를 공유하지 않는다.

## global

그렇다면, 함수 내에서 전역 변수를 건들고 싶다면 어떻게 해야할까?

```python
n = 10

def test():
	global n
	n= 20
	return

test()
print(n)

#  결과 n : 20
```

global 변수 선언으로 함수 내부에서 전역 변수 컨트롤을 할 수 있다.  

  
## nonlocal

global 변수가 아닌 함수 내부에서 존재하는 변수를 컨트롤 하려면  nonlocal변수를 사용하면 된다.

단, 바로 위의 단계 함수하고만 바인딩이 된다.

```python
def test():
	n = 30
	def inner():
		nonlocal n
		n = 20
	inner()
	print(n)
	retrun

test()

#  결과  n : 20
```

보통 개발 시 global 변수 사용하는 것을 지양하라고 한다.

난 알고리즘 풀이 시 공간복잡도가 큰 매개변수를 재귀함수 등을 통해서 반복 호출 하는경우 부담이 되기 때문에 가끔 사용하는 경우가 있다.

> Call by value 에 대해 자세히 알고싶다면 ↓  

[https://moo-on.github.io/java/Call-by-value-and-JVM-memory-structure/](https://moo-on.github.io/java/Call-by-value-and-JVM-memory-structure/)  
  

[reference]
- [https://devbruce.github.io/python/py-42-call+by+assignment/](https://devbruce.github.io/python/py-42-call+by+assignment/)

