---
title: "git 블로그 댓글 추가하기"
categories: git

tags: git comment

---



# 댓글 추가하기

보통 블로그에는 댓글 기능이 있지만 git블로그는 설정을 해야 댓글을 사용할 수 있다.


mmistakes 가이드 사이트를 보면 여러가지 종류의 댓글 기능이 내장되어 있고 이것들을 설정해서 사용 가능하다고 나온다.<br>

![image](https://github.com/user-attachments/assets/7adf836a-d906-4bb2-8ba0-87cc951ad4ff)


먼저 사이트에 나온대로 config의 defaults에 있는 comments 부분을 true로 바꿔줬다.



![image](https://github.com/user-attachments/assets/f5fb8155-a7f7-4667-bbdd-4092852ecff8)


먼저 디스쿠스는 댓글 기능을 활성화 하려면 계정을 만들어야 한다고 나온다. 

![image](https://github.com/user-attachments/assets/2c389cd3-2314-4738-9509-dd5259af200b)

https://help.disqus.com/en/articles/1717111-what-s-a-shortname 여기로 들어가서 디스쿠스 계정을 만들고 사이트를 등록해줬다.

![image](https://github.com/user-attachments/assets/e0b94d8f-6e24-4698-842e-73675c692e7b)


그리고 생성된 shortname을 config 파일에 지정해주고 comment를 disqus로 바꿔줬다.

![image](https://github.com/user-attachments/assets/ee2b6aa2-8001-4735-88ab-9e559f01fb30)

![image](https://github.com/user-attachments/assets/94d43166-ad68-4956-a73e-62d71a9babdf)


그렇게 했더니 댓글이 추가되었다.


![image](https://github.com/user-attachments/assets/e3cf922c-482c-4841-a0a5-5052c86a1cbb)


찾아보니까 댓글 불러오는 코드는 disqus.html에 등록되어 있었다.

![image](https://github.com/user-attachments/assets/227449f2-1b8e-44a8-86d6-57a5bcb247e8)

이렇게 되있는거 보니까 따로 서버 만들고 스크립트로 댓글같은 정보를 불러와서 사용해도 될꺼 같다는 생각이 들었다.

참고로 로컬에서 실행할 때는 single.html에 있는 댓글을 출력하기 위한 조건들을 출력해보면 

![image](https://github.com/user-attachments/assets/970f6521-48dc-4f71-bf6b-f677a94c9395)

![image](https://github.com/user-attachments/assets/de7d8ba8-cf94-4df0-83e6-92e045ae4bc0)

이렇게 출력되는데 로컬에서는 jekyll.environment 이게 develoipment인데 production인 경우에만 댓글이 나오게 설정되어 있어서 


![image](https://github.com/user-attachments/assets/8664d017-93f6-4a2c-ab61-575a0085a070)

이렇게 jekyll.environemnt를 체크하는 부분을 없애면 

![image](https://github.com/user-attachments/assets/5bdad113-6752-4526-a42b-b369d579c1ff)

로컬에서도 댓글이 잘 출력된다.