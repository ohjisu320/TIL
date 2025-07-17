> GIt과 GitHub
>

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