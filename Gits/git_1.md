## Git!!!

> 버전 관리 시스템

- git ?
    - 분산 **버전(history) 관리 시스템**: 코드의 변경이력 기록 & 협업
- 버전 관리
    - 변화를 기록하고 추적하는 것
    - 이전 버전으로 돌아가기(롤백) 가능!
    - 게임에서 세이브하는 것과 같음
    - 각 버전은 이전 버전으로부터의 변경사항을 기록하고 있다
    - 마지막 최종 모습 + 그간의 변경사항만 기록하는 것 - git의 원칙
- 분산?
    - 중앙 vs 분산
        - 중앙 집중식
            - 버전은 중앙 서버에 저장되고 중앙 서버에서 파일을 가져와 다시 중앙에 업로드
            - 모든 파일을 중앙 서버에서 관리하고 각각의 로컬 컴퓨터는 클라우드를 이용하고 다시 중앙에 업로드 하는 방식
        - 분산식: 버전을 여러 개의 복제된 저장소에 저장 및 관리
            - 장점
                - 중앙 서버에 의존하지 않고도 동시에 다양한 작업 수행 가능
                    - 개발자들 간의 작업 충돌 줄여줌
                - 백업과 복구가 용이
                - 인터넷 연결되지 않아도 작업 가능

> git의 영역: 세 가지 다 **“정확히”** 알아두기
> 
- Working Directory( = 작업디렉토리, 작업영역)
    - 실제 작업 중인 파일들이 위치하는 영역
- Staging Area( = “스테이징 에어리어”그대로 씀)
    - Working Directory에서 변경된 파일 중, 다음 버전에 포함시킬 파일들을 선택적으로 추가하거나 제외할 수 있는 중간 준비 영역
- **Repository: 저장소**
    - 실제로 있는 영역
    - 버전 이력과 파일들이 영구적으로 저장되는 영역
        - commit: 깃발을 꽂는 것: 버전을 찍는다: snapshot(사진 찍듯이 기록한다)
        - push:

> git의 동작
> 
- terminal → [+] →[select default profile] → [git bash] 로 변경하면 new terminal 열었을 때 bash가 나옴
- `git init`
    - 로컬 저장소 설정(초기화) == 깃 초기화
    - git의 버전 관리를 시작할 디렉토리에서 진행
        - 내가 버전관리를 시작할 디렉토리인 prac_md라는 폴더 안에서 `git init` 수행
        - (master) vs (main)의 차이
            
            ```bash
            $ git init
            Initialized empty Git repository in C:/Users/SSAFY/Desktop/prac_md/.git/
            
            SSAFY@2□□PC081 MINGW64 ~/Desktop/prac_md (master)
            ```
            
- `git add`
    - 변경 사항이 있는 파일을 staging area에 올리기
- `git commit`
    - 커밋 수행
    - staging area에 있는 파일들을 저장소에 기록
    - 해당 시점의 버전을 생성하고 변경 이력을 남기는 것

<aside>
💡

- `ls -a`
    - 숨긴 파일 보는 방법
    - **a: all**(모두)의 약자
        - `rm -r`에서 `-r` 옵션은 **recursive**의 약자
        - `rm -rf`에서 `-rf` 옵션은 **recursive force**의 약자
</aside>

> git 실습
> 
1. 파일 생성 후 로컬 저장소의 파일 상태 확인 `git status` : 파일 상태 확인하는 명령어

```bash
$ git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        sample.txt

nothing added to commit but untracked files present (use "git add" to track)
```

1. sample.txt 파일을 staging area에 추가 - Index Added

```bash
SSAFY@2□□PC081 MINGW64 ~/Desktop/git_practice (master)
$ git add sample.txt

SSAFY@2□□PC081 MINGW64 ~/Desktop/git_practice (master)
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   sample.txt

```

- `git rm --cached <file>...` : unstage 하는 git 명령어
    
    ```bash
    SSAFY@2□□PC081 MINGW64 ~/Desktop/git_practice (master)
    $ git rm --cashed sample.txt
    error: unknown option `cashed'
    usage: git rm [-f | --force] [-n] [-r] [--cached] [--ignore-unmatch]
                  [--quiet] [--pathspec-from-file=<file> [--pathspec-file-nul]]
                  [--] [<pathspec>...]
    
        -n, --[no-]dry-run    dry run
        -q, --[no-]quiet      do not list removed files
        --[no-]cached         only remove from the index
        -f, --[no-]force      override the up-to-date check
        -r                    allow recursive removal
        --[no-]ignore-unmatch exit with a zero status even if nothing matched
        --[no-]sparse         allow updating entries outside of the sparse-checkout cone
        --[no-]pathspec-from-file <file>
                              read pathspec from file
        --[no-]pathspec-file-nul
                              with --pathspec-from-file, pathspec elements are separated with NUL character
    
    SSAFY@2□□PC081 MINGW64 ~/Desktop/git_practice (master)
    $ git status
    On branch master
    
    No commits yet
    
    Changes to be committed:
      (use "git rm --cached <file>..." to unstage)
            new file:   sample.txt
    
    ```
    
1. commit 생성하기
    
    `git commit` 만 하면 에러가 남. 메시지를 함께 넣어야 함
    
    → `git commit -m "message"` 를 해야 함
    
    ```bash
    SSAFY@2□□PC081 MINGW64 ~/Desktop/git_practice (master)
    $ git commit
    Author identity unknown
    
    *** Please tell me who you are.
    
    Run
    
      git config --global user.email "you@example.com"
      git config --global user.name "Your Name"
    
    to set your account's default identity.
    Omit --global to set the identity only in this repository.
    
    fatal: unable to auto-detect email address (got 'SSAFY@2��PC081.(none)')
    ```
    
    ```bash
    SSAFY@2□□PC081 MINGW64 ~/Desktop/git_practice (master)
    $ git commit -m "first commit"
    Author identity unknown
    
    *** Please tell me who you are.
    
    Run
    
      git config --global user.email "you@example.com"
      git config --global user.name "Your Name"
    
    to set your account's default identity.
    Omit --global to set the identity only in this repository.
    
    fatal: unable to auto-detect email address (got 'SSAFY@2��PC081.(none)')
    ```
    
- commit의 작성자 정보가 필요함!
사용자 정보 등록 방법
    
    `git config --global [user.email](http://user.email) "ohjisu320@gmail.com"`
    
    `git config --global [user.email](http://user.email) "유저네임"`
    
    ```bash
    SSAFY@2□□PC081 MINGW64 ~/Desktop/git_practice (master)
    $ git config --global user.email "ohjisu320@gmail.com"
    
    SSAFY@2□□PC081 MINGW64 ~/Desktop/git_practice (master)
    $ git config --global user.name "ohjisu320"
    
    SSAFY@2□□PC081 MINGW64 ~/Desktop/git_practice (master)
    $ git commit -m "first commit"
    [master (root-commit) 48f6270] first commit
     1 file changed, 0 insertions(+), 0 deletions(-)
     create mode 100644 sample.txt
    ```
    
- commit 목록 확인
    
    ```bash
    $ git log
    commit 48f62705c5c09ee978554a4fcd799d368eee49ec (HEAD -> master)
    Author: unknown <ohjisu320@gmail.com>
    Date:   Wed Jul 16 17:27:37 2025 +0900
    
        first commit
    
    ```