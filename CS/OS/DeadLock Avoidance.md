# 교착 상태 회피
> 교착 상태를 회피하는 대안은 자원이 어떻게 요청될지에 대한 **추가 정보**를 받아 회피를 한다. 

## Safe state (안전 상태)
**항상 Safe State로 만들어 놓자**
> 교착 상태가 일어나지 않는 상태를 safe state라 하고 재 이용 가능한 자원, 
> 현재 각각의 프로세스에게 할당되어 있는 자원 그리고 각각의 프로세스들이 사용하고 반납할 자원들의 정보를 바탕으로 잠재적 Deadlock의 유무를 판단
>
> 모든 비 안전 상태가 교착 상태를 발생하지는 않지만 미연에 비 안전 상태로 들어가는걸 방지하자는 취지이다.

## 교착 상태 탐지 (DeadLock Detection)
### 각 자원 유형이 한 개의 인스턴스만 있는경우
> wait-for-graph를 사용한다, wait-for-graph에서 사이클을 포함하는 경우에만 교착 상태이므로 wait-for-graph를 유지하고 주기적으로 
> 그래프에서 사이클을 탐지하는 알고리즘을 호출한다.

### 각 유형의 자원을 여러 개 가진 경우
> 은행원 알고리즘과 마찬가지로 시시각각 내용이 달라지는 자료구조를 사용한다.

## 교착 상태 회복
교착 상태가 발생하면 운영자에게 통지해 운영자가 처리하게 하거나 **시스템이 교착 상태에서 회복**해야 한다.
### 1. 프로세스와 스레드의 종료
교착 상태 프로세스 모두 중지와 교착 상태가 제거될 때까지 한 프로세스씩 중지하는 방법 두 가지가 있다.
> **모두 중지** : 부분의 연산 과정을 모두 폐기해야 하며 나중에 다시 작업해야 하므로 비용이 크다.
> 
> **하나씩 중지** : 중지할 때마다 확인을 하는 오버헤드가 존재한다. 또한 어떠한 프로세스를 먼저 중지 시킬 건지 요인을 따져봐야 한다.

### 2. 자원 선점
교착 상태가 깨어질 때까지 프로세스로부터 자원을 계속 선점해 이들을 다른 프로세스에게 주어야 하며 다음 3가지 사항들을 고려해야 한다.
> **희생자 선택** : 비용을 최소화하기 위해 선점의 순서를 결정해야 한다.
> 
> **롤백** : 자원을 앗아온 프로세스를 롤백시킨다. (프로세스를 중지시키고 재시작 또는 안전 상태까지)
>
> **기아 상태** : 우선순위에서 계속해서 밀려 자원을 지속적으로 앗아간 프로세스는 기아 상태를 방지하기 위해서 후퇴 횟수를 포함해 회생자 선택을 해야한다.