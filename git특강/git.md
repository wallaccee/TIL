# Git

> Git은 분산형 버전관리시스템(DVCS) 중 하나이다. 

## Git 사전준비

> git을 사용하기 전에 커밋을 남기는 사람에 대한 정보를 설정(최초) 
>
> ```bash
> $ git config --global user.name 'chaehyeonlim'
> $ git config --global user.email '{covoco2345@gmail.com}'
> ```

* 추후에 commit을 하면, 작성한 사람(aurthor)으로 저장된다.
* email 정보는 github에 등록된 이메일로 설정을 하는 것을 추천(잔디밭)
* 설정 내용을 확인하기 위해서는 아래의 명령어를 입력한다.

```bash
$ git config --global -l
user.name=chaehyeonlim
user.email=covoco2345@gmail.com
```

> git bash 설치 [링크](https://gitforwindows.org/) 

# 기초 흐름

> 작업 -> add -> commit

## 0.저장소 설정

```bash
$ git init
Initialized empty Git repository in C:/Users/user/Desktop/test2/.git/
```

* git 저장소를 만들게 되면 해당 디렉토리 내에 `.git/` 폴더가 생성
* git bash 에서는 `(master)`로 현재 작업중인 브랜치가 표기된다.

##  1.`add`

> 커밋을 위한 파일 목록(staging area)

```bash
$ git add.			# 현재 디렉토리의 모든 파일 및 폴더
$ git add a.txt		# 특정 파일
$ git add md-images/#특정 폴더
$ git status
# master 브랜치에 있다.
On branch master	

No commits yet
# 커밋이 될 변경사항들(changes)
# staging area 단계
Changes to be committed:
  # unstage를 하기 위해서...명령어
  # working directory 단계 
  (use "git rm --cached <file>..." to unstage)
        new file:   a.txt
# 트래킹 X 파일들
# git으로 아직 관리를 X
Untracked files:
   # 커밋이 될 것에 추가하려면.....
   # staging area에 보내려면, add 명령어 입력!!!
  (use "git add <file>..." to include in what will be committed)
        b,txt

```

## 2.`commit`

> 버전을 기록(스냅샷)

```bash
$ git commit -m '커밋 메세지'
[master (root-commit) 3e17c58] First commit
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 a.txt
 create mode 100644 b,txt
```

* 커밋 메세지는 현재 버전을 알 수 있도록 명확하게 작성한다.
* 커밋 이력을 남기기 확인하기 위해서는 아래의 명령어를 입력한다.

```bash
$ git log
commit 3e17c587a31b33d3b50744a118d2790be4965e84 (HEAD -> master)
Author: chaehyeonlim <covoco2345@gmail.com>
Date:   Thu Sep 17 13:25:41 2020 +0900

    First commit
$ git log -1 	# 최근 한개의 버전
$ git log --oneline	#한줄로 간단하게 표현
3e17c58 (HEAD -> master) First commit
$ git log -1 --oneline
```

## status - 상태 확인

> git 에 대한 모든 정보는 status를 통해 확인 할 수 있다

```bash
$ git status
```

## 원격 저장소 활용하기

> 원격 저장소를 제공하는 서비스는 github, gitlab, bitbucket 등이 있다.

### 1. 원격 저장소 설정하기

```bash
$ git remote add origin {URL}
```

* 깃아, 원격(remote)저장소로 추가해줘(add) origin이라는 이름으로 URL을 //외우기..ㅋ

### 2.원격 저장소 확인하기

```bash
$ git remote -v
origin  https://github.com/chaehyeonlim/git-test.git (fetch)
origin  https://github.com/chaehyeonlim/git-test.git (push)
```

### 3.push

```bash
$ git push origin master
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Delta compression using up to 4 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 217 bytes | 217.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/chaehyeonlim/git-test.git
 * [new branch]      master -> master
```

* origin 원격저장소의 master branch

 ** 로컬 과 git 차이점

-> add, commit를 해준것만 push를 통해 github에 올라간다 //최신의 버전들만 올라가짐