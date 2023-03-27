# GDSC 웹스터디 1~2주차 정리
## 1. URL이란?
###  **URL** : Uniform Resource Identifier   
내가 원하는 리소스의 위치를 나타낸 것. 프로토콜 + DNS 주소로 이루어짐.
### **DNS** : Domain Name Server
길고 복잡하며, 바뀔 위험성이 있는 IP 주소 대신 도메인 이름을 통해 웹사이트 (리소스) 에 연결하게 해줌. 
### **리소스** : HTML, CSS, JS 파일
브라우저는 리소스를 받은 뒤 HTML, CSS, JS를 사용해 우리가 보는 사이트의 모습을 그려냄.   
+ HTML : 자료 (뼈대)
+ CSS : UI (살과 옷)
+ Java Script : 제어체계
<br/><br/>
## 2. GIT
컴퓨터 파일의 변경사항을 추적하고, 여러 명의 사용자들간 파일들의 작업을 조율하는 시스템.
### **git을 쓰는 이유**
1. 코드의 수많은 분기들 (다른 버전들) 을 만들 수 있다. => branch
2. 분기들을 나누고, 합칠 수 있다.
3. 특정 시점으로 되돌릴 수 있다.
4. 변화를 추적할 수 있다. (버전 관리)
### **git의 기본 동작 방식**
파일의 4가지 상태 : Untracked, Unmodified, Modified, Staged   

![image1](https://blog.kakaocdn.net/dn/FvEt2/btrp7jAYEYB/5uKL7iCcngY2afbEgkI8Ek/img.png)
파일들은 조건에 따라 이 4가지 상태를 오감.   

![image2](https://blog.kakaocdn.net/dn/dejHNX/btrIcHK29NB/T7NKy6SOdPVdMQ26kwKKdK/img.png)
- **working directory** : 코드를 작업하는 공간.
- **staging area** : 다양한 변화를 논리적으로 엮어 이름 지어주기 위해 변화들을 쌓아놓는 공간. (중간 저장소)
- **local repository** : git에서 관리하는 저장소. 커밋을 마친 코드를 저장. (메인 저장소)
<br/>  
<br/>
- **git add** : working directory 상의 변경 내용을 staging 영역에 추가하기 위해 사용하는 명령어.
- **git commit** : staging 영역에 쌓인 변화들을 논리적으로 끊어 이름을 지어주고 repository에 넘기기 위해 사용하는 명령어. 

이 과정은 모두 '내 컴퓨터' 안에서 일어나는 일. 다른 사람과 공유하려면? => 공통의 외부 저장소 필요   
### **github** 
remote repository 를 제공해주는 서버 중 하나.

![image3](https://blog.kakaocdn.net/dn/mxN2t/btqNVA1lYXu/nUgk69MJaY2wxW8wfQmES0/img.png)

- push : local repository 로부터 변경사항을 remote repository 로 보냄.
- fetch : remote repository 에 변경사항이 있는지 확인만 함. (내가 작업한 파일을 github에 올리고 퇴근했는데, 다음날 누군가 내 파일을 수정했는지 확인하고 싶을때.)
- pull : remote repository 의 변경사항을 확인할 뿐만 아니라 자동으로 로컬 데이터와 병합함.   
fetch 와 pull 은 병합(merge) 여부의 차이가 있음

