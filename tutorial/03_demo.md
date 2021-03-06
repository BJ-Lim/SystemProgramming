## 개요
- 이 과정에서는 프로그램을 실행해보고, 올바르게 실행되었는지 확인합니다.

## 데모
1. 각 서버에 전송할 명령어를 파일로 정리합니다. 우리는 잘 작동하는지 쉽게 확인하기 위해서 각 서버의 호스트명을 바꿔놓았습니다.
명령어 샘플은 [여기](https://github.com/BJ-Lim/SystemProgramming/blob/master/code/client/cmd.sh)에서 볼 수 있습니다.
2. 서버 리스트를 수정합니다. 서버 리스트 예제는 [여기](https://github.com/BJ-Lim/SystemProgramming/blob/master/code/client/server_list)
에서 볼 수 있습니다. 이때 주의할 점은 IP는 본인의 IP를 사용해야 합니다.
3. 클라이언트를 실행합니다. 명령어는 다음과 같습니다. 다음과 같은 명령어를 사용하면 바로 결과를 확인할 수 있습니다.
    ```
    ./client cmd.sh < server_list
    ```
    우리는 결과를 파일로 확인하기 위해서 다음과 같은 명령어를 사용할 것입니다.
    ```
    ./client cmd.sh < server_list > client_result
    ```
4. 결과는 [여기](https://github.com/BJ-Lim/SystemProgramming/blob/master/code/client/client_result) 파일에서 확인할 수 있습니다.
주의해야 할 점은, 서버별로 출력 순서가 다를 수 있습니다. 이는 내부적으로 fork()로 구현되었기 때문입니다.

## 데모2
우리는 위에서 데모를 해봤지만, 출력 결과가 너무 길어서 웹상에서 보기에는 무리가 있었습니다. 따라서 간단한 데모를 한 번 더 실행해 보겠습니다.
1. 조건은 모두 위와 동일합니다. 하지만 cmd.sh가 간단해 졌습니다.
  ```
  #!/bin/bash             이 프로그램에는 빠져있습니다. 하지만 잘 작동합니다!

  echo "-------------------------------------[hosts]------------------------------------------
  cat /etc/hosts
  ```
2. 실행 결과는 다음과 같습니다.
![Style Images](https://github.com/BJ-Lim/SystemProgramming/blob/master/captures/tutorial_03_demo_01.jpg)</br>
![Style Images](https://github.com/BJ-Lim/SystemProgramming/blob/master/captures/tutorial_03_demo_02.jpg)</br>
![Style Images](https://github.com/BJ-Lim/SystemProgramming/blob/master/captures/tutorial_03_demo_03.jpg)</br>

