---
date: 2021-08-20

title: "Error-Pycharm"
excerpt: "about the Pycharm Error"

categories: Error
tags: error, pycharm

toc: true  
toc_sticky: true
toc_label: "contents"
toc_icon : 

last_modified_at : 2021-08-20
---

## Module already exist in project

## Cannot load settings from file

이거 말고도 에러가 여러개 떴었는데, 왜 떴냐면 아무 생각없이 프로젝트명을 바꿔서이다..ㅎㅎ
왜 이런짓을 했냐면 외부에서 뭐 받아오거나 추가 라이브러리 설치 같은거 안하고 정말로 단순하게 하드코딩만 하는게 있어서
줄 쳐지는 메모장인줄 알았나보다.
>solution  

1. .idea 파일 들어가서 기존 프로젝트명인거 전부 바꿔주자 iml파일은 당연하고, modules.xml 들어가보면 path가 기존 프로젝트명으로 되있을수도있다.
2. system venv쓰는 경우는 거기서 해결하면 되겠지만, 나는 모든 프로젝트가 아나콘다로 가상환경 만드는 구조다.인터프리터 위치를 못찾길래 기존 env폴더 찾아가서 다 바꿔줬지만 실패.
3. file-setting-interpreter들어가서 새로운환경을 만들어주거나 세팅해둔 환경으로 바꿔주면된다.

가끔 다양한 문제에서 에러 해결방법으로 재설치하기 다시 만들기 등등..억 하는 방법들이 소개되는데, 가능하다면 에러가 발생한 이유를 찾고 해결해보자*^^*  

