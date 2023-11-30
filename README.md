# git_study
git, github
- git
    - 분산 버전 관리 시스템으로서, 소스 코드의 변경사항을 추적하는 데 사용
    - 로컬 시스템과 원격 시스템을 두어, 로컬에서 작업 후 원격공간 동기화
    - 주요 명령어에는 add, commit, push, pull, merge, branch, checkout 등
    - 브랜치(branch) 기능을 통해 여러 개발자가 동시에 개발하면서도 충돌 없이 작업
    - pr : pull request => main branch에 merge해달라고 요청하는 것 = 한 branch에 누가 계속 작업했는지 남는다.

버전관리 시스템
    - Working Directory에서 작업 후 새로운 버전이 될 후보군은 Staging Area로 이동
        - 파일 수정 / 생성 후

    - Staging Area
        - git add .
        - 이 단계에서는 local repository로 파일을 넣기 위한 대상 목록 관리
        - stage, 인덱스는 Staging을 가리키는 같은 용어
        - 로컬저장소로 넣으면, 그 때부터 이력이 생성

    - 로컬 저장소(local repo)
        - git commit -m "남길메시지"
        - staging area에서 commit을 하고 나면 새로운 버전이 생성

소스트리
    - git repo 파일들의 branch 관계를 시각적으로 보여줌

git 연동 인증방식
- OAuth : 자동으로 이루어진다.(VScode에서 git 최초 연동 시 OAuth 방식으로 인증)
- PAT(Personal access tokens) : git에서 수동으로 token을 생성해서 Windows 자격증명 - '일반자격증명추가'에 git 증명을 추가.
    - 이 PAT 키값은 최초 생성했을때만 확인 가능, 관리를 잘해야 한다.
        - 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

git 명령어
- git status
    - 현재 작업 디렉토리와 staging area의 상태를 보여주는 명령어

- git add .
    - staging area로 업로드
    - git status로 staging 상태확인

- git commit -m "first commit"
    - local repository로 업로드 및 커밋이력 생성
    - git commit -m "제목파트" -m"내용파트"
    - git log로 커밋이력 확인
    - git commit 만 하게 되면 메시지 입력모드로 전환. 첫줄에 title, 두번째 줄부터 contents

- git commit -am "커밋메시지"
    - add와 commit을 동시에

- git push origin main
    - commit 했던 파일 origin으로 psuh

- git branch
    - 최초로 만들어졌던 branch 확인(main)

- git log
    - git commit log 확인


git 프로젝트 생성 및 수정절차

- 신규 프로젝트 생성시
    - 방법1
        - git clone repository 주소
        - 해당 폴더로 이동하여 개발시작
    - 방법2
        - **로컬 컴퓨터에서부터 이미 개발된 프로젝트가 존재시**
            - 로컬 컴퓨터에서 github로 프로젝트 올리는
        - git init
            - .git파일(commit 이력, 원격지(github) 주소, branch 정보) 생성
            - .git 폴더가 위치한 곳에서 git config —list를 통해 컨피그 정보 조회
        - git remote add origin [repository 주소]
            - origin이란, 깃허브 저장소 주소를 의미(즉, 원격저장소를 의미)
        - git remote set-url origin [repository 주소]
            - url변경 후 main에 push하면 main의 commit 이력과 함께 업로드
        - git remote remove origin

- 모든 이력 push
    - git push —all origin
        - 모든 브랜치의 커밋이력 push
        
        git checkout -b main
        - commit branch main으로 변경


        **Commit 이력까지 내걸로 초기화 해서 Repo 복제하기**

        git clone https://github.com/kimseonguk198/test_spring.git
        - git repo 다운로드
        
        clone 받은 repo파일내에 .git 파일 삭제(파일 탐색기)

        git init
        - repo파일내에 .git 파일 다시 생성
        
        git remote add origin [repository 주소]
        - .git 파일에 나의 repo 주소 입력
        git add .
        git commit -m “first commit”
        git branch
        git checkout -b main
        git push origin main
        

        **이전 Commit 이력을 다 살려서 Repo 복제하기**

        git clone https://github.com/kimseonguk198/test_spring.git
        - git repo 다운로드
        
        cd .\test_spring\
        - clone 된 해당 repo로 이동
        
        git remote set-url origin https://github.com/GreatJang/Test_Git2.git
        - 내 repo url로 변경
        
        git push origin main
        - main branch에 push