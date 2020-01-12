## 텐서플로와 머신러닝으로 시작하는 자연어 처리 - 설치

1. 가상 환경 구성

   가상환경은 각 프로젝트마다 파이썬 실행 환경을 독립적으로 활용 할 수 있게 해주는 기능이다.

   - 가상환경 생성 

     ```shell
     conda create --name pr_tensorflow python=3
     ```

     `--name` : 가상환경 이름

     `python` : 파이썬 버전 

   - 가상 환경 실행

     ```shell
     conda activate pr_tensorflow
     ```

2. 실습 프로젝트 구성

   1. 실습 프로젝트 git clone

   2. 필요한 파이썬 패키지 설치

      ```shell
      pip install -r requirements.txt
      ```

      -  대부분 라이브러리 설치 전 아나콘다 업데이트와 파이썬 패키지를 모두 업데이트 후 필요한 패키지는 설치하더라  `conda update conda` `pip update --all`

   - pip 설치 중 에러 

     ##### JPype1 설치 중  c++ Build Tools 설치 문제

     ```shell
       error: Microsoft Visual C++ 14.0 is required. Get it with "Microsoft Visual C++ Build Tools": https://visualstudio.microsoft.com/downloads/
     
       ----------------------------------------
       Failed building wheel for JPype1
       Running setup.py clean for JPype1
       Building wheel for bz2file (setup.py) ... done
       Stored in directory: C:\Users\user\AppData\Local\pip\Cache\wheels\81\75\d6\e1317bf09bf1af5a30befc2a007869fa6e1f516b8f7c591cb9
     Successfully built sklearn bs4 nltk absl-py termcolor gast smart-open bz2file
     Failed to build JPype1
     ```

     - 해결 방법

       1. ~~setuptools 업그레이드~~

       ```shell
       pip install --upgrade setuptools
       >Requirement already up-to-date: setuptools in c:\users\user\anaconda3\envs\pr_tensorflow\lib\site-packages (40.8.0)
       ```

       2. ~~Visual Studio 2017용 Build Tools install~~

          <https://visualstudio.microsoft.com/ko/downloads/>

          - ~~하단의 Visual Studio 2017용 도구 > Visual Studio 2017용 Build Tools 설치~~ 
          - 설치 후 재설치 : 여전히 같은 에러

       3. Microsoft Build Tools 2015 업데이트 3 install

          <https://visualstudio.microsoft.com/ko/downloads/>

          - 하단의 재배포 가능 패키지 및 빌드 도구 > Microsoft Build Tools 2015 업데이트 3 설치 

          - 설치 후 재설치 : 성공 

      ##### JPype1 설치 중 rc.exe 관련 문제

      ```shell
       LINK : fatal error LNK1158: cannot run 'rc.exe'
       error: command 'C:\\Program Files (x86)\\Microsoft Visual Studio 14.0\\VC\\BIN\\x86_amd64\\link.exe' failed with exit status 1158
      ```

      - 해결 방법

        1. conda install -c conda-forge implicit

           <!-- <https://github.com/benfred/implicit/issues/76>-->

        2. 먼저 설치한 ‘Visual Studio 2017용 Build Tools’와의 충돌로 보여서 Visual Studio 2017용 Build Tools 삭제 후 재설치

           <b> Jpype 설치 성공</b>

3. 주피터 노트북 실행 후 테스트

      - 가상환경에서 주피터 노트북 설치

        ```shell
        pip install ipykernel
        ```

      - base에서 주피터 노트북에 가상환경 커널 추가
        ```shell
        python -m ipykernel install --user --name [virtualEnv] --display-name "[displayKenrelName]"
        ```

   - tensorflow 패키지 사용 테스트까지 하면 실습 프로젝트 구성 끝!

     ```python
        import tensorflow as tf
     ```
