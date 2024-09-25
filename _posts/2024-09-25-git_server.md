---
title: "git 블로그 서버 만들기"
categories: git

tags: git server

---



# git 블로그용 서버 만들기

git 블로그에 댓글을 추가할 때 댓글 html 코드를 보는데 ajax를 사용하여 외부 서버와 통신을 하는거 보고
생각해보니까 git 블로그는 html 코드로 되어 있는데 스크립트 사용해서 통신하면 git 블로그의 데이터를 자신의 서버로 관리 할 수 있겠다라는 생각이 들었다.

그래서 이번에는 git 블로그와 통신하는 아주아주 간단한 서버를 만들어서 아주아주 간단한 댓글 기능을 만들어 보려고 한다.


먼저 댓글 기능을 커스텀해서 사용하는거니까 config.yml의 댓글 부분을 custom으로 변경해줬다.

![image](https://github.com/user-attachments/assets/4850615c-a52b-40e6-832d-531e88eadc69)


이걸 custom으로 설정하면 /comments-providers/custom.html이 댓글 부분에 실행되서 이 html코드를 수정해준다.

![image](https://github.com/user-attachments/assets/a05aed2e-5426-4ede-aa5b-c370b57f3d9a)


댓글은 입력하는 부분이 있어야 하기 때문에 간단하게 작성자와 내용 부분을 입력할 수 있는 html 코드를 추가했다.

![image](https://github.com/user-attachments/assets/84bd091d-b0cd-439e-bb11-bd4b9ef19e91)

그리고 작성 내용을 서버에 보내는 함수를 만들고 작성 버튼을 누르면 함수를 호출하게 했다.

![image](https://github.com/user-attachments/assets/146ac962-4d1f-47a1-9431-a423acd3c2d3)

이제 front 부분에서 댓글을 작성하는 코드를 작성했으니까 서버를 만들어서 요청 받으면 댓글을 저장하는 부분을 만들면 된다.

서버는 간단히 만들 수 있는 node의 express 프레임워크로 만들려고 한다.

url은 라우터로 관리 하게 router를 사용하였고 포트는 8888로 하여 서버를 만들었다

![image](https://github.com/user-attachments/assets/1d4adc36-1a83-403b-b7a2-c559242e218e)

그리고 데이터베이스를 사용하는데 간단한 서버여서 sqlite를 사용하였고 데이터베이스를 관리하는 파일을 만들어 sql을 사용할 수 있게 간단히 설정하였다.

![image](https://github.com/user-attachments/assets/1db35f53-90a2-4d76-8d52-dc952b16420e)

그리고 댓글을 관리하는 아주 간단한 테이블을 만들었다.

![image](https://github.com/user-attachments/assets/dcb2c92e-71ed-413f-a823-7f336c3bb150)

라우터 파일에는 요청 들어오면 확인용으로 로그 찍고 db에 댓글 넣는 코드를 추가했다.

![image](https://github.com/user-attachments/assets/5d8d5faf-9366-4e21-9e24-e53d91bb76e3)

이제 댓글을 작성하는 서버도 완성됐는데 블로그에서 쓸떄는 외부에서 접속해서 포트포워딩 설정을 해줬다.

![image](https://github.com/user-attachments/assets/e4a2b51a-b3db-4f54-a85f-4cf455b46eb5)

이제 댓글 작성 세팅이 완료되었으니 잘 동작하는지 확인한다.

![image](https://github.com/user-attachments/assets/7522b3a9-6114-4091-8d26-b2a32744a159)

작성 버튼을 누르니 서버에 로그가 출력되고 데이터베이스에도 데이터가 추가됐다.

![image](https://github.com/user-attachments/assets/29d40bbe-0659-476f-8b1d-0b47e68be198)

이제 작성한 댓글을 불러오는 코드를 간단하게 작성해보자


먼저 서버에는 url 받으면 그 url에서 작성된 댓글을 응답해주는 부분을 만들고

![image](https://github.com/user-attachments/assets/68914187-9a29-47cc-80cf-6427fffc155b)

댓글 출력하는 부분 만들고 서버에 요청 보내서 댓글 응답받고 댓글 출력하는 부분에 댓글을 출력해주는 함수를 만들었다.

![image](https://github.com/user-attachments/assets/137165c5-358a-44fc-8571-2e7cf00ea69e)

이제 완성된 나만의 custom 댓글을 사용해보자

![Honeycam 2024-09-25 22-23-47](https://github.com/user-attachments/assets/87483bf9-710f-4ab0-9666-1bae121c5bc1)

아주 잘 동작한다!!

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>














![image](https://github.com/user-attachments/assets/00bf53e2-a75e-4814-b90b-32970407fd59)
<br><br><br><br><br><br><br><br><br><br><br><br><br><br>
<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

![Honeycam 2024-09-25 22-27-33](https://github.com/user-attachments/assets/8318866c-ed20-4825-85d2-70709b960019)

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

![image](https://github.com/user-attachments/assets/088c5bc4-6c37-4bc6-9bcb-335e803652f9)

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

![image](https://github.com/user-attachments/assets/aa83571a-55b5-4b0e-afc1-635bd397d30b)