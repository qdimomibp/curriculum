# Shell Script
이번 시간에는 Bash 쉘 스크립트 작성을 다룹니다.

원리는 단순합니다.
터미널에서 사용하는 명령어의 각줄을 파일로 저장하면 순차적으로 실행되는 Shell Script가 됩니다.

## Hello World

test.sh
```bash
#!/bin/sh
echo `Hello World`
```

맨 윗줄 `#!/bin/sh` 문장은 이 스크립트를 실행할 기본 명령어를 지정하는 줄입니다. 우리는 Shell Script를 작성하기 때문에 `/bin/sh` 명령어가 이 스크립트를 실행하도록 선언하였습니다.

chmod 명령을 이용해서 실행권을 주고, 실행은 아래처럼 할 수 있습니다.
```
$ chmod 755 test.sh
$ ./test.sh
```

## 변수 선언

```
#!/bin/sh
VAR="Hello World"
echo $VAR
```

## 사용자 값 받기
```
#!/bin/sh
echo What is your name?
read MY_NAME
echo "Hello $MY_NAME"
```

## 인수처리
argv.sh

```bash
#!/bin/sh
echo $1
echo $2
```

## 경로체크
우리는 지난시간에 뉴크를 $HOME 경로에 설치했습니다.
bash 스크립트를 통해서 뉴크가 설치되어있는지 체크하는 방법은 아래와 같습니다.

```bash
if [ -d "$HOME/Nuke11.2v5" ]; then
    echo "뉴크가 설치되어있습니다."
fi
```

## 파일체크
~/test.py 파일이 존재하는지 체크하는 방법

```bash
if [ -f "$HOME/test.py" ]; then
    echo "홈디렉토리에 test.py 파일이 존재합니다."
fi
```

파일이 존재하지 않는 것을 체크하고 싶을 때는 `!`문자를 사용합니다.

```bash
if [ ! -f "$HOME/test.py" ]; then
    echo "홈디렉토리에 test.py 파일이 존재하지 않습니다."
fi
```

위 형태의 코드를 통해서 "무언가가 설치되어있지 않다면 설치해라!" 형태의 쉘 스크립트를 제작할 수 있습니다.

## Reference
- http://www.compciv.org/recipes/cli/basic-shell-scripts/