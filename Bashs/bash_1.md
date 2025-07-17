## 경로 실습

> 상대경로 vs 절대경로
> 
- 경로 = 내가 어디에 있는가?
    - CLI에서 가장 중요한 것
- 경로의 핵심 개념
    - 루트 디렉토리 (/)
        - 모든 주소의 시작점
    - 홈 디렉토리 (~)
        - 터미널 처음 켰을 때 시작하는 나의 기본 공간
        
        ```bash
        SSAFY@2▒▒PC081 MINGW64 /
        $ cd ~
        
        SSAFY@2▒▒PC081 MINGW64 ~
        $ pwd
        /c/Users/SSAFY
        ```
        
- 절대경로
    - 누가 어디서 어떻게 보든 항상 똑같은 주소
- 상대경로
    - 내 위치에 따라서 상대적으로 결정됨

`pwd` : print working directory

```bash
PS C:\Users\SSAFY> pwd

Path
----
C:\Users\SSAFY
```

`cd` : change directory

```bash
PS C:\Users\SSAFY> cd Desktop
PS C:\Users\SSAFY\Desktop> pwd

Path
----
C:\Users\SSAFY\Desktop
```

`mkdir` : make directory

```bash
SSAFY@2▒▒PC081 MINGW64 ~/Desktop
$ mkdir edu

SSAFY@2▒▒PC081 MINGW64 ~/Desktop
$ ls
'A형 검정_SW역량테스트.url'   Excel.lnk*        SW검정/                                     Webex.lnk*    edu/         설치파일/
'B형 검정_SW역량테스트.url'   GitLab.lnk*      'VS Express 2017 for Windows Desktop.lnk'*   a/            edu_sky/
'Eclipse Java 2018-09.lnk'*   Mattermost.lnk*  'Visual Studio Code.lnk'*                    desktop.ini   edu_sky_1/

```

`touch`: 파일 새로 만들 때

```bash
SSAFY@2▒▒PC081 MINGW64 ~/Desktop/edu_sky_1
$ touch a.txt
```

`start`: 파일 열기 == mac.os - open

```bash
SSAFY@2▒▒PC081 MINGW64 ~/Desktop/edu_sky_1
$ start a.txt
```

`rm`: 파일 삭제

```bash
SSAFY@2▒▒PC081 MINGW64 ~/Desktop/edu_sky_1
$ start a.txt
```

`rm -r`: 디렉토리 삭제

```bash
SSAFY@2▒▒PC081 MINGW64 ~/Desktop/edu_sky_1
$ ls
a.txt  edu1/

SSAFY@2▒▒PC081 MINGW64 ~/Desktop/edu_sky_1
$ rm -r edu1

SSAFY@2▒▒PC081 MINGW64 ~/Desktop/edu_sky_1
$ ls
a.txt

```