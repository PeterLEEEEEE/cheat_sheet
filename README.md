# pin
zero to hero maybe ;)

# pin
zero to hero maybe ;)
source: 실용주의 프로그래머님의 [작정하고 장고](https://www.youtube.com/watch?v=fz6hYVOer2Y&list=PLQFurmxCuZ2RVfilzQB5rCGWuODBf4Qjo&index=1)를 토대로 작성하였습니다.

<br><br><br>

## 디버깅
- break point 설정
- Run, debug configuration/template/python에서 script path 지정(내 프로젝트 가상환경의 script), parameter: runserver로 지정  
- manage.py를 Debug 함 --> runserver 설정이 실행됨
- break point에 딱 멈춰있는 것을 확인할 수 있음

## 환경 설정 
* 파이참은 cmd와는 다르게 프로젝트 만들때 자동으로 가상환경 생성해줌(굳)

pip list: 현재 내 가상환경에 설치된 라이브러리 조회
*나는 conda를 쓰므로 가상환경이 anaconda 폴더에 존재함, 따로 하려면 만들때 설정을 바꾸면 됨*

장고 설치하고 다시 pin list로 조회하면 장고가 설치된 것을 확인 가능
<br><br>

## 장고 프로젝트 생성
django-admin startproject (프로젝트명) 을 통해 장고 프로젝트를 새로 생성
* 원하는 이름의 디렉토리를 만들고 그 안에 들어가서 django-admin startproject config . 이렇게 치면 디렉토리와 하위 디렉토리 이름을 다르게 생성할 수 있음(pin<상위> - config<하위>)*

<br><br>

## MVT
M - Model: 데이터베이스(데이터)를 효율적으로 다룰 수 있게 해줌
V - View: 유저로부터 request 받고 response 해줌(서버가 계산 및 처리) -- MVC 모델에서의 Controller와 같은 역할
T - Template: 유저 인터페이스

<br><br>

## CRUD

요약
C: Create - Post 방식
R: Read - Get 방식(list 조회, detail 등)
U: Update - Put or Patch(Put은 전체 수정, Patch는 일부 수정)
D: Delete - Delete

Django는 CRUD view class를 지원해줌으로서 우리는 굉장히 편리하게 CRUD를 만들 수 있다.(CBV: Class Based View)

<br><br>

## app 설치
python manage.py startapp (앱 이름)

<br><br>

## git setting
컴퓨터에 깃 설치 후 
git init 으로 해도되고 파이참은 VCS 버전 컨트롤로 해도 된다.

- git reset --hard HEAD (HEAD로 롤백)
- git branch -M main(master -> main)
<br>

*gitignore
https://github.com/github/gitignore/blob/master/Global/JetBrains.gitignore 에서 jetbrain용 gitignore 내용을 제공해줌
외에 추가적으로 venv, DB, cache 등 원하지 않는 내용 추가
특히 키 값은 절대 올리면 안된다. 올리면 gitguardian한테서 메일 폭탄 맞음(django-environ을 사용한 방법도 있고 json파일로 따로 관리하는 방법도 있고 방법은 여러가지인듯)

<br><br>

## Templates

view에서 html 파일을 보낼때는 render로 return! ex) return render(request, template name) // 경로 연결 꼭 확인해야 한다.

<br>

## Model

python manage.py makemigrations 
--> models.py에 쓰는 내용을 DB와 연동시킬 파이썬 파일로 만들어주는 작업 
python manage.py migrate를 통해 최종적으로 적용된다.

<br>

## HTTP protocol

유저는 서버로 GET/POST 방식을 통해 request를 보냄
GET: CRUD에서 언급되었듯이 주로 조회를 하기 위해 사용(주소 안에 추가적인 파라미터를 적어서 보냄) 

POST: create, update 와 같이 서버 내에 어떤 정보를 새로 만들거나 수정할 때 사용 / 주소 안에 파라미터를 넣는 방식이 아닌 추가적인 body 안에 데이터를 넣어서 보냄(https에서는 body가 암호화되어 전송된다)

<br>

## Reverse, Reverse_lazy

reverse: 함수형 뷰에서 사용
Reverse_lazy: 클래스형 뷰에서 사용

<br>

## Login 기능

로그인 기능 구현 후 로그인을 하기 되면 /profile로 넘어가기 때문에 따로 처리를 해주어야 한다.
setting.py에서 LOGIN_REDIRECT_URL을 설정
**ex)**
- LOGIN_REDIRECT_URL = reverse_lazy('account:hello_world')
- LOGOUT_REDIRECT_URL = reverse_lazy('account:login')

<br>

## aws

pem 키 생성 후 인스턴스 생성, 내 컴퓨터 bash 에서 pem키가 존재하는 경로에 ssh -i (pem) ubuntu@(aws아이피)로 접속하면 서버 연결 끝 굳!

이러면 putty 안써도 된다 개꿀팁임 진짜

## Docker

- 설치
docker docs 홈피에 install using the repository에서 절차에 따라 다운

*portainer(docker GUI) 설치 역시 홈페이지 들어가서 다운(내가 루트가 아니면 앞에 sudo 붙이면 된다)

<br>

**왜 도커를 쓰는가?**

- 기존의 가상머신과는 달리(Hyperviser를 쓰지 않는듯) 컨테이너를 사용하여 OS 그 자체와 비견될 정도로 빠르다. 빠른게 장점이네

docker image 안에 모든 설정을 완료하고 이를 복사(container)하여 서버에 배포하면 후에 서버가 터지든 옮기든 관리하기 편하다. (image - container, 클래스 - 객체 관계라고 보면 편할 듯하다)









