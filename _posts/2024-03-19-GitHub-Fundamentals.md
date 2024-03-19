---
layout: post
title:  "깃허브 기본"
date:   2024-03-19
categories: Github
---

깃허브<br>
  개발 중 작성한 소스 코드를 효과적으로 관리해주는 협업 기능을 지원하는 형상관리 툴.<br>
  수정한 소스 코드끼리 충돌하거나 소스코드를 주고 받을 필요 없음.<br><br>

깃허브 작업순서<br>
  *상황에 따라 다르기 때문에 간단하게만 작성. 원격에서 로컬로 저장소를 받은 다음, 로컬에서 작업 후 커밋해서 로컬에 저장. 작업이 완료되면 원격에 푸시 후 PR 요청하는 듯<br><br>
  
  로컬 저장소 생성 > 파일 작업 > 커밋 > 원격 저장소에 푸시.<br>
  
  원격 저장소 생성 > 파일 작업 커밋 > 새로 받아오면 clone or 기존에 받았으면 pull > 로컬에서 파일 작업 후 커밋 > 원격 저장소 pull 싱크 맞춤. conflict 발생 시 어느 버전 놔둘 지 선택 > 내가 작업한 파일을 푸시 > PR 요청 > 저장소 관리자가 merge.<br><br>
    
Repository(저장소 생성)  <br>
    Owner: 계정<br>
    Repository name: 저장소 이름<br>
    Description: 저장소 설명. *README 파일 생성해서 적는 게 더 좋은 듯.<br>
    Public || Private: 공개 여부.<br><br>
  
깃허브 데스트톱에 저장소 연결.<br>
  Setup in Desktop > 로컬 저장 주소 설정 > clone <br><br>
  
깃허브 데스크톱 <br>
1. Repository 메뉴 > open in external editor > visual studio code 설치. <br>
	  *없어도 커밋이나 푸시는 가능하지만 있으면 코드 수정할 때 편리할 듯. <br>
2. 커밋: 소스코드를 로컬 저장소에 저장. <br>
  수정한 파일 내용이 깃허브 데스크탑에 표시됨. <br>
  Summary에 수정한 내용의 제목을 넣음 > Commit to main <br>
	  *버전관리를 위해 무얼 수정한 건지 설명 첨부. 제목만 적어도 커밋은 가능. <br>
  잘못 커밋 시 왼쪽 하단 Undo 클릭. <br>
3. 푸시: 소스코드를 깃허브에 저장. <br>
  Publish branch: 맨 처음 커밋 시 활성화되는 버튼 <br>
  Push origin: 두 번째 커밋부터 활성화되는 버튼 <br>
  Fetch origin: 새로 커밋할 내용이 없을 떄 활성화되는 버튼 <br>
    *origin 브랜치는 보통 master || main <br><br>
    
브랜치: 현재 버전을 나눠서 개발 후 병합할 수 있는 협업 기능. <br>
  Current branch > New branch > 브랜치명 입력 <br>
  새 브랜치에서 작업 후 커밋 > 푸시 <br><br>

  pull: 원격 저장소의 소스를 지역 저장소로 가져오는 작업. 변경사항이 있을 시 pull로 싱크를 맞추고 작업한 다음 push하는 게 안전. <br>
  
  Create Pull Request  <br>
    - 다른 브랜치에서 작업한 것을 원격 브랜치에 병합할 때 필요.  <br>
    - 작업이 완료된 것을 다른 사람에게 알리는 목적으로 사용.  <br>
    - PR을 받은 원본 저장소 관리자는 코드 변경 내역을 확인하고 Merge 여부를 결정.  <br>
        *수정했으니 메인 브랜치에 pull 요청을 보내고 이걸 관리자가 승인하면 병합되는 듯.  <br><br>

----------------------------------------------------------------------------------------------------------------<br>
[https://eunyoe.tistory.com/m/210#google_vignette](https://eunyoe.tistory.com/m/210#google_vignette)  <br>
1. 깃허브란 <br>
2. 깃허브 데스크탑에서 저장소 생성 및 깃허브와 연결 <br>
3. 파일 업로드 > 커밋 > 푸시 <br>
4. 브랜치 생성 > 커밋 푸시 > create pull request > merge pull request <br>
5. 브랜치 병합(Merge) <br>
    브랜치 메뉴 > choose a branch to merger into 새브랜치 > main 선택 (main 브랜치와 병합) > create a merge commit > main과 내 파일 강 충돌이 있으면 팝업 뜸. <br><br>
    
    초록색: current change(내가 수정한 영역) <br>
    파란색: main. <br><br>
  
    Accept current change: 내가 수정한 걸로 유지(초록색) <br>
    Accept incoming change: main으로 유지(파란색) <br>
    Accept both change: 둘 다 남김 <br>
    Compare change: 충돌 부분을 보기 쉽게 출력 <br><br>
    
  충돌 해결 후 Continue merger > 푸시 <br><br>

---------------------------------------------------------------------------------------------------------------- <br>
[https://developer-eun-diary.tistory.com/42](https://developer-eun-diary.tistory.com/42)  <br>
Git 도스 명령어로 브랜치 생성 ~ pull request(PR) <br>
1. 원격 저장소에서 내용을 로컬 저장소로 가져온다 <br>
	로컬 저장소가 없을 시: git clone ~ <br>
	로컬 저장소가 이미 있을 시: git pull origin master <br>
     *clone, pull 둘 다 내려받는 건데 clone은 전체 복사고 pull은 싱크를 맞춘다고 보면 될 듯. 만약 pull해서 오류 나면 지우고 clone 해야 할 것 같다. <br><br>

2. 로컬 저장소에서 작업할 브랜치를 생성 후 해당 브랜치로 이동 <br>
	git branch 브랜치이름 (브랜치 생성) <br>
	git checkout 브랜치이름 (브랜치 변경) <br>
	git checkout -b 브랜치이름 (브랜치 생성 및 변경) <br><br>
 
3. 브랜치 안에서 원하는 작업을 수행 <br>
4. 브랜치에서 수행한 작업을 git의 작업중인 브랜치에 푸시 <br>
	(작업 중인 브랜치 안에서 명령어 실행) <br>
	git add . <br>
	git commit -m ~ <br>
	원격 저장소에 해당 브랜치가 이미 존재할 때 : git push <br>
	원격 저장소에 해당 브랜치가 없을 때 : git push origin 브랜치이름 <br>
	※원격 저장소에 브랜치가 없을 떄 git push만 하면 upstream이 없다는 오류 발생. 따라서 원격 저장소에 브랜치 생성 후 브랜치 내용 push를 해야 함. <br>

5. 로컬 master 브랜치로 이동 > 원격 저장소의 master 변경사항을 pull. <br>
	git checkout main (작업 중인 브랜치 안에서 명령어 실행) <br>
	git pull origin master (master 브랜치 안에서 명령어 실행) <br>
  ※브랜치를 생성해서 작업하는 동안 다른 협업자가 원격 저장소의 master에 push를 진행했을 수 있으므로 로컬의 master 브랜치의 내용을 최신으로 업데이트. <br><br>

6. 로컬의 작업한 브랜치로 이동 > 로컬의 master 내용을 해당 브랜치에 merge <br>
	(작업 중인 브랜치 안에서 명령어 실행) <br>
	git merge master <br>
	git push <br>
	※merge 과정에서 conflict가 난다면 해결 후 push! <br><br>

1~6 과정을 통해 master와 merge 된 브랜치 내용이 원격 저장소 작업 브랜치에 업데이트되었다. <br>

7. github 홈페이지의 repository로 이동 후 pull request 요청 <br>
8. 담당자가 확인 후 pull request를 수락하면 원격 저장소 master에 브랜치의 내용이 업데이트된다 <br><br>

---------------------------------------------------------------------------------------------------------------- <br>
[https://yeon-kr.tistory.com/189](https://yeon-kr.tistory.com/189)   <br>
깃허브 브랜치 단위로 PR(도스) <br><br>

git add <br>
	로컬 작업을 staging area(index)에 등록. <br>
	이 과정을 staging이라 부름. <br>
	staging area 업로드 된 것만 커밋 가능. 로컬에서 작업한 파일 중 일부만 공개 가능. 보안 향상. <br><br>

git commit -m "커밋 메시지(바꾼 내 작성)" <br><br>

git status <br>
	Changes to be committed: staging area에 등록된 상태. 커밋 시 사라짐. <br>
	Untracked files: staging area에 비포함. <br><br>

git remote add origin(원격저장소 이름) https://github.com/~(원격저장소 주소): 로컬 저장소에 origin이란 원격 저장소 추가. <br><br>

git branch: 브랜치 목록 <br>
git push --set-upstream origin master(로컬 브랜치): 로컬 브랜치 master를 원격저장소 origin에 푸시. 최초 1번만 실행. 이후는 git push. <br>
git remote -v: 현재 저장된 원격 저장소 이름 찾기 <br><br>

병합 방식 <br>
1. merge <br>
	하나의 브랜치에서 여러 번 커밋했을 때 모두 기록. <br>
	커밋 단위의 그래프. <br>
	모든 변경사항 확인 가능. <br> 
	사소한 것까지 다 기록돼서 문제 파악 힘듬. <br>
2. squash and merge <br>
	한 브랜치에서 발생한 여러 커밋을 하나로 합침. <br>
	깔끔한 브랜치 단위의 그래프. <br>
	병합된 건 확인 가능하지만 상세한 커밋 내용은 알 수 없음. 코드 변경 이유를 알 수 없다. <br>
3. rebase and merge <br>
	모든 커밋을 한 줄기로 합침. <br>
	merge와 비슷해보이나 merge는 줄기가 나눠짐. <br>
	rebase는 merge 커밋이 남지 않아서 해당 커밋이 어디서 언제 병합됐는지 알 수 없음. <br><br>

---------------------------------------------------------------------------------------------------------------- <br>
[https://im-developer.tistory.com/182](https://im-developer.tistory.com/182) <br>
병합 방식. merge, squash and merge, rebase and merge <br><br>
 
---------------------------------------------------------------------------------------------------------------- <br>
[https://wayhome25.github.io/git/2017/07/08/git-first-pull-request-story/](https://wayhome25.github.io/git/2017/07/08/git-first-pull-request-story/) <br>
포크 > 클론 > 브랜치 > add > commit > 푸시 > pull request > merger pull request > 병합 이후 동시화 > 브랜치 삭제
