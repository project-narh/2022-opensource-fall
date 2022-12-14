# 2022-opensource-fall
서강대학교 겜교원 오픈소스 이해, 가을학기 수강

## 리눅스 커맨드라인 기초
> 모르면 실습이 불가능한 기초 커맨드라인 3가지
1. pwd : print working directory
2. ls : list
3. cd : change directory

## vim 에디터
```bash
vim abc.txt // abc.txt 파일을 vim 에디터로 넣기
```

- 파일은 처음에 열면 명령모드로 진입
- 입력하려면 입력모드로 진입
- 입력 모드 : 키보드 i 입력

- 명령 모드 : 키보드 ESC

- 명령 모드에서 작업
  -저장하기 w(write) --> :w
  -나오기(quit) --> :q
  -저장하고 나오기 --> :wq
  -강제 종료 및 나오기 -->  :wq!
  
## 스왑파일 생성시 해결 방법
#### 스왑파일이 생기는 경우
- VIM 을 작성하다가 저장을 하지 않고 강제 종료하고 다시 열어보면 어텐션(Attention)이 뜨게 된다.
- 파일은 .swp 파일로 생성이 되어 있다

이게 뜨는 이유
  1. 두 사람 이상의 사람이 한번에 작성할 경우
  2. 파일이 crash
#### 해결방법
리커버리를 사용하여 열면 된다

```bash
vim -r 파일.확장자
```

만일 그냥 먼저 열고 어텐션이 뜨면 R을 눌러서 리커버리 모드로 들어가고 엔터를 누른다

만일 해결했는데도 위와 같은 문제가 계속 발생되면 .swp 파일을 제거하면 된다
 
 ## git

  대표적으로 사용되는 버전 관리 시스템(Version Control System, VCS)

### git 과 github의 차이점
  - git은 버전 관리 시스템
  - github는 git이라는 기술을 기반으로 만든 플랫폼
    - github에서 만들었는데 마이크로소프트가 인수하였다

### 다양한 버전 관리 시스템
 - 이름 변경
   - 최종.hwp, 최종1.hwp, 최종2.hwp
  - 자동 저장 기능
  - git 이전의 버전 관리 시스템
    - SYN, CVS, Mercurial
  - 요즘엔 git이 거의 표준이 되었다

# 2022-09-29
## 커밋은 언제 만드는가?
- 논리적 변경이 있을때!
  - 커밋을 쪼갤 수도 있고 합칠수도 있으며 순서를 변경하는것도 가능
  - 책에서 목차를 만드는거랑 저장소에서 커밋 만드는게 유사
    - 장애 대응에 유연하게 하기 위해서,
    - 그리고 코드를 리뷰하기 위해서는 너무 많은 코드를 커밋하는건 좋지 않다
    - 즉 커밋 크기는 작게 하는것을 대기업에서 많이 사용 중

- 커밋을 최소하는데도 작아야 유리하기 때문에 커밋을 작게 작게 하자

## 커밋으로 버그 찾기
- 커밋 이력 확인 -> checkout으로 되돌려서 진행
- 버그 유발 코드를 찾았다면 다시 되돌아와야 한다
- 그리고 최신 HEAD 에서 수정을 하도록 하자 안그러면 참사야

## 로그를 보는 법
- GUI이용하거나 git log (나올때는 VIM 과 동일 q 누르기)

## git 커밋 수정 및 합치기

- 예를 들어 컴퓨터와 노트북을 왔다갔다 하며 작업할때
- 내용을 옮기기 위해서 필요없는 커밋이 발생된다 이럴경우는 커밋을 합치면 되는 문제
- git rebase -i(Interactive) haed~1 이런식으로 합치면 된다.
  - 뒤 숫자는 몇개의 커밋을 합칠지 결정하는 것이다

- 또는 pull 하고 해당 커밋을 삭제하던가

- git push -f origin master를 이용해서 올려준다

## 저장소와 디렉토리의 차이
- 저장소(repository) -> 무언가를 담아두는 곳
- 저장소냐 아니냐의 차이는 숨긴 파일에 .git이 있냐 없냐

## 저장소 만들기
- git init(initialization)

- $ mkdir Test-git-repository

- $ cd Test-git-repository/

- $ git init
- Initialized empty Git repository in C:/Users/
- (bash를 보면 (master)가 생긴다)

- $ pwd

- 일반 파일도 저장소로 바꾸는 명령어

## 저장소 제거
- re -rf .git 명령어를 치면 저장소에서 일반 폴더로 바뀌게 된다
- (bash를 보면 (master)가 사라진다)
- 아니면 그냥 .git 삭제
# 2022-10-06

## 스테이징 영역
 - 커밋에 포함시킬 변경분만 올리는 영역
   -   stage의 뜻 : 무대
- 스테이징 영역을 잘 활용해야 커밋을 잘 만들 수 있다.

# 2022-10-06
## 커밋 로그를 성의 있게 작성하기
  - 코드를 고친 이유와 고친 코드를 설명하기
  - 포크한 저장소와 본인이 만든 저장소가 구분이 되도록 설명을 작성하기
  - github 이슈와 풀리퀘스트 활용
  - <트위터 - 이재홍>

## 커밋을 위해서는 왜? ADD를 써야 하는가?

  - 앞서 작성한 스테이징 영역에 업로드 하는 것
  - 스테이징 영역에 있어야 커밋을 할때 같이 업로드가 된다.

## 브랜치란?

  - 브랜치는 나무의 가지라고 보면 된다

  - 과거의 최상위 브랜치 명은 master을 사용했지만 현재는 main을 사용중

  - 브랜치를 생성하는 것은 기능을 추가하거나 버그를 고치거나 어떠한 새로운 행동을 할때 진행된다.

  - 따로 작업한 브랜치는 분기가 이어지기 위해서는 병합 또는 rebase를 진행해주면 된다

##  git branch 브랜치 이름
  - 브랜치로 이동
    - git switch 브랜치 이름
    - git branch 브랜치 이름

## checkout(조사하다) vs switch(전환하다)
 - 기능은 동일
 - 예전이는 switch가 없었지만 시간이 지나고 직관성이 떨어져서 사용하게 됨

## non fast-forward 병합
   - 병합(머지)할때 분기가 안보이고 일자가 되는 현상은 fast-forward 머지가 되었기 때문
   - 커밋을 남기지 않고 병합한것(따라간다)

   - non fast-forward 의 경우는 커밋을 남기고 병합을 진행하는것을 뜻합니다

   - 머지 : git merge (브랜치)
   
   - non fast-forward : git merge --no-ff (브랜치)
   
   - 브랜치가 Fast-Forward인 경우에만 병합 : git merge --ff-only (브랜치)

## gitignore란?
   - 그냥 커밋을 하면 필요없는 파일마저 업로드 될 가능성이 존재합니다.
   - 이를 방지하기 위해서 깃이그노어로 걸러질 파일을 구분하는 것

   - 생성은 깃허브에서 리포지토리를 만들때 진행해도 되지만 https://www.toptal.com/developers/gitignore
   - 해당 사이트에서 제작후 복사하고
   - .gitignore 라는 파일명으로 위 내용을 복사한후 생성해도 무관하다

# 2022-10-13

## 중간고사 내용 정리

  1. 기본적으로 알아야 하는 커맨드라인 명령어
      - pwd, cd, ls : 약자
  2. vim 사용법
      - 명령모드와 입력모드의 차이, 어떻개 각 모드로 전활할 수 있는지
      - 명령모드에서 저장하고 빠져나오는 방법
  3. 버전관리는 사용하는 이유
    - 3가지
  4. git과 github의 차이
  5. 저장소와 일반 폴더의 차이
    - 저장소 만들때 쓰는 명령어 git init
  6. 커밋 로그 보고 싶을때 치는 명령어
  7. 커밋은 언제 만드는가
  8. HEAD의 정의 : 현재 체크아웃한 브랜치의 가장 최신 커밋을 나타내는 포인터
  9. 현재 상태를 확인하는 명령어 git status
  10. 스테이징 영역이 왜 존재하는가? (서술형)
  11. 원하는 파일을 스테이징 영역에 올릴떄 쓰는 명령어
  12. 커맛 메시지가 "abc"인 커밋을 만들고 싶을때 어떻게 해야 하나?
    - git commint -m "abc"
    - git commint 엔터치고 abc 입력
  13. .gitignore파일의 역할
  14. 브랜치는 언제 만드는가?
  15. 브랜치 관련 명령어
    - 현재 현재 생성된 브랜치 목록 확인 : git branch
    - 브랜치 생성 : git branch (브랜치명)
    - 브랜치 삭제 : git branch -d (브랜치명)
    - 브랜치 이동 : git checkout (브랜치명) / git switch (브랜치명)
    - 브랜치 생성하고 이동 : git checkout -b (브랜치명)
  16. a라는 브랜치를 b라는 브랜치로 병합할때
    - 1. B라는 브랜치 checkout
    - 2. git merge a
    
    # 기말
  ## 병합의 방법
  - 1. 일반 병합
  - 2. Rebase
  - 각 병합하는 커밋의 아래  커밋들중 중복이 되는것을 제외하고 기준이 되는 브랜치 아래에 재정렬 한다
  - 그래프가 깔끔해지는 효과가 있다.

  ### 차이점
   - 일반 병합은 머지 차이가 생기고 그래프가 복잡해진다.
   - Rebase는 그래프가 깔끔한 장점이 존재

   ### 회사에서는?
    - 회사마다 다르다.
    - 다만 대부분에서는 그냥 머지(머지를 한 지점을 확실하게 알기 위해서)
    - 풀 리퀘스트를 할때 그냥 머지를 하고 진행하면 커밋 이력에 머지 이력이 남아있게 된다.
    - 다만 회사에서는 이렇게 진행하면 안된다 곤란하다.
    - 그렇기 떄문에 rebase를 진행하고 풀리퀘스트를 많이 진행하고 있다.

    ### 리베이스 쓰는 경우
      1. 커밋 메시지 변경하고 싶을때
      2. 커밋 순서 바꾸고 싶을떄
      3. 중간 커밋만 삭제하고 싶을때
      4. 중간에 있는 커밋을 

 - gitk : 깃에서 제공해주는 그래픽 파일

 ## 윈도우와 맥의 엔터 처리 방식
  - 윈도우는 CRLF 맥은 LF 방식을 사용중
  - 사용하다보면 워닝이 뜨는 경우 발생 이는 사용자와 다른 사용자의 환경이 달라서 엔더 방식에서 충돌이 생김
  - git config --global core.autocrlf true 를 활성화 해주면 자동 변경
  - 자동 변경의 원리는 커밋을 하면 자동으로 LF로 변경 윈도우 사용자가 체크아웃을 하면 CRLF로 변경
  - 교수님은 그냥 어떤 환경이든 LF으로 변경해서 진행하심(그러면 문제 생길일 없음)

## 마지막 커밋을 수정하는 방법
 - git commit --amend -m  "내용"(커밋 메시지를 수정하겠다)
 - 중간에 꺼를 수정하고 싶으면 rebase-i
 Commands:
- p, pick <commit> = use commit
- r, reword <commit> = use commit, but edit the commit message
- e, edit <commit> = use commit, but stop for amending
- s, squash <commit> = use commit, but meld into previous commit
- f, fixup [-C | -c] <commit> = like "squash" but keep only the previous
-                    commit's log message, unless -C is used, in which case
-                    keep only this commit's message; -c is same as -C but
-                    opens the editor
- x, exec <command> = run command (the rest of the line) using shell
- b, break = stop here (continue rebase later with 'git rebase --continue')
- d, drop <commit> = remove commit
- l, label <label> = label current HEAD with a name
- t, reset <label> = reset HEAD to a label
- m, merge [-C <commit> | -c <commit>] <label> [# <oneline>]
- .       create a merge commit using the original merge commit's
- .       message (or the oneline, if no original merge commit was

# 깃 활용 공부를 하는 https://git-school.github.io/visualizing-git/
## 여기서 화살표가 우리가 생각하는 방향과 반대인 이유
 - 깃은 Linked List로 구현되어 있음
  - 여기서 화살표는 부모 노드를 가리키는 것
