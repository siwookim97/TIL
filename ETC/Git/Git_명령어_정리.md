## Gif 초기 Config 세팅
```bash
$ git config --global init.defaultBranch main
$ git config --global user.name <GitHub-ID>
$ git config --global user.email <GitHub-Email>
```
<br>
<hr/>

## (init) 로컬 Repository 생성
```bash
$ git init
```
- 프로젝트를 버전관리 하기 위해 저장소로 사용하고자 하는 디렉터리로 이동 후 실행
<br><br>
<hr/>

## (remote) 원격 Repository 와의 연결
```bash
$ git remote # 저장소 리스트의 저장소 이름만 보여줌
$ git remote -v # 현재 git에 등록된 원격 저장소 리스트를 보여줌
$ git remote remove <alias> # 저장소 리스트에서 원격 저장소 삭제
$ git remote add <alias> <url> # 입력한 저장소 이름으로 url의 저장소를 등록
```
<br>
<hr/>

## (add / status) commit 까지 변경분 모으기 / 상태 확인
```bash
$ git add 파일명 
$ git add . # 전체 add (점(.)은 모든 것을 의미)
$ git add *.txt # 모든 txt 파일 업로드
$ git add project/app/*/ # 디렉토리 업로드
$ git add --update # 현재 git이 추적하고 있는 파일들만 add

$ git status # add확인 (git의 상태 확인, Staging Area, UnStage Area)
```
- add 명령어를 통해 Staging Area에 넣어준다
- status 명령어를 통해 Staging Area의 상황을 확인 -> commit으로 변경
<br><br>
<hr/>

## (commit) 로컬의 저장소에 기록 
```bash
$ git commit -m <message>
$ git commit --amend # 이전의 커밋 재작성 (Staging Area에 있는 것 추가)
```
- 로컬Repo의 .git파일에 기록
- Staging Area에 있는 변경분을 모두 적용
- commit 메시지는 `Commit Message Convention`을 따르도록 하자 
<br><br>
<hr/>

## (push) 로컬 브랜치를 원격 저장소로 푸시
```bash
$ git push <alias> <branch_name> # ex> git push origin main
$ git push --force <alias> <branch_name> # 강제로 병합해 덮어쓸때 사용
$ git push --force-with-lease <alias> <branch_name> # 다른 사람이 브랜치를 기여하지 않은 경우에만 덮어쓰기
```
<br>
<hr/>

## (pull) 원격 저장소 불러오기
```bash
$ git pull <alias> <branch_name> # ex) git pull origin main
```
- `fetch` + `merge` 
- 원격 저장소의 내용을 가져와서 현재 브랜치와 병합(merge)까지 수행
- 기존 작업 내용을 유지할 수 있다
- 병합 과정이 있기에 `pull 하기 전에 commit`을 하여 덮어쓰기 에러 예방
<br><br>
<hr/>

## (clone) 원격 저장소 불러오기
```bash
$ git clone <url>
```
- 로컬 저장소의 내용이 원격 저장소의 내용과 일치해짐
- 기존에 작업했던 내용들은 사라짐
- 처음 `프로젝트 투입 시` 사용되어야 한다
<br><br>
<hr/>

## (branch / checkout) branch 관리하기
```bash
$ git branch # branch 목록 조회
$ git branch -r # 원격 branch 목록 조회
$ git branch -a # 전체 branch 목록 조회
$ git branch <name> # branch 생성

$ git checkout # branch 변경
```
<br>
<hr/>

## (fetch) 원격 저장소 변경 내역 확인
```bash
$ git fetch <alias> # 원격 저장소의 변경된 것을 확인차 가져옴
```