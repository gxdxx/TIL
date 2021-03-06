# **리눅스**

intel과 amd에서 나오는 CPU에서 동작하도록 나온 유닉스이다.

---

## **유닉스의 설계 철학**

- 단순성
- 이식성
- 개방성

---

## **유닉스의 특징**

- 다중 사용자, 다중 프로세스
- 쉘 프로그래밍 지원
  - 명령어나 유틸리티 등을 사용하여 작성한 프로그램
- 훌륭한 네트워킹 지원
  - ftp, telnet, WWW 등

---

## **유닉스 운영체제 구조**

- 운영체제
  - 컴퓨터의 하드웨어 자원을 운영 관리한다.
  - 프로그램을 실행할 수 있는 환경을 제공한다.
- **커널(kernel)**
  - 운영체제의 핵심으로 하드웨어 운영 및 관리를 한다.
    - 프로세스, 메모리, 파일, 주변장치, 통신 등
- **시스템 호출(system call)**
  - 커널이 제공하는 서비스에 대한 프로그래밍 인터페이스 역할을 한다.
- **쉘(shell)**

  - 사용자와 운영체제(커널) 사이의 인터페이스 역할을 한다.
  - 사용자로부터 명령어를 입력 받아 해석하여 수행해주는 명령어 해석기이다.
  - 배시쉘(Bash Shell)

  <br/>

  <img width="300" alt="1_1" src="https://user-images.githubusercontent.com/35963403/132097543-a0a25403-a796-4aa6-9041-f826fd5f3233.PNG">

---

## **커널의 역할**

- 프로세스 관리(Process Management)
  - 여러 프로그램이 실행될 수 있는 환경을 제공한다.
  - CPU 스케줄링을 통해 여러 프로세스들이 동시에 수행되도록 한다.
- 메모리 관리(Memory Management)
  - 메인 메모리가 효과적으로 사용될 수 있도록 관리한다.
  - 가상 메모리 관리 및 메모리 교체 정책을 실행한다.
- 파일 관리(File Management)
  - 저장장치(HDD, SSD)에 파일 시스템을 구성하여 파일을 관리한다.
- 주변장치 관리(Device Management)
  - 모니터, 키보드, 마우스와 같은 장치를 사용할 수 있도록 관리한다.
- 통신 관리(Communication Management)
  - 네트워크를 통해 정보를 주고받을 수 있도록 관리한다.

---

## **리눅스 장점**

- 풍부하고 다양한 하드웨어를 효과적으로 지원한다.
- 저렴한 성능 요구 사양 및 안정성
- 인터넷에 맞는 강력한 네트워크 구축
- 다양한 응용 프로그램이 개발돼있다.
- 다양한 배포판이 있다.
  - 레드햇, 우분투, 페도라, CentOS 등
- 안드로이드: 리눅스를 기반으로 한다.

---

## **원격 로그인**

### 텔넷

- 보안상의 이유로 사용되지 않는다.
- 주고받는 패킷에 담긴 데이터들이 암호화 되어 있지 않아서 노출이 된다.

### PuTTY

- ssh(secure shell)을 이용해서 원격 로그인한다.
- 패킷이 암호화 되어서 노출 위험이 없다.

---

## **시스템 관리자**

### 슈퍼유저

- 시스템을 관리할 수 있는 사용자이다.
- root 계정을 사용한다.

### 슈퍼유저 로그인

- 직접 root 계정으로 로그인
  - 보안상 취약
- 다른 계정으로 로그인 후
  ```javascript
  $ su [사용자명]     // substitute user
  ```
  - 사용자 명을 주지 않으면 root로 로그인된다.

---

## **사용자 계정 추가**

### 사용자 추가/삭제

```javscript
# useradd [옵션] 사용자명
# userdel [-r] 사용자명     // -r: 사용자 홈디렉토리 파일 삭제
# passwd  사용자명
```

---

## **그룹 추가**

- 유닉스/리눅스에서 사용자는 하나 이상의 그룹에 속한다.
- 그룹 추가/삭제
  ```javascript
  # groupadd [-g gid] 그룹명
  # groupdel 그룹명
  ```

<br/>

# **리눅스 사용**

## **기본 명령어**

### 날짜 및 시간 확인

```javascript
$ date
```

### 호스트 이름 확인 (시스템 관리자가 부여한 이름)

```javascript
$ hostname
```

### 운영체제 확인 (설치된 운영체제 이름)

```javascript
$ uname
```

### 로그인 한 사용자 확인 (다중)

```javascript
$ who
```

### 로그인 한 사용자 확인

```javascript
$ whoami
```

### 현재 디렉토리 내부의 파일 목록 확인

```javascript
$ ls
```

### 화면을 정리하고 첫째줄에 프롬프트 표시

```javascript
$ clear
```

### 암호 변경

```javascript
$ passwd
```

### 온라인 매뉴얼

- 뒤에 명령어를 입력하면 명령어에 대한 설명을 알려준다.

```javascript
$ man
```

### 명령어에 대한 간단한 설명

```javascript
$ whatis
```

### all 옵션

```javascript
-a;
```

---

## **파일의 종류**

- 일반 파일(ordinary file)
  - **데이터를 가지고 있다.**
  - 디스크에 저장된다.
- 디렉토리 파일(directory file)
  - **자신이 가지고 있는 내부 디렉토리 또는 파일을 가지고 있다.**
  - 폴더(folder)와 같다.
  - 디렉토리(폴더) 자체도 하나의 파일이다.
  - 한 디렉토리는 다른 디렉토리를 포함함으로써 계층 구조를 이룬다.
- 특수 파일(special file)
  - 물리적인 장치(device)에 대한 내부적인 표현이다.
  - 키보드(stdin), 모니터(stdout), 프린터 등도 파일처럼 사용한다.
    - ex) 프린터 출력 -> 프린터 파일에 대한 쓰기 연산 수행

---

## **디렉토리 계층구조**

- ### 리눅스 디렉토리

  - 루트로부터 시작한다.
  - Tree 형태의 계층구조를 이룬다.
  - 루트가 한 개만 있다.

  <img width="500" alt="2_1" src="https://user-images.githubusercontent.com/35963403/134766060-3ed19a6b-8bb1-42ac-a8d2-0986d486bab5.PNG">

---

## **홈 디렉토리 / 현재 작업 디렉토리**

- 홈 디렉토리(home directory)
  - 각 사용자마다 별도의 홈 디렉토리가 있다.
  - 사용자가 로그인하면 홈 디렉토리에서 작업을 시작한다.
- 현재 작업 디렉토리(current working directory)
  - 현재 작업 중인 디렉토리이다.

---

## **경로명**

- 파일이나 디렉토리에 대한 **정확한 이름**
- 절대 경로명 (absoulte path name)
  - **루트 디렉토리로부터 시작**하여 경로 이름을 정확하게 적는 것이다.
- 상대 경로명 (relative path name)
  - **현재 작업 디렉토리로부터 시작**해서 경로 이름을 적는 것이다.

---

## **파일명 개수**

```javascript
$ 명령어 파일명
$ 명령어 파일명*      // 0개 혹은 그 이상
$ 명령어 파일명+      // 1개 혹은 그 이상
```

---

## **디렉토리 관련 명령**

### **pwd (print working directory)**

- 현재 작업 디렉토리의 **절대 경로명**을 출력한다.

```javascript
$ pwd
```

---

### **cd (change directory)**

- 현재 작업 디렉토리를 지정된 디렉토리로 이동한다.
- 디렉토리를 지정하지 않으면 홈 디렉토리로 이동한다.
- **$ cd ~** : 홈 디렉토리로 이동한다.

```javascript
$ cd [디렉토리]
```

---

### **which**

- 명령어의 절대 경로를 보여준다.

```javascript
$ which 명령어
```

---

### **mkdir (make directory)**

- 새 디렉토리를 생성한다.
- -p: 중간 디렉토리 자동 생성 옵션
  - ex) ~/dest 디렉토리가 없는 경우

```javascript
$ mkdir ~/dest/dir1
mkdir: '/home/chang/dest/dir1' 디렉토리를 만들 수 없습니다: 그런 파일이나 디렉토리가 없습니다.

$ mkdir -p ~/dest/dir1  // 가능
```

```javascript
$ mkdir [-p] 디렉토리
```

---

### **rmdir (remove directory)**

- 디렉토리를 삭제한다.
- **빈 디렉토리만 삭제할 수 있다.**

```javascript
$ rmdir 디렉토리
```

---

### **ls (list)**

- 디렉토리의 내용을 리스트로 보여준다.

```javascript
$ ls
$ ls -a     //  -a(all): 숨김 파일 표기
$ ls -s     //  -s(size): 크기 표기
$ ls -l     //  -l(long): 자세한 정보(파일 속성) 표기
$ ls -F     //  파일 종류 표기(*: 실행파일, /: 디렉토리, @: 심볼릭 링크)
$ ls -R     //  -R(Recursive): 모든 하위 디렉토리 표기, 재귀적으로 실행된다.
$ ls -asl   //  -a, -s, -l을 결합
```

---

### **cat (concatenate)**

- 파일(들)의 내용을 그대로 화면에 출력한다.
- 파일을 지정하지 않으면 표준입력 내용을 그대로 화면에 출력한다.
- -n을 입력하면 줄번호가 나타난다.

```javascript
$ cat [-n] 파일*
```

**파일 읽기**

```javascript
$ cat cs1.txt
```

**파일 결합**

```javascript
$ cat cs1.txt cs2.txt
```

**파일 편집**

```javascript
$ cat     //  키보드로부터 입력받아 그대로 출력
...
^D        //  (ctrl-D: 입력의 끝을 나타냄)
```

```javascript
$ cat > cs1.txt     //  키보드로부터 입력받은 내용을 파일로 저장 (파일 라인 단위 편집)
...
^D
```

```javascript
$ cat cs1.txt cs2.txt > cs3.txt     //  파일 결합하고 저장
```

---

### **more**

- 파일(들)의 내용을 페이지 단위로 화면에 출력한다.

```javascript
$ more 파일+
```

---

### **head**

- 파일(들)의 앞부분을 화면에 출력한다.
- 파일을 지정하지 않으면 표준입력 내용을 대상으로 한다.
- -n으로 보고싶은 라인 수를 지정할 수 있다.
  - 기본적으로 처음 10줄을 출력한다.

```javascript
$ head [-n] 파일*

ex) $ head -5 cs1.txt
```

---

### **tail**

- 파일(들)의 뒷부분을 화면에 출력한다.
- 파일을 지정하지 않으면 표준입력 내용을 대상으로 한다.
- -n으로 보고싶은 라인 수를 지정할 수 있다.
  - 기본적으로 마지막 10줄을 출력한다.

```javascript
$ tail [-n] 파일*

ex) $ tail cs1.txt
```

---

### **wc (word count)**

- 파일에 저장된 줄(l), 단어(w), 문자(c)의 개수를 세서 출력한다.
- 파일을 지정하지 않으면 표준입력 내용을 대상으로 한다.

```javascript
$ wc [-lwc] 파일*

ex)
$ wc cs1.txt
38 218 2088 cs1.txt
$ wc -l cs1.txt
38 -l cs1.txt
$ wc -w cs1.txt
218 -w cs1.txt
$ wc -c cs1.txt
2088 cs1.txt
```

---

### **cp (copy)**

- 파일1의 복사본 파일2를 현재 디렉토리 내에 생성(복사)한다.
- 복사 대상 파일과 이름이 같은 파일이 이미 존재하면 덮어쓰기한다(overwrite).
  - -i (interactive) 대화형 옵션으로 덮어쓰기 전 확인할 수 있다.

```javascript
$ cp [-i] 파일1 파일2

ex) $ cp cs1.txt cs2.txt
```

**파일(들)의 복사본을 디렉토리 내에 생성한다.**

```javascript
$ cp 파일(들) 디렉토리

ex) $ cp cs1.txt /tmp
```

**디렉토리1을 디렉토리2로 복사한다.**

- **디렉토리1의 하위 파일도 모두 복사된다.**

```javascript
$ cp -r 디렉토리1 디렉토리2
```

---

### **mv (move)**

- 파일1의 이름을 파일2로 변경한다.
- rename의 개념이다.
- -i는 대화형 옵션이다.

```javascript
$ mv [-i] 파일1 파일2
```

**파일을 디렉토리 내로 이동한다.**

```javascript
$ mv cs3.txt /tmp
```

**디렉토리1을 지정된 디렉토리2로 이름을 변경한다.**

- **디렉토리도 파일이기 때문에 파일에 작업 가능한 명령어는 디렉토리에서도 가능하다.**

```javascript
$ mv 디렉토리1 디렉토리2
```

---

### **rm (remove)**

- 파일(들)을 삭제한다.
- -i는 대화형 옵션이다.

```javascript
$ rm [-i] 파일+
```

**디렉토리를 전체 삭제한다.**

- -r은 리커젼 옵션으로 디렉토리 아래의 모든 것을 삭제한다.

```javascript
$ rm [-ri] 디렉토리
```

- -i: 확인 후 삭제 (interactive)
- -f: 무조건 삭제 (force)
- -r: 디렉토리 삭제 (recursion)

<br/>

# **파일 속성**

## **파일 속성 (file attribute)**

| 파일 속성      | 의미                                                                                      |
| :------------- | :---------------------------------------------------------------------------------------- |
| 블록 수        | 파일의 블록 수                                                                            |
| 파일 타입      | 일반 파일(-), 디렉토리(d), 링크(l), 파이프(p), 소켓(s), 디바이스(b 혹은 c) 등의 파일 종류 |
| 사용권한       | 소유자, 그룹, 기타 사용자의 파일에 대한 읽기/쓰기/실행 권한                               |
| 소유자 및 그룹 | 파일의 소유자 및 소유자가 속한 그룹                                                       |
| 크기           | 파일을 구성하는 블록 수 (블록의 실제 크기)                                                |
| 수정 시간      | 파일을 최후로 생성 혹은 수정한 시간                                                       |

---

</br>

## **파일 종류**

| 파일 종류      | 표시 | 설명                                                    |
| :------------- | :--- | :------------------------------------------------------ |
| 일반 파일      | -    | 데이터를 갖고 있는 텍스트 파일 또는 이진 파일           |
| 디렉토리 파일  | d    | 디렉토리 내의 파일들의 이름과 파일 정보를 관리하는 파일 |
| 문자 장치 파일 | c    | 문자 단위로 데이터를 전송하는 장치를 나타내는 파일      |
| 블록 장치 파일 | b    | 블록 단위로 데이터를 전송하는 장치를 나타내는 파일      |
| FIFO 파일      | p    | 프로세스 간 통신에 사용되는 파일                        |
| 소켓           | s    | 네트워크를 통한 프로세스 간 통신에 사용되는 파일        |
| 심볼릭 링크    | l    | 다른 파일을 가리키는 포인터와 같은 역할을 하는 파일     |

- 파일의 종류에 대한 자세한 정보를 출력한다.

```javascript
$ file 파일
```

---

## **사용 권한 (permission mode)**

- 다중 사용자 시스템이다.
- 읽기(r), 쓰기(w), 실행(x) 권한이 있다.
- 접근 권한과 의미가 같다.

| 권한 | 파일                  | 디렉터리                                            |
| :--- | :-------------------- | :-------------------------------------------------- |
| r    | 파일에 대한 읽기 권한 | 디렉터리 내에 파일명을 읽을 수 있는 권한            |
| w    | 파일에 대한 쓰기 권한 | 디렉터리 내에 파일을 생성하거나 삭제할 수 있는 권한 |
| x    | 파일에 대한 실행 권한 | 디렉터리 내로 탐색을 위해 이동할 수 있는 권한       |

- 파일의 사용권한은 소유자(owner)/그룹(group)/기타(others)로 구분하여 관리한다.
  - ex) 소유자: rw-, 그룹: r--, 기타: r--

---

## **접근 권한의 예**

| 접근 권한 | 의미                                                                   |
| :-------- | :--------------------------------------------------------------------- |
| rwxrwxrwx | 소유자, 그룹, 기타 사용자 모두 읽기, 쓰기, 실행 가능                   |
| rwxr-xr-x | 소유자만 읽기, 쓰기, 실행 가능하고 그룹, 기타 사용자는 읽기, 실행 가능 |
| rw-rw-r-- | 소유자와 그룹만 읽기, 쓰기 가능하고 기타 사용자는 읽기만 가능          |
| rw-r--r-- | 소유자만 읽기, 쓰기 가능하고 그룹과 기타 사용자는 읽기만 가능          |
| rw-r----- | 소유자만 읽기, 쓰기 가능하고 그룹은 읽기만 가능                        |
| rwx------ | 소유자만 읽기, 쓰기, 실행 가능                                         |

---

### **chmod (change mode)**

- 파일 혹은 디렉터리의 사용 권한을 변경하는 명령어이다.
- -R 옵션은 디렉터리 내의 모든 파일 및 하위 디렉터리에 대해서도 이 명령어를 적용한다는 의미이다.

```javascript
$ chmod [-R] 사용권한 파일
```

---

**8진수를 이용한 접근권한 변경**

|                         |             |
| :---------------------- | :---------- |
| 사용권한                | rw- rw- r-- |
| 2진수                   | 110 110 100 |
| 8진수                   | 6 6 4       |
| ex) $ chmod 664 cs1.txt |

---

**기호를 이용한 접근권한 변경**

| 사용자범위       | 연산자      | 권한         |
| :--------------- | :---------- | :----------- |
| [u / g / o / a]+ | [+ / - / =] | [r / w / x]+ |

| 구분        | 기호와 의미                         |
| :---------- | :---------------------------------- |
| 사용자 범위 | u(user), g(group), o(other), a(all) |
| 연산자      | +(추가), -(제거), =(지정)           |
| 권한        | r(읽기), w(쓰기), x(실행)           |

- ex) $ chmod g+w cs1.txt
  - 그룹에 쓰기 권한을 부여
- ex) $ chmod g+w, o+rw cs1.txt
  - 그룹에 쓰기 권한 부여하고 기타에 읽기, 쓰기 권한 부여

---

### **umask (기본 권한 설정)**

- 새로운 파일이 만들어질 때 적용되는 기본 권한이다.
- 마스크 값을 지정하지 않으면 현재의 마스크 값을 보여준다.
  - 마스크 값이란 세팅된 권한 값이다.
- **사용권한에서 허용하지 않을 값을 지정한다.**
  - chmod와 반대이다.

| 파일                                  | 기본 접근 허가권  |
| :------------------------------------ | :---------------- |
| 실행할 수 없는 일반 파일 (.txt)       | 666 (rw- rw- rw-) |
| 실행할 수 있는 일반 파일 (.exe, .out) | 777 (rwx rwx rwx) |
| 디렉터리                              | 777 (rwx rwx rwx) |

권한 설정 방법

1. 최대권한 rw- rw- rw- 666
2. 마스크값 --- -w- -w- 022
3. 뺄셈결과 rw- r-- r-- 644

| 마스크 값 | 실행할 수 없는 일반 파일 | 실행할 수 있는 일반 파일 | 디렉터리 | 의미                                                  |
| :-------- | :----------------------- | :----------------------- | :------- | ----------------------------------------------------- |
| 022       | 644                      | 755                      | 755      | 소유자는 모두 할 수 있고 그 이외의 사용자는 쓰기 금지 |
| 077       | 666 - 077 => 600 (예외)  | 700                      | 700      | 소유자 이외는 파일 접근 금지                          |

---

### **chown (change owner)**

- 파일이나 디렉터리 소유자를 변경할 때 사용한다.
- 파일의 소유자 또는 슈퍼 유저만이 사용 가능하다.
- -R 옵션: 디렉터리 아래의 모든 파일과 하위 디렉터리에 대해서도 소유자를 변경한다.

```javascript
$ chown 사용자 파일
$ chown [-R] 사용자 디렉터리
```

### **chgrp (change group)**

- 파일이나 디렉터리 그룹을 변경할 수 있다.
- 파일의 소유자 또는 슈퍼 유저만이 사용 가능하다.
- -R 옵션: 디렉터리 아래의 모든 파일과 하위 디렉터리에 대해서도 그룹을 변경한다.

```javascript
$ chgrp 그룹 파일
$ chgrp [-R] 그룹 디렉터리
```

<br/>

# **입출력 재지정 및 파이프**

## **출력 재지정 (output redirection): >**

- 명령어의 표준출력 내용을 모니터에 출력하는 대신에 파일에 저장한다.
- 표준입력: 키보드, 표준출력: 모니터
- c언어에서 fopen()를 실행하면 fd (file descriptor) 번호가 리턴된다.
  - 0번: 표준입력 파일 (키보드), 1번: 표준출력 파일 (모니터), 2번: 표준에러 메시지 파일이 reserved 되어있다.

```javascript
$ 명령어 > 파일

ex) $ who > names.txt
```

---

## **출력 재지정 이용: 간단한 파일 만들기**

- 표준입력 내용을 모두 파일에 저장한다.
- 파일이 없으면 새로 만든다.
- 기존에 파일이 있으면 기존 내용이 사라지고 새로운 파일로 만들어진다(overwrite).

```javascript
$ cat > 파일
```

---

## **두 개의 파일을 붙여서 새로운 파일 만들기**

- 파일1과 파일2의 내용을 붙여서 새로운 파일3을 만든다.

```javascript
$ cat 파일1 파일2 > 파일3
```

---

## **출력 추가: >>**

- 명령어의 표준출력을 모니터 대신에 기존 파일에 추가(append)한다.

```javascript
$ 명령어 >> 파일
```

---

## **입력 재지정 (input redirection): <**

- 명령어의 표준입력을 키보드 대신에 파일에서 받는다.

```javascript
$ 명령어 < 파일

ex) $ wc < list1.txt  // wc list1.txt와 같은 결과
```

---

## **문서 내 입력: <<**

- 명령어 실행 시, 입력을 문서 내에서 받을 수 있다.
- 명령어의 표준입력을 문서내의 특정 단어가 나타날 때까지 수행한다.
- 일반적으로 스크립트 내에서 입력을 받을 때 **입력의 끝을 명시하기 위해 사용한다.**

```javascript
$ 명령어 << 단어

ex)
$ wc << end
hello!
word count
end
2 4 20
```

---

## **오류 재지정**

- 명령어의 표준 에러를 모니터 대신에 파일에 저장한다.

```javascript
$ 명령어 2> 파일
```

---

## **표준 에러의 재지정 예시**

- 표준 출력 (1)은 hold1으로, 표준 에러 (2)는 hold2로 지정하라는 의미이다.

```javascript
$ cat x y 1> hold1 2> hold2
```

- 표준 출력 (1)은 hold, 표준 에러 (file descriptor 2)는 file descriptor 1의 사본 즉, hold로 지정하라는 의미이다.

```javascript
$ cat x y 1> hold 2>&1
```

---

## **파이프**

- 명령어1의 표준출력을 명령어2의 표준입력으로 바로 받는다.

```javascript
$ 명령어1 | 명령어2
```

- 로그인 된 사용자들을 정렬해서 보여주기

```javascript
$ who > names.txt
$ sort < names.txt
```

- 로그인 된 사용자들을 정렬해서 보여준다.

```javascript
$ who | sort
```

- 로그인한 사용자 수를 출력한다.
- -l은 줄 수를 나타낸다.

```javascript
$ who | wc -l
```

- 특정 디렉터리 내의 파일의 개수를 출력한다.

```javascript
$ ls 디렉터리 | wc -w
```

<br/>

# **후면 처리 및 프로세스**

## **전면 처리 vs 후면 처리**

전면 처리

- 명령어를 입력하면 명령어가 전면에서 실행되며 명령어 실행이 끝날 때까지 쉘이 기다려준다.
- 전면 처리를 강제 종료하기 위해서는 ctrl-C 입력, 실행 중단을 위해서는 ctrl-Z 입력, 중단 명령어의 재실행은 fg를 입력한다.
  - fg: 제일 최근 job을 전면에서 실행 재계한다.

후면 처리

- 명령어들을 후면에서 처리하고 전면에서는 다른 작업을 할 수 있으면 동시에 여러 작업을 수행할 수 있다.
- 시간이 오래 걸리는 작업등의 실행에 유용하다.

```javascript
$ 명령어 &
```

---

## **$ jobs (후면 실행 작업 목록 표시)**

| 항목     | 출력 예제  | 의미                                                                                                                                                  |
| :------- | :--------- | :---------------------------------------------------------------------------------------------------------------------------------------------------- |
| 작업번호 | [1]        | 백그라운드로 실행시킬 때마다 순차적으로 증가 ([1], [2], [3], ...)                                                                                     |
| 작업순서 | +, -       | +: 가장 최근에 접근한 작업, -: + 작업보다 바로 전에 접근한 작업, 공백: 그 외의 작업                                                                   |
| 상태     | 실행중     | - 실행중(Running): 현재 실행중, 완료됨(Done): 작업이 정상적으로 종료, 종료됨(Terminated): 작업이 비정상적으로 종료, 정지(Stopped): 작업이 잠시 중단됨 |
| 명령     | sleep 100& | 실행중인 명령                                                                                                                                         |

- 후면에서 실행되고 있는 작업들을 리스트 한다.
- 작업번호를 명시하면 해당 작업만 리스트한다.

```javascript
$ jobs [%작업번호]
```

---

## **$ fg (후면 작업을 전면 작업으로 전환)**

- 작업번호에 해당하는 후면 작업을 전면 작업으로 전환시킨다.

```javascript
$ fg %작업번호
```

---

## **$ bg (전면 작업을 후면 작업으로 전환)**

- 작업번호에 해당하는 전면 작업을 후면 작업으로 전환시킨다.
- ctrl-Z 키를 눌러 전면 실행중인 작업을 중지시켜야 한다.

```javascript
$ bg %작업번호
```

---

## **후면 작업의 입출력 제어**

후면 작업의 출력

- 후면 작업을 표준출력으로 보내면 전면 작업과 출력이 뒤섞이게 된다.
- 출력 재지정을 통해 사용한다.

```javascript
$ 명령어 > 출력파일 &
```

후면 작업의 입력

- 키보드 입력은 전면 작업만 가능하다.
- 파일로부터 입력받는다.

```javascript
$ 명령어 < 입력파일 &
```

---

## **후면 처리 예시**

- $ jobs는 후면 실행 작업 목록을 표시해준다.

```javascript
$ (sleep 100; echo done) &
[1] 8320
$ find . -name test.c -print &
[2] 8325
$ jobs
[1] - Running (sleep 100; echo done)
[2] + Running find . -name test.c -print
```

- 후면 실행 작업 중 하나를 선택하여 전면으로 실행한다.

```javascript
$ fg %작업번호

ex)
$ fg %1
(sleep 100; echo done)
```

- 후면 처리 작업의 출력 결과를 조정하지 않으면 전면 처리 작업 화면과 뒤섞이게 된다.
  - 가급적 입출력을 파일로 받도록 설정해야 한다.

```javascript
$ find . -name test.c -print > find.txt &   // 파일로 저장
$ find . -name test.c -print | mail don &   // 메일로 전달
$ wc < inputfile &
```

---

## **프로세스 (process)**

- 실행중인 프로그램을 뜻한다.
- 각 프로세스는 유일한 프로세스 번호 PID를 갖는다.

<img width="450" alt="2_1" src="https://user-images.githubusercontent.com/35963403/134843200-a76bb3fb-903e-4e04-854e-ac7e36d5ea33.PNG">

---

## **프로세스 종류**

| 종류         | 설명                                                                                                       |
| :----------- | :--------------------------------------------------------------------------------------------------------- |
| 데몬(demon)  | UNIX커널에 의해 시작되는 프로세스로 서비스 제공을 위한 프로세스, 서버 프로세스                             |
| 부모(parent) | 자식 프로세스를 만드는 프로세스                                                                            |
| 자식(child)  | 부모에 의해 생성된 프로세스로 실행이 끝나면 부모 프로세스로 돌아감                                         |
| 고아(orphan) | 자식 프로세스가 종료되기 전에 부모가 종료된 프로세스로, 1번 프로세스를 새로운 부모로 가짐                  |
| 좀비(zombie) | 실행이 끝났지만 부모 프로세스에 의해 종료 처리되지 않은 (자식) 프로세스로, 프로세스 테이블을 여전히 차지함 |

---

## **ps (process status)**

- 나의 프로세스들을 볼 수 있다.

```javascript
$ ps
PID TTY TIME CMD
8695 pts/3 00:00:00 csh
8720 pts/3 00:00:00 ps
```

```javascript
$ ps u
USER PID %CPU %MEM VSZ RSS TTY STAT START TIME COMMAND
don 8695 0.0 0.0 5252 1728 pts/3 Ss 11:12 0:00 -csh
don 8793 0.0 0.0 4252 940 pts/3 R+ 11:15 0:00 ps u
```

- u: 프로세스에 대한 보다 자세한 정보
- VSZ(Virtual Memory Size): 가상 메모리 크기
  - 태스크가 접근 가능한 모든 메모리 영역
  - 스와핑 영역
  - 공유 라이브러리 영역
- RSS(Resident Set Size): 실제 태스크에 할당된 물리 메모리 크기(스위핑 영역 제외)

| STAT 첫 번째 필드 |                                                                       |
| :---------------- | :-------------------------------------------------------------------- |
| D                 | IO와 같이 중지(interrupt)시킬 수 없는 잠자고 있는(휴지) 프로세스 상태 |
| R                 | 현재 동작중이거나 동작할 수 있는 상태                                 |
| S                 | 잠자고 있지만 중지시킬 수 있는 상태                                   |
| T                 | 작업 제어 시그널로 정지되었거나 추적중에 있는 프로세스 상태           |
| X                 | 완전히 죽어 있는 프로세스                                             |
| Z                 | 죽어 있는 좀비 프로세스                                               |

| STAT 두 번째 필드 |                                                                 |
| :---------------- | :-------------------------------------------------------------- |
| <                 | 프로세스의 우선순위가 높은 상태                                 |
| N                 | 프로세스의 우선순위가 낮은 상태                                 |
| L                 | 실시간이나 기존 IO를 위해 메모리 안에 잠겨진 페이지를 가진 상태 |
| s                 | 세션 리터(주도 프로세스)                                        |
| I                 | 멀티 쓰레드                                                     |
| +                 | 포어그라운드 상태로 동작하는 프로세스                           |

```javascript
$ ps -ef | more
UID PID PPID C STIME TTY TIME CMD
root 0 0 0 3월04 ? 0:00 sched
root 1 0 0 3월04 ? 0:53 /etc/init-
user1 25786 25600 0 10:30:05 pts/6 0:00 vi prog3.c
user2 25600 25598 0 10:03:51 pts/6 0:00 -ksh
```

| 구분  | 설명                  |
| :---- | :-------------------- |
| UID   | 소유자의 사용자 ID    |
| PID   | 프로세스 번호         |
| PPID  | 부모 프로세스 번호    |
| C     | 프로세스 우선순위     |
| STIME | 프로세스 시작시간     |
| TTY   | 터미널 번호 (?: 데몬) |
| TIME  | CPU 사용시간          |
| CMD   | 명령어 이름           |

ps 명령어는 시스템에 따라 옵션 및 사용 방법의 차이가 크다.

```javascript
$ ps -aux
```

- BSD 유닉스
- -a: 모든 사용자의 프로세스 정보를 출력
- -u: 프로세스에 대한 좀 더 자세한 정보를 출력
- -x: 더 이상 제어 터미널을 갖지 않은 프로세스들도 함께 출력

```javascript
$ ps -ef
```

- 시스템 V
- -e: 모든 사용자 프로세스 정보를 출력
- -f: 프로세스에 대한 좀 더 자세한 정보를 출력

---

## **pgrep (특정 프로세스 리스트)**

```javascript
$ pgrep [옵션] [패턴]
```

- $ ps -ef | grep -w [프로세스] 와 같다.
- 패턴에 해당하는 프로세스들만 리스트한다.
- -l: PID와 함께 프로세스의 이름을 출력한다.
- -f: 명령어의 경로도 출력한다.
- -n: 패턴과 일치하는 프로세스들 중에서 가장 최근 프로세스만을 출력한다
- -x: 패턴과 정확하게 일치되는 프로세스만 출력한다.

---

## **pgrep 예시**

```javascript
$ pgrep sshd
1720
1723
5032
```

```javascript
$ pgrep -l sshd
1720 sshd
1723 sshd
5032 sshd
```

```javascript
$ pgrep -ln sshd
5032 sshd
```

---

## **kill (프로세스 강제 종료)**

```javascript
$ kill [시그널] 프로세스번호
$ kill %작업번호
```

- 프로세스에게 특정한 시그널을 전달한다.
- 시그널이란?
  - 운영체제가 프로세스에게 보내는 신호
  - 프로세스는 이 신호에 응답
  - 응답의 종류: 신호 무시, 프로세스 종료 등

| 시그널 번호 | 시그널 이름 | 기능                                                                                   | 기본응답 |
| :---------- | :---------- | :------------------------------------------------------------------------------------- | :------- |
| 1           | SIGHUP      | 터미널 연결이 끊어진 경우에 발생                                                       | 종료     |
| 2           | SIGINT      | ctrl-C에 의해 발생                                                                     | 종료     |
| 9           | **SIGKILL** | 프로세스를 kill 시킴, 이 시그널은 무시할 수 없음                                       | 종료     |
| 15          | SIGTERM     | 프로세스를 종료시킴, 이 시그널은 무시할 수 있음, **kill 명령이 보내는 default 시그널** | 종료     |

---

## **sleep (지정된 시간만큼 실행 중지)**

```javascript
$ sleep 초
```

---

## **exit (쉘 종료)**

```javascript
$ exit [종료코드]
```

- 로그아웃 후 종료코드(exit code)를 부모 프로세스에 전달한다.

<br/>

# **유틸리티**

## **grep**

- 파일(들)을 대상으로 지정된 패턴의 문자열을 검색한다.
  - 해당 문자열을 포함하는 줄들을 출력한다.

```javascript
$ grep 패턴 파일*
```

### **grep 명령어의 옵션**

| 옵션 | 기능                                       |
| ---- | ------------------------------------------ |
| -i   | 대소문자를 무시하고 검색한다.              |
| -l   | 해당 패턴이 들어있는 파일 이름을 출력한다. |
| -n   | 각 줄의 줄번호도 함께 출력한다.            |
| -v   | 명시된 패턴을 포함하지 않는 줄을 출력한다. |
| -c   | 패턴과 일치하는 줄 수를 출력한다.          |
| -w   | 패턴이 하나의 단어로 된 것만 검색한다.     |

---

## **정규표현식 (regular expression)**

### **정규표현식을 이용한 패턴 기술**

| 문자 | 의미                            | 예           | 결과                                                                                      |
| ---- | ------------------------------- | ------------ | ----------------------------------------------------------------------------------------- |
| ^    | 라인의 시작                     | '^문자열'    | 문자열로 시작하는 모든 행                                                                 |
| $    | 라인의 끝                       | '문자열$'    | 문자열로 끝나는 모든 행                                                                   |
| .    | 한 글자                         | 'a...b'      | 한 글자 대응, a로 시작해서 b로 끝나는 5글자 검색                                          |
| ?    | 없거나 한 글자                  | 'patter?'    | patter 또는 patter과 한 문자 더 있는 문자열 검색, 즉 없거나 한 글자 (pattern, pattera 등) |
| \*   | 앞의 항목이 없거나 여러 번 반복 | 'ab\*'       | a 다음에 b가 없거나 반복적으로 나타나는 라인 검색                                         |
| []   | 괄호안의 글자 중 하나           | '[Pp]attern' | Pattern 또는 pattern이 나타나는 라인 검색                                                 |
| [^]  | 괄호 안에 있는 글자가 아닌 글자 | '[^a-m]att'  | att앞에 a부터 m까지 나오지 않는 라인 검색                                                 |

```javascript
$ grep -w 'st.*' you.txt  // st로 시작하는 모든 단어
$ grep -w 'w.*t' you.txt  // w로 시작하여 t로 끝나는 모든 단어
```

---

## **pipe와 함께 grep 명령어 사용**

- 어떤 명령어를 실행한다.
  - 그 실행 결과 중에서 원하는 단어 혹은 문자열 패턴을 찾고자 할 때 사용한다.

```javascript
ex)
$ ls -l | grep don
$ ps -ef | grep don
```

---

## **sort**

```javascript
$ sort [-옵션] 파일*
```

- 텍스트 파일(들)의 내용을 줄 단위로 출력한다.
- 기본적으로 첫 번째 필드 알파벳 (a to z)로 정렬한다.
- 정렬 필드는 0부터 시작한다.

### **정렬 필드 지정**

| 필드 지정           | 기능                                                                 |
| ------------------- | -------------------------------------------------------------------- |
| -k 필드번호         | 필드번호에 해당하는 필드를 기준으로 정렬한다. 1부터 시작             |
| +시작필드 -종료필드 | 시작필드부터 종료필드-1까지의 필드들을 기준으로 정렬한다. 0부터 시작 |

### **sort 명령어의 옵션**

| 옵션    | 기능                                                |
| ------- | --------------------------------------------------- |
| -b      | 앞에 붙는 공백은 무시한다.                          |
| -c      | 정렬이 되지 않은 상태로 출력한다.                   |
| -d      | 숫자, 문자, 공백만 비교하여 사전식 순서로 정렬한다. |
| -f      | 대소문자를 구분하지 않고 정렬한다.                  |
| -n      | 숫자 문자열의 숫자 값에 따라 비교하여 정렬한다.     |
| -r      | 역순(내림차순)으로 정렬한다.                        |
| -t 문자 | 지정한 문자를 필드 구분자로 사용한다.               |
| -o      | 정렬된 내용을 지정된 파일에 저장할 수 있다.         |

---

## **split**

```javascript
$ split [-옵션] 입력파일 [출력파일]
```

- 하나의 파일을 일정한 크기의 여러 개 작은 파일로 분할한다.
- 기본적으로 1000줄씩 분할하여 xaa, xab, ... 형태의 파일명으로 저정한다.

### **split 명령어의 옵션**

| 옵션 | 기능                        |
| ---- | --------------------------- |
| -l n | 분할할 줄 수(n)를 지정 |

---

## **cat**

```javascript
$ cat 파일1 파일2 > 파일3
```

- **여러 파일들을 파일 단위로 합병**한다.
- 파일1과 파일2의 내용을 붙여서 새로운 파일3을 만들어 준다.

---

## **paste**

```javascript
$ paste [-s] [-d구분문자] 파일*
```

- **여러 파일들을 줄 단위로 합병**하여 하나의 파일을 만들어 준다.
- -s: 한 파일의 끝에 다른 파일 내용을 덧붙인다.

```javascript
ex) $ paste -s xaa xab > xmerge
```

---

## **cmp**

```javascript
$ cmp 파일1 파일2
```

- 두 파일이 같은지 비교한다.
- 두 파일이 같으면 아무것도 출력하지 않는다.
- 두 파일이 서로 다르면 서로 달라지는 위치를 출력한다.
- 보안 관련 설정 파일 검토(수정 여부 파악)용으로 사용이 가능하다.

```javascript
ex) $ cmp you.txt me.txt
you.txt me.txt differ : byte 340, line 10
( 10번째 행 340번째 부터 문자가 다르다는 것을 의미)
```

---

## **diff**

```javascript
$ diff 파일1 파일2
```

- 두 파일을 줄 단위로 비교하여 그 차이를 출력한다.
- -i: 대소문자를 무시하여 비교한다.
- 출력은 첫 번째 파일을 두 번째 파일 내용과 같도록 바꿀 수 있는 편집 명령어 형태이다.

| 편집 명령어 종류 | 예시            | 의미                                                                                                      |
| ---------------- | --------------- | --------------------------------------------------------------------------------------------------------- |
| 추가 (a)         | n1 a n3, n4     | 첫 번째 파일의 줄 n1 이후에 두 번째 파일의 n3부터 n4까지의 줄들을 추가                               |
| 삭제 (d)         | n1, n2 d n3     | 첫 번째 파일의 n1부터 n2까지의 줄들을 삭제하면 두 번째 파일의 줄 n3 이후와 서로 같음                     |
| 변경 (c)         | n1, n2 c n3, n4 | 첫 번째 파일의 n1부터 n2까지의 줄들을 두 번째 파일의 n3부터 n4까지의 줄들로 대치하면 두 파일은 서로 같음 |

```javascript
ex) diff you.txt me.txt
9a10, 13 (첫 번째 파일의 9줄 이후에 두 번째 파일의 10~13줄을 추가하면 두 파일이 같아짐을 의미한다.)
```

---

## **ln (링크)**

```javascript
$ ln [-s] 파일1 파일2
파일1에 대한 새로운 이름(링크)로 파일2를 만들어 준다.
$ ln [-s] 파일1 디렉터리
파일1에 대한 링크를 지정된 디렉터리에 같은 이름으로 만들어 준다.
```

- 기존의 파일에 또 하나의 새로운 이름 혹은 경로를 부여한다.
- -s: 심볼릭 링크

### **하드 링크 (hard link)**

- 기존 파일에 대한 새로운 이름이다.
- 원본을 수정하면 다른 파일도 수정된다.
- 원본을 삭제해도 다른 파일로 접근이 가능하다.

```javascript
ex)
$ ln hello.txt hi.txt
$ ls -l

-rw------ 2 don faculty 15 10월 20일 12:31 hello.txt  // 2는 링크 갯수
-rw------ 2 don faculty 15 10월 20일 12:31 hi.txt
```

### **심볼릭 링크 (symbolic link)**

- 다른 파일을 가리키고 있는 별개의 파일이다.
- 원래 파일의 위치에 대한 정보가 들어있다.
  - 심볼릭 링크를 참조하면 가리키고 있는 파일을 대신 참조한다.
- 심볼릭 링크의 원본이 삭제되면 참조가 불가능하다.

```javascript
ex)
$ ln -s hello.txt hi.txt
$ ls -l

-rw------ 1 don faculty 15 10월 21일 10:00 hello.txt
|rwxrwxrwx 1 don faculty 9 12월 1일 19:31 hi.txt -> hello.txt
```

### **하드 링크 vs 심볼릭 링크**

| 차이                             | 하드 링크             | 심볼릭 링크           |
| -------------------------------- | --------------------- | --------------------- |
| 디렉터리                         | 슈퍼 유저만 가능 | 일반 유저도 가능 |
| 물리적으로 서로 다른 파일 시스템 | 불가능           | 가능              |
| 삭제된 원본 접근                 | 가능             | 불가능           |

---

## **복사 (cp) vs 링크 (ln)**

| cp                                              | ln                                             |
| ----------------------------------------------- | ---------------------------------------------- |
| 완전 별도 파일을 생성                      | 이름만 다르고 내용은 동일                 |
| 둘 중 하나를 수정해도 다른 파일에 영향이 없음  | 둘 중 하나를 수정하면 두 파일이 같이 수정됨 |
| 같은 파일을 별도로 수정하여 작업할 때 사용 | 파일을 공동으로 관리해야 할 때 사용       |

---

## **find**

```javascript
$ find 디렉터리 [-옵션]
```

- 옵션의 검색 조건에 따라 지정된 디렉터리 아래에서 해당되는 파일들을 모두 찾아 출력한다.

```javascript
$ find 범위 표현식 동작
```

### **find 명령어 범위 종류**

| 경로 표현 | 찾기 시작 위치                                              |
| --------- | ----------------------------------------------------------- |
| ~         | 홈 디렉터리에서 찾기 시작                              |
| .         | 현재 디렉터리에서 찾기 시작                            |
| /etc      | /etc 디렉터리에서 찾기 시작 (절대 경로)                |
| /         | /(root) 디렉터리에서 찾기 시작 (전체 파일 시스템 검색) |
| unix      | unix 디렉터리에서 찾기 시작 (상대 경로)                |

### **find 명령어 표현식 종류**

| 검색 조건 표현 | 의미 | 기능 |
| ------------ | ---- | ---- |
|-name filename|파일 이름|특정 파일명에 일치하는 파일 검색|
|-type|파일 종류|특정 파일 종류에 일치하는 파일 검색|
|-mtime [+/-]n|수정 시간|m 시간이 +n일보다 오래되거나, -n일보다 짧거나, 정확히 n일에 일치하는 파일 검색|
|-atime [+/-]n|접근 혹은 읽기 시간|a 시간이 +n일보다 오래되거나, -n일보다 짧거나, 정확히 n일에 일치하는 파일 검색. 현재부터 24시간 이내: +1, 현재 이후: -1, 현재부터 24시간 이후: +2~|
|-ctime [+/-]n|소유자 혹은 권한 변경 시간|c 시간이 +n일보다 오래되거나, -n일보다 짧거나, 정확히 n일에 일치하는 파일 검색|
|-user loginID|사용자 ID|loginID가 소유한 모든 파일 검색|
|-group gname|사용자 ID|소유 그룹 또는 gid 검색
|-size [+/-]n [bck]|파일 크기|+n보다 크거나, -n보다 작거나, 정확히 크기가 n인 파일 검색 b(512byte), c(byte), k(kilobyte)|
|-newer|기준 시간|기준 시간보다 이후에 생성된 파일 검색|
|-prune|검색 범위|서브 디렉터리로 내려가지 않고 현재 디렉터리에서만 검색|
|-perm|사용 권한|사용 권한과 일치하는 파일 검색(8진수)

### **find 명령어 동작 종류**
|동작|의미|
|---|---|
|-exec 명령 {} \;|exec 옵션은 \;으로 끝남. 검색된 파일은 {} 위치에 적용됨|
|-ok 명령 {} \;|exec의 확인모드 형태. 사용자의 확인을 받아야 명령을 적용|
|-print|화면에 경로명을 출력 (default 동작)|
|-ls|긴 목록 형식으로 검색 결과를 출력|

### **find 명령어 예**
```javascript
$ find /usr -name '*.c' -print  // /usr 밑에 .c 파일들을 찾아 경로명 출력
$ find . -name '*.c' -atime +30 -exec ls -l {} \; // 30일 이전에 접근된 파일 중, *.c를 찾아 ls -l 명령어 수행
```