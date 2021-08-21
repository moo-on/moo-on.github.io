---
date: 2021-08-21

title: "Web Application Directory Architecture"
excerpt: "about the WAS Directory"

categories: WebServer
tags: tomcat, WAS

toc: true  
toc_sticky: true
toc_label: "contents"
toc_icon : 

last_modified_at : 2021-08-21
---

![WAS디렉터리구조](https://user-images.githubusercontent.com/70089259/130313356-2da78aff-b2b2-4348-919c-a905611f7943.png)

일반적인 java project는 src의 java파일과 bin의 컴파일된 class파일로 작동이 된다.

## Web Project의 기본 구성도.

- webapp: root directory
    - WEB-INF : client와 상호작용을 할 수 있도록 만들어진 파일들의 directory
        - lib : api(.jar)등 파일들 상호작용용 도구들이 만들어져있다.
        - classes : webapp폴더 밖의 src파일들이 컴파일된 class 파일들이 만들어져있다.
        - web.xml : 클라이언트들이 원하는 동작을 하기 위해서 web-inf안에 구현되어 있는 파일들을 끌어와서 쓰기위해 일일히 찾는 것이 아니라 web.xml파일 안에 맵핑이 되어있다. 즉 클라이언트의 요청 - web.xml파일이 어디로 가라는지 알려줌 - 동작 후 리턴
    - web-inf파일을 벗어나면 img나 css같은 정적인 요청 파일을 반환해준다.
