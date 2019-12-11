# 2019.12.11 수요일

### :movie_camera: Django

- **#0.0 ~ #0.5 Introduction**
- **#1.1 ~ #1.4 Evironment Setup**
  - pipenv
    - pip으로 설치하면 전역(global)으로 설치되기 때문에, python이나 django등을 업데이트 할 경우, 이전에 생성했던 프로젝트들이 버전이 일치하지 않아 오류가 발생할 수 있다.
    - pipenv를 이용해서 설치를 하면 프로젝트별로 필요한 패키지들을 설치할 수 있다.
    - virtualenv 나 anaconda의 conda 같은 가상환경과 비슷한 형식.
    - \$ brew install pipenv
    - python3 버전으로 설치 : \$ pipenv --three
  - Django 설치
  ```bash
  $ pipenv install Django==2.2.5
  ```
  - github 연동
  ```bash
  $ git init
  $ git remote add origin 경로
  $ git add .
  $ git commit -m "메세지"
  ```
  - 정상적으로 작동하는지 확인
  ```bash
  $ pipenv shell
  ```
- **#2.0 ~ #2.7 Introduction to Django**

  - django project 생성
    1. 먼저 `startproject`로 프로젝트명을 같은 프로젝트가 아닌 다른이름으로 프로젝트를 생성한다. config라는 이름으로 프로젝트를 생성했다.
    ```bash
    $ django-admin startproject config
    ```
    2. 밖의 config 폴더를 Aconfig로 변경(다른 이름이어도 상관 없음)한 후 config 폴더와 manage.py파일을 Aconfig와 동등한 위치에 위치시킨 후 비어있는 Aconfig 폴더는 삭제한다.
  - 개발에 필요한 라이브러리 설치
    - Linter (flake8)
      ```
      - 오류 : line too long (91 > 79 characters)flake8(E501)
      - 오류 제거 방법 : .vscode/settings.json에 아래 요소 추가
      "python.linting.flake8Args": ["--max-line-length=88"]
      ```
    - black
      - formatter
      - \$ pipenv install black --dev --pre

### :pen: Note

- 컴파일 언어 : 프로그램이 시작되기 전에 오류를 발견함.  
  런타임 언어 : 프로그램이 시작해서 오류를 발견하면 모든 작업이 취소됨. (파이썬)

  -> `Linter`가 코드를 실행하기 전에 에러가 생길 부분을 미리 감지해서 표시해줌. (pep8준수)  
  주로 flake8 많이 사용

- **flake8 + black 의 조합은 쵝오**:+1:
