#영화 예약 시스템
1. 영화예약 시스템 개요
  1.1 시스템 개요
  1.2 참여 인력 현황
2. 개발 환경
3. 영화예약 시스템 구조
  3.1 데이터 베이스 설계
4.테스트
  4.1 pycharm 터미널에서 python manage.py runserver 명령어를 입력한다.
  4.2 회원가입
4.3 예매하기
5. 참고문헌



1.	영화예약 시스템 개요
1.1	시스템 개요
Pycharm과 flask를 이용해 프론트엔드와 애플리케이션틀을 갖고 데이터베이스 모델 설계와 비즈니스 로직을 만든다.
1.2 참여 인력 현황
한국복지대학교 컴퓨터공학과 20224504 윤선아

2.	개발환경
	플랫폼:  windows 10 x64bit
	웹컨테이너:  
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
