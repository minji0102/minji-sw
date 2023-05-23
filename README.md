### 오픈소스 과제 20223192 김민지

## TOP 명령어


시스템의 상태를 전반적으로 가장 빠르게 파악 가능(CPU, Memory, Process)


옵션 없이 입력하면 interval 간격(기본 3초)으로 화면을 갱신하며 정보를 보여줌



* **top 명령어 실행 화면**
```bash
$ top [option]
```


![top1](https://github.com/minji0102/minji-sw/assets/133829885/b87c0928-53d8-4c3e-be84-b33eeafffa53)



* **용어 정리**

 
  **171 days,  1:20** : 171일 1시간 20분 전에 서버가 구동


  **load average**: 현재 시스템이 얼마나 일을 하는지를 나타냄. 3개의 숫자는 1분, 5분, 15분 간의 평균 실행/대기 중인 프로세스의 수. CPU 코어수 보다 적으면 문제 없음


  **Tasks** : 프로세스 개수


  **KiB Mem, Swap** : 각 메모리의 사용량


  **S** : 프로세스 상태(작업중, I/O 대기, 유휴 상태 등)


  **PID**:
프로세스 ID이며 프로세스를 구분하기 위한 겹치지않는 고유한 값.


  **USER**: 
해당 프로세스를 실행한 USER 이름 또는 효과를 받는 USER의 이름.


  **PR** : 커널에 의해서 스케줄링되는 우선순위.


  **NI** : PR에 영향을 주는 nice라는 값입니다.



  **VIRT** : 프로세스가 소비하고 있는 총 메모리입니다. 프로그램이 실행중인 코드, heap, stack과 같은 메모리, IO buffer 메모리를 포함합니다.


  **RES** : RAM에서 사용중인 메모리의 크기를 나타냅니다.


  **SHR** : 다른 프로세스와의 공유메모리(Shared Memory)를 나타냅니다.


  **%MEM** : RAM에서 RES가 차지하는 비율을 나타냅니다.


  **TIME+** : 프로세스가 사용한 토탈 CPU 시간


  **COMMAND** : 해당 프로세스를 실행한 커맨드를 나타냅니다.



* **top 실행 전 옵션**

```bash
  $ top -b : 순간의 정보를 확인하려면 -b 옵션 추가(batch 모드)
  $ top -n : top 실행 주기 설정(반복 횟수)
  ```
  
  
* **top 실행 후 옵션**


  **shift + p** : CPU 사용률 내림차순


  **shit + m** : 메모리 사용률 내림차순


  **shift + t** : 프로세스가 돌아가고 있는 시간 순
 

  **k** : kill. k 입력 후 PID 번호 작성. signal은 9


  **f** : sort field 선택 화면 -> q 누르면 RES순으로 정렬


  **a** : 메모리 사용량에 따라 정렬


  **b** : Batch 모드로 작동


  **1** : CPU Core별로 사용량 보여줌
  
  
## 2. PS 명령어


ps 명령어는 현재 실행중인 프로세스 목록과 상태를 보여줌.

```bash
$ ps [option]

System V : $ ps -ef
BSD : $ ps aux
```


```bash
$ ps -ef : 모든 프로세스를 풀 포맷으로 출력
```


 ```bash
 $ ps -ef | grep '프로세스명' : '프로세스명'의 프로세스 구동 확인
 ```
 
 
 ```bash
$ ps aux : 실행중인 모든 프로세스 확인
```


* **실행화면**


![ps1](https://github.com/minji0102/minji-sw/assets/133829885/3ab7dddb-8249-4df7-ba79-a485a24f6dfa)

* **ps옵션**


  **-A**: 모든 프로세스를 출력한다.
  
  
  **a (BSD계열)**: 	터미널과 연관된 프로세스를 출력하는 옵션이다. 보통 x 옵션과 연계하여 모든 프로세스를 출력할 때 사용한다. 
  
  
  **-a**	:세션 리더(일반적으로 로그인 셸)을 제외하고 데몬 프로세스처럼 터미널에 종속되지 않은 모든 프로세스를 출력한다.
  
  
  **-e**	:커널 프로세스를 제외한 모든 프로세스를 출력해 준다.
  
  
  **-f**	:풀 포맷으로 보여준다.
                 유닉스 스타일로 출력해주는 옵션으로 UID, PID, PPID등이 함께 표시된다.
  **-l (sys V)
  l (BSD계열)**:   긴 포맷으로 보여준다.
                 프로세스의 정보를 길게 보여주는 옵션으로 우선순위와 관련된 PRI와 NI값을 확인할 수 있다. 
  **-o**  :값 출력 포맷을 지정하는 옵션으로 값으로는 pid, tty, time, cmd 등을 지정할 수 있다.
  
  
  **-M**  :64비트 프로세스들을 보여준다.
  
  
  **-m**	:프로세스들 뿐만 아니라 커널 스레드들도 보여준다. 
  
  
  **-p**	:특정 PID를 지정할 때 사용합니다 
  
  
  **-r**	:현재 실행 중인 프로세서를 보여준다. 
  
  
  **u (BSD계열)**: 	프로세스의 소유자를 기준으로 출력한다. (ps ax만 하면 USER 기준의 정보가 안뜸, 따라서 aux 이렇게 같이 대게 써준다) 
  
  
  **-u**:	특정 사용자의 프로세스 정보를 확인할 때 사용한다. 사용자를 지정하지 않으면 현재 사용자를 기준으로 정보를 출력한다. 
  
  
  **x**: (BSD계열)	데몬 프로세스처럼 터미널에 종속되지 않는 프로세스를 출력한다. 보통 a옵션과 결합하여 모든 프로세스를 출력할 때 사용한다
  
  
  **-x**:	로그인 상태에 있는 동안 아직 완료되지 않은 프로세서들을 보여준다. 유닉스 시스템은 사용자가 로그아웃 한 후에도 임의의 프로세서가 게속 동작하게 할 수 있다. 그러면 그 프로세서는 자신을 실행시킨 셸이 없이도 계속 자신의 일을 수행하는데 이러한 프로세스는 일반적인 ps 명령으로 확인할 수 잆다. 이 때 -x 옵션을 사용하면 자신의 터미널이 없는 프로세서들을 확인할 수 있다. 
 
 
 ## jobs 명령어
 
 
백그라운드로 실행된 프로그램이나 "<Ctrl> + z"를 입력하여 실행한 프로그램에 대해서 확인하는 명령어.

  
 ```bash
$ jobs [option]
```
  
  
* **옵션**
  

  -p	백그라운드에 있는 프로세스의 프로세스 아이디(PID)만 출력한다.
  
  
  -l	백그라운드에 있는 프로세스의 프로세스 아이디(PID)를 함께 출력한다.
  
  
  -s	백그라운드에 있는 프로세스 중 멈춰있는 프로세스만 출력한다.
  
  
  -r	백그라운드에 있는 프로세스 중 실행중인 프로세스만 출력한다.
  
 * **실행화면**
  
  
  ![jobs1](https://github.com/minji0102/minji-sw/assets/133829885/1112209e-f1ad-4459-9759-125dce55aab7)
  
  
## kill 명령어
  
 * 프로세스에 시그널을 보내 원하는 작업을 하게 하는 명령어
  ```
  $ kill [options] <pid> [...]
  ```
    
  
 * 대개 프로세스를 죽일 때 사용됨
  
  ```
  $ kill [pid]
  ```
  
  * **kill -l**
  
  
    * 지원하는 시그널 목록을 볼수있음
  
  
  ![kill 1](https://github.com/minji0102/minji-sw/assets/133829885/dadea8e8-f0e4-4f80-85f9-e90fbc96d0fb)

  
  
  
  
