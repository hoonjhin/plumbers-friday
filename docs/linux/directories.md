# 디렉토리

디렉토리라는 말이 어떤 사람에게는 어색한 시대가 되었습니다.
디렉토리는 파일이 수록되는 논리적으로 구분된 공간입니다.
디렉토리는 파일을 담고 있고, 다른 디렉토리를 담을 수 있습니다.
그래서 디렉토리 아래에 디렉토리 아래에 디렉토리를 만들 수 있어 계층구조가 형성됩니다.
최상위 디렉토리는 루트 디렉토리(root directory)라고 부르며, / (슬래시) 로 표기합니다.

## 기본 사항

### 루트 디렉토리

최상위 디렉토리를 루트 디렉트로 root directory라고 부릅니다. 표기는 앞서 이야기 한 것과 같이
/ 라고 적고, 슬래시 slash라고 읽습니다.

/ 는 디렉토리의 시작을 의미합니다.
앞서 설명한 것과 같이 root directory는 / 로 표기되며
root directory 아래에 위치하는 디렉토리는 /usr 과 같이 표기할 수 있습니다.
만약 /usr 아래에 또 다른 디렉토리, bin 이 존재한다면, /usr/bin 이렇게 표기할 수 있습니다.

### 현재 디렉토리와 상위 디렉토리

디렉토리를 표기하거나 기능적으로 지칭하는 방식 중에 . 과 .. 이 있습니다.
. 은 현재 디렉토리를 의미하고 .. 은 상위 디렉토리를 의미합니다.
아래의 예제를 보겠습니다.

```bash
$ pwd
/usr/local
$ ls -al
total 0
drwxr-xr-x 1 root root 512 Feb  8 01:57 .
drwxr-xr-x 1 root root 512 Feb  8 01:57 ..
drwxr-xr-x 1 root root 512 Feb  8 01:57 bin
drwxr-xr-x 1 root root 512 Feb  8 01:57 etc
drwxr-xr-x 1 root root 512 Feb  8 01:57 games
drwxr-xr-x 1 root root 512 Feb  8 01:57 include
drwxr-xr-x 1 root root 512 Feb 16 23:00 lib
lrwxrwxrwx 1 root root   9 Feb  8 01:57 man -> share/man
drwxr-xr-x 1 root root 512 Feb  8 01:57 sbin
drwxr-xr-x 1 root root 512 Feb 15 02:13 share
drwxr-xr-x 1 root root 512 Feb  8 01:57 src
$
```

/usr/local 디렉토리에서 `ls -al` 명령을 수행한 결과입니다.
그 중 . 과 .. 이 보일 것입니다. 모든 디렉토리에서 . 와 .. 은 조회됩니다.

### 홈 디렉토리

사용자의 공간을 home directory 홈 디렉토리 라고 합니다.
변수로는 $HOME 이라고 정의합니다.
사용자의 홈 디렉토리의 위치는 `/etc/passwd` 파일에 정의됩니다.  
`$ cat /etc/passwd | grep $USER`로 현재 사용자의
설정을 확인해 봅니다. 그리고,
`echo $HOME`이라고 명령 내려봅니다. 출력되는 결과가 지금 로그인한
사용자의 홈 디렉토리입니다.

홈 디렉토리로 이동하는 방법이 몇 가지 있습니다.

1. 직접 자신의 홈 디렉토리를 입력한다.  
  `cd /home/ubuntu`
2. 환경 변수를 활용한다.  
  `cd $HOME`
3. 다음과 같이 간단히 한다.  
  `cd ~`

UNIX/Linux에서 `~`는 사용자의 홈 디렉토리를 뜻 합니다.

### 상대경로와 절대경로

디렉토리의 위치에 접근하는 방식을 경로라고 하거나, 디렉토리의 위치 자체를 경로라고
설명하는 사람도 있습니다. 실제 우리가 사용하는 '경로'라는 단어는 經路라는 것으로
'지나는 길'이라는 뜻을 담고 있습니다.

UNIX/Linux에는 `$PATH`라는 변수가 있고, `$PATH`는 디렉토리의 위치를 지시합니다.
이 PATH를 번한문서에서는 '경로'라고 번역한 것으로 보입니다. 다음의 예제를 보겠습니다.

```bash
$ pwd
/home/pi
$ ls -al ../../usr/local
total 40
drwxr-xr-x 10 root root 4096 Jan 11 12:50 .
drwxr-xr-x 11 root root 4096 Jan 11 12:58 ..
drwxr-xr-x  2 root root 4096 Jan 11 12:50 bin
drwxr-xr-x  2 root root 4096 Jan 11 12:50 etc
drwxr-xr-x  2 root root 4096 Jan 11 12:50 games
drwxr-xr-x  2 root root 4096 Jan 11 12:50 include
drwxr-xr-x  5 root root 4096 Jan 11 13:00 lib
lrwxrwxrwx  1 root root    9 Jan 11 12:50 man -> share/man
drwxr-xr-x  2 root root 4096 Jan 11 12:50 sbin
drwxr-xr-x  7 root root 4096 Jan 11 13:00 share
drwxr-xr-x  2 root root 4096 Jan 11 12:50 src
$ ls -al /usr/local
total 40
drwxr-xr-x 10 root root 4096 Jan 11 12:50 .
drwxr-xr-x 11 root root 4096 Jan 11 12:58 ..
drwxr-xr-x  2 root root 4096 Jan 11 12:50 bin
drwxr-xr-x  2 root root 4096 Jan 11 12:50 etc
drwxr-xr-x  2 root root 4096 Jan 11 12:50 games
drwxr-xr-x  2 root root 4096 Jan 11 12:50 include
drwxr-xr-x  5 root root 4096 Jan 11 13:00 lib
lrwxrwxrwx  1 root root    9 Jan 11 12:50 man -> share/man
drwxr-xr-x  2 root root 4096 Jan 11 12:50 sbin
drwxr-xr-x  7 root root 4096 Jan 11 13:00 share
drwxr-xr-x  2 root root 4096 Jan 11 12:50 src
$
```

## 관련 명령어들

### cd - change directory

명령어 중에, `cd`가 있습니다.
디렉토리를 변경할 때 사용합니다. 용례는, `cd /var/log`와 같이
목적하는 디렉토리로 변경할 수 있습니다. `cd` 명령 뒤에 아무런
선언이 오지 않으면, 사용자의 홈 디렉토리로 이동합니다.

`cd ..`라고 명령하면 상위 디렉토리로 이동하게 되며, `ls ./example`라는 명령은 '현재 디렉토리에 위치한 example이라는 파일(혹은 디렉토리)를 조회하라'가 됩니다. 응용하면, `ls ../example2`라는 명령은 '상위 디렉토리에 위치한 example2라는 파일(혹은 디렉토리)를 조회하라'가 됩니다.

### pwd - return working directory name

현재 사용자가 위치한 디렉토리를 화면에 출력해 줍니다.

```bash
$ pwd
/usr/local/lib
$
```

### mkdir, rmdir

`mkdir`은 디렉토리를 생성하는데 사용됩니다. make directory.
`rmdir`은 디렉토리를 삭제하는데 사용됩니다. remove directory.
