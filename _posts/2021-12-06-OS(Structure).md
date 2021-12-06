---
date: 2021-12-06

title: "OS Structure"
excerpt: "about OS introduction & structure"

categories: OS
tags: cs

toc: false  
toc_sticky: false
toc_label: "contents"
toc_icon : 

last_modified_at : 2021-12-06
---

[공룡책의 OS introduction - OS struction(OS 구조) 부분을 요약한 내용입니다]

## [운영체제의 정의]
- H/W - OS - application
- application을 관리해준다. 중간매개자 역할
- 항상 작동하는 컴퓨터, 커널
    - system program, application program을 인터페이스를 제공해준다.
- 정보처리방법
    최소단위 : bit
    정보의 처리 : 정보의 상태 변환, 부울 대수 - 논리게이트 - 논리회로(무어의 법칙, 황의 법칙)
    정보의 저장,전송 : 플립-플롭, 데이터 버스  
<br>
<br> 

## [Classical Computer-System Organization] - 1.2
    
![image](https://user-images.githubusercontent.com/70089259/144777916-193a1164-8fa5-414b-8186-eff1bfb95331.png)
<div align = "center">
<aside>
💡  bus를 이용하여 각 하드웨어에 맞는 시스템 구성요소와 통신.
</aside>
</div>

### bootstrap program

1. 파워가 켜지면, 하드에 있는 운영체제를 메모리로 옮긴다.
2. 그 후 메모리에 기타 프로그램들이 운영체제를 통해서 올라간다.

### Interrupts

1. 하드웨어는 인터럽트를 항상 트리거 해둠
2. 입력이 들어오면, 인터럽트가 신호를 보내고 system bus를 통해 CPU가 받는다.
3. cpu와 I/O 디바이스간의 소통방법

### 폰노이만 아키텍쳐

- instruction-execution cycle이라고도 한다.
1. Instruction-set이 존재하고, 해당 Instruction을 이루어진 system을 메모리에 올린다.
2. memory에서 fetch후 cpu에서 execute된다.

### storage system
<p align = "center">
<img src = "https://user-images.githubusercontent.com/70089259/144778232-a3fc777f-f193-42f5-86fa-cb21d384624a.png">
</p>

이런 계층 구조를 관리한다.

### I/O Structure
<p align = "center">
<img src = "https://user-images.githubusercontent.com/70089259/144778251-47f15435-77ed-426e-b372-44d4cd2dfc9f.png">
</p>

DMA : Direct Memory Access, ex)유튜브

- network card가 데이터 받아와서 다이렉트로 lcd모니터가 출력, cpu가 할 일은 많이없다.

- **커널은 안정화되있기에, 커널 개발보다 새로운 장치를 사용할 수 있는 디바이스 컨트롤러 만드는 일이 많다.**
<br>
<br> 
<br> 

## [Computer System Architecture, Operating System Operation]- 1.3, 1.4
- CPU
- Processor
- Core/ Multicore/ Multiprocessor

### Symmetric multiprocessing(SMP)

- 멀티 CPU

![image](https://user-images.githubusercontent.com/70089259/144778490-4834bdd7-5cce-44c5-89f6-42dd9fc9156e.png)

### Multi-core design

- cpu하나에 여러개의 코어 넣기.

![image](https://user-images.githubusercontent.com/70089259/144778511-7de6c6f3-6963-4ef0-ae04-e0f6b2fa0e67.png)

### Multiprogramming

- 프로세스가 동시에 돌아간다 → cpu를 효율적이게 사용한다.

### Multitasking(multiprocessing)

- 여러개의 프로세스를 자주 바꿔주면서, 유저는 여러개와 상호작용함.
- CPU scheduling : 프로세스를 어떻게 선택 할지
<br>
<br>
## Virtualization - 1.7

![image](https://user-images.githubusercontent.com/70089259/144778623-cbab77ef-4fdb-43e8-ba36-ff1ecce509c0.png)

- 단일 h/w에 여러개의 os 사용.
<br>
<br>

## [Operating System Services] -2.1

- OS : 프로그램이 시작 할 수 있는 환경을 제공 해준다.
    - prcoess를 multitasking을 하면서 동기화 문제(Dead lock)와 scheduling 문제
