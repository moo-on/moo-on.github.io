---
date: 2021-10-16

title: "Call by value in Java"
excerpt: "about the Call by value "

categories: Java
tags: java, JVM

toc: true  
toc_sticky: true
toc_label: "contents"
toc_icon : 

last_modified_at : 2021-10-16
---
## Call by Value란?

문자 그대로 **값**을 호출 합니다.

즉 전달 받은 값을 복사하여서 사용하기에, 원본은 변경되지 않습니다.

## Call by Reference란?

참조에 의한 호출 입니다.

즉 전달 받은 값을 직접 참조하기에, 원본 역시 변경이 됩니다.

Java에는 해당 호출 방식을 안 쓰지만, 원본이 변경되는 경우가 있어서(array, 객체) 오해의 여지가 있습니다.

  예시로 살펴보겠습니다.

 

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a8ac6934-ed30-4207-95f0-6bc907e27cee/Untitled.png)

클래스를 만들고, 메서드 실행 시  매개변수로 원본을 변경하는 일이 발생합니다.

하지만 run메서드에 매개변수로 넘길 때, 주소 값을 복사해서 넘겼습니다.

그리고 복사된 주소값으로 참조가 가능해져, 주소 값이 가르키는 객체가 변경됩니다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a83d15c2-0777-4bd3-b7a6-898ca2df0daa/Untitled.png)

a1, a2를 생성해주고, 메서드를 돌려 인자로 넣어줄 때 arg1, arg2가 주소값을 복사해서 독자적으로 가지고 있습니다. 여기서 주소값을 복사해서 가지는 **call by value**인겁니다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/06fb605e-8129-4681-b0ce-5fe8faa42568/Untitled.png)

여기서 arg1의 가진 주소 값을 이용해서 값을 변경하기에 a1이 가르키는 객체의 값도 변경이 됩니다.

arg2는 단순히 a2의 주소값을 가지고 있다가 arg1의 주소값을 가지게 됩니다. 

arg2가 가지고 있던 주소 값을 변경한 것이기 때문에 원본인 a2는 변동이 없습니다.

즉 자바는 모든 전달 방식이 call by value 입니다.


* reference  
https://deveric.tistory.com/92  
https://medium.com/@lunay0ung/stack-vs-heap-a0a0fe5ec5ce  
https://steady-coding.tistory.com/305  
