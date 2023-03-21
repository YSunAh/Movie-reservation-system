영화 예약 시스템 구조



목차
1. 영화예약 시스템 개요
  1.1 시스템 개요
2. 개발 환경
3. 영화예약 시스템 구조
  3.1 데이터 베이스 설계
4.테스트
  4.1 pycharm 터미널에서 python manage.py runserver 명령어를 입력한다.
  4.2 회원가입
  4.3 예매하기
5. 참고문헌




	1.영화예약 시스템 개요
	1.1	시스템 개요
	Pycharm과 flask를 이용해 프론트엔드와 애플리케이션틀을 갖고 데이터베이스 모델 설계와 비즈니스 로직을 만든다.

	2.	개발환경
		플랫폼:  windows 10 x64bit
		웹컨테이너:  
	-	Flask  1.1.4
	-	가상환경 venv
	-	설치한 패키지
	flask==1.1.4
	Flask-Script==2.0.6
	Flask-Migrate==2.7.0
	Flask-SQLAlchemy==2.5.1
	Flask-WTF==0.14.3
	Flask-Login==0.5.0
	mysqlclient==2.0.3
	redis==2.10.6
	unittest2==1.1.0
	requests==2.25.1
	email-validator==1.1.2
	itsdangerous==1.1.0
	markupsafe==2.0.1
		Database:  MySQL Community Server 8.0.29
		언어:  Python 3.9
		IDE:  PyCharm professional-2021.3.2
		test 도구:  POSTMAN win64




	3.영화예약 시스템 구조
	스템 전체 디렉토리, 파일 
	-base: apps/controllers/
	-파일 이름
	1. /users/controller.py (유저 테이블)
	2. /movies/controllers.py (영화 테이블)
	3. /cinemas/controllers.py (영화관 테이블)
	4. /showtimes/controllers.py (상영 시간 테이블)
	5. /theaters/controlles.py (극장 테이블)
	6. /theater_tickets/controllers.py (예매한 좌석 테이블)
	7. 
	데이터베이스
	-데이터베이스 이름: flask_movie




	3.1 데이터 베이스 설계

	영화 예매는 기본적으로 로그인한 유저만 수행할 수 있습니다. 따라서 users 테이블이 필요합니다. 영화를 보려면 영화 목록이 있어야 하므로 movies 태이블을 만들어줍니다. 영화관도 선택해야 하니 cinemas 테이블을 만들어줍니다. 이제 영화를 선택하고 영화관도 선택했으니 극장도 선택해야 합니다. theaters 테이블을 만들어줍니다. theater_tickets 태이블은 좌석 예매를 위해 만들어줍니다. 상영시간도 필요하므로 showtimes 테이블을 만들어줍니다.


	 3.1.1 먼저 회원가입 페이지입니다. 입력 값으로는 이메일, 닉네임, 나이, 비밀번호를 받습니다. 
	유효성 검사도 같이 만들어 줍니다.
	 ![image](https://user-images.githubusercontent.com/93770261/226702619-dbc4b616-cff9-4eda-99f2-023995a42b99.png)

	3.1.2 다음은 영화 목록 페이지입니다. 보여줘야 할 정보로는 제목, 감독, 나이, 상영 시간등이 있습니다. 그대로 데이터베이스에 적용해줍니다. 
	 ![image](https://user-images.githubusercontent.com/93770261/226702638-34759086-7eb2-44b2-bf07-9eca785462be.png)

	3.1.3 다음은 영화관 모델을 만들어줍니다. 영화와 영화관을 선택했다면 다음으로 상영 시간과 극장을 선택해야 합니다. 상영 정보에는 영화 정보와 시간， 남은 좌석 수 등의 정보가 필요합니다. 따라서 해당 테이블은 영화와 영화관, 극장 정보를 가지고 있어야 합니다. 테이블명은 showtimes로 지었습니다. 
	 ![image](https://user-images.githubusercontent.com/93770261/226702691-cafb8ae5-f224-4f0a-aa84-048be9d9b716.png)

	3.1.4 다음은 상영시간표 모델입니다. 극장에는 여러 개의 좌석이 있습니다. 이때 어느 좌석은 이미 예매가 끝났고 어느 좌석은 아직 남아 있는 상황이 생깁니다. 따라서 극장과 극장 좌석 테이블이 요합니다 theater와 theater_tickets 테이블을 만들어줍니다. 
	 ![image](https://user-images.githubusercontent.com/93770261/226702708-8fcf77b5-ad62-4cd1-a27e-40c089608e9a.png)

	3.1.5
	데이터베이스 설계가 끝났으면 migrate로 테이블 마이그레이션 파일을 만들어주고 upgrade 
	로 실제 데이터베이스에 적용합니다.   
	![image](https://user-images.githubusercontent.com/93770261/226702727-907b522e-50d3-48e9-9a30-69c67f0b9a06.png)

	4.테스트 
	4.1pycharm 터미널에서 python manage.py runserver 명령어를 입력합니다.
	 ![image](https://user-images.githubusercontent.com/93770261/226702787-27b779f7-8e5e-469f-b447-0be339e9b0bc.png)

	4.2회원가입
	4.2.1 크롬 웹 브라우저에서 localhost/users/signup을 입력하여 회원가입 페이지에 접속합니다.
	![image](https://user-images.githubusercontent.com/93770261/226702809-1c0931f9-e85b-4ece-b72d-6cab227cc4c0.png)

	4.2.2 이메일, 별명, 나이 그리고 비밀번호를 입력한 뒤 signup 버튼을 클릭하여 사용자 계정을 생성합니다.
	![image](https://user-images.githubusercontent.com/93770261/226702853-4a729c55-5539-491c-b6e1-7a0cfaf63785.png)

	4.2.3 유효성 검사도 가능하다.
	![image](https://user-images.githubusercontent.com/93770261/226702873-8132e9e6-e9eb-4983-9043-0de3f9bb08d6.png)

	4.3	예매하기
	4.3.1signup 버튼을 누르면 영화 예매시간 showtimes 화면으로 넘어가게 됩니다.
	 ![image](https://user-images.githubusercontent.com/93770261/226702899-9bb7d5b1-92bf-410e-a9ff-047221c30512.png)

	4.3.2 오른쪽 상단에 영화를 누르면 현재 상영되고 있는 영화 포스터가 나옵니다
	![image](https://user-images.githubusercontent.com/93770261/226702917-699553fc-2f99-47d8-9c03-060a6d82cd99.png)

	4.3.3 스크롤을 내려서 예매하기 버튼을 누르면 영화관 목록 나옵니다
	![image](https://user-images.githubusercontent.com/93770261/226702934-a5920e10-7b0e-4be0-9980-91362f875aa3.png)

	4.3.4 여기서 다시 예매하기를 누르면 현재 상영 되고 있는 영화가 나옵니다.
	![image](https://user-images.githubusercontent.com/93770261/226702948-7fe2d7f6-e6da-4786-9978-3f524f04d4f2.png)




	5.참고문헌 
	처음 배우는 플라스크 웹프로그래밍_3장 영화 예매 사이트 만들기(윤정현_한빛_2021)
