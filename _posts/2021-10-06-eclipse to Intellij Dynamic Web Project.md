---
date: 2021-10-06

title: "eclipse to Intellij Dynamic Web Project"
excerpt: "about the eclipse Project use to Intellij "

categories: DevTool
tags: eclipse, Intellij, tomcat

toc: true  
toc_sticky: true
toc_label: "contents"
toc_icon : 

last_modified_at : 2021-10-06
---

이런 포스팅을 하는 이유는 이것 때문에 나의 소중한 시간을 꽤나 날렸기에, 희생자를 줄이고자 쓰게 되었다...

원래 좀 변태 같은 성향이 있기에 클래식은 역시 eclipse라며 dynamic web project를 생성 후 프로젝트를 진행을 하였다.

어느정도 진행을 하고 이제는 intellij로 갈아타려는데 Build tool을 안썼기에 디렉토리 구조가 꽤나 달랐다. 개발환경은 맞추지 않아도 Build tool은 꼭 쓰자!!

1. Projcet Structure에 들어간다.  

2. Project Settings - Project에서 jdk버전을 골라준다.  

3. Modules에서 +버튼을 누르고 Web과 Web Service 2개를 추가 해준다.  
    - Web항목에서의 Deployment Descriptors는 web.xml경로
    - Web항목에서의 Web Resource Directory는 eclipse에서의 Webcontent이니, 해당 경로로 바꿔준다
    - Web Service의 항목에서는 apache axis를 설정해준다.
  
4. library에서는 eclipse의 경우 tomcat환경으로 가상환경을 만들어서 쓰는 것이였는지 intellij에서는 
서버 관련 모듈들이 작동을 안하길래 tomcat폴더에 있는 library를 그대로 추가해줬다.  

5. Facets의 경우에는 Modules와 똑같다.  

6. Artifacts에서는 war_exploded 추가를 해준다.  

7. outputroot에서 WEB-INF 폴더를 생성 후, 오른쪽 available Elements에 있는 compile output을 그대로 옮겨준다.  

8. 밑에 Web facet resources를 끌어오거나 이미 있을 것이다.  

9. 이제 세팅에서 tomcat을 추가로 넣어주면 된다. 여기서 본인이 단순 포트가 아닌 contextroot를 사용하는 경우에는 Application context를 알맞게 수정해줘야한다.  

