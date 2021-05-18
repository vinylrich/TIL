# git 입문
## git & github

git의 목적

    1. 버전 관리: 데이터가 기하급수적으로 늘어나면서 저장 할 때마다 적절한 설명을 넣을 수 있고 싶게 됐다.
    2. 백업: 이전에 commit 했던 데이터를 뽑아 쓸 수 있다
    3. 협업: 협업 과정에서 일어날 수 있는 덮어쓰기 등등의 문제를 일어나지 않게 할 수 있다

기본 명령어

    - git init: 레포 initialize
    - git log:커밋 로그
    - git commit
    - git status: 상태
        --stat
    - git add: filename 추가
    - git commit : create version
    - git diff: show changes
    - git reset: 코드 폐기
git에는
Working tree, staging Area, Repository 가 있다.

Working tree: 우리가 수정한 파일들
Staging Area: 버전을 만들려고 하는 파일들
Repository: 만들어진 버전

### untracked files
git add "filename" filename의 버전을 만들거니까 올려라