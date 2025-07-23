# GIt과 GitHub


## Remote Repository

> 원격저장소
> 
- 코드와 버전 관리 이력을 온라인 상의 특정 위치에 저장하여 여러 개발자가 협업하고 코드를 공유할 수 있는 저장 공간
- 다양한 원격저장소 서비스
    - Gitlab
    - GitHub
    - Bitbucket
  
## repository와 연결하기: remote
- `$ git remote add origin remote_repo_url`
    - `origin` : 추가하는 원격 저장소 별칭
    - `remote_repo_url` : 추가하는 원격 저장소 주소
- `$ git remote -v` : remote 확인
- `$ git remote remove repository_name` : 원격 저장소 삭제 명령


## repository에 올리기: add - commit - push
- `add`
     ```bash
     $ git add test.py
     ```
- `commit`
     ```bash
     $ git  commit -m"message"
     ```
- `push`
    ```bash
    $ git push origin master
    ```

## repository에서 local로 받기: clone or pull
- `clone`
     ```bash
     $ git clone URL.git
     ```
- `pull`
     ```bash
     $ git pull origin master
     ```
    > 둘의 차이는?
    
    - clone - init이 되지 않고, 프로젝트가 없는 상태 
    - pull - 이미 프로젝트가 repository에 연결되어 있는 상태

### 바로 직전 생성한 commit 수정하기

- `$ git commit --amend`  → [i]: message  → 수정 → `:wq`
- `$ git commit --amend`  → `:wq`  : 지금 staging area에 있는 파일도 해당 커밋으로 들어감
- 커밋의 횟수 / 날짜+시간 은 바뀌지 않지만 hash 값은 바뀜

<aside>
💡

[[git] 커밋 메세지 수정하기 (changing commit message)](https://velog.io/@mayinjanuary/git-%EC%BB%A4%EB%B0%8B-%EB%A9%94%EC%84%B8%EC%A7%80-%EC%88%98%EC%A0%95%ED%95%98%EA%B8%B0-changing-commit-message)

- 직전 뿐만 아니라 그 이전 commit 메시지도 수정하고 싶을 때 참고하기
<aside>

## gitignore

- Git에서 특정 파일이나 디렉토리를 추적하지 않도록 설정하는 데 사용되는 텍스트 파일
    - gitignore 예시
        - .gitignore 파일 생성(확장자X)
        - 추적하지 않을 파일명 작성
        - git init 전에 해야 함
        - 프로젝트에 따라 공유하지 않아야 하는 것들도 있기 때문
        - 이미 git의 관리를 받은 이력이 있느 파일이나 디렉토리는 나중에 gitignore 작성해도 적용  X → `git rm --cached` 하면 가능

> gitignore 목록 생성 서비스
> 

https://www.toptal.com/developers/gitignore

### Revert vs Reset + Reflog  -push 전 commit 상태에서만 적능

> Git revert
> 
> - `git revert <commit id>`
>     - commit id: hash 값 앞 4자리
> - 특정 commit을 실행 취소하는 것
- a 수행 → b 수행 → c 수행 → revert b
    - b 수행 commit은 남아 있으며, b를 없앴다는 기록이 최신으로 추가됨
- 정리
    - 변경 사항을 안전하게 실행 취소할 수 있도록 도와주는 **순방향** 실행 취소 작업
        - 역방향도 있다?
            - `reset`
    - commit 기록에서 commit을 삭제하거나 분리하는 대신, 지정된 변경 사항을 반전시키는 새 commit 생성
        - git에서 기록이 손실되는 것 방지 + 기록의 무결성과 **협업**의 신뢰성을 높임
        - 협업할 때에는 `reset` 대신 `revert` 사용!
- 추가 명령어
    - `git revert hash hash hash` : 여러 commit을 한꺼번에 취소 가능
    - `git revert hash..hash` : ..를 활용해서 범위 지정
    - `git revert --no-edit hash` : Vim editor 열지 않고 자동으로 진행
    - `git revert --no-commit hash`
        - commit 하지 않고 staging area에만 올리는 것
        - VIM editor도 열리지 않고 commit되지도 않음
    

> Git reset
> 
> - `git reset [option] <commit id>`
> - 이전으로 “되돌아가기” = 특정 commit으로 되돌아감
- 작동원리
    - 특정 commit으로 되돌아 갔을 때, 되돌아간 commit 이후의 commit은 모두 삭제
- reset의 3가지 옵션
    - 삭제되는 commit들의 기록을 어떤 영역에 남겨둘 것인지 옵션을 활용해 조정할 수 있
        - `—soft`: 삭제된  commit의 기록을 staging area에 남김
            - 다시 commit하고 싶다면 add 없이 바로 commit하면 됨
                
                ```bash
                SSAFY@2□□PC081 MINGW64 ~/Desktop/reset-revert-practice/reset/soft (master)
                $ git log
                commit d7c85015ea5776d87ee6b494f869644d065af6ee (HEAD -> master)
                Author: eduharryjjun <eduharryjjun@gmail.com>
                Date:   Thu Oct 12 21:24:20 2023 +0900
                
                    third
                
                commit 91cbd74ec969ce40577658673789755440b7bd18
                Author: eduharryjjun <eduharryjjun@gmail.com>
                Date:   Thu Oct 12 21:24:04 2023 +0900
                
                    second
                
                commit f7b3a3d879dbfcab4ae90f1c3c7050ef0cd29913
                Author: eduharryjjun <eduharryjjun@gmail.com>
                Date:   Thu Oct 12 21:23:08 2023 +0900
                
                    first
                
                SSAFY@2□□PC081 MINGW64 ~/Desktop/reset-revert-practice/reset/soft (master)
                $ git reset --soft f7b3
                
                SSAFY@2□□PC081 MINGW64 ~/Desktop/reset-revert-practice/reset/soft (master)
                $ git log
                commit f7b3a3d879dbfcab4ae90f1c3c7050ef0cd29913 (HEAD -> master)
                Author: eduharryjjun <eduharryjjun@gmail.com>
                Date:   Thu Oct 12 21:23:08 2023 +0900
                
                    first
                    
                SSAFY@2□□PC081 MINGW64 ~/Desktop/reset-revert-practice/reset/soft (master)
                $ git status
                On branch master
                Changes to be committed:
                  (use "git restore --staged <file>..." to unstage)
                        new file:   2.txt
                        new file:   3.txt
                
                Untracked files:
                  (use "git add <file>..." to include in what will be committed)
                        untracked.txt
                
                ```
                
        - `—mixed`: default: 삭제된 commit의 기록을 working directory에 남김
            - 다시 commit하고 싶다면 add → commit해야
                
                ```bash
                SSAFY@2□□PC081 MINGW64 ~/Desktop/reset-revert-practice/reset/mixed (master)
                $ git log --oneline
                d7c8501 (HEAD -> master) third
                91cbd74 second
                f7b3a3d first
                
                SSAFY@2□□PC081 MINGW64 ~/Desktop/reset-revert-practice/reset/mixed (master)
                $ git reset f7b3
                
                SSAFY@2□□PC081 MINGW64 ~/Desktop/reset-revert-practice/reset/mixed (master)
                $ git log --oneline
                f7b3a3d (HEAD -> master) first
                
                SSAFY@2□□PC081 MINGW64 ~/Desktop/reset-revert-practice/reset/mixed (master)
                $ git status
                On branch master
                Untracked files:
                  (use "git add <file>..." to include in what will be committed)
                        2.txt
                        3.txt
                        untracked.txt
                
                nothing added to commit but untracked files present (use "git add" to track)
                ```
                
        - `—hard`: 삭제된 commit의 기록을 남기지 않음
            
            ```bash
            SSAFY@2□□PC081 MINGW64 ~/Desktop/reset-revert-practice/reset/hard (master)
            $ git log --oneline
            d7c8501 (HEAD -> master) third
            91cbd74 second
            f7b3a3d first
            
            SSAFY@2□□PC081 MINGW64 ~/Desktop/reset-revert-practice/reset/hard (master)
            $ git reset --hard f7b3
            HEAD is now at f7b3a3d first
            
            SSAFY@2□□PC081 MINGW64 ~/Desktop/reset-revert-practice/reset/hard (master)
            $ git log --oneline
            f7b3a3d (HEAD -> master) first
            
            SSAFY@2□□PC081 MINGW64 ~/Desktop/reset-revert-practice/reset/hard (master)
            $ git status
            On branch master
            Untracked files:
              (use "git add <file>..." to include in what will be committed)
                    untracked.txt
            
            nothing added to commit but untracked files present (use "git add" to track)
            ```
            
            - 참고
                - 이미 삭제한 commit으로 다시 돌아가고 싶다면?
                    - `git reflog` : HEAD가 이전에 가리켰던 모든 commit을 보여줌
                        - reset의 —hard 옵션을 통해 지워진 commit도 reflog로 조회하여 복구 가능
                        - 

###### 그럼 산출물은 그대로, commit 기록'만'을 지우고 싶을 땐? - test해보자 -> 가능한!
`git reset --soft hash` -> `git commit --amend --no-edit`

