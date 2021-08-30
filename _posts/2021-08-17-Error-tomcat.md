---
date: 2021-08-17

title: "Error-Tomcat Server"
excerpt: "about the tomcat error"

categories: Error
tags: tomcat, error

toc: true  
toc_sticky: true
toc_label: "contents"
toc_icon : 

last_modified_at : 2021-08-17
---
## the server cannot be started because one or more of the ports are invalid. open the server editor and correct the invalid ports.  
 
라는 에러의 발생.

>why?  

tomcat설치 후 8080으로 http/1.1이 연결되있었지만, admin port번호가 공란으로 되있었다.

>solution  

1. **server tab의 overview**에서 
2. **tomcat admin port and http/1.1**를 각기 다른 번호로 포트번호를 수정을 하면된다.  

참고로 이미 사용중이거나, 다른곳에 쓰이는 포트번호 괜히 건들지말고 무난하게 8081같은걸로 하자.  
hosting은 http/1.1번호로 되지만 admin port 설정이 이상해도 작동 오류가 나니 둘 다 해줘야한다.
...  

로컬에서 ide는 http1.1로 연동이 된다. 그러므로 admin port는 원격배포할 때 신경을 쓰면 될거 같다!  
**[정리]**  
http1.1로 연동이되지만, adminport의 번호가 이상해도 작동 에러가 난다. 

---  
## web.xml이 없을 때

>solution  

1. 프로젝트 오른마우스
2. java EE toolsGenerate Deployment Discriptor stub
3. web.xml이 생성

가끔 dynamic web 생성 시에 오류로 안만들어진다는데, 프로젝트 생성할 때 해당 파일 체크해제해서 그런거다.