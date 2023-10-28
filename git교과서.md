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
$ git mv index.htm home.htm
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
$ git remote add origin/master
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
$ git push -u origin hotfix ☜  -u 옵션은 "set upstream"  현재 브랜치의 기본 업스트림으로 원격 저장소 remote의 hotfix 브랜치를 설정합니다. 다음 upload시엔 "git push" 사용 가능.
```

### __6.9.5 이름이 다른 브랜치

```
$ git push origin 브랜치이름:새로운브랜치
```

local hotfix 브랜치 상태에서 local feature 브랜치를 remote function 브랜치로 설정할 때

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

다른 개발자 생성한 원격 저장소를, 로컬 저장소에 새로운 브랜치를 생성하여 동기화

```
$ git checkout -b 새이름 origin/브랜치이름
```

### __6.9.8 업스트림 연결

```
git branch -u origin/브랜치이름
```

> * -u 옵션은 --set-upstream-to로 기존 브랜치를 특정 원격 브랜치로 추적
> * remote에 aaa, local에 bug branch일 때 업스트림 설정을하면 git branch -u origin/aaa

## 6.10 브랜치 전송

### __6.10.1 브랜치 푸시

현재 브랜치(master)를 원격 서버(origin)의 master로 전달

```
git push -u origin master
```

> * 직접 서버를 운영한다면 다음과 같이 계정 권한을 변경해 줍니다.
>   [root@ns /home/git]# chmod -R g+ws *
>   [root@ns /home/git]# chgrp -R git *

### __6.10.2 브랜치 페치

리모트 브랜치가 페치되면 깃은 단순히 **원격저장소별칭/브랜치** 포인터만 생성합니다. 원격 저장소에서 페치된 커밋들을 새로운 로컬 브랜치로 반영하려면 병합 명령을 실행해야 합니다.

```
$ git merge 원격저장소별칭/브랜치이름
```

페치된 브랜치를 병합하지 않고 테스트만 하고 싶을 때

```
$ git checkout -b 임시브랜치이름 origin/브랜치이름
```

## 6.11 브랜치 삭제

```
git branch -d 브랜치이름
```

### __6.11.1 일반적인 삭제 방법

```
git branch -d footer
```

### __6.11.2 강제로 삭제하는 방법

워킹 디렉터리에 작업한 기록이 있거나 **add** 명령어로 스테이지의 인덱스가 변경된 상태라면 삭제되지 않습니다. 삭제하려면 반드시 최종 상태가 커밋되어 깨끗한 스테이지 상태여야 합니다. 또 병합되지 않은 브랜치는 -d 옵션으로 삭제할 수 없습니다.

```
$ git checkout hotfix
$ code hotfix.html
$ git commit -am "hotfix working"
$ git checkout master
$ git branch -d hotfix
```

### __6.11.3 소스트리에서 삭제하는 방법

### __6.11.4 리모트 브랜치를 삭제하는 방법

$ git push origin --delete **리모트브랜치이름**

```
$ git push origin --delete aaa
```

## 6.12 정리

# 7장 임시 처리

## 7.1 스태시

완료되지 않은 작업(커밋되지 않은 변경 내용)이 남아 있을 때, 현재 작업을 임시로 저장할 수 있는 **스태시 기능**

### __7.1.1 기존 작업 도중에 새로운 변경 요청

```
$ git checkout -b feature
$ code stash.htm ☜ commit하지 않고 저장만 함.
$ git commit -am "new feature start" 
$ code stash.htm
$ git status ☜ modified 상태

```

## __7.1.2 새 코드 작성 중 기존 코드를 수정

원본 **master** 브랜치로 체크아웃되지 않습니다! 오류 메시지만 출력됩니다. 오류 메시지 내용은 **워킹 디렉터리에 커밋하지 않은 작업이 남아 있어 현재 브랜치를 변경할 수 없다**.

## __7.1.3 스태시의 임시 스택 영역에 작업 중인 코드 저장

스태시 명령어는 수정 중인 내역을 커밋하지 않고도 **브랜치를 이동할 수 있게 워킹 디렉터리를 깨끗이 청소**합니다. 따라서 커밋 대신 스태시 명령을 실행하면 됩니다. 스태시는 영구적인 커밋 기록 대신 **현재 작업들을** **임시 스택 영역에 저장**합니다.

```
$ git stash
```

```
$ git stash save "WIP: 메시지~~~"1
$ git stash 
$ git status
$ git checkout master
```

## __7.1.4 임시 저장 영역의 스택 목록

```
$ git stash list
```

확인은 $ cat .git/refs/stash

```
$ git stash show 
$ git stash show -p stash@{0}
```

### __7.1.5 임시 저장한 스태시 불러오기

filo(First In Last Out)

```
$ code stash.htm
$ git commit -am "bug fix master" 
$ git checkout feature
$ git stash pop  ☜ pop 옵션을 사용하면 스태시 저장 스택에서 항목을 가져오는 동시에 저장된 항목을 삭제
$ git stash list ☜ 스태시 스택 목록에 내용이 없습니다.
```

### __7.1.6 스태시 복원으로 충돌

스택에 저장된 스태시 내용이 다시 워킹 디렉터리로 복구될 때, 수정된 작업 내용과 현재 워킹 디렉터리를 병합하기 때문에, 스태시를 복원할 때 워킹 디렉터리의 상태는 깨끗해야 합니다.

태시 충돌이 예상된다면 스태시용 브랜치를 하나 생성해서 작업하는 것을 추천

```
$ git stash
$ git stash list ☜ stash@{0}: WIP on feature: a43043e new feature start 스태시 내용이 하나 있는 것을 확인
$ git stash branch test
$ git stash list ☜ 정상적으로 스태시 복원이 적용되면 저장된 스택은 자동으로 삭제
```

### __7.1.7 스태시 복사

스태시는 브랜치 작업들을 임시로 저장할 때 사용

**스태시 스택에 저장된 항목들은 어느 브랜치에서나 복원이 가능.** **apply** 옵션은 스택에 저장된 항목을 불러와 현재 브랜치로 복원

스태시의 **pop** **명령어는 스택 내용을 복원한 후 스택 목록에서 자동으로 삭제**

```
$ git stash apply
$ git checkout feature 
$ git stash list 
```

### __7.1.8 스태시 삭제

스태시는 복원할 때 한 번 호출하면 자동으로 스택에서 삭제

남아 있는 스택 목록을 삭제

```
$ git stash list
$ git stash drop
```

### __7.1.9 소스트리에서 스태시 사용

## 7.2 워킹 디렉터리 청소

개발하는 과정에서는 컴파일 등 임시로 생성되는 파일들이 생깁니다. **clean** 명령어를 실행하는 순간 워킹 디렉터리의 추적되지 않는 모든 파일을 삭제한다

```
$ echo "this is temp" > temp.htm
$ git status
$ git clean
$ git clean -f ☜ 강제 청소
```

## 7.3 정리

# 8장 병합과 충돌

## 8.1 병합

분리된 브랜치를 한 브랜치로 합치는 작업

### __8.1.1 하나씩 직접 비교하는 수동 병합

### __8.1.2 깃으로 자동 병합

깃의 자동 병합은 원본을 기준으로 두 파일의 변경 이력을 비교하여, 변경된 파일 내용이 발견되면 자동으로 수정된 코드 내용을 병합

### __8.1.3 병합 방식

깃의 병합은 브랜치를 기반으로 실행

> * Fast-Forward 병합
> * 3-way 병합

```
$ mkdir gitstudy08
$ cd gitstudy08
$ git init
$ code index.htm
$ git add . ☜ 전체 파일을 등록. 추적 상태
$ git commit -m "first" ☜ master 브랜치 상태
```

## 8.2 Fast-Forward 병합

브랜치가 분기되지만 전체 커밋 그림으로 보면 모든 변경 사항은 순차적으로 진행됩니다. 이러한 순차적 커밋에 맞추어 병합을 처리하는 방법

### __8.2.1 브랜치 생성과 수정 작업

```
$ git branch feature
$ git checkout feature
$ git rev-parse feature ☜ 브랜치 커밋 확인
$ code index.htm
$ git commit -am "add header"  ☜ feature 브랜치가 master 브랜치보다 커밋이 하나 더 있는 것을 볼 수 있습니다.
$ code index.htm
$ git commit -am "add menu1" 
$ code index.htm
$ git commit -am "add menu2"
$ git log  ☜ 로그 확인
```

### __8.2.2 병합 위치

**merge** 명령어는 **현재 브랜치를 기준**으로 다른 브랜치의 모든 커밋을 병합합니다.

브랜치를 병합하려면 기준과 대상이 있어야 합니다. 기준은 체크아웃된 현재 브랜치입니다. 따라서 병합하려면 먼저 기준이 되는 브랜치로 이동해야 합니다

기존 **master** 브랜치에서 **feature** 브랜치로 분기하여 작업한 상태로 병합을 하려면 먼저 **master** 브랜치로 체크아웃해야 합니다.

```
$ git checkout master 
$ code index.htm
```

### __8.2.3 Fast-Forward 병합 적용

커밋 작업은 분기된 **feature** 브랜치에서 모두 수행했습니다. 아직 **master** **브랜치에는 추가된 커밋이 없습니다.** 이러한 상태에서 두 브랜치를 병합합시다.

```
$ git merge feature
```

"$ git log -1" ☜ 로그 확인
$ code index.htm  ☜ master 브랜치

### 8.3 3-way 병합

### __8.3.1 브랜치 생성과 수정 작업

새로운 작업을 할 **hotfix** 브랜치를 생성하고, **hotfix** 브랜치로 체크아웃

```
$ git checkout -b hotfix ☜ hotfix 브랜치
$ code index.htm
$ git commit -am "add footer" 
$ code index.htm
$ git commit -am "add copyright"
```

### __8.3.2 마스터 변경

**master** 브랜치에도 새로운 커밋을 추가하여 브랜치 모양을 변경해 보겠습니다.

```
$ git checkout master ☜ master 브랜치
$ code index.htm
$ git commit -am "add menu3"
$ code index.htm
$ git commit -am "add menu4"
```

### __8.3.3 공통 조상

  `                                     |-----c5df346-----7277f2d-----hotfix

e762475-----7caf5f0-----|

  `                                     |-----49c98af-----8583edf-----master

### __8.3.4 병합 커밋

실습한 **hotfix** 브랜치를 **master** 브랜치에 병합

  `                                     |-----c5df346-----7277f2d-----hotfix-----|

e762475-----7caf5f0--------------------------------------------------|-----a48d563

  `                                     |-----49c98af-----8583edf-----master-----|

```
$ git merge hotfix
$ git log -1 로그
```

### __8.3.5 병합 메시지

자동으로 작성되는 메시지 외에 직접 커밋 메시지를 작성할 수도 있습니다. **merge** 명령어를 실행할 때 **-**e 또는 **--**edit **옵션**을 사용하면 됩니다.

```
$ git reset --hard HEAD^  ☜ 병합 취소
$ git merge hotfix --edit  ☜ 병합 명령
```

## 8.4 브랜치 삭제

일반적으로 병합한 이후에는 병합된 브랜치를 삭제합니다. 하지만 지속적인 통합과 개발을 해야 하는 브랜치라면 병합 후에도 계속 남겨 둡니다.

### __8.4.1 병합 후 삭제

**master** 브랜치에 병합된 **hotfix** 브랜치를 삭제

```
$ git branch -d hotfix 
```

병합을 완료하지 않은 브랜치를 삭제하고 싶다면 대문자 -D 옵션을 사용

## 8.5 충돌

### __8.5.1 충돌이 생기는 상황

대부분의 충돌 원인은 같은 위치의 코드를 동시에 수정했기 때문입니다. 파일을 수정할 때 여러 개발자가 서로 다른 위치를 수정했다면 깃에서 서로 다른 위치의 소스를 자동으로 병합하기 때문에 문제가 없습니다. 하지만 파일에서 동일한 위치에 두 명 이상이 서로 다르게 수정했다면 충돌이 발생합니다.

### __8.5.2 실습을 위한 충돌 만들기

기준 브랜치 master

```
infoh@DESKTOP MINGW64 /e/gitstudy08 (master) 
$ git checkout -b footer
$ code index.htm
$ git commit -am "edit footer"
$ git checkout master
$ code index.htm
$ git commit -am "edit copyright"
```

기준 브랜치 master

두 브랜치의 **index**.**htm** 파일에서 같은 위치의 내용을 각각 다르게 수정했기 때문에 충돌 발생

```
infoh@DESKTOP MINGW64 /e/gitstudy08 (master) 
$ git merge footer
Auto-merging index.htm
CONFLICT (content): Merge conflict in index.htm
Automatic merge failed; fix conflicts and then commit the result. 

$ git status 
$ git merge --abort  ☜ 병합 명령 취소
```

### __8.5.3 수동으로 충돌 해결

충돌은 두 부분으로 표시됩니다. 하나는 기준이 되는 브랜치 내용이고, 다른 하나는 병합하고자 하는 브랜치 내용입니다.

```
$ code index.htm 
$ git ls-files -u  ☜ 충돌한 파일들의 집합을 확인
$ git add index.htm  ☜ 스테이지에 등록
$ git commit -m "resolve complicit"  ☜ 병합 커밋 작성, 충돌 해결

```

### __8.5.4 소스트리에서 충돌 해결

## 8.6 브랜치 병합 여부 확인

```
infoh@DESKTOP MINGW64 /e/gitstudy08 (master) 
$ git branch --merged 브랜치 목록
  feature
  footer
* master
```

병합하지 않은 브랜치는 --no-merged 옵션으로 확인.

```
$ git branch --no-merged
```

병합하지 않은 브랜치는 -d 옵션으로 삭제되지 않으므로 -D 옵션을 사용합니다.

## 8.7 리베이스

### __8.7.1 베이스

브랜치를 합치는 방법은 두 가지입니다. 앞에서 배운 병합**(**merge**)**과 이 절에서 학습할 리베이스**(**rebase**)**입니다. 이번에는 커밋 순서를 재배열하는 리베이스 병합을 알아보겠습니다.

리베이스는 커밋의 트리 구조를 재배열합니다. 커밋을 재배열하는 변경 결과가 병합과 유사합니다.

브랜치는 특정 커밋을 가리키는 포인터, 가리키는 특정 커밋은 브랜치가 파생된 기준.

새로운 **브랜치가 파생되는 커밋를** **베이스**(**base**)**라고 합니다.** 병합에서는 이를 공통 조상 커밋이라고 합니다.

### __8.7.2 베이스 변경

리베이스**(**rebase**)**는 파생된 브랜치의 기준이 되는 베이스 커밋을 변경하는 것.

### __8.7.3 리베이스 vs 병합

병합은 파생된 두 브랜치를 하나로 합치는 과정입니다. 병합하려면 두 브랜치의 공통 조상 커밋을 먼저 찾아야 합니다. 공통 조상 커밋을 찾으면 서로 다르게 커밋이 진행된 두 브랜치를 **3**-**way** 방식으로 병합할 수 있습니다.

공통 조상 커밋은 두 브랜치를 병합하는 베이스 커밋입니다. 병합하는 두 브랜치는 순차적으로 커밋을 비교하면서 마지막 최종 커밋을 생성합니다.

반면에 **리베이스는 두 브랜치를 서로 비교하지 않고 순차적으로 커밋 병합**을 시도합니다.

결과적으로 첫째, **3**-**way** 병합은 병합 커밋이 있지만, 리베이스를 하면 병합 커밋은 없습니다. 둘째, 브랜치의 마지막을 가리키는 커밋 위치가 다릅니다.

### __8.7.4 리베이스 명령어

```
infoh@DESKTOP MINGW64 /e/gitstudy08 (master)
$ git checkout -b description**
$ code index.htm 
$ git commit -am "add description"
$ git checkout master
$ code index.htm
$ git commit -am "add menu5"
$ code index.htm
$ git commit -am "add menu6"
```

### __8.7.5 리베이스 병합

리베이스는 병합 기준 브랜치가 **merge** 명령어와 반대

리베이스를 할 수 있게 **description** 브랜치로 체크아웃

```
$ git checkout description ☜ 리베이스 브랜치
```

description 브랜치에서 원본 master 브랜치를 리베이스합니다.

```
$ git rebase master ☜ master 브랜치를 리베이스
```

리베이스 명령이 실행되면 파생 브랜치의 커밋들은 기준 브랜치의 마지막 커밋으로 재정렬됩니다.

### __8.7.6 리베이스되었는지 확인

리베이스는 베이스 커밋을 변경하여 병합한다고 했습니다. 베이스 커밋을 변경하는 과정에서 커밋들은 재배치 작업을 합니다.

```
$ git log -3
commit 48caea016f0e330cfc1dfcd587996fa9a32042fd (HEAD -> description)
Author: hojin <infohojin@gmail.com>
Date:   Sat May 18 17:27:09 2019 +0900
    add description

commit a7fe40bb622f6c8af0b1f25b0d86ea96c7896c50 (master)
Author: hojin <infohojin@gmail.com>
Date:   Sat May 18 17:28:59 2019 +0900
    add menu6

commit 8959f0cca024504cfe321adf440c9c888f8e4693
Author: hojin <infohojin@gmail.com>
Date:   Sat May 18 17:28:29 2019 +0900
    add menu5
```

### __8.7.7 리베이스 후 브랜치

리베이스 병합 이후 커밋은 정리되었다. 일반적으로 병합을 한 후 두 브랜치는 같은 커밋 **ID**를 가리킵니다. 하지만 브랜치 모양이 약간 다릅니다.

**리베이스는 커밋 위치를 재조정할 뿐 브랜치의****HEAD****포인터까지 옮겨 주지는 않습니다.** 리베이스한 후에는 이러한 병합 브랜치의 **HEAD**를 맞추어야 합니다. 즉, 리베이스된 브랜치를 병합해야 합니다.

병합을 위해 **master** 브랜치로 체크아웃합니다. 그리고 **master** 브랜치에서 **merge** 명령어를 실행합니다.

```
$ git checkout master 
$ git merge description

```

### __8.7.8 리베이스 충돌과 해결

리베이스는 기준점을 변경합니다. 리베이스 역시 병합 과정에서 충돌이 발생할 수 있습니다. 리베이스 충돌 또한 사용자가 직접 수동으로 해결해야 합니다.

```
$ git checkout -b menu  ☜ 브랜치 생성
$ code index.htm 
$ git commit -am "edit menu5"
$ code index.htm
$ git commit -am "edit menu6" 
$ git checkout master
$ code index.htm
$ git commit -am "edit submenu for menu5"
$ git checkout menu
$ git rebase master  ☜ 충돌발생
```

리베이스는 커밋을 하나씩 따라가면서 위치를 재조정합니다. 충돌을 수정한 후에는 rebase 명령어와 --continue 옵션을 사용합니다.

```
$ git add index.htm
$ git rebase --continue  ☜ 계속 진행, 충돌해결
```

리베이스 충돌을 해결했다면 이제 브랜치를 정리할 차례입니다. master 브랜치로 체크아웃한 후 menu 브랜치를 병합합니다. 그리고 병합된 menu 브랜치는 삭제합니다.

```
$ git checkout master
$ git merge menu  ☜ 병합, HEAD 일치
$ git branch -d menu  ☜ 브랜치 삭제
```

### __8.7.9 rebase 명령어로 커밋 수정

마지막 커밋은 **--**amend 옵션으로 수정할 수 있습니다. 이 방법 외에 **rebase** 명령어로도 최종 커밋을 수정할 수 있습니다.

```
우리는 세 번 커밋해서 리베이스했습니다. 하지만 이 커밋들은 작업이 비슷합니다. 이 커밋들을 커밋 하나로 묶어 봅시다.
```

$ git rebase -i HEAD~3

```
$ git log -3
commit 690cc959dd410aad516c17c3bd1b46e3e022b2b6 (HEAD -> master)
Author: hojin <infohojin@gmail.com>
Date:   Sat May 18 18:08:28 2019 +0900
    edit menu5

commit 93aa6eb8ad3cf50845dd04d9b4e92838279df2b4
Author: hojin <infohojin@gmail.com>
Date:   Sat May 18 18:12:56 2019 +0900
    edit submenu for menu5

commit 48caea016f0e330cfc1dfcd587996fa9a32042fd
Author: hojin <infohojin@gmail.com>
Date:   Sat May 18 17:27:09 2019 +0900
    add description
```

명령어를 입력하면 메시지를 입력할 수 있는 vi 에디터가 실행됩니다. 리베이스 병합할 커밋들의 정보도 자동으로 작성됩니다.

### __8.7.10 리베이스할 때 주의할 점

리베이스는 커밋 위치와 해시 값을 변경합니다. **저장소를 외부에 공개했다면 공개된 순간부터 커밋은 리베이스를 사용하지 않는 것이 원칙**입니다.

리베이스는 외부로 코드를 푸시하거나 공개하기 전에 로컬에서만 실행하는 것이 좋습니다. 외부에 공개된 커밋을 리베이스하면 커밋 위치와 해시 값이 변경되어 너무 혼란스럽습니다. 공개된 커밋을 변경할 때는 다음 장에서 배울 **revert** 명령어를 사용합니다.

## 8.8 정리

다수의 개발자와 협업할 때 병합과 충돌은 매우 자주 발생합니다. 충돌을 해결하고 병합을 처리하는 것은 쉬운 작업이 아닙니다. 개발 과정에서 병합 충돌을 최소화하고 예방하려면, **master** 브랜치 내용을 자주 반영하여 병합하는 것이 좋습니다.

# 9장 복귀

## 9.1 되돌리기

### __9.1.1 다시 시작

깃에서 코드 작업을 되돌리는 방법은 크게 **reset**과 **revert** 두 가지입니다. 리셋**(**reset**)**과 리버트**(**revert**)** 동작을 좀 더 쉽게 이해할 수 있도록 실습으로 익혀 보겠습니다. 먼저 실습을 위해 새 깃 저장소 폴더를 만들고 초기화합니다.

```
$ cd 실습폴더
$ mkdir gitstudy09 새 폴더 만들기
$ cd gitstudy09
$ git init 
$ code menu.htm
$ git add menu.htm
$ git commit -m "first"

$ git commit -am "menu1"
$ git commit -am "menu2"
$ git commit -am "menu3"
$ git commit -am "menu4"
$ git commit -am "menu5"
$ git commit -am "menu6"
```

## 9.2 리셋

리셋**(**reset**)**은 커밋을 기준으로 이전 코드로 되돌리는 방법

### __9.2.1 복귀 시점

**log** 명령어를 실행하면 커밋의 해시 값과 메시지를 출력합니다. 따라서 복귀하고자 하는 특정 시점을 찾는 데 매우 유용합니다.

```
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git log --oneline 로그 확인

7f068b6 (HEAD -> master) menu5
6619c99 menu4
b728366 menu3
f1c704f menu2
b741eef menu1
69bf712 first
```

first -----menu1-----menu2-----menu3-----menu4-----menu5(HEAD)

HEAD 포인터를 이용하여 상대적 위치를 지정할 수도 있습니다. 다음과 같이 캐럿(^) 또는 물결(~) 기호를 사용하여 HEAD의 상대 커밋 위치를 지정합니다.
$ **git reset --hard HEAD^^^**

### __9.2.2 reset 명령어

**reset** 명령어는 옵션을 함께 사용해야 하며, 세 가지 옵션이 있습니다.

* **soft**: 스테이지 영역을 포함한 상태로 복원합니다.
* **mixed**: 기본 옵션 값은 **mixed**입니다. **reset** 명령어를 사용할 때 옵션을 지정하지 않으면 기본값인 **mixed**로 선택됩니다.
* **hard**: 실제 파일이 삭제된 이전 상태로 복원합니다.

### __9.2.3 soft 옵션

**soft** 옵션은 가장 낮은 단계의 리셋 동작입니다.

```
$ git reset --soft HEAD~  ☜ 이전 커밋으로 soft 옵션을 사용한 리셋
```

log 명령어로도 커밋 기록을 확인

```
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git log --oneline 로그 확인
6619c99 (HEAD -> master) menu4 
b728366 menu3
f1c704f menu2
b741eef menu1
69bf712 first
```

**diff** 명령어로 비교

```
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git diff HEAD 커밋 비교
diff --git a/menu.htm b/menu.htm
index f717854..9ae7cfc 100644
--- a/menu.htm
+++ b/menu.htm
@@ -3,4 +3,5 @@
     <li>menu2</li>
     <li>menu3</li>
     <li>menu4</li>
+    <li>menu5</li> 파일 수정이 추가됨
 </ul>
\ No newline at end of file
```

깃 상태 확인

```
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git status 상태 확인
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)
 modified:   menu.htm 파일이 변경된 상태
```

다음 실습을 위해 다시 menu5를 등록해서 커밋

```
$ git commit -m "menu5"
```

해시 값이 변경되었는지 로그 확인

```
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git log --oneline 로그 확인
34df5c3 (HEAD -> master) menu5 커밋 해시 값이 변경되었음
6619c99 menu4
b728366 menu3
f1c704f menu2
b741eef menu1
69bf712 first
```

reset --soft 명령어의 원리를 이용하면 마지막 커밋을 수정

### __9.2.4 mixed 옵션

**reset** 명령어의 기본값은 **mixed** 옵션

```
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git reset --mixed HEAD~ mixed 옵션을 사용한 리셋 실행
Unstaged changes after reset:
M       menu.htm
```

메시지 내용은 unstaged 상태로 변경되었다.

**status** 명령어로 깃의 상태를 확인

```
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git status 상태 확인
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)
  modified:   menu.htm
no changes added to commit (use "git add" and/or "git commit -a")
```

soft 옵션은 스테이지 상태까지 복원하기 때문에 바로 commit 명령어를 실행할 수 있었습니다. 하지만 mixed 옵션은 스테이지 상태를 제외하고 복원하기 때문에 Unstaged 상태가 되어 메시지가 빨간색으로 표시됩니다. 따라서 커밋하려면 add 명령어를 먼저 실행해야 합니다.

먼저 리셋한 후 **menu**.**htm** 파일을 확인

```
$ code menu.htm 
```

리셋한 후에도 `<li>`menu5 `</li>` 소스 코드가 남아 있습니다. 이전과 파일 내용이 동일합니다. diff 명령어로 좀 더 확인해 보겠습니다.

```
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git diff HEAD 커밋 비교
diff --git a/menu.htm b/menu.htm
index f717854..9ae7cfc 100644
--- a/menu.htm
+++ b/menu.htm
@@ -3,4 +3,5 @@
     <li>menu2</li>
     <li>menu3</li>
     <li>menu4</li>
+    <li>menu5</li> 파일 수정이 추가됨
 </ul>
\ No newline at end of file
```

새로운 menu5가 추가되었다고 나옵니다. 변경 파일 내용은 워킹 디렉터리에 저장되었습니다.
다음 실습을 위해 다시 menu5를 등록하여 커밋

```
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git commit -m "menu5" 커밋 실패
On branch master
Changes not staged for commit:
  modified:   menu.htm
no changes added to commit
```

앗, 커밋에 실패했네요. mixed 옵션은 스테이지 영역을 같이 복사하지 않기 때문에 수정된 파일은 스테이지 영역이 아닌 워킹 디렉터리 안에 남아 있습니다. 따라서 mixed 옵션을 사용하여 리셋한 후 다시 커밋하려면 반드시 add 명령어를 실행해야 합니다.
add 명령어로 등록하고 다시 커밋합니다.

```
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git add menu.htm 스테이지에 등록

infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git commit -m "menu5" 커밋
[master 1a79348] menu5
 1 file changed, 1 insertion(+)
```

이제 처음과 동일한 상태가 되었습니다.

### __9.2.5 hard 옵션

**hard** 옵션은 리셋되는 복귀 시점의 커밋 상태와 해당 커밋의 워킹 디렉터리까지 모두 되돌립니다. 즉, **reset** **--**hard **명령어**를 사용한 커밋 이후의 모든 내용은 삭제됩니다. 따라서 **hard** 옵션은 주의해서 사용해야 합니다.

**hard** 옵션을 사용해 봅시다.

```
$ git reset --hard HEAD~ 완전 삭제
HEAD is now at 6619c99 menu4
```

hard 옵션을 실행하면 리셋된 결과 메시지가 출력됩니다. 그리고 삭제 이후의 마지막 HEAD 커밋의 해시 값이 출력됩니다.Soft 옵션 리셋과 달리 ‘커밋하지 않은 변경 사항’이 없습니다. 그리고 menu4로 HEAD 포인터가 변경되었습니다.

로그 기록 확인

```
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git log --oneline 로그 확인
6619c99 (HEAD -> master) menu4
b728366 menu3
f1c704f menu2
b741eef menu1
69bf712 first
```

```
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ code menu.htm VS Code 실행
```

깃의 상태도 다시 한 번 확인

```
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git status 상태 확인
On branch master
nothing to commit, working tree clean
```

### __9.2.6 소스트리

### __9.2.7 커밋 합치기

리베이스 병합의 -i 옵션을 사용하면 여러 커밋을 하나로 합치는 동작을 수행할 수 있었습니다. 또 단일 커밋은 커밋 명령어의 --amend 옵션으로 커밋을 수정할 수 있었습니다. 리셋의 동작 원리를 이해하고 있다면, 커밋도 수정할 수 있습니다.

리셋의 **soft** 옵션은 **HEAD**를 해당 커밋으로 이동합니다. 그리고 원본 내용은 그대로 워킹 디렉터리에 남겨 둡니다.

실습으로 커밋을 수정해 봅시다.

수정하기 전에 먼저 로그를 확인

```
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git log --oneline 로그 확인
6619c99 (HEAD -> master) menu4
b728366 menu3
f1c704f menu2
b741eef menu1
69bf712 first
```

menu3과 menu4 커밋을 reset 명령어를 사용하여 하나로 합쳐 보겠습니다.

```
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git reset --soft HEAD~2 2단계 전의 커밋으로 리셋(soft 옵션)
```

최신 커밋 HEAD를 기준으로 2단계 전 상태로 리셋됩니다. 즉, menu2를 가리키는 f1c704f 커밋을 의미합니다.

로그를 다시 실행

```
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git log --oneline 로그 확인
f1c704f (HEAD -> master) menu2
b741eef menu1
69bf712 first
```

리셋한 후 내용을 diff 명령어로 확인

```
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git diff HEAD~ 커밋 비교
diff --git a/menu.htm b/menu.htm
index d11d058..f717854 100644
--- a/menu.htm
+++ b/menu.htm
@@ -1,3 +1,6 @@
 <ul>
     <li>menu1</li>
+    <li>menu2</li> 추가로 상태가 변경됨
+    <li>menu3</li>
+    <li>menu4</li>
 </ul>
\ No newline at end of file
```

소스 코드는 기존 menu2에 추가된 내용과 menu3, menu4가 남아 추가된 상태이며, 워킹 디렉터리와 스테이지 영역이 변경되었습니다.

커밋을 합쳐 다시 메시지를 작성

```
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git commit -m "menu3/4" 커밋
[master dd6d215] menu3/4
 1 file changed, 2 insertions(+)
```

합친 커밋을 생성한 후 소스트리의 그래프를 확인하면, menu3과 menu4를 합친 커밋을 볼 수 있습니다.

**menu**3과 **menu**4는 커밋 **2**개를 합쳐 커밋 하나를 만든 것과 같습니다.

### __9.2.8 스테이지 리셋

스테이지 영역은 커밋을 하려고 임시로 결과물을 보관해 두는 공간입니다. 커밋을 하려면 워킹 디렉터리에서 작업한 내용을 스테이지 영역에 등록해야 합니다.

스테이지 영역에 등록할 때는 **add** 명령어를 사용

```
$ git add 파일이름
```

또 add 명령어로 등록된 스테이지 영역의 파일을 다시 unstage 상태가 되도록 스테이징을 취소할 수 있습니다. 스테이지 영역에서 등록된 파일을 다시 unstage 상태로 만들 때는 reset 명령어를 사용합니다.

```
$ git reset 파일이름
```

reset 명령어 다음에 커밋 ID 대신 파일 이름을 사용하면 됩니다. 파일 이름을 지정하여 리셋하면 해당 파일은 unstage 상태가 됩니다. 하지만 이 명령어는 몇 가지 옵션이 축약되어 있습니다. 내부적으로 다음과 같이 여러 단계로 처리하여 파일을 unstage 상태로 변경합니다.

```
$ git reset --mixed HEAD 파일이름
```

원래는 중간에 --mixed HEAD가 생략된 형태입니다. 최신 커밋에서 지정 파일을 리셋하고 mixed 옵션으로 스테이지 영역도 같이 제거합니다. 다음과 같이 HEAD 대신 다른 커밋 ID를 사용할 수도 있습니다.

```
$ git reset 커밋ID 파일이름
```

### __9.2.9 작업 취소

보통은 다음과 같이 워킹 디렉터리에서 코드를 수정하고, 수정한 코드는 다시 스테이지 영역에 등록합니다.

수정 작업을 완전히 취소하려면 **워킹 디렉터리와 스테이지 상태를 모두 제거하여 마지막 커밋 상태로 되돌려 놓아야 합니다.** **HEAD** 포인터는 가장 마지막의 커밋 위치를 가리킵니다. 그리고 수정 작업들은 모두 워킹 디렉터리 안에 남아 있습니다. 리셋할 때의 **시점을 현재** **HEAD**를 기준으로 하면 해당 시점의 수정 작업을 모두 삭제할 수 있습니다.

```
$ git reset --hard HEAD
```

### __9.2.10 병합 취소

리셋은 병합된 브랜치도 취소할 수 있습니다.

먼저 실습을 위해 커밋 환경을 준비합니다. 다음과 같이 브랜치를 만들어 보겠습니다.

**menu**2의 커밋 해시키를 직접 지정하여 **menu** 브랜치를 생성할 것입니다. 그리고 **menu** 브랜치로 체크아웃하겠습니다.

```
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git checkout -b menu f1c704f menu2의 커밋 해시키를 직접 지정(자신의 실습에 맞는 값으로 입력)
Switched to a new branch 'menu'
```

만든 브랜치에서 menu.htm 파일을 수정하고 저장한 후 커밋

```
infoh@DESKTOP MINGW64 /e/gitstudy09 (menu)
$ code menu.htm VS Code 실행
```

```
infoh@DESKTOP MINGW64 /e/gitstudy09 (menu)
$ git commit -am "menu1-1" 커밋
[menu 7f5fad8] menu1-1
 1 file changed, 5 insertions(+), 1 deletion(-)
```

이제 menu 브랜치와 master 브랜치를 병합하겠습니다. 다른 브랜치로 체크아웃되어 있다면 병합을 위해 먼저 master 브랜치로 체크아웃합니다

```
infoh@DESKTOP MINGW64 /e/gitstudy09 (menu)
$ git checkout master 브랜치 이동
Switched to branch 'master'
```

merge 명령어를 실행합니다. 두 브랜치는 3-way 방식으로 병합하는데, 병합 메시지를 작성해야 합니다. 명령어를 실행한 후 vi 에디터 창이 열리면 메시지를 작성하고 저장하여 빠져나옵니다.

```
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git merge menu 병합
Auto-merging menu.htm
Merge made by the 'recursive' strategy.
 menu.htm | 6 +++++-
 1 file changed, 5 insertions(+), 1 deletion(-)
```

이번에는 방금 전에 병합한 커밋을 리셋하여 취소하겠습니다.

```
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git reset --merge HEAD~ 이전 커밋 리셋
```

### __9.2.11 주의할 점

## 9.3 리버트

공개된 커밋은 보통 리셋 작업을 하지 않는다고 했습니다. 그러면 공개한 저장소에서는 이전 상태로 되돌리려면 깃 커밋의 버전을 되돌릴 수 있는  리버트를 제공합니다. 리버트와 리셋 차이점은 커밋 정보 삭제 여부입니다.

### __9.3.1 취소 커밋

리셋은 기존 커밋 정보를 삭제하는 반면, **리버트는 기존 커밋을 남겨 두고 취소에 대한 새로운 커밋을 생성**합니다.

취소 커밋을 생성할 때는 **revert** 명령어를 사용합니다. 취소 커밋은 지정한 커밋을 삭제하지 않눈 대신 삭제를 위한 새로운 커밋을 생성합니다.

리버트를 실습할 수 있도록 **master** 브랜치에서 코드를 수정한 후 커밋을 몇 개 추가하겠습니다. 먼저 **menu**.**htm** 파일에 **menu**5~**menu**7을 차례로 입력한 후 커밋합니다.

```
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git commit -am "menu5" menu5 등록 및 커밋
[master e19c0b4] menu5
 1 file changed, 1 insertion(+)
```

```
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git commit -am "menu6" menu6 등록 및 커밋
[master 1ea5e47] menu6
 1 file changed, 1 insertion(+)
```

```
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git commit -am "menu7" menu7 등록 및 커밋
[master 5374918] menu7
 1 file changed, 1 insertion(+)
```

 직전의 커밋인 menu7을 취소하고 싶다면 어떻게 해야 할까요? 공개된 커밋은 삭제하지 않으므로 취소하고자 하는 커밋을 리버트합니다.

직전의 커밋을 리버트할 때는 HEAD 포인터를 사용하면 편리합니다. 리셋으로 커밋을 삭제하지 않고 리버트로 취소 커밋을 생성하겠습니다.

```
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git revert HEAD 현재 커밋을 리버트
```

revert 명령어를 사용하면 병합할 때처럼 메시지를 작성할 수 있는 vi 에디터가 실행됩니다. 리버트 메시지를 작성한 후 저장합니다.

```
 [master 00d7770] Revert "menu7"
 1 file changed, 1 deletion(-)
```

menu.htm 파일을 확인

```
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ code menu.htm VS Code 실행
```

마지막에 있던 menu7 태그가 삭제되었습니다. 소스트리에서 커밋 그래프를 확인하면, menu7 커밋 위에 새로운 리버트 커밋이 하나 생성되어 있습니다.

### __9.3.2 리버트 지정

직전의 커밋은 간단하게 **HEAD** 포인터를 이용하여 리버트했습니다.

한 번에 여러 커밋을 리버트해야 한다면 어떻게 해야 할까요? **리버트는 한 번에 커밋 하나만 취소할 수 있습니다.** 따라서 여러 커밋을 리버트하려면 최신 커밋부터 순차적으로 취소해야 합니다.

그렇다면 직전의 커밋이 아닌 다른 커밋을 취소할 때는 어떻게 해야 할까요? 커밋 해시 값을 지정합니다.

```
$ git revert 커밋ID
```

깃의 범위 지정 연산자를 사용하여 여러 커밋을 리버트할 수도 있습니다. 연산자 ..를 같이 사용합니다.

```
$ git revert 커밋ID .. 커밋ID
```

### __9.3.3 소스트리에서 리버트

### __9.3.4 병합 취소

리버트를 이용하여 병합한 커밋을 취소할 수 있습니다. 리셋은 방금 전 실행한 병합만 삭제합니다. 하지만 리버트는 시간이 지난 후에도 과거의 병합을 선택하여 취소할 수 있습니다.

실습을 위해 **menu** 브랜치를 다시 병합하겠습니다. 병합 메시지 입력창이 뜨면 메시지를 입력하고 저장합니다.

```
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git merge menu 병합
Auto-merging menu.htm
Merge made by the 'recursive' strategy.
 menu.htm | 6 +++++-
 1 file changed, 5 insertions(+), 1 deletion(-)
```

그리고 master 브랜치의 코드를 수정하고 커밋합니다. menu7을 다시 등록하겠습니다.

```
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ code menu.htm VS Code 실행
```

```
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git commit -am "menu7" 등록 및 커밋
[master da4d8e4] menu7
 1 file changed, 1 insertion(+)
```

 리버트로 병합을 취소할 때는 --mainline 옵션을 같이 사용할 수 있습니다.

```
$ git revert --mainline 숫자 병합커밋ID
```

 참고로 병합은 두 브랜치가 결합된 형태입니다. 리버트로 병합이 취소 상태가 되면 둘 중 한 브랜치로 체크아웃해야 합니다. --mainline 옵션은 병합을 취소한 후 체크아웃되는 브랜치를 표시합니다. --mainline은 체크아웃으로 되돌아가는 커밋 번호입니다.

아주 간단하게 실습해 보겠습니다. 먼저 로그를 확인합니다. **--**graph 옵션을 사용하면 그래프 형태로 지금까지 로그를 볼 수 있습니다.

```
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git log --oneline --graph
* da4d8e4 (HEAD -> master) menu7
*   84b6618 Merge branch 'menu'
|\
| * 7f5fad8 (menu) menu1-1
* | 00d7770 Revert "menu7"
* | 5374918 menu7
* | 1ea5e47 menu6
* | e19c0b4 menu5
* | dd6d215 menu3/4
|/
* f1c704f menu2
* b741eef menu1
* 69bf712 first
```

그리고 -5처럼 숫자를 추가하면 로그 5개만 출력됩니다.

```
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git log --oneline --graph -5 로그 확인
* da4d8e4 (HEAD -> master) menu7
*   84b6618 Merge branch 'menu'
|\
| * 7f5fad8 (menu) menu1-1
* | 00d7770 Revert "menu7"
* | 5374918 menu7
```

출력 결과에서 84b6618은 병합 시점의 커밋 ID입니다. 이 시점으로 리버트하겠습니다. 리버트 메시지도 작성해 줍니다.

```
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ git revert --mainline 1 84b6618 리버트
[master 4399642] Revert "Merge branch 'menu'"
 1 file changed, 1 insertion(+), 5 deletions(-)
```

이제 기존 병합이 리버트됩니다.

제대로 리버트되었는지 **menu**.**htm** 파일을 확인

```
infoh@DESKTOP MINGW64 /e/gitstudy09 (master)
$ code menu.htm VS Code 실행
```

제대로 잘 리버트되었습니다. 참고로 리베이스된 병합은 리버트하기 어렵습니다. 리베이스로 병합된 공통 조상 커밋을 찾기 어렵기 때문입니다.

### __9.3.5 리버트 히스토리

저장소를 공개했다면 리셋으로 커밋을 삭제하는 것은 협업 차원에서 위험합니다. 이때는 리버트가 유용합니다.

## 9.4 정리

# 10장 배포 관리와 태그

## 10.1 배포

개발 단계에서 발생한 테스트 메시지나 불필요한 주석들을 정리합니다. 이러한 정리 작업을 거쳐 코드를 좀 더 깔끔하게 만들 수 있고, 배포도 가능합니다. 더불어 정리 작업은 조금이지만 코드 용량을 줄이는 효과도 있습니다. 즉, 배포는 정리된 최종 결과물을 만드는 과정

## 10.2 버전

코드는 개발을 완료한 후에도 계속 수정됩니다.

첫 자리가 **0**으로 시작하면 아직 초기 개발 중인 제품이라는 의미입니다.

정식 버전은 **1**부터 시작합니다. 보통 두 번째 자리는 메이저 버전에서 기능을 추가하거나 변경 사항이 있을 때 바꿉니다. 다른 말로 **마이너**(**minor**) **번호**라고도 합니다.

메이저 버전 다음으로 작은 코드의 변화는 점(.)을 사용하여 구분합니다. 보통 두 자리 또는 세 자리 형태의 숫자로 작성합니다.

세 번째 자리는 버그 수정 등 미미한 변화가 있을 때 바꿉니다. 다른 말로 패치**(**patch**)** 버전이라고 합니다. 이처럼 세 자리 숫자 형태로 표기하는 버전을 **SemVer**(**Semantic** **Versioning**) **방식**이라고 합니다.

## 10.3 태그

정리된 커밋을 배포할 수 있도록 특수한 포인터를 제공하며, 특정 커밋을 가리키는 포인터로 버전을 관리합니다. 그리고 이 포인터를 태그라고 합니다.

* **A**nnotated: 태그 이름 + 정보 포함
* **L**ightweight: 태그 이름만 포함

## 10.4 태그 목록

tag명령어 실습

```
$ cd 실습폴더
$ mkdir gitstudy10 새 폴더 만들기
$ cd gitstudy10

infoh@DESKTOP MINGW64 /e/gitstudy10
$ git init 깃 초기화
Initialized empty Git repository in E:/gitstudy10/.git/
```

version.htm 파일을 생성하고 코드를 입력한 후 저장합니다. 그리고 첫 번째 커밋을 합니다.

```
$ code version.htm VS Code 실행
$ git commit -m "first" 커밋
[master (root-commit) 3c92e35] first
 1 file changed, 1 insertion(+)
 create mode 100644 version.htm
```

```
$ code version.htm VS Code 실행
```

## 10.5 Annotated 태그

### __10.5.1 태그 생성

**Annotated**는 ‘주석이 달린’이라는 뜻

커밋의 해시 값뿐 아니라 추가로 생성자 정보를 같이 넣을 수 있습니다. 예를 들어 이메일, 날짜, 메시지 등 정보입니다. 또 **GPG** 방식으로 서명도 가능합니다.

```
$ git tag -a 버전
$ git commit -am "test 1.0.0" 등록 및 커밋
$ git tag -a 1.0.0 태그 추가
$ git tag 태그 목록
$ git log --decorate 로그 확인
```

### __10.5.2 간단한 메시지

**Annotated** **태그를 생성할 때는 메시지를 작성**해야 합니다. 작성할 태그 정보가 간단하다면 **vi** 에디터를 사용하지 않고, **-**m 옵션으로 대체할 수 있습니다. 커밋 명령어의 **-**m 옵션과 유사합니다.

```
$ code version.htm VS Code 실행
$ git commit -am "test 1.1.0" 등록 및 커밋
$ git tag -a 1.1.0 -m "simple tag 1.1.0" 태그 생성
$ git tag 태그 목록
```

### __10.5.3 소스트리에서 태그 생성

```
$ code version.htm VS Code 실행
$ git commit -am "test 1.1.1" 등록 및 커밋

```

### __10.5.4 태그는 중복해서 생성할 수 없다

```
$ code version.htm VS Code 실행
$ git commit -am "test 1.1.2" 등록 및 커밋
$ git tag 태그 목록
$ git tag -a 1.1.1 -m "test 1.1.1" 태그 생성

```

### __10.5.5 태그 삭제

```
$ git log --oneline 커밋 로그
$ git tag -d 1.1.1 태그 삭제
$ git log --oneline 커밋 로그
$ git tag 태그 목록
```

### __10.5.6 태그의 상세 정보 확인: show 명령어

```
$ git show 1.0.0 태그 정보
```

### 10.6 Lightweight 태그

**Lightweight** 태그는 가장 기본적인 태그입니다. **Annotated** 태그와 달리 버전 이름만 있습니다.

### __10.6.1 체크섬

```
$ code version.htm VS Code 실행
$ git commit -am "test 2.0.0" 등록 및 커밋
$ git tag 2.0.0 태그 이름만 작성
$ git tag 태그 목록
```

### __10.6.2 태그의 상세 정보 확인

```
$ git show 2.0.0 태그 정보
```

## 10.7 특정 커밋 태그

**tag** 명령어는 기본적으로 현재 **HEAD**가 가리키는 커밋을 기준으로 태그를 생성합니다. 현재 **HEAD** 포인터가 가리키는 커밋이 아닌 특정 커밋을 직접 지정하여 태그를 생성할 수 있습니다.

```
$ git log --oneline 커밋 로그
$ git tag 1.1.2 80f8890 커밋 지정한 태그
$ git log --oneline 커밋 로그
```

### __10.7.1 소스트리에서 특정 커밋 지정

## 10.8 태그를 사용한 체크아웃

태그를 사용하여 특정 커밋으로 체크아웃할 수 있습니다. **체크아웃할 때 브랜치 이름 대신 태그 이름을 입력하면 됩니다.**

```
$ git checkout 1.0.0 태그로 브랜치 이동
```

### __10.8.1 태그 브랜치

```
$ git checkout -b fix 1.0.0 태그 기준으로 브랜치 생성
```

## 10.9 태그 공유

### __10.9.1 원격 저장소 생성

깃허브에 **로그인**한 후 **New** 버튼 또는 **+** **>** **New repository >** 원하는 저장소 **이름**을 입력하고 **Create repository**를 누릅니다. > 주소를 복사 > Git bash

```
$ git checkout master master 브랜치로 체크아웃
$ git remote add origin https://github.com/jinygit/gitstudy10.git 원격 저장소 등록
$ git remote -v 원격 저장소 목록
```

### __10.9.2 태그 동기화

```
$ git push origin master 커밋 전송
```

생성된 로컬 저장소의 태그 정보 중 하나를 원격 저장소로 전송

```
$ git push origin 1.0.0 태그 전송
```

깃허브는 깃의 태그 정보를 releases 탭에 표시합니다.
깃허브에서 releases 탭을 선택하면 방금 로컬 저장소에서 전송한 태그 정보를 확인할 수 있습니다.

### __10.9.3 전체 태그 동기화

실습한 로컬 저장소의 태그를 다시 확인

```
$ git tag 태그 목록
```

로컬 저장소의 모든 태그를 원격 서버로 전송해 보겠습니다.

```
$ git push origin --tags 모든 태그 전송
```

### __10.9.4 원격 저장소의 태그 수정과 삭제

원격 저장소에 등록된 태그를 깃허브에서 직접 수정할 수 있습니다. 깃허브에서 **Tags**를 누른 후 수정할 태그를 클릭합니다.

선택한 화면에서 오른쪽 위의 **Edit** **tag**를 누릅니다.

로컬 저장소의 태그를 삭제할 때는 **tag** 명령어를 사용합니다. 하지만 **원격 저장소로 공유된 태그를 삭제할 때는** **push** **명령어를 사용**해야 합니다.

```
$ git push --delete origin 2.0.0 명령어 전송
```

push 명령어로 원격 저장소의 태그를 삭제했습니다. 하지만 로컬 저장소의 2.0.0 태그는 삭제되지 않고 남아 있습니다. 원격 저장소의 태그를 삭제했으면 로컬 저장소의 태그도 삭제합시다.

```
$ git tag -d 2.0.0 로컬 저장소 태그 삭제
```

이처럼 태그는 저장소 간 자동으로 동기화되지 않습니다.

그렇다면 전송된 태그 이름을 변경하고 싶을 때는, 원격 저장소의 태그와 로컬 저장소의 태그를 모두 삭제합니다. 그리고 로컬 저장소에서 다시 새로운 태그를 생성한 후 원격 저장소로 생성된 태그를 재전송하면 됩니다. 원격 저장소의 태그가 삭제되어 있지 않고, 동일한 태그 이름으로 전송하면 오류가 발생합니다.

반대로 원격 저장소의 태그 목록을 가져올 때는 pull 명령어를 사용합니다. 참고로 clone 명령어를 사용해서 복제할 때는 태그 정보도 같이 가져옵니다.

### __10.9.5 원격 저장소에 로컬과 다른 이름으로 태그 전송

**push** 명령어는 로컬 저장소의 정보를 원격 저장소로 전송합니다. 이때 **push** 명령어를 사용하여 로컬 저장소의 브랜치를 원격 저장소의 브랜치로 전송할 경우, 다른 이름으로 전송할 수 있었습니다.

```
$ git push origin master:master1
```

이 예는 로컬 저장소의 master 브랜치를 origin 서버(원격 저장소)의 master1 브랜치로 등록하는 방법입니다. 이 원리를 응용하여 태그도 동일한 이름이 아닌 다른 이름으로 전송할 수 있습니다. 다음과 같이 콜론(:)을 사용하여 로컬 저장소의 태그 이름과 원격 저장소의 태그 이름을 지정합니다.

```
$ git push origin 1.1.2:3.0.0 다른 이름의 태그 전송
```

깃허브 저장소를 확인합니다. 변경된 3.0.0 태그가 등록되었네요. 주의 깊게 살펴보면 1.1.2 태그와 3.0.0 태그가 모두 동일한 80f8890 해시 값을 가리킵니다.

태그 생성 원리

```
$ git tag 태그 목록
$ ls .git/refs/tags 저장소 태그 기록
$ git log --decorate 커밋 로그
$ echo f2691a05b82233acf5b37ffeae738ee07a596bde > .git/refs/tags/1.1.1 수동으로 태그 생성
$ ls .git/refs/tags/ 저장소 태그 기록
$ git tag 태그 목록


```

## 10.10 정리

# 11장 서브모듈

## 11.1 대형 프로젝트

## __11.1.1 저장 용량

### __11.1.2 저장소 분리

### __11.1.3 상하 관계

## 11.2 실습을 위한 저장소 준비

### __11.2.1 메인 저장소 생성

먼저 부모 역할의 메인 저장소를 생성

```
$ mkdir gitstudy11_parent 새 폴더 만들기
$ git init 저장소 초기화
$ code parent.htm VS Code 실행
$ git add parent.htm 등록
$ git commit -m "parent first" 커밋

```

메인 저장소와 동기화할 원격 저장소를 생성합시다. 먼저 깃허브에 **로그인**한 후 **New 버튼** 또는 **+ > New repository**를 클릭합니다. 원하는 **저장소 이름**을 입력하고 **Create** **repository**를 누릅니다.

저장소가 생성되면 **https**://**github**.**com**/onespace10/**onespace10**.**git** 주소가 나옵니다. 이 주소와 로컬 저장소를 연결할 것입니다. 이 주소를 복사해 둡니다.

다시 **깃 배시** 화면으로 돌아갑니다. 메인 저장소에 리모트 등록을 합시다.

```
$ git remote add origin https://github.com/jinygit/gitstudy11_parent.git 원격 저장소 등록
$ git push -u origin master 커밋 전송
```

깃허브에서 커밋 정보가 잘 전송된 것을 확인

### __11.2.2 자식 저장소 생성

```
$ mkdir gitstudy11_child 새 폴더 만들기
$ git init 저장소 초기화
$ code child.htm VS Code 실행
$ git add child.htm 등록
$ git commit -m "child first" 커밋
$ git remote add origin https://github.com/jinygit/gitstudy11_child.git 원격 저장소 등록
$ git push -u origin master 커밋 전송
```

## 11.3 서브모듈 추가

두 저장소를 생성하고 원격 저장소와 연결. **서브모듈은 2**개 이상인 저장소를 부모와 자식 관계로 연결

**submodule** 명령어는 옵션을 사용하여 다양한 동작을 실행할 수 있습니다. 자세한 옵션은 -help 명령어로 확인합니다.

```
$ git submodule -help
```

### __11.3.1 저장소 연결

메인 저장소에 자식 저장소를 연결합니다. 메인 저장소에 자식 저장소를 추가하는 옵션은 add 명령어입니다.

```
$ cd ../gitstudy11_parent 메인 저장소로 이동
$ git submodule add https://github.com/jinygit/gitstudy11_child.git child 자식 저장소 등록

```

명령어로 목록을 확인

```
$ ls -all 파일 목록
```

### __11.3.2 설정 파일

처음으로 메인 저장소에 서브모듈이 등록되면 **깃은 루트 위치에 설정 파일을 생성**합니다. 설정 파일은 메인 저장소와 연결된 자식 저장소들을 관리합니다. 설정 파일 이름은 .**gitmodules**입니다. 파일 이름이 점(.)으로 시작되기 때문에 숨김 파일 형태로 관리합니다.

```
$ cat .gitmodules 서브모듈 설정 파일
```

### __11.3.3 모듈 커밋

서브모듈 명령을 실행하여 메인 저장소에 자식 저장소를 연결했습니다. 서브모듈이 추가된 부모 저장소의 상태를 확인해 보겠습니다. **status** 명령어를 입력합니다.

```
$ git status 상태 확인
```

메인 저장소에 자식 저장소의 폴더와 환경 설정 파일을 생성했습니다. 메인 저장소와 서브모듈인 자식 저장소 간 관계를 지속적으로 유지하려면 추가된 정보들을 계속 가지고 있어야 합니다. 메인 저장소가 자식들의 정보를 계속 가지려면 이를 커밋하여 저장해야 합니다.

```
$ git add .gitmodules 등록
$ git commit -m "add submodule" 커밋
```

커밋한 후에는 다시 status 명령어로 상태를 확인

```
$ git status 상태 확인
```

사실은 자식들의 서브모듈 환경 설정 파일인 .gitmodules 파일만 등록하여 커밋했습니다. 복제된 자식 저장소는 커밋하지 않았습니다.

## 11.4 서브모듈 작업

메인 저장소에 등록된 서브 저장소는 독립된 별도의 저장 공간

### __11.4.1 모듈 저장소

독립된 자식 저장소에서 새롭게 작업해 봅시다. 먼저 메인 저장소 내용을 확인해 보겠습니다.

```
$ ls 파일 목록
```

메인 저장소에 등록된 서브모듈의 폴더로 이동

```
$ cd child 서브모듈 폴더
```

child는 자식 저장소의 원격 저장소를 복제한 폴더입니다. 서브 폴더 안의 내용을 확인합니다.

```
$ ls -all 서브모듈의 파일 목록

```

child 폴더 안에 또 다른 숨긴 저장소인 .git 폴더가 있습니다. 서브 폴더는 서브모듈로 분리한 독립된 깃 저장소입니다.

### __11.4.2 모듈 상태

모듈로 등록된 자식 저장소를 수정합시다. 메인 저장소의 **child** 폴더에서 **child**.**htm** 파일의 내용을 수정합니다.

```
$ code child.htm VS Code 실행-----서브모듈 폴더
$ git status 서브 폴더 안에서 상태 확인
$ cd .. 상위 메인 저장소로 이동
$ git status 상위 폴더의 상태 확인
```

메인 저장소의 상위 폴더에서는 child 폴더만 변경했다고 출력합니다. child 서브 폴더 안에서는 자식 저장소의 변경된 파일만 추적하고, 상위 메인 저장소에서는 서브모듈의 저장소 자체를 추적합니다.

diff 명령어로 확인

```
$ git diff 커밋 비교
```

### __11.4.3 모듈 커밋

**parent**/**child** 저장소의 내용을 수정했습니다. 자식의 서브 폴더 저장소에서 수정한 내용을 커밋합시다. 먼저 메인 저장소의 **parent**/**child** 폴더로 이동합니다.

```
$ cd child 서브모듈 폴더 이동
$ git commit -am "add content of child" 등록 및 커밋
```

이 커밋은 메인 저장소에서 하위로 복제 생성된 자식 저장소에만 커밋하는 것입니다. 저장소 상태를 다시 확인합니다.

```
$ git status 서브 폴더의 상태 확인
```

커밋으로 메인 저장소 안에 있는 복제된 자식 저장소가 깨끗한 상태입니다. 복제된 자식 저장소에만 커밋했을 뿐, 수정한 내용을 자식의 원격 저장소에는 아직 전송하지 않았습니다. parent/child에는 자식의 원격 저장소보다 앞선 커밋들이 있습니다.

parent/child 폴더에서 원격 저장소 정보를 확인해 봅시다. remote 명령어로 목록을 확인합니다.

```
$ git remote -v  서브 폴더
```

서브모듈을 추가할 때 원격 저장소를 복제합니다. 복제할 때 원격 저장소의 정보들이 자동으로 설정됩니다. parent/child의 원격 저장소로 수정된 커밋을 푸시합니다.

```
$ git push 서브 폴더
$ git status 상태 확인
```

### __11.4.4 부모 커밋

이제 상위 메인 저장소로 이동하여 부모 저장소의 상태를 다시 확인해 보겠습니다.

```
$ cd .. 메인 저장소로 이동
$ git status 상위 폴더의 상태 확인
```

메인 저장소의 parent/child 폴더를 수정한 후 커밋했다면, 메인 저장소의 서브모듈도 변경됩니다. 이 변경 사항을 커밋하여 기록합니다. 메인 저장소를 커밋하고 다시 상태를 살펴봅시다.

```
$ git commit -am "child update" 등록 및 커밋
$ git status 상위 폴더의 상태 확인
```

메인 저장소도 변경된 커밋 때문에 원격 저장소로 미전송된 ahead가 남아 있습니다. 메인 저장소의 원격 저장소 목록을 확인합니다.

```
$ git remote -v 상위 폴더
```

부모 메인 저장소의 원격 저장소 주소가 출력됩니다.

메인 저장소와 서브 저장소에 연결된 원격 저장소 주소는 서로 다릅니다. 각 저장소의 폴더에서 **remote** 명령어로 확인할 수 있습니다.

메인 저장소의 커밋을 전송합니다. 서브모듈은 원격 저장소와 연결되어 있기 때문에 저장소마다 푸시해야 합니다.

```
$ git push 커밋 전송
```

## 11.5 자식 저장소 갱신

지금까지 한 작업은 메인 저장소에 복제된 **parent**/**child** 저장소에서만 작업했습니다. 수정된 **parent**/**child** 저장소의 커밋들은 원격 저장소와 동기화했습니다.

### __11.5.1 자식 저장소

자식 저장소( **gitstudy**11_**child**)와 메인 저장소(**parent**/**child**)에 등록된 저장소는 서로 다른 영역입니다. **gitstudy**11_**child** 저장소는 처음에 생성한 자식 저장소고, 메인 저장소에 등록된 **parent**/**child** 원격 저장소로 동기된 복제본입니다.

따라서 서로 다른 두 저장소는 아직 동일한 커밋 정보를 가지고 있지 않습니다. 자식 저장소에 연결된 원격 저장소를 이용하여 실제 자식 저장소( **gitstudy**11_**child**)를 최신 커밋 정보로 갱신해야 합니다.

### __11.5.2 자식 저장소 갱신

메인 저장소에 등록된 서브모듈(**parent**/**child**)의 커밋들은 자식의 원격 저장소로 푸시되었습니다. 이제는 수정 반영된 커밋들을 실제의 자식 저장소( **gitstudy**11_**child**)로 가져와야 합니다.

```
$ cd ../gitstudy11_child 자식 원본 저장소
$ cat child.htm
```

부모 저장소의 parent/child에서 수정된 내용을 실제 자식 저장소에는 반영하지 않았습니다. 자식 저장소의 원격 저장소를 이용하여 갱신합니다.

```
$ git pull origin master 커밋 내려받기
```

다시 child.htm 파일을 확인하면, 부모 저장소의 parent/child에서 수정한 작업들이 실제 자식 저장소에도 적용되었습니다.

```
$ cat child.htm 확인
```

### __11.5.3 자식 저장소 작업

지금까지는 메인 저장소에서 복제한 자식 저장소(**parent**/**child**)에서 수정 작업을 했습니다. 그리고 수정 내역의 커밋을 자식 저장소의 원격 저장소를 거쳐 실제 자식 저장소에 반영했습니다. 이번에는 반대로 실제 자식 저장소에서 코드를 수정하고, 이를 자식 저장소의 원격 저장소를 거쳐 부모 저장소의 서브모듈(**parent**/**child**)로 적용하는 방법을 알아보겠습니다.

먼저 실제 자식 저장소에서 **child**.**htm** 파일을 수정하고 커밋합니다.

```
$ code child.htm VS Code 실행
$ git commit -am "give me 100 wan" 등록 및 커밋
```

수정된 코드를 자식 저장소의 원격 저장소로 전송

```
$ git push origin master 커밋 전송
```

이제 자식 저장소의 원격 저장소에도 정보가 갱신되었습니다.

### __11.5.4 부모 저장소 적용

실제 자식 저장소에서 변경한 커밋을 메인 저장소의 서브모듈(**parent**/**child**)에 반영해 보겠습니다. 로컬 저장소의 부모 저장소로 이동합니다.

```
$ cd ../gitstudy11_parent 부모 원본 저장소
$ cd child/ 서브모듈 폴더 이동
$ cat child.htm 확인
```

파일 내용은 이전 작업 상태 그대로입니다. 자식 저장소의 원격 저장소에서 최신 정보를 갱신합니다.

```
$ git pull origin master 커밋 내려받기
$ cat child.htm 확인
```

### __11.5.5 부모 저장소 갱신

자식 저장소의 원격 저장소를 이용하여 메인 저장소의 서브모듈을 갱신했습니다.

```
$ git status 상태 확인
```

서브모듈을 갱신하면 메인 저장소는 자신의 서브 폴더가 변경된 것을 인식합니다.

부모 폴더로 이동해서 상태를 확인해 보겠습니다.

```
$ cd .. 메인 저장소 이동
$ git status 상태 확인
```

즉, 메인 저장소는 서브모듈의 변경 내용을 모니터링하고 있는 것입니다. 메인 저장소의 서브 폴더 자체를 변경했기 때문에 변경된 내용을 다시 메인 저장소로 커밋해야 합니다.

```
$ git commit -am "update submodule" 등록 및 커밋
```

## 11.6 부모 저장소 복제

서브모듈로 구성된 저장소는 부모/자식 관계를 맺습니다. 서브모듈의 저장소를 복제하거나 배포할 때는 부모/자식 관계도 같이 복제해야 합니다.

### __11.6.1 부모 저장소 복제

```
$ cd 실습폴더
$ git clone https://github.com/jinygit/gitstudy11_parent.git gitstudy11 복제
```

gitstudy11은 부모/자식 관계인 서브모듈 형태로 되어 있습니다. 현재는 메인 저장소만 복제했습니다.

```
$ cd gitstudy11
$ ls -all 파일 목록
```

서브모듈에 대한 .gitmodules 설정 파일을 확인할 수 있습니다. 그리고 서브모듈인 child 폴더로 이동합니다.

```
$ cd child 서브모듈 폴더 이동
$ ls -all 파일 목록
```

서브모듈의 폴더 안에는 아무 내용도 없습니다.

### __11.6.2 모듈 업데이트

메인 저장소를 복제할 때는 서브모듈 정보만 같이 복제할 뿐, 실제 하위 저장소는 같이 복제하지 않습니다. 서브모듈의 하위 저장소는 직접 명령어를 실행하여 가져와야 합니다. 하위 저장소의 내용을 가져오려면 먼저 초기화와 갱신 작업을 해야 합니다.

```
$ cd .. 메인 저장소
$ git submodule init 서브모듈 초기화
$ git submodule update 서브모듈 업데이트
```

서브모듈 update 옵션으로 관련 하위 저장소를 복제합니다.
서브모듈 초기화와 업데이트를 진행했습니다. 다시 폴더 내용을 확인해 봅시다.

```
서브모듈 child 폴더에 복제한 하위 저장소 내용이 추가되었습니다.

깃 배시에서 서브 저장소의 브랜치 이름을 주의 깊게 살펴보세요. 브랜치 이름이 master가 아닌 a7709f5...로 되어 있습니다. 서브모듈을 업데이트할 때는 메인 저장소의 비어 있는 서브모듈 커밋 위치를 리모트 체크아웃합니다.
$ cd child 서브모듈 폴더 이동
$ ls -all 파일 목록
```

## 11.7 부모 저장소 업데이트

메인 저장소는 서브모듈 형태로 구성되어 있습니다. 부모 저장소도 별도로 관리하므로 갱신이 필요합니다.

### __11.7.1 부모 업데이트

서브모듈 형태로 구성된 부모/자식 저장소도 커밋을 갱신합니다. 새로운 하위 저장소를 추가하거나 하위 저장소를 갱신할 때 메인 저장소의 설정 파일과 폴더가 변경되기 때문입니다. 따라서 자식 저장소에 코드 수정으로 커밋이 발생하면, 부모에도 자연스럽게 새로운 커밋이 발생합니다. 갱신된 메인 저장소 내용을 정기적으로 갱신하여 서브모듈 상태를 최신으로 유지해야 합니다.

### __11.7.2 부모 저장소로 풀

하위 저장소에 새로운 커밋이 생성되면 메인 저장소는 이를 반영합니다. 메인 저장소에는 반영한 하위 저장소의 변경된 내용 때문에 추가 커밋이 발생합니다. 자신이 메인 저장소를 복제하여 운영하고 있다면, 메인 저장소를 주기적으로 풀**(**pull**)** 작업해 주어야 합니다.

하지만 부모 저장소를 풀했다고 해서 부모 저장소에 종속된 모든 서브 저장소까지 자동으로 갱신되지는 않습니다. 다음과 같이 서브모듈의 업데이트는 별도로 명령어를 실행해 주어야 합니다.

```
$ git pull origin master
$ git submodule update
```

## 11.8 정리

서브모듈은 큰 프로젝트를 쪼개서 작은 프로젝트로 만들고, 저장소 크기를 줄여 가볍게 저장소를 운영할 수도 있습니다. 서브모듈 형태로 코드를 분리하면 다른 프로젝트에서도 모듈을 재사용할 수 있는 장점이 있습니다. 또 각 모듈을 원격 저장소와 연결해서 협업하여 개발을 진행할 수도 있습니다.

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

## 12.8 정리

> * git pull ☜ 변경 내용 추가
> * git fetch RemoteURL
> * git clone https://github.com/onespace10/onespace10.git .
> * git branch -u Newbranch ☜ 생성
> * git checkout -b Newbranch origin/Newbranch ☜ origin/Newbranch 기반하여  local Newbranch생성 후 이동
> * git log --graph --all
> * git merge origin/branch
> * git push origin Currentbranch:Newbranch ☜ Local Currentbranch TO Remote Newbranch
>   ** git push -u origin main ☜ origin이라는 원격 저장소의 master 브랜치와 로컬의 main 브랜치의 관계가 설정됨. 다음부턴 git push만 사용 가능.
> * git remote add origin https://github.com/onespace10/onespace10.git
