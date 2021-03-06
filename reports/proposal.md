## 제목
- 여러개의 다른 서버 일괄 제어 프로그램

## 개요
- 일반적으로 리눅스 서버는 SSH를 통해 한 대의 서버에 접속이 가능하다. 동시에 여러대의 서로다른 서버에 SSH를 사용하여 개별적으로 접속은 가능하지만 일괄 제어는 어렵다.(툴을 쓰면 손쉽게 가능하다. [Link](https://www.tecmint.com/run-commands-on-multiple-linux-servers/)) 여러대의 서버를 관리하는 툴은 존재하지만, 이 주제를 통해서 시스템프로그래밍과 네트워크의 밀접한 관계를 생각해보고 정리할 수 있을 것이라고 생각했다.
- 한 대의 서버가 여러대의 서로 다른 서버에 일괄적으로 명령을 내리고 결과를 돌려받는 프로그램 작성
  
## 개발목표 및 개발/구현 내용
- 개발 목표
  - 한 대의 서버가 여러대의 서로 다른 서버에 일괄적으로 명령을 내리고 결과를 돌려받는 프로그램 작성
- 구현 내용
  - 클라이언트
    - 여러대의 서버에 명령을 내릴 수 있는 소켓 프로그램 작성
    - 여러대의 서버에 대한 정보(IP / Port 등)를 가지는 파일 관리
    - 명령어 실행 옵션
      - 관리 서버 추가
      - 관리 서버 삭제
      - 특정 서버에서만 해당 명령어 실행
  - 여러대의 서버
    - 클라이언트에서 명령어를 받을 수 있는 소켓 프로그램 작성
    - 쉘 스크립트의 실행 권한을 변경
    - 쉘 스크립트 실행

## 어플리케이션의 구성도
- 기능
  - 한 대의 서버가 여러대의 서로 다른 서버에 일괄 명령을 내리고 결과를 돌려받는다.
- 그림 </br>
  ![Style Images](https://github.com/BJ-Lim/SystemProgramming/blob/master/captures/process_diagram.jpg)</br>
  (1,2) 연결해야 할 서버 리스트를 메모리에 로드</br>
  (3,4) 공유메모리를 생성하고 수행할 명령어를 메모리에 로드</br>
  (5) commander는 fork 후 execl로 서로 다른 프로세스로 소켓 생성 및 연결 / 공유메모리의 수행 명령어 전송</br>
  (6, 7) 수신받은 명령어를 파일로 저장 / 파일의 권한 변경 / 출력 결과를 파일로 redirect</br>
  (8) 서버는 실행 결과파일의 내용을 클라이언트로 각각 전송 / commander는 수신받은 내용을 모두 메시지 큐에 등록</br>


## 기대효과 및 활용방안
 - 여러 대의 서버가 동시에 같은 동작을 수행해야 할 때 쉽게 활용 가능
 - 여러 대의 서버 자원 관리에 용이
 - tutorial을 통해 쉽게 과정을 따라하며 이해 가능
