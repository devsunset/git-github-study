--------------------------------------------------------------------------------

			# GIT-GITHUB-WORK #

--------------------------------------------------------------------------------

--- Git Reference ---
[[Git]]
https://git-scm.com/
 
 [[Git Book]]
 https://git-scm.com/book/ko/v2
 	https://git-scm.com/book/en/v2

[[Git GUI Client]]
https://git-scm.com/download/gui/linux

[[Git ignore]]
.gitignore
https://www.toptal.com/developers/gitignore

[[Git Guide]]
https://www.youtube.com/watch?v=Bd35Ze7-dIw
https://www.youtube.com/watch?v=FXDjmsiv8fI
https://www.youtube.com/watch?v=GaKjTjwcKQo

https://rogerdudler.github.io/git-guide/index.ko.html
	http://rogerdudler.github.io/git-guide/
https://www.pigno.se/barn/tutorial-git/docs/#/?id=innocent-%eb%b0%94%ec%81%98%ec%9e%96%ec%95%84%ec%9a%94-%eb%8b%a4%eb%93%a4
https://backlog.com/git-tutorial/kr/


[[Git Hub]]
https://github.com/
https://docs.github.com/en

[[Etc]]
https://about.gitlab.com/
https://bitbucket.org/

--------------------------------------------------------------------------------

--- Git Study ---
https://www.youtube.com/watch?v=Bd35Ze7-dIw
https://www.youtube.com/watch?v=FXDjmsiv8fI
https://www.youtube.com/watch?v=GaKjTjwcKQo
https://rogerdudler.github.io/git-guide/index.ko.html
https://www.pigno.se/barn/tutorial-git/docs/#/?id=innocent-%eb%b0%94%ec%81%98%ec%9e%96%ec%95%84%ec%9a%94-%eb%8b%a4%eb%93%a4
https://backlog.com/git-tutorial/kr/
 https://git-scm.com/book/ko/v2

--------------------------------------------------------------------------------

[[ git simple guide summary]]

* 새로운 저장소 만들기
git init

* 저장소 받아오기
로컬 저장소를 복제(clone)
git clone /로컬/저장소/경로

원격 서버의 저장소를 복제
git clone 사용자명@호스트:/원격/저장소/경로

* 작업 흐름
working dir --- (add) ---> index (Stage) ---(commit) ---> Head ---(push) ---> 원격 저장소

* 변경된 파일은 아래 명령어로 (인덱스에) 추가
git add <파일 이름>
git add *

* 변경 내용을 확정
git commit -m "이번 확정본에 대한 설명"

* 변경 내용을 원격 서버
git push origin master
- branch로 적용시 master를 원하는 branch 이름으로 설정

기존에 있던 원격 저장소를 복제한 것이 아니라면,
원격 서버의 주소를 git에 설정
git remote add origin <원격 서버 주소>

* branch 
"feature_x"라는 이름의 branch 생성 후 변경
git checkout -b feature_x

master로 변경
git checkout master

branch 삭제
git branch -d feature_x

* merge
로컬 저장소를 원격 저장소에 맞춰 갱신
git pull  -> 원격 저장소의 변경 내용이 로컬 작업 디렉토리에 받아지고(fetch), 병합(merge)됨

다른 branch에 있는 변경 내용을 현재 branch(예를 들면, master)에
병합하려면 아래 명령을 실행하세요.
git merge <branch name>

conflicts 발생시 수동으로 병합 
git add <파일 이름>

변경 내용을 병합하기 전에, 어떻게 바뀌었는지 비교
git diff <원래 branch> <비교 대상 branch>

* tag
git tag 1.0.0 1b2e1d63ff
1b2e1d63ff 부분은 꼬리표가 가리킬 확정본 식별자
아래 명령으로 확정본 식별자 조회
git log

확정본 식별자의 앞부분 일부만 입력해도 꼬리표를 붙일 수 있지만,
그 일부분이 반드시 고유하다는 조건이 필요

* 로컬 변경 내용 되돌리기
git checkout -- <파일 이름>
로컬의 변경 내용을 변경 전 상태(HEAD)로 되돌림
다만, 이미 인덱스에 추가된 변경 내용과
새로 생성한 파일은 그대로 남음

로컬에 있는 모든 변경 내용과 확정본을 포기하려면,
아래 명령으로 원격 저장소의 최신 이력을 가져오고,
로컬 master 가지가 저 이력을 가리키도록 설정

git fetch origin
git reset --hard origin/master

* 유용한 힌트
git의 내장 GUI
gitk
콘솔에서 git output을 컬러로 출력하기
git config color.ui true
이력(log)에서 확정본 1개를 딱 한 줄로만 표시하기
git config format.pretty oneline
파일을 추가할 때 대화식으로 추가하기
git add -i

--------------------------------------------------------------------------------

[[git]]

$ git config --global user.name "devsunset"
$ git config --global user.email "devsunset@gmail.com"

$ git init

$ git remote add origin https://github.com/devsunset/git-github-work.git

$ git clone https://github.com/devsunset/git-github-work.git

$ git add .
$ git add . -f

$ git remote show origin

$ git status

$ git add *
$ git commit -m "commit message"
option --amend ; overwrite

fetch
pull -> fetch + merge

$ git reset HEAD^ --soft
--soft는 약한특성의 리셋입니다, 되돌릴 때 기존의 인덱스와 워킹트리를 보존합니다.
--hard는 강한특성의 리셋입니다, 되돌릴 때 기존의 인덱스와 워킹트리를 버립니다.
--mixed는 중간특성의 리셋입니다, 되돌릴 때 기존의 인덱스는 버리고 워킹트리를 보존합니다.

# 바로 이전 단계로 인덱스와 워킹트리를 버리고 리셋.
$ git reset HEAD^ --hard 
# 바로 두번째 전 단계로 인덱스와 워킹트리를 버리고 리셋.
$ git reset HEAD~2 --hard 
# 특정 리비전의 기록으로 인덱스는 버리고 워킹트리를 보존하여 리셋.
$ git reset 991ee8c --mixed

$ git log
$ git reflog

$ git branch new

$ git checkout new

# 브랜치 new를 생성과 동시에 체크아웃.
$ git checkout -b new

$ git push new

$ git checkout -d new

$ git rebase

$ git merge