---
date: 2021-12-06

title: "OS - Process"
excerpt: "about OS Process"

categories: OS
tags: cs

toc: false  
toc_sticky: false
toc_label: "contents"
toc_icon : 

last_modified_at : 2021-12-06
---

[공룡책의 OS introduction - OS Process(OS 프로세스) 부분을 요약한 내용입니다]

## Process Concept - 3.1
- **process란? 실행 중인 프로그램** 
    - 운영체제 입장에서는 관리해야되는  단위.
    - HDD 안에 있는 실행 파일은 CPU가 execute못한다. HDD가 instruction set으로 이루어진 시스템으로 메모리에 올라와 있을 때 process라고 한다.
- memory section
    - text - data - heap - stack
- as a process executes, 상태변화
    - new - running -  waiting - ready - terminated
    
<p align = "center">
<img src = "https://user-images.githubusercontent.com/70089259/144798868-81ca28d5-c3bd-415a-82ac-a72dd65e0335.png">
</p>

    
- **PCB(Process Control Block) or TCB**
    - 프로세스 관리하는 가장 좋은 방법은 PCB라는 구조체를 만드는 것이다.
    - 이 구조체 안에 각 프로세스가 가져야하는 모든 정보를 저장한다.
    - **PCB 안에 존재하는 정보들**
        - process state : new/running/wait/ready 상태인지 확인
        - program counter : 다음에 실행될 명령어의 주소, 명령어 포인트라고도 한다. 메모리는  PCB에 있는 주소를 가져온다.
        - CPU registers를 가지고 있다. 이 안에 program counter, IR 등 들어 있다.
        - scheduling information, memory-management information, Account IF I/O status IF

<p align = "center">
<img src = "https://user-images.githubusercontent.com/70089259/144799044-c8be1ba4-1fd7-4843-8732-c3d8d7afb130.png">
</p>
            
            
- **program that single thread of execution이다.**
    1. CPU에 Program Counter, IR이 하나씩 있고, Data Register들이 있다. 
    2. PC에 따라서 프로세스가 올라가고, IR을 가져온다.그리고 순차적인 실행. 
    3. P0라는 프로세스가 쭉 동작하다가, PCB가 바뀌고 P1이 동작 완료 후 P0로 돌아왔을 때 이어서 동작 한다 = single thread of execution
- multi thread of execution은 multitasking, multiprocess이다. = 운영체제의 핵심 기능.
- process를 여러개하는 것보다 thread 여러개 하는게 장점이 많다.(multiprocessing 보단 multi threading)
    
## Process Scheduling - 3.2
- **multiprogramming의 목적**
    - 동시에 하는것과 parallel와는 다른 말
    - CPU를 효율적이게 사용하자. 여러개의 프로세스가 돌아가는 것.
- **time sharing's objective**
    - process를 자주 바꿔주면서, 동시에 돌아가는 것 처럼 상호작용하는것이다.
- **Scheduling Queues**
    - time sharing을 하기 위해 스케쥴을 짜는 것. ready queue에서 cpu로 들어감.
    - i/o를 기다리는 경우 wait queue에서 기다리다가 완료 후  ready queue로 간다.
- Queue diagram
<p align = "center">
<img src = "https://user-images.githubusercontent.com/70089259/144799285-cd66f5d5-1e70-45da-bf59-a1daa096c9bc.png">
</p>

- context switch
<p align = "center">
<img src = "https://user-images.githubusercontent.com/70089259/144799300-bfd0886a-8363-4c75-b040-1b1515e06a6e.png">
</p>



## Operation on Processes - 3.3
- **process는 새로운 프로세스를 만들 수 있다.**
    - 만든 프로세스 : parent process
    - 만들어진 프로세스 : child process
    - parent 와 child가 concurrently하게 실행하거나 parnet가 wait하는 동안 child가 돌아간다.
<p align = "center">
<img src = "https://user-images.githubusercontent.com/70089259/144799430-3cdc463f-5a12-4ed0-9920-f736d5b8e7c7.png">
</p>

    
- **Zombie and Orphan**
    - zombie : wait호출 없이 부모 일하고, 차일드 남아 계속 일할 때
    - orphan :  wait호출 없이 부모 종료했을 때, 차일드만 남아있는 경우

<<aside>
💡 메모리에 하나의 프로세스가 있다면, 이에 대한 정보를 담은 PCB가 CPU에서 context-switch되면서 동작함.
main.c → 컴파일 → a.out(= 프로그램, set of instruction) → os가 메모리를 잡아줌  → PCB생성
</aside>



- fork() → 프로세스 생성 system call
    - parent의 address base를 그대로 복사하고 parent는 그대로 실행.
    - 혹은 child가 돌아가는 동안 가만히 있는다. → wait() → child가 종료되면 interrupt에 의해 ready queue로 이동한다.


<aside>

💡 주로 쓰레드를 새로 만들지만, 프로세스를 이와 같이 만드는 이유?
- P0와 전혀 다른 것을 하고 싶을 때, execlp()명령어를 하면 fork()로 똑같은 프로그램이 아닌 입력한 프로그램으로 새로 갈아끼워진다.
</aside>



**프로세스들이 concurrent하게 동작하기 위해서는 timesharing이 필요하고, PC, Register 등의 정보가 보존되기 위해서 context switch가 이루어져하며 이를 위해서는 동기화가 중요하다.**
    
## Inter-process Communication - 3.4
- **프로세스가 concurrently하게 실행되는 2가지 경우**
    1. Independent processes : 공유하는 데이터가 없음
    2. cooperating processes : 데이터가 공유되는 등, 서로에게 영향을 줌
- **IPC(Inter-Process Communication)**
    - cooperating의 환경에서 문제를 해결하는 법.(서로 데이터를 공유하는 경우)
    - 두 가지 해결법
        - shared memory
        - msg passing → 운영체제에게 맡기는 경우
## IPC in Shared-Memory Systems -3.5
- **Producer-Consumer Problem**
    - ex) P : compiler, WS - C : assembler, browser
    - shared - memory 로 해결하기
        - 운영체제가 따로 관리해주는 메모리 영역
        - P가 buffer에 메모리를 채워놓고 C가 buffer에 있는 메모리를 사용
## IPC in Message-Passing Systems - 3.6
- **scheme of using shared-memory의 문제**
    - P와 C가 1대1이 아닌 경우, 프로그래머가 다 짜야함.
- **Message - Passing**
    - OS가 cooperating processes를 처리해준다.
    - send - receive만 있으면 된다.
- **Communication Links**
    - P(보내는자)와 Q(받는자)가 있을때, 2개의 system call만 적용(send, receive)
    - Direct
        - P와 Q가 명시적으로 Direct이면 automatically하게 C_Link가 생성. 1대1 방법
    - InDirect
        - Indirect이면  mailbox(port)가 공유되면서 link가 생성되며 N:M의 복잡한 링크 생성 가능. OS가 mailbox create, send&receive, delete mailbox 기능 제공해준다.
        - Blocking send, receive(synchronous) : receive 다 받을 때 까지 대기.
        - non Blocking send, receive(asynchronous) : 상대방 전송 안됬는지 확인 불가능함.
    - Synchronous or Asynchronous
    - Automatic or explicit buffering
        
## Examples of IPC Systems - 3.7
- **Shared Memory : POSIX Shared Memory**
    - POSIX : Portable Operating System Interface
        - memory에 file을 mapping 시킴
        - fd = shm_open(~) → memory 생성
        - ftrimcate(fd, 2048) → memory 크기 설정
        - mmap(~) → file mapping
        
- Message Passing : Pipes
    - UNIX system에서 가장 많이 쓰이는 방법
    - unidirectional 방법
    - **Ordinary pipes**
        - 송수신자는 편의상 parent - child 관계를 가져야한다.
        - 2가지의 커뮤니케이션을 가지고 싶다면, 파이프 하나 더 생성하면된다.
        
        ![image](https://user-images.githubusercontent.com/70089259/144799991-b1de5c6e-3d62-4912-9349-6bd97ff81de5.png)
        
    - **Named pipes**
        - pipes에 이름을 붙여주고 여러개의 파이프를 가지면, P-C관계가 없어도 된다.
        
## Communication in Client-Server Systems - 3.8
- **Socket**
    - Ip_address로 각 Client Server를 Define하고Port로 Data를 주고 받음(TCP,UDP, Multiple recipients)
- **RPCs(Remote Procedure Calls)**
    - IPC가 서로 다른 컴퓨터에서 적용되는 경우를 RPC