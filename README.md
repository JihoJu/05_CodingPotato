# ACCS 
Abnormal Climate Control System(이상기후통합관제체계)

# Frontend
## 사용기술 
 - React 
 - deck.gl 
 - chart.js 
 - Firestore: 게시판 데이터 CRUD를 프론트단에서 간결하게 처리 
 - firebase hosting: 웹 프론트앤드 배포

## 실행방법 
- 배포된 서비스 이용 (아래 url로 접근 가능)
> codingpotato-6daf2.web.app
- Local환경에서 실행 (React)
```
cd frontend
npm start
```
## 기능 설명
### 전국 무더위쉼터 지도 
- 지도에 무더위 쉼터의 위치를 표현
  (tooltip을 통해 근처 쉼터 갯수, 좌표 정보 제공)
- 각 지역의 하루 최대기온, 평균기온, 최소기온, 위험도를 표현
### 온열질환자 데이터
- 각 년도 기준 전체환자, 실외환자, 실내환자 수를 제공
- 각 년도 지역별 환자의 분포를 차트를 통해 표현
### 지원요청 게시판 
- 폭염 위험에 대처하기 위한 지원요청 게시판
- Firestore와 연동해 CRUD 구현 

# Backend
## 사용기술
  - Django
  - WebSocket: 실시간으로 client에게 폭염관련정보를 보내기 위함
  - BeautifulSoup
  - channels
  - docker: redis를 구동하기 위한 container
  - redis: channels를 구현하기 위해 서버
  
## 배포된 서비스 이용(아래 url로 접근 가능)
> http://34.64.174.66:8000/
 ```
 cd backend
 python manage.py runserver
 ```
 
 ## 기능 설명
 /heatwave/total
 > 온열질환자에 대한 전국 통계 api
 
 /heatwave/region
 > 온열질환자에 대한 지역별 통계 api
 
 /heatwave/response/<field>
 > 온열 대처요령 category별 api
 
 /shelter
 > 전국 무더위쉼터 정보 및 위치
 
 /ShareMe
 > 사용자 위치별 가장 가까운 무더위쉼터 정보, category별 대처요령 유저에게 socket을 통해 전송
 
 /Alarm
 > client와 socket 연결 및 socket을 통해 전달받은 정보 표시 
