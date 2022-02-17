# package.json
터미널에 명령어 `npm init` 을 실행할 경우 생기는 파일.  
이 파일 내에 있는 `scripts` 라는 객체 내에 명령어를 생성해 줄 수 있다.

ex)  
```JSON
 "scripts": {
    "dev": "parcel index.html",
    "build": "parcel build index.html"
  },
```

생성된 명령어의 경우 터미널에서 `npm run 명령어` 를 통해서 실행할 수 있다.