# IPC (Inter Process Communication)
> 프로세스는 독립적으로 실행되며 다른 프로세스에게 영향을 받지 않고 메모리 영역이 나누어져 있다. 
>
> 독립적 구조를 가진 `프로세스 간의 통신`을 해야 하는 상황에 IPC 통신을 사용한다.
> 
> 크게 `Shared Memory`와 `Message Passing`의 2가지 방법이 있다.

![img](https://blog.kakaocdn.net/dn/bDS16L/btq6cUgBhUP/ctoU6yixvYtxP6TDYgU4zK/img.png) 

##  Shared Memory (공유 메모리)

> 하지만 원래 프로세스 간에 메모리 영역은 분리되어 있지만 공유 메모리의 방법을 사용하기 위해서는 프로세스가 이 제약 조건을 제거하는 것에 동의하는 것을 필요로 한다

### 생산자-소비자 문제 (클라이언트 서버 패러다임)

>공유 메모리 프로세스 간의 연결에서 생산자-소비자 문제의 해결은 다음과 같다.
>
>생산자와 소비자가 Concurrently하게 접근을 하게 하는데 이 방법은 `버퍼`를 두어 접근하게 한다.



##  Message Passing (메시지 패싱)

> 공유 메모리 방법을 통해서 애플리케이션을 만드는 사람들 입장에서는 메모리 영역을 고려하기 쉽지 않다.
따라서 OS에서 Message Passing을 통해 프로세스간의 통신을 구현했다.
> 
> 사용자는 send와 receive만 이용
> 
> 크게 Direct 방식과 Indirect 방식의 2가지가 있다.

### Direct & Indirect 메시지 패싱
> **Direct** : 자동적으로 링크가 연결되고 링크는 1대 1의 원링크만 설정됨
> 
> **Indirect** : mailbox또는 port를 통해 메시지를 주고받는다, 2개 이상의 프로세스가 연결이 될 수 있다.

### 동기화 방법 (Synchronization or Blocking/Non-Blocking)
> **Blocking Send** : 발신자는 메시지가 받아질 때까지 블락
> 
> **Non-Blocking Send** : 발신자는 메시지를 보내고 작업을 재시작
> 
> **Blcoking Receive** : 메시지가 이용 가능할 때까지 블락
> 
> **NonBlcoking Receive** : 유효한 메시지나 Null을 받는다

Synchronous한 프로그램을 만드려면 Blocking I/O를 이용한다.