# 세팅과정
- 1. 파이썬 설치
- 2. 가상환경 생성
- 3. 가상환경 활성화
- 4. fastAPI 및 필요한 모듈 설치
- 5. `main.py` 파일 생성

## 파이썬 설치
- [Python 공식 사이트 방문하여 설치](https://www.python.org/downloads/)

## 가상환경 생성
- powerShell 열기
- 가상환경 생성을 원하는 경로로 이동
- 가상환경 생성 명령어 입력
```
python -m venv venv
```
- 폴더 내부에 `venv`라는 가상환경 폴더 생성됨

## 가상환경 활성화
- git bash 열기
- 아래의 명령어 입력
```
source ./venv/Scripts/activate
```
-  git bash가 아래와 같이 바뀌면 정상적으로 활성화된 것임
```
(venv) 
[사용자명]@ [경로]
$ 
``` 

### powerShell로 활성화하는 경우
- git bash와 명령어 및 설정이 다르므로 아래의 링크를 참고한다
- [윈도우의 powershell에서 가상환경이 활성화 안되는 이유](https://dreamlog.tistory.com/603)

### 가상환경 비활성화
- 활성화된 상태의 터미널창에서 아래의 명령어를 입력하면 된다
```
deactivate
```

## fastAPI 및 필요한 모듈 설치
- fastAPI 설치
```
pip install fastapi
```

- uvicorn[standard] 설치

```
pip install uvicorn[standard]
```

### 모듈 한번에 설치하기
- 설치하고 싶은 모듈을 `requirements.txt` 파일에 작성
- 아래의 명령어를 입력하여 한번에 설치 진행
```
pip install -r requirements.txt
```


## `main.py` 파일 생성
- 파일 내부에 아래와 같이 작성
```
from fastapi import FastAPI

app = FastAPI()


@app.get("/")
async def root():
    return {"message": "hello world"}

```

### 파일 실행
```
uvicorn main:app
```

```
INFO:     Started server process [4336]
INFO:     Waiting for application startup.
INFO:     Application startup complete.
INFO:     Uvicorn running on http://127.0.0.1:8000 (Press CTRL+C to quit)
```

#### 실행 포트 번호 변경
- `portnum`부분에 원하는 포트번호 숫자 입력
```
uvicorn main:app --port=portnum
```

#### 파일 수정시 자동 리로드
- 파일이 수정될 때마다 자동 리로드해주도록 하는 명령어이다
- react처럼 자바스크립트 환경이 아니므로 페이지 새로고침은 해주어야한다
- 페이지 새로고침 단축키 : `ctrl + r` 또는 `F5`
```
uvicorn main:app --reload
```

### API 문서
- 아래의 주소로 이동하면 API문서를 확인할 수 있다
- `http://127.0.0.1:8000/docs`
