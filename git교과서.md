### # 목차

# 1장 깃과 버전 관리

## 1.1 버전 관리

### __1.1.1 버전이란?

### __1.1.2 버전 관리는 왜 필요할까?

## 1.2 버전 관리 시스템

## __1.2.1 버전 관리 소프트웨어

## 1.3 깃

### __1.3.1 백업 기능

### __1.3.2 협업 개발

## 1.4 깃의 동작 한눈에 보기

### 1.5 정리

# 2장 깃과 소스트리 설치 및 환경 설정

## 2.1 깃 설치

### __2.1.1 윈도에서 설치

### __2.1.2 리눅스에서 설치

### __2.1.3 macOS에서 설치

## 2.2 소스트리 설치

### __2.2.1 설치 파일 내려받기

### __2.2.2 설치

## 2.3 첫 번째 깃 실행

### __2.3.1 터미널

### __2.3.2 깃 명령어로 실행

### __2.3.3 소스트리로 실행

## 2.4 환경 설정

### __2.4.1 config 명령어

### __2.4.2 로컬 사용자

```
cd 저장소 폴더
git config user.name "사용자이름"
git config user.email "사용자이메일"

ls ~/.gitconfig
cat .gitconfig
```

### __2.4.3 글로벌 사용자(추천)

```
cd 저장소 폴더
git config --global user.name "사용자이름"
git config --global user.email "사용자이메일"
```

### __2.4.4 환경 설정 파일 확인 및 직접 수정

### __2.4.5 소스트리의 환경 설정

### __2.4.6 별칭

## 2.5 비주얼 스튜디오 코드

## 2.6 정리

# 3장 깃 개념 잡기

## 3.1 깃 저장소 생성

### __3.1.1 폴더와 깃 저장소

### __3.1.2 초기화

### __3.1.3 숨겨진 폴더 = .git 폴더

### __3.1.4 소스트리와 연결

## 3.2 워킹 디렉터리

### __3.2.1 워킹 디렉터리란?

### __3.2.2 파일의 untracked 상태와 tracked 상태

## 3.3 스테이지

### __3.3.1 스테이지 = 임시 영역

### __3.3.2 파일의 stage 상태와 unstage 상태

```
git status
git ls-files --stage
```

### __3.3.3 파일의 modified 상태와 unmodified 상태

## 3.4 파일의 상태 확인

### __3.4.1 status 명령어로 깃 상태 확인

### __3.4.2 소스트리에서 깃 상태 확인

## 3.5 파일 관리 목록에서 제외: .gitignore

### __3.5.1 .gitignore 파일

### __3.5.2 .gitignore 파일 표기법

```
# 현재 디렉터리 안에 있는 파일 무시
/readme.txt

# /pub/ 디렉터리 안의 모든 것을 무시
/pub/

# doc 디렉터리 아래의 모든 .txt 파일 무시
doc/**/*.txt
```

## 3.6 깃 저장소 복제

### __3.6.1 공개 저장소

### __3.6.2 다운로드 vs 복제

### __3.6.3 복제 명령어

```
$ git clone 원격저장소URL.git
$ git clone https://github.com/jinyphp/jiny
```

## 3.7 정리

# 4장 커밋

## 4.1 코드의 변화

### __4.1.1 파일 관리 방법

## 4.2 새 파일 생성 및 감지

### __4.2.1 새 파일 생성

### __4.2.2 깃에서 새 파일 생성 확인

### __4.2.3 소스트리에서 새 파일 감지

## 4.3 깃에 새 파일 등록

### __4.3.1 스테이지에 등록

스테이지 영역에 파일이 등록되면 파일은 `tracked 상태`로 변경됩니다.

전체 파일과 폴더를 `모두 등록`

```
$ git add 파일이름
$ git add .
```

### __4.3.2 파일의 추적 상태 확인

```
$ git status 
```

### __4.3.3 파일 등록 취소

#### rm 명령 삭제

스테이지 삭제

```
$ git rm --cached index.htm 
```

상태확인

```
$ git status 
```

#### reset으로 삭제

```
$ git rm --cached index.htm
$ git status
$ git reset HEAD index.htm 
```

### __4.3.4 등록된 파일 이름이 변경되었을 때

#### git mv 명령어

```
$ git mv index,htm home.htm
$ git status
```

### git mv의 실제동작

```
$ mv index.htm home.htm
$ git rm index.htm
$ git add home.htm
```

## 4.4 첫 번째 커밋

### __4.4.1 HEAD

`HEAD`는 커밋을 가리키는 묵시적 `참조 포인터`

### __4.4.2 스냅샷

깃의 스냅샷은 HEAD가 가리키는 커밋을 기반으로 사진을 찍습니다. 그리고 이를 스테이지 영역과 비교하여 새로운 커밋으로 기록합니다.

### __4.4.3 파일 상태와 커밋

$ git commit

## 4.5 커밋 확인

### __4.5.1 스테이지 초기화

커밋을 하면 스테이지 영역은 초기화

```
$ git status
```

### __4.5.2 로그 기록 확인

og 명령어는 시간 순으로 커밋 기록을 출력하는데, 최신 커밋 기록부터 내림차순으로 나열

```
$ git log
```

### __4.5.3 소스트리에서 로그 기록 확인

## 4.6 두 번째 커밋

### __4.6.1 파일 수정

### __4.6.2 파일 변경 사항 확인

파일을 수정하면 modified 상태로 변경됩니다.

```
$ git status ☜ 상태 확인 명령.
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)
        modified:   index.htm ☜ 파일 수정
no changes added to commit (use "git add" and/or "git commit -a")
```

### __4.6.3 수정된 파일 되돌리기

수정 파일을 되돌리면 이전 커밋 이후에 작업한 수정 내역은 모두 삭제합니다.

```
$ git checkout -- 수정파일이름
```

### __4.6.4 스테이지에 등록

1) 기존 파일을 수정하면 해당 파일은 modified 상태로 변경됩니다. 그리고 다시 워킹 디렉터리로 이동합니다.
2) 파일이 수정되면 반드시 add 명령어로 스테이지 영역에 재등록해야 합니다. 즉, 파일을 수정할 때마다 등록 작업을 반복해야 한다는 것을 잊지 마세요.

```
$ git add 수정파일이름
```

### __4.6.5 두 번째 커밋

-a 옵션은 commit 명령어를 실행하기 전에 워킹 디렉터리에 있는 파일을 스테이지 영역으로 등록합니다.

-m 옵션은 간단한 커밋 메시지를 함께 등록합니다.

`-a` 옵션은 이미 추적된 파일 상태가 변경되었을 때만 함께 사용이 가능합니다. 저장소를 새롭게 생성하고, 새 파일을 작성한 후라면 -am 옵션을 사용하여 커밋할 수 없습니다.

```
$ git commit -am "커밋메시지"
```

### __4.6.6 두 번째 커밋 확인

```
$ git log ☜ 로그 확인
commit aa1dd51a8883b2ea9a54209a00f434a2da01ee85 (HEAD -> master)
Author: hojin <infohojin@gmail.com>
Date:   Sat Jan 5 19:31:46 2019 +0900
    hello git world 추가 ☜ 추가된 커밋 확인

commit e2bce41380691b0a34aeab7db889a6c30fed8287
Date:   Sat Jan 5 18:24:50 2019 +0900
    인덱스 페이지 레이아웃
```

### __4.6.7 깃허브에서 확인

깃은 자신의 컴퓨터뿐만 아니라 원격 저장소를 같이 연동할 수 있습니다. 대표적인 원격 저장소로는 깃허브가 있습니다.

## 4.7 메시지가 없는 빈 커밋

### __4.7.1 세 번째 커밋

파일을 수정한 후에는 반드시 수정된 파일을 스테이지 영역에 `재등록`합니다.

```
$ code index.htm ☜ VS Code 실행
$ git add index.htm ☜ 스테이지 등록
```

터미널에서 메시지가 없는 빈 커밋을 작성하려면 `--allow-empty-message` 옵션을 사용합니다.

```
$ git commit --allow-empty-message -m "" ☜ 커밋 메시지를 작성하지 않음
[master 42250c6] ☜ 빈 커밋
 1 file changed, 1 insertion(+), 1 deletion(-)
```

### __4.7.2 소스트리에서 빈 커밋

### __4.7.3 빈 커밋 확인

커밋 메시지를 입력할 때 방금 전에 작성한 커밋 메시지를 수정할 수 있는 `--amend` 옵션을 제공합니다.

```
$ git commit --amend
```

## 4.8 커밋 아이디

### __4.8.1 SHA1

SHA1 해시키 값은 `40자리`의 복잡한 `hexa` 값으로 `콘텐츠 추적`과 분산형 저장 관리를 운영하면서 `충돌을 방지`하기 위함 입니다.

### __4.8.2 단축키

해시는 `매우 큰 값`으로 해시의 `앞쪽 7자만`으로도 중복을 방지하면서 전체 키 값을 사용할 수 있습니다.

## 4.9 커밋 로그

### __4.9.1 간략 로그

로그 옵션 중에서 `--pretty=short`를 사용하면 로그를 출력할 때 첫 번째 줄의 커밋 메시지만 출력합니다.

```
$ git log --pretty=short ☜ 로그 확인
```

특정 커밋의 상세 정보를 확인하고 싶다면 `show` 명령어를 사용합니다.

```
$ git show 커밋ID
```

### __4.9.2 특정 파일의 로그

전체 커밋과 달리 특정 파일의 로그 기록만 볼 수도 있습니다.

-p 옵션: diff 기능(수정한 라인 비교)을 같이 포함하여 출력.

–stat 옵션: 히스토리를 출력.

–pretty=oneline 옵션: 각 커밋을 한 줄로 표시.

```
$ git log index.htm ☜ 파일의 로그 확인
```

## 4.10 diff 명령어

### __4.10.1 파일 간 차이

파일들의 수정 이력을 비교해 볼 수 있는 `diff` 기능

### __4.10.2 워킹 디렉터리 vs 스테이지 영역

아직 add 명령어로 파일을 추가하지 않은 경우, 워킹 디렉터리와 스테이지 영역 간 변경 사항을 비교할 수 있습니다.

diff 명령어를 실행해 봅시다.

```
$ git diff ☜ 스테이지 vs 워킹 디렉터리 비교.
diff --git a/index.htm b/index.htm
index f5097d9..56af0de 100644
--- a/index.htm
+++ b/index.htm
@@ -7,5 +7,6 @@
 </head>
 <body>
     <h1>hello GIT world!</h1>
+    <h2>깃을 이용하면 소스의 버전 관리를 쉽게 할 수 있습니다.</h2> ☜ 추가
 </body>
 </html>
\ No newline at end of file
```

이번에는 변경한 파일을 `add` 명령어로 추가하여 스테이지 영역에 등록합시다.

```
$ git add index.htm
$ git diff
```

아무 내용도 출력되지 않습니다. 이것은 등록 과정을 거쳐 워킹 디렉터리의 수정 내역을 스테이지 영역에 반영했기 때문입니다.

### __4.10.3 커밋 간 차이

스테이지 영역에 있는 수정된 파일을 아직 커밋하지 않았다면, 최신 커밋과 변경 내용을 비교하여 볼 수 있습니다. `HEAD`는 마지막 커밋을 가지고 있는 포인터입니다.

```
$ git diff head ☜ head 포인터를 입력
diff --git a/index.htm b/index.htm
index f5097d9..56af0de 100644
--- a/index.htm
+++ b/index.htm
@@ -7,5 +7,6 @@
 </head>
 <body>
     <h1>hello GIT world!</h1>
+    <h2>깃을 이용하면 소스의 버전 관리를 쉽게 할 수 있습니다.</h2>
 </body>
 </html>
\ No newline at end of file
```

### __4.10.4 소스트리에서 간단하게 변경 이력 확인

### __4.10.5 diff 내용을 추가하여 커밋

```
$ git commit -v ☜ diff 내용 추가
```

## 4.11 정리

# 5장 서버

## 5.1 서버 저장소

### __5.1.1 협업 저장소

분산형 모델

### __5.1.2 연속된 작업

깃은 분산된 저장소 여러 개를 하나로 `통합`하고, 최신 코드를 `배포`할 수 있습니다.

서버 저장소는 여러 컴퓨터에 동일한 깃 저장소를 `복제`하고, 작업한 결과물을 다시 `서버로 통합`합니다.

### __5.1.3 새 멤버

깃의 원격 저장소 `주소`만 알려 주면 원격 저장소로 모든 구성원에게 코드의 최종 결과물을 동기화

## 5.2 깃허브 서버 준비

### __5.2.1 깃허브

### __5.2.2 저장소 생성

## 5.3 깃허브 연동 및 원격 등록

### __5.3.1 로컬 저장소

새로운 로컬 저장소를 생성하고 원격 저장소를 연결하는 방법

기존 저장소를 연결하는 방법

```
# 새 로컬 저장소를 생성하고 초기화
$ git init
$ echo "# gitstudy05" >> README.md ☜ 파일 생성
... 스테이지 등록
    $ git add README.md 
... 커밋
    $ git commit -m "first commit" 
```

### __5.3.2 프로토콜

깃은 기본적으로 `Local`, `HTTP`, `SSH`, `Git` 네 종류의 전송 방식을 지원합니다.

#### Local(로컬)

```
$ git remote add 원격저장소별칭 폴더경로
```

#### HTTP

기존 아이디와 비밀번호만으로 접속자를 인증하여 처리

#### SSH

주소 앞에 ‘ssh://계정@주소’처럼 프로토콜 타입을 지정해야 합니다.

#### Git

SSH와 유사하지만 인증 시스템이 없어 보안에 취약할 수 있습니다.

### __5.3.3 원격 저장소의 리모트 목록 관리

#### 리모트 목록

```
$ git remote
```

#### 상세한 목록

```
$ git remote -v
```

### __5.3.4 주소와 별칭

깃허브 같은 저장소를 이용해 보면 `프로토콜` + `도메인 주소` 형태

`origin`은 대표적으로 사용하는 별칭입니다.

기본적으로 원격 서버와 연결할 때 별칭으로 origin을 사용하는 것을 많이 볼 수 있습니다.

### __5.3.5 원격 저장소에 연결

원격 저장소와 연결하려면 `add<span> </span>`옵션을 사용

```
# $ git remote add 원격저장소별칭 원격저장소URL
$ git remote add origin https://github.com/jinygit/gitstudy05.git
$ git remote -v
```

원격 저장소가 연결되면 `fetch`와 `push` 두 주소를 출력합니다.
push(푸시)는 서버로 전송하는 동작을 의미하고, fetch(페치)는 반대로 서버에서 가지고 오는 동작을 의미합니다.

### __5.3.6 소스트리에서 원격 브랜치

### __5.3.7 별칭 이름 변경과 정보

```
$ git remote rename 변경전 변경후
```

### __5.3.8 원격저장소의 정보 출력하기

```
$ git remote show origin
* remote origin
  Fetch URL: https://github.com/jinygit/gitstudy05.git
  Push  URL: https://github.com/jinygit/gitstudy05.git
  HEAD branch: master
  Remote branch:
    master tracked
  Local ref configured for 'git push':
    master pushes to master (up to date)
```

### __5.3.9 원격 서버 삭제

origin 저장소를 삭제

```
$ git remote rm origin
```

정상적으로 삭제가 되었는지 목록을 확인

```
$ git remote -v
```

## 5.4 서버 전송

### __5.4.1 push: 서버에 전송

서버에 전송-로컬 저장소의 커밋을 원격 저장소로 전송하는 방법

원격  저장소와 연결된  서버 목록을 확인

```
$ git remote -v
```

push 명령어

```
# $ git push 원격저장소별칭 브랜치이름
$ git push origin master ........ 원격 서버로 전송
```

## 5.5 자동으로 내려받기

### __5.5.1 clone: 복제

서버의 연결 설정을 마친 후 서버 안에 있는 `모든 커밋된 코드 이력`들을 한 번에 내려받습니다.

```
$ git clone https://github.com/jinygit/gitstudy05.git .
Cloning into '.'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 3 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
```

```
$ ls -all
total 13
drwxr-xr-x 1 infoh 197609  0 12월 12 17:23 .
drwxr-xr-x 1 infoh 197609  0 12월 12 17:23 ..
drwxr-xr-x 1 infoh 197609  0 12월 12 17:23 .git
-rw-r--r-- 1 infoh 197609 14 12월 12 17:23 README.md
```

### __5.5.2 pull: 서버에서 내려받기

pull 명령어는 로컬 저장소보다 최신인 갱신된 원격 저장소의 커밋 정보를 현재 로컬 저장소로 내려받습니다. 복제 후 원격 저장소의 갱신된 내용을 추가로 내려받으려면 pull 명령어를 사용해야 합니다.

### __5.5.3 pull: 별개의 저장소 pull 하기

```

# 로컬저장소를 생성합니다.
$ git init .
# 파일을 생성하고, 커밋을 합니다.
$ echo "hello" > hello.md
$ git add .
$ git commit -m "hello"
$ git remote add origin https://github.com/hojinio/daelim_20202-2.git
$ git remote -v
origin  https://github.com/hojinio/daelim_20202-2.git (fetch)
origin  https://github.com/hojinio/daelim_20202-2.git (push)

# 원격저장소에서 pull을 합니다.
$ git pull
warning: no common commits
remote: Enumerating objects: 6, done.
remote: Counting objects: 100% (6/6), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 6 (delta 0), reused 6 (delta 0), pack-reused 0
Unpacking objects: 100% (6/6), 456 bytes | 38.00 KiB/s, done.
From https://github.com/hojinio/daelim_20202-2
 * [new branch]      master     -> origin/master
There is no tracking information for the current branch.
Please specify which branch you want to merge with.
See git-pull(1) for details.

    git pull <remote> <branch>

If you wish to set tracking information for this branch you can do so with:

    git branch --set-upstream-to=origin/<branch> master
하지만, pull 동작을 하지 못하고 오류가 발생합니다.
오류의 내용은 로컬저장소가 원격저장소의 트래킹 정보가 설정되어 있지 않기 때문입니다.

```

#### __문제해결 하기1

브랜치의 `업스트림` 설정을 해주어야 합니다.

```
$ git branch --set-upstream-to=origin/master master
$ git pull
$ git branch -vv
$ git checkout origin/master
$ git checkout master
$ git checkout FETCH_HEAD
$ git checkout -
```

### __문제해결 하기2

처음부터 저장소를 생성한 후에 새로운 원격저장소를 만들어 유지하는 것 또는, 기존의 원격저장소를 clone 하여 작업을 하는 것

`pull` 명령에 `--allow-unrelated-histories` 옵션을 추가하여 실행하는

```
$ git pull origin master --allow-unrelated-histories
$ ls
$ git log
```

## 5.6 수동으로 내려받기

### __5.6.1 자동 병합

pull(풀)로 내려받은 커밋 정보는 임시 영역에 저장합니다. 스테이지 영역이 아닌 원격 저장소를 위한 전용 임시 브랜치가 따로 있습니다. 내려받은 최신 커밋들을 현재 브랜치로 자동으로 병합 처리합니다.

### __5.6.2 fetch: 가져오기

fetch(페치)는 원격 저장소에서 코드를 수동으로 내려받는 작업을 합니다. 페치는 원격 저장소에서 커밋된 코드를 임시 브랜치로 내려받습니다. 내려받은 후 현재 브랜치와 자동 병합하지 않습니다.

```
$ git fetch 원격저장소URL
```

그럼 페치 동작을 실습해 봅시다. 먼저 실습 원본 저장소로 이동합니다.

```
$ code server.htm ☜ VS Code 실행
```

수정된 파일을 스테이지 영역에 등록과 동시에 커밋합니다.

```
$ git commit -am "look sky"
```

커밋된 수정 내용을 원격 저장소로 전송합니다. 원본 저장소 변경과 원격 저장소를 갱신했습니다.

```
infoh@hojin MINGW64 /e/gitstudy05 (master)
$ git push origin master
To https://github.com/jinygit/gitstudy05.git
   6a947b8..668b5ef  master -> master
```

이제는 다시 복제된 로컬 저장소로 이동하여 갱신된 원격 저장소 내용을 페치해 보겠습니다.

```
infoh@hojin MINGW64 /e/gitstudy05_clone (master)
$ git fetch
From https://github.com/jinygit/gitstudy05
   6a947b8..668b5ef  master     -> origin/master
```

원격 저장소의 커밋 내용을 페치한 후 커밋 로그를 확인합니다.

```
$ git log
```

pull 명령어와 달리 fetch 명령어를 실행한 후에는 커밋이 추가된 것을 확인할 수 없습니다. 페치는 원격 저장소의 커밋들만 가지고 왔을 뿐 로컬 저장소에서 어떤 작업도 하지 않습니다.

### __5.6.3 merge 명령어로 수동 병합

페치는 데이터를 내려받기만 할 뿐 자동 병합하지 않습니다. 내려받은 커밋을 로컬 저장소에 적용하려면 병합 명령을 실행해야 하는데, merge 명령어를 사용합니다.

```
$ git merge 원격저장소별칭/브랜치이름
```

fetch 명령어로 내려받은 커밋을 로컬 저장소에 병합

```
$ git merge origin/master
```

로컬 저장소의 로그 기록을 확인

```
$ git log
```

`fetch` 명령어로 내려받은 커밋들이 추가된 것을 확인할 수 있습니다.

## 5.7 순서

### __5.7.1 최신 상태

#### 커밋의 순서와 상태

푸시는 서버의 `마지막 커밋`과 푸시되는 `커밋`을 `병합`합니다.

#### push 거부

커밋이 순차적이지 않을 때 깃은 푸시 동작을 `거부`합니다.
푸시 동작이 거부되면 `pull` 또는 `patch` 작업으로 자신의 로컬 저장소를 갱신해 주어야 합니다.

#### 인증 정보 캐시

깃허브, 비트버킷 같은 호스팅 원격 저장소를 이용할 때는 아이디와 비밀번호가 있어야 접속할 수 있습니다. 매번 아이디와 비밀번호를 입력하는 것은 귀찮습니다. 그래서 깃은 인증 정보 캐시(credential cache) 기능을 이용하여 아이디와 비밀번호를 임시적으로 보관할 수 있습니다.

```
$ git config --global credential.helper cache
```

#### 원격 저장소 원리

깃을 원격 저장소에 연결하면 `.git/config` 파일 안에 리모트 연결에 대한 설정 정보가 자동으로 추가됩니다.

```
[remote "origin"]
        url = https://github.com/jinygit/gitstudy05.git
        fetch = +refs/heads/*:refs/remotes/origin/* 
```

### __5.7.2 충돌 방지

원격 저장소의 커밋을 내려받는 `pull` 작업은 내려받은 커밋들을 `현재 브랜치`로 `자동 병합`합니다.
이때 커밋 내용이 `순차`적이지 않으면 `병합` 과정에서 `충돌`이 발생합니다.

## 5.8 정리

# 6장 브랜치

## 6.1 새로운 작업

### __6.1.1 브랜치 작업

`커밋`은 파일의 수정 `이력`을 관리하는 데 사용한다면, 브랜치는 프로젝트를 `독립적`으로 관리하는 데 사용합니다.

### __6.1.2 깃 브랜치 특징

#### 가상 폴더

#### 독립적인 동작

#### 빠른 동작

## 6.2 실습 준비

### __6.2.1 저장소 생성 및 초기화

저장소가 초기화되면 현재 브랜치가 `master`라는 것을 확인할 수 있습니다.

```
$ git init
infoh@DESKTOP MINGW64 /e/gitstudy06 (master)
```

### __6.2.2 기본 브랜치

#### master 브랜치

첫 번째 커밋은 master 브랜치에서 시작

#### status 명령으로 확인

```
$ git status 
On branch master ☜ 브랜치 작업 위치
```

#### branch 목옥으로 확인

```
$ git branch
* master
```

## 6.3 브랜치 생성

브랜치는 가상의 작업 폴더입니다. 처음 깃을 초기화할 때 워킹 디렉터리는 master 브랜치를 생성합니다. 브랜치를 생성하려면 기준이 되는 브랜치 또는 커밋이 하나 있어야 합니다. 그리고 깃은 master 브랜치를 기준으로 새로운 브랜치를 생성합니다.

### __6.3.1 브랜치 생성

기본 master 브랜치 외의 브랜치는 사용자가 직접 branch 명령어를 입력하여 생성

#### 분기점

깃에서 또 하나의 개발 `분기점`을 의미

브랜치 생성 개수에는 제한이 없습니다.

#### 브랜치의 생성기준

`현재 HEAD 포인터`를 기준으로 새로운 브랜치를 생성합니다. 직접 `커밋 ID` 인자 값을 지정하면, 지정한 커밋 ID를 기준으로 브랜치를 생성

#### 브랜치 생성

```
$ code branch.htm ☜ VS Code로 파일을 작성
$ git add branch.htm ☜ 추적 등록
$ git commit -m "first" ☜ 커밋 작성
```

#### 새로운 브랜치 생성

```
infoh@DESKTOP MINGW64 /e/gitstudy06 (master)
$ git branch footer
$ git branch
  footer
* master
```

### __6.3.2 브랜치 이름

#### 브랜치 이름 규칙

* 기호(-)로 시작할 수 없습니다.
* 마침표(.)로 시작할 수 없습니다.
* 연속적인 마침표(..)를 포함할 수 없습니다.
* 빈칸, 공백 문자, 물결(~), 캐럿(^), 물음표(?), 별표(*), 대괄호([ ]) 등은 포함할 수 없습니다.
* 아스키 제어 문자는 포함할 수 없습니다. 주의할 점은 브랜치 이름은 중복해서 사용하지 않아야 한다.

#### 계층적 이름 생성

브랜치 이름은 슬래시(/)를 사용하여 계층적인 구조로 만들어서 사용

### __6.3.3 소스트리 브랜치

## 6.4 브랜치 확인

### __6.4.1 간단 브랜치 목록

```
$ git branch
* feature
  footer
master
```

#### 현재 브랜치

브랜치 이름 앞에 별표(`*`)

### __6.4.2 브랜치 해시

#### 브랜치의 sha1

현재 브랜치가 어떤 커밋 해시 값(`SHA1`)을 가리키는지 확인

```
$ git rev-parse 브랜치이름
```

#### 커밋 관계

로그에서 커밋의 `d84766c7f87b1d9d234050949c48681ba4e35da8` 해시 값(SHA1)을 확인

```
$ git log
```

#### 브랜치 커밋

footer 브랜치의 커밋 해시(SHA1)를 확인

```
$ git rev-parse feature
d84766c7f87b1d9d234050949c48681ba4e35da8
```

### __6.4.3 브랜치 세부 사항 확인

#### -verbose 옵션

브랜치 이름, 커밋 ID, 커밋 메시지

```
$ git branch -v
* feature d84766c first
  footer  d84766c first
  master  d84766c first
```

## 6.5 브랜치 이동

### __6.5.1 체크아웃

#### 브랜치 이동

```
$ git checkout 브랜치이름
```

#### 워킹디렉토리

깃은 하나의 워킹 디렉터리만 가지고 있다.

```
infoh@DESKTOP-MINGW64 /e/gitstudy06 (feature)
$ git checkout footer
Switched to branch 'footer'
infoh@DESKTOP MINGW64 /e/gitstudy06 (footer)
```

#### 브랜치 이동처리

#### 커밋, 파일로 체크 아웃

체크아웃은 브랜치 외에 특정 `커밋`이나 `파일`로도 할 수 있습니다.

```
$ git checkout 브랜치 ☜ 브랜치로 체크아웃
$ git checkout -- 파일명 ☜ 파일로 체크아웃
```

### __6.5.2 브랜치 동작 원리

#### HEAD 정보

`HEAD` 정보는 항상 변경된 브랜치의 `마지막 커밋`을 가리킵니다.

#### 워킹디렉터리

기존 브랜치의 워킹 디렉터리를 정리하지 않고서는 브랜치를 변경할 수 없습니다.

### __6.5.3 소스트리

### __6.5.4 이전 브랜치

이전 돌아가기

```
$ git checkout -
```

master 브랜치로 `변경된 것`을 확인

```
$ git branch -v
  feature d84766c first
  footer d84766c first
* master d84766c first
```

### __6.5.5 워킹 디렉터리 정리

#### 워킹디렉토리 변환

브랜치 동작 원리에서 브랜치가 변경되면 워킹 디렉터리도 같이 `변환`된다고 했습니다.
따라서 워킹 디렉터리 안에서 작성하던 내용이 있고, 커밋을 하지 않았다면 체크아웃할 때 `경고`가 발생합니다.

```
$ git checkout master
$ code branch.htm
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)
        modified:   branch.htm ☜ 워킹 디렉터리 수정 상태
no changes added to commit (use "git add" and/or "git commit -a")
```

#### 정리하지 않은 워킹디렉토리에서 브랜치 변경

워킹 디렉터리에서 작업하다 커밋하지 않고 남겨 둔 상태에서 다른 브랜치로 체크아웃하면 이처럼 브랜치 이동이 제한됩니다.

브랜치 간에 정상적으로 이동하려면 남아 있는 작업들을 이전으로 돌아가 수정된 내용을 커밋해줘야 합니다.

```
infoh@DESKTOP MINGW64 /e/gitstudy06 (master)
$ git checkout footer
Switched to branch 'footer'
M       branch.htm ☜ 워킹 디렉터리 수정 상태
```

작업된 워킹 디렉터리를 커밋하지 않고 브랜치를 변경할 때는 `스태시` 기능을 이용하면 좋습니다.

### __6.6.1 브랜치 로그

작업한 로그 기록을 확인하기 위해 브랜치 흐름도 같이 보려면 –graph 옵션을 함께 사용합니다. –graph –all 옵션 사용

```
$ git log --graph --all
```

–more 옵션으로 출력될 커밋 개수를 제한할 수 있습니다.

```
$ git show-branch --more=10
```

### __6.6.2 브랜치 소스 확인

```
$ cat branch.htm ☜ footer의 내용
<h1>브랜치 실습을 합니다.</h1>
$ git checkout master
$ cat branch.htm ☜ master의 내용
<h1>브랜치 실습을 합니다.</h1>
<h2>마스터 워킹 디렉터리 작업 중</h2>
```

두 소스 코드에 차이가 있습니다. 브랜치를 이동하면 변경된 각자 브랜치의 마지막 워킹 디렉터리 상태로 빠르게 변경됩니다. footer는 아직 한 줄짜리 정보를 워킹 디렉터리에 가지고 있는 상태고, master는 두 줄짜리 정보를 워킹 디렉터리에 가지고 있는 상태입니다.

## 6.7 HEAD 포인터

### __6.7.1 마지막 커밋

깃은 마지막 커밋 정보를 기반으로 새로운 커밋을 생성합니다.

HEAD는 작업 중인 브랜치의 마지막 커밋 ID를 가리키는 참조 포인터입니다.

깃은 마지막 커밋을 가리키는 HEAD 포인터를 부모 커밋으로 대체하여 사용합니다.

```
$ git checkout footer ☜ 브랜치를 이동합니다
$ git log --graph --all
* commit dcdb1c1fa4ef78bedd8dc13bc267e99391cc9782 (master)
| Author: hojin <infohojin@gmail.com>
| Date:   Sat May 11 18:45:35 2019 +0900
|     master working...
|
* commit d84766c7f87b1d9d234050949c48681ba4e35da8 (HEAD -> footer, feature) ☜ HEAD 위치
  Author: hojin <infohojin@gmail.com>
  Date:   Sat May 11 17:10:02 2019 +0900
      First
```

master 브랜치의 마지막 커밋은 dcdb1c1이고, footer 브랜치의 마지막 커밋은 d84766c입니다. master 브랜치에서 새로운 커밋을 생성할 때 부모 커밋으로 dcdb1c1을 가리키는 HEAD 포인터를 사용합니다. footer 브랜치에서 새로운 커밋을 생성할 때는 d84766c를 가리키는 HEAD 포인터를 사용합니다. 그리고 각 브랜치의 마지막 HEAD 포인터를 사용하여 커밋합니다. 현재 HEAD는 footer 브랜치의 d84766c를 가리킵니다.

### __6.7.2 브랜치 HEAD

브랜치를 이동하면 HEAD 포인트도 이동됩니다. 브랜치가 여러 개면 HEAD 포인트도 여러 개입니다. 각각의 브랜치마다 마지막 커밋이 다르기 때문입니다. 브랜치마다 마지막 커밋 ID를 가리키는 HEAD 포인터가 하나씩 있습니다.

```
$ git checkout master ☜ 브랜치를 이동합니다
$ git log --graph --all
* commit dcdb1c1fa4ef78bedd8dc13bc267e99391cc9782 (HEAD -> master) ☜ HEAD 위치
| Author: hojin <infohojin@gmail.com>
| Date:   Sat May 11 18:45:35 2019 +0900
|     master working...
|
* commit d84766c7f87b1d9d234050949c48681ba4e35da8 (footer, feature)
  Author: hojin <infohojin@gmail.com>
  Date:   Sat May 11 17:10:02 2019 +0900
      first
```

master 브랜치로 변경한 후 HEAD 포인터 위치는 이동된 브랜치의 마지막 커밋 dcdb1c1을 가리킵니다. HEAD 포인터는 브랜치에 따라서 위치가 달라집니다. HEAD는 현재 작업하는 브랜치를 가리키기 때문입니다.

### __6.7.3 소스트리 HEAD

### __6.7.4 상대적 위치

깃의 HEAD 포인터는 내부적으로 커밋을 생성하고 브랜치를 관리하는 데 매우 유용합니다.

상태적 커밋 위치를 지정할 때는 캐럿(^)과 물결(~) 기호를 같이 사용합니다.

HEAD를 기준으로 이전 3개 위치를 지정하고 싶다면 HEAD^^^, HEAD~~~처럼 사용합니다. 하지만 좀 더 먼 상대적 위치를 지정할 때는 기호가 많아져 이렇게 사용하기 어렵습니다. 이때는 숫자를 사용하여 HEAD^3 또는 HEAD~3처럼 표현합니다.

> Note: 최근의 특정 위치를 지정할 때는 100644처럼 해시키를 사용하는 것이 편리합니다.

### __6.7.5 AHEAD, BHEAD

AHEAD와 BHEAD는 서로 다른 저장소 간 HEAD 포인터의 위치 차이를 의미합니다.

AHEAD
AHEAD는 서버로 전송되지 않은 로컬 커밋이 있는 것입니다.

BHEAD

BHEAD는 로컬 저장소로 내려받지 않은 커밋이 있는 것입니다.

## 6.8 생성과 이동

### __6.8.1 자동 이동 옵션

브랜치 생성과 이동 명령을 따로 두 번씩 입력하는 것은 불편합니다. 다음과 같이 체크아웃할 때 -b 옵션을 같이 사용하면 브랜치 생성과 이동을 한 번에 할 수 있습니다.

```
$ git checkout -b 브랜치이름
```

```
$ git checkout -b hotfix ☜ 체크아웃합니다
Switched to a new branch 'hotfix' ☜ ①브랜치를 생성합니다

infoh@DESKTOP MINGW64 /e/gitstudy06 (hotfix) ☜ ②체크아웃

$ git branch -v
  feature d84766c first
  footer  d84766c first
* hotfix  dcdb1c1 master working...
  master  dcdb1c1 master working...
```

### __6.8.2 커밋 이동

브랜치로 이동할 때 꼭 브랜치 이름만 사용할 필요는 없습니다. 브랜치 이름 대신 커밋 해시키를 사용하여 체크아웃할 수도 있습니다.

```
$ git checkout dcdb1c1
```

### __6.8.3 HEAD를 활용한 이동

```
$ git checkout HEAD~5
```

### __6.8.4 돌아오기

```
$ git checkout -
```

```
$ git checkout master
```

## 6.9 원격 브랜치

### __6.9.1 리모트 브랜치

원격 저장소와 로컬 저장소의 브랜치 이름은 보통 같지만, 반드시 일치하지 않아도 괜찮습니다. 서로 다른 이름으로 브랜치를 연결할 수도 있습니다. 두 저장소는 서로 다른 브랜치로 운영·관리할 수 있습니다.

```
$ git remote add origin https://github.com/jinygit/gitstudy06.git☜ 자기계정 
$ git remote -v
origin  https://github.com/jinygit/gitstudy06.git (fetch)
origin  https://github.com/jinygit/gitstudy06.git (push)

```

### __6.9.2 실습 준비

### __6.9.3 브랜치 추적

원격 저장소의 브랜치를 가리키는 것을 브랜치 추적이라고 합니다. 다른 용어로 추적 브랜치를 트래킹 브랜치라고 합니다.

```
$ ls .git/refs/
heads  tags
```

### __6.9.4 브랜치 업로드

등록된 원격 저장소의 리모트 `브랜치는 remote show` 명령어로 확인

```
$ git remote show origin
* remote origin
  Fetch URL: https://github.com/jinygit/gitstudy06.git
  Push  URL: https://github.com/jinygit/gitstudy06.git
  HEAD branch: (unknown)
```

```
$ git push 원격저장소별칭 브랜치이름
```

```
$ git push -u origin master
```

```
$ git branch -v
```

```
$ git push -u origin hotfix ☜  -u 옵션은 "set upstream"  현재 브랜치의 기본 업스트림으로 원격 저장소 remote의 hotfix 브랜치를 설정합니다. 
```

### __6.9.5 이름이 다른 브랜치

```
$ git push origin 브랜치이름:새로운브랜치
```

```
$ git push -u origin feature:function ☜  -u 옵션은 "set upstream" 현재 브랜치를 서버(origin)의 새로운 브랜치 이름 function으로 전송하라
```

### __6.9.6 업스트림 트래킹

업스트림(upstream)은 브랜치 추적을 다르게 표현한 것입니다. 

리모트 브랜치는 브랜치 이름을 동일하게 생성할 수도 있고, 다른 이름으로 생성할 수도 있습니다. 이처럼 로컬 저장소의 브랜치와 원격 저장소의 브랜치는 업로드할 수 있도록 매칭되어 있습니다. 이러한 매칭을 업스트림 트래킹이라고 합니다.

```
$ git clone https://github.com/jinygit/gitstudy06.git gitstudy06_clone
☜ 원격 저장소를 복제합니다. 복제 폴더 이름은 gitstudy06_clone입니다.
```

```
$ git branch -v
```

-r 옵션을 사용하면 원격 저장소의 리모트 브랜치 목록을 확인

```
$ git branch -r
```

모든 브랜치 정보를 확인

```
$ git branch -a
```

복제한 저장소의 트래킹 브랜치 목록을 확인

```
$ git branch -vv ☜ 모든 트래킹 브랜치 목록
* master dcdb1c1 [origin/master] master working...
```

로컬 저장소에서 feature 브랜치를 function 리모트 브랜치로 등록

```
$ git checkout --track origin/브랜치이름
```

```
$ git checkout --track origin/function
$ git branch -vv ☜ 모든 트래킹 브랜치 목록
* function d84766c [origin/function] first ☜ 트래킹 브랜치
master   dcdb1c1 [origin/master] master working...
```

```
$ code branch.htm ☜ VS Code 실행
```

```
$ git commit -am "function working"
[function 85f1dfa] functionmaster2 working
 1 file changed, 2 insertions(+), 1 deletion(-)

infoh@DESKTOP MINGW64 /e/gitstudy06_clone (function)
$ git branch -vv
* function 85f1dfa [origin/function: ahead 1] functionmaster2 working ☜ AHEAD 표시
master   dcdb1c1 [origin/master] master working...
```

function 브랜치 정보에 AHEAD 1이 표시됩니다. 원격 저장소로 전송되지 않은 커밋이 하나 있다는 의미입니다.

push 명령어를 사용하여 원격 저장소로 새롭게 추가된 커밋을 전송

```
$ git push
```

원본 저장소( gitstudy06)에서 git pull 명령어를 실행하면 feature 브랜치 정보로 자동 병합됩니다.

```
$ git checkout feature ☜ feature 브랜치로 체크아웃
```

원격 저장소의 function 브랜치를 로컬 저장소의 feature 브랜치로 내려받습니다.

```
$ git pull ☜ 원격 저장소의 function 브랜치를 feature 브랜치로 다운로드
```


### __6.9.7 원격 브랜치 복사

### __6.9.8 업스트림 연결

## 6.10 브랜치 전송

### __6.10.1 브랜치 푸시

### __6.10.2 브랜치 페치

## 6.11 브랜치 삭제

### __6.11.1 일반적인 삭제 방법

### __6.11.2 강제로 삭제하는 방법

### __6.11.3 소스트리에서 삭제하는 방법

### __6.11.4 리모트 브랜치를 삭제하는 방법

## 6.12 정리

# 7장 임시 처리

## 7.1 스태시

### __7.1.1 기존 작업 도중에 새로운 변경 요청

## __7.1.2 새 코드 작성 중 기존 코드를 수정

## __7.1.3 스태시의 임시 스택 영역에 작업 중인 코드 저장

## __7.1.4 임시 저장 영역의 스택 목록

### __7.1.5 임시 저장한 스태시 불러오기

### __7.1.6 스태시 복원으로 충돌

### __7.1.7 스태시 복사

### __7.1.8 스태시 삭제

### __7.1.9 소스트리에서 스태시 사용

## 7.2 워킹 디렉터리 청소

## 7.3 정리

# 8장 병합과 충돌

## 8.1 병합

### __8.1.1 하나씩 직접 비교하는 수동 병합

### __8.1.2 깃으로 자동 병합

### __8.1.3 병합 방식

## 8.2 Fast-Forward 병합

### __8.2.1 브랜치 생성과 수정 작업

### __8.2.2 병합 위치

### __8.2.3 Fast-Forward 병합 적용

### 8.3 3-way 병합

### __8.3.1 브랜치 생성과 수정 작업

### __8.3.2 마스터 변경

### __8.3.3 공통 조상

### __8.3.4 병합 커밋

### __8.3.5 병합 메시지

## 8.4 브랜치 삭제

### __8.4.1 병합 후 삭제

## 8.5 충돌

### __8.5.1 충돌이 생기는 상황

### __8.5.2 실습을 위한 충돌 만들기

### __8.5.3 수동으로 충돌 해결

### __8.5.4 소스트리에서 충돌 해결

## 8.6 브랜치 병합 여부 확인

## 8.7 리베이스

### __8.7.1 베이스

### __8.7.2 베이스 변경

### __8.7.3 리베이스 vs 병합

### __8.7.4 리베이스 명령어

### __8.7.5 리베이스 병합

### __8.7.6 리베이스되었는지 확인

### __8.7.7 리베이스 후 브랜치

### __8.7.8 리베이스 충돌과 해결

### __8.7.9 rebase 명령어로 커밋 수정

### __8.7.10 리베이스할 때 주의할 점

## 8.8 정리

# 9장 복귀

## 9.1 되돌리기

### __9.1.1 다시 시작

## 9.2 리셋

### __9.2.1 복귀 시점

### __9.2.2 reset 명령어

### __9.2.3 soft 옵션

### __9.2.4 mixed 옵션

### __9.2.5 hard 옵션

### __9.2.6 소스트리

### __9.2.7 커밋 합치기

### __9.2.8 스테이지 리셋

### __9.2.9 작업 취소

### __9.2.10 병합 취소

### __9.2.11 주의할 점

## 9.3 리버트

### __9.3.1 취소 커밋

### __9.3.2 리버트 지정

### __9.3.3 소스트리에서 리버트

### __9.3.4 병합 취소

### __9.3.5 리버트 히스토리

## 9.4 정리

# 10장 배포 관리와 태그

## 10.1 배포

## 10.2 버전

## 10.3 태그

## 10.4 태그 목록

## 10.5 Annotated 태그

### __10.5.1 태그 생성

### __10.5.2 간단한 메시지

### __10.5.3 소스트리에서 태그 생성

### __10.5.4 태그는 중복해서 생성할 수 없다

### __10.5.5 태그 삭제

### __10.5.6 태그의 상세 정보 확인: show 명령어

### 10.6 Lightweight 태그

### __10.6.1 체크섬

### __10.6.2 태그의 상세 정보 확인

## 10.7 특정 커밋 태그

### __10.7.1 소스트리에서 특정 커밋 지정

## 10.8 태그를 사용한 체크아웃

### __10.8.1 태그 브랜치

## 10.9 태그 공유

### __10.9.1 원격 저장소 생성

### __10.9.2 태그 동기화

### __10.9.3 전체 태그 동기화

### __10.9.4 원격 저장소의 태그 수정과 삭제

### __10.9.5 원격 저장소에 로컬과 다른 이름으로 태그 전송

## 10.10 정리

# 11장 서브모듈

## 11.1 대형 프로젝트

## __11.1.1 저장 용량

### __11.1.2 저장소 분리

### __11.1.3 상하 관계

## 11.2 실습을 위한 저장소 준비

### __11.2.1 메인 저장소 생성

### __11.2.2 자식 저장소 생성

## 11.3 서브모듈 추가

### __11.3.1 저장소 연결

### __11.3.2 설정 파일

### __11.3.3 모듈 커밋

## 11.4 서브모듈 작업

### __11.4.1 모듈 저장소

### __11.4.2 모듈 상태

### __11.4.3 모듈 커밋

### __11.4.4 부모 커밋

## 11.5 자식 저장소 갱신

### __11.5.1 자식 저장소

### __11.5.2 자식 저장소 갱신

### __11.5.3 자식 저장소 작업

### __11.5.4 부모 저장소 적용

### __11.5.5 부모 저장소 갱신

## 11.6 부모 저장소 복제

### __11.6.1 부모 저장소 복제

### __11.6.2 모듈 업데이트

## 11.7 부모 저장소 업데이트

### __11.7.1 부모 업데이트

### __11.7.2 부모 저장소로 풀

## 11.8 정리

# 12장 고급 기능

## 12.1 refs

### __12.1.1 실습 환경 준비

### __12.1.2 해시

### __12.1.3 역조회

### __12.1.4 참조 목록

## 12.2 reflog

### __12.2.1 참조 기록

### __12.2.2 기록 확인

### __12.2.3 기간 확인

### __12.2.4 기록 유지

## 12.3 파일 애너테이션

### __12.3.1 blame

### __12.3.2 실습 환경 준비

### __12.3.3 blame 명령어

### __12.3.4 옵션 활용

## 12.4 replace

### __12.4.1 실습 환경 준비

### __12.4.2 저장소 분리

### __12.4.3 저장소 분리

### __12.4.4 저장소 연결

## 12.5 가비지 콜렉트

### __12.5.1 가비지

### __12.5.2 압축 관리

### __12.5.3 실행

### __12.5.4 refs 압축

### __12.5.5 환경 설정

## 12.6 prune

### __12.6.1 고립된 객체

### __12.6.2 실습 환경 준비

### __12.6.3 객체 삭제

### __12.6.4 객체 정리

### __12.6.5 원격 작업

## 12.7 rerere

### __12.7.1 동일한 충돌

### __12.7.2 활성화

### __12.7.3 실습 준비

### __12.7.4 충돌 및 기록

### __12.7.5 자동 해결

* [ ] 12.8 정리
