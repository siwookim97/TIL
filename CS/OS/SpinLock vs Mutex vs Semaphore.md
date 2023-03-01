# 뮤텍스(Mutex) & 스핀락(SpinLock) & 세마포어(Semaphore)
> 프로세스가 공유된 자원에 여러개의 프로세스가 **임계 구역(Critical Section)** 에 접근하고자 할 때의 문제를 하나의 프로세스만 접근할 수 있도록
> 제한을 두는 동기화 도구들, **뮤텍스와 세마포어** 가 있다.

## 뮤텍스(Mutex)
> **"공유자원에 접근하기 위한 Key인 락을 얻어 동기화"**

- mutual exclusion의 축약 형태로 key를 기반으로 한 동기화 도구이다.
- wait와 signal이라는 원자적 연산을 사용한다.
- **Sleep Lock** 을 사용한다.
- **2개의 프로세스** 에 관련해서 임계 구역 문제를 해결이 가능하다. 
- 프로세스/스레드가 임계구역에 들어가기 전에 Boolean 타입의 **Lock** 을 획득한 후 들어가고, 나올 때 락을 반환한다.
- 공유자원을 사용중인 스레드가 있을 때, 다른 스레드가 공유자원에 접근한다면 Blocking후 대기 큐로 보낸다.
- Lock을 건 스레드만 Lock을 해제할 수 있다.

## 스핀락(SpinLock)
> **"Critical Section에 진입이 가능할 때까지 루프를 돌면서 재시도하는 방식으로 구현된 락"**

- 뮤텍스와 Lock을 얻는다는 점에서 비슷하지만 계속해서 Lock을 얻으려는 시도를 한다.
- Critical Section(임계 구역)에 진입하지 못하면 계속해서 루프를 돌기에 **Busy wating**이 발생한다.
- 운영체제의 스케줄링 지원을 받지 않게 때문에, 해당 스레드, 프로세스에 대한 context switch가 일어나지 않는다.

### busy waiting
락을 받기 위해서 계속해서 락을 획득하고자 하는 반복문을 계속해서 실행하느라 CPU의 자원을 낭비하는 상태가 Mutex에서 발생한다.

## 세마포어(Semaphore)
> **"멀티 프로그래밍 환경에서 공유된 자원에 대한 접근을 세마포어 값을 확인하고 허용치만큼 제한하는 방법"**

- 0 이상의 정수형 세마포어 변수를 통해 wait, signal을 관리한다.
    - **wait 연산** : 세마포어 값을 감소, 값이 음수가 되면 wait를 호출한 스레드는 블록, 아니면 작업을 수행
    - **signal 연산** : 세마포어 값을 증가, 값이 양수가 아니라면 wait연산에서 블록된 스레드를 다시 wake 시킨다.
- 접근 가능한 공유 자원의 수가 1개일 때는 이진 세마포어로 뮤텍스처럼 사용할 수 있다.
- Lock을 걸지않은 스레드도 Signal을 보내 Lock을 해제할 수 있다.