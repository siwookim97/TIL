# 메모리 할당
> 프로그램이나 데이터를 주기억장치 (Main memory)에 할당하는 기법을 말한다.
> 
> 메모리 할당은 연속 로딩 기법(고정, 가변 분할 할당)과 분산 로딩 기법(페이지, 세그멘테이션) 으로 나뉜다.



## 외부 & 내부 단편화
### 외부 단편화
- 프로그램의 크기보다 분할의 크기가 작은 경우에는 해당 분할이 비어 있는데도 불구하고 프로그램을 적재하지 못하는 현상

### 내부 단편화
- 프로그램의 크기보다 분할의 크기가 큰 경우 해당 분할에 프로그램을 적재하고 남는 현상

## 연속 로딩 기법
- 각 프로세스가 하나의 연속된 메모리 공간에 포함된다.
- 각 프로세스가 필요로 하는 메모리 요구량을 분석해 그 프로세스의 메모리르 하나의 덩어리로 메모리에 할당한다.
- 외부 단편화와 내부 단편화가 발생할 수 있다.
- 동적 메모리 할당 문제의 해결책은 3가지로 다음과 같다.
> **최초 적합** : 가장 처음으로 사용 가능한 가용 공간을 할당한다. **일반적으로 속도가 빠름, 공간 효율성 좋음**
>
> **최적 적합** : 사용 가능한 공간 중에서 가장 작은 것을 택한다. **공간 효율성 좋음**
>
> **최악 적합** : 가장 큰 가용 공간을 택한다.
> 
## 분산 로딩 기법
### **페이징**
- 메모리의 할당을 **연속적이지 않게 할당**하는 것이다.
- **물리 메모리는 프레임**이라는 같은 크기 블록으로, **논리 메모리는 페이지**라 불리는 같은 크기 블록으로 나뉜다.
- **외부 단편화를 피할 수 있다.**
- 메모리에 있는 page table에서 관리되는 page number와 page offset으로 논리 주소로 찾아간다.

![img](https://blog.kakaocdn.net/dn/HNKio/btrnyI3uXYF/5B8HR1lwrFO0FOZdK1f3k0/img.png)

## 스와핑
- 프로세스를 메모리에 올려야 실행되지만 프로세스는 실행 중 임시로 **백업 저장장치(backing store)** 로 내보내어 졌다가 실행을 하기 위해 메모리로 돌아 올 수 있다.
- 실행할 모든 프로세스의 크기가 메인 메모리의 총합 보다 크더라도 백업 저장장치와의 스왑인, 스왑아웃을 한다면 동시에 실행하는 것이 가능해 진다.

