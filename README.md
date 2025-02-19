# DRT-Location-Analysis
[제2회 B.D.A. 채용 연계 데이터 분석 공모전](https://cerulean-cord-e77.notion.site/2-B-D-A-9c6d89fccccf4ccf8079e5570d854a19) 우수상 수상


![BDA 공모전 로고](https://github.com/user-attachments/assets/83c3a32a-0ce5-456b-b3c4-85fa58e0e59a)


# 프로젝트 소개
**공공데이터를 활용하여 서울시 내 교통 취약 지역의 마을 버스를 수요응답형(DRT)으로 변경하는 방식과 그 경제적 효과 분석**


**프로젝트 기간: 2024/06/04~2024/07/27**


**멤버 구성: 피하영, 맹선영, 강민채, 배소현**

### 개발 툴

* **언어**: 파이썬 <img src="https://github.com/user-attachments/assets/3159747f-08b8-423a-bae3-776e5e233be1" width="35" height="35"/>

* **개발환경**: 구글 코랩 <img src="https://github.com/user-attachments/assets/d301ccf8-c112-4567-9fd2-31a32a6b0641" width="60" height="35"/>


* **협업도구**: [Notion](https://mixolydian-paint-5ff.notion.site/f1fb19c9c29e461e90ad2720f9a6d15d?pvs=4)


# 프로젝트 설명

## 1. 개요

### 제안 배경 및 필요성
- **마을버스의 재정난** : 코로나 팬데믹 이후 서울시 마을버스 이용수요가 28.6% 감소. 이에 따라 운행감축, 배차간격 증가가 일어나고 그 결과 이용수요가 감소하는 악순환 발생.
  
   <img src="https://github.com/user-attachments/assets/a869b3f3-9805-4978-8570-06748cddaee0" width="300" height="300"/>
  
### 아이디어 핵심 내용
- <b> DRT (Demand Responsive Transport)</b> : 수요응답형 이동서비스로, 대중교통의 노선을 미리 정하지 않고 승객의 수요에 따라 운행구간, 정류장 등을 정해 노선을 탄력적으로 운행하는 서비스. 

- <b>현재 DRT 운영 상황</b> :  주로 농어촌 지역 등 대중교통 취약 지역을 대상으로 제공, 하지만 도시에도 대중교통 취약점 존재. 특히 마을버스는 코로나 팬데믹 이후 수요가 매우 감소하면서 적자를 감당하기 어려운 상황에 처해있음. 그 결과 서비스의 질이 떨어지고 이용량 또한 감소하는 추세임을 확인.

- <b>목표</b>: 서울시 기존 마을버스 정류장 중 DRT 입지를 분석해, 마을버스의 취약 지점 개선. 

- **노선 선정**
    1. 먼저 적합한 노선을 찾기 위해 두 벡터의 집합을 이용한 자카드 유사도와 두 벡터의 집합과 방향을 고려한 코사인 유사도로 유사한 노선쌍 선정. 
    2. 이 중 과부하를 막기 위해 신설된 노선은 DRT의 의도와 맞지 않기에 제외.
    3. 마지막으로 이용량이 타 노선쌍에 비해 감소하는 추세를 보이는 강서01과 강서02 버스가 drt 서비스 입지 분석에 적합한 노선이라고 판단. 따라서 두 노선으로 분석을 진행함.
 
   <img src="https://github.com/user-attachments/assets/19c25b40-7297-497b-9284-dd03dba42eb2" width="800" height="300"/>

- <b>기대효과</b> : 중복되지 않는 노선의 이용량을 파악하여 정기 노선이 아닌 DRT 서비스로 대체한다면 승객들의 불편함을 줄임과 동시에 효율적인 마을버스 운행 기대.


  
### 아이디어의 독창성
- **대도시인 서울에 DRT 도입**: DRT 서비스의 특징을 살려 ‘시골 및 교외지역’이 아닌, ‘대도시’인 서울에 적용해보고자 함.

- **구간 DRT 도입** : 서울과 같은 대도시는 이미 대부분 대중교통 시스템이 고도화되어 기존 ‘노선 전체’를 DRT로 대체하기에 적합한 지역을 찾기 쉽지 않음. 따라서 수요가 많은 구간은 기존 노선을 유지하되, 수요가 적은 구간 ‘일부’ 노선에만 DRT를 도입하여, 실제 서울 지역에 DRT 도입의 실현 가능성을 높이고자 함.

## 2. 분석
### 마을버스 사용량 및 노선 대체형 DRT 입지 선정
![자카드와 코사인 유사도](https://github.com/user-attachments/assets/d143b096-9e74-4e30-8652-dc8bc557f63d)

[자카드 유사도 상위 15개 노선, 코사인 유사도 상위 15개 노선]

각 유사도 상위 15개 노선 중
1. 신설된 노선 제외
2. 2018년부터 2023년까지의 이용량을 분석하여 이용량이 낮고 & 감소 추세를 보이는 <b>'강서01', '강서02'</b>를 채택

   
![유사 노선 이용량 분석](https://github.com/user-attachments/assets/cfe3491e-5541-4114-8881-74ee97958e39)
### 강서01, 강서02 노선 대체형 DRT 분석
- **두 노선의 평균 이용량 분석** : 평일 출퇴근과 공휴일의 예상치 못한 이용량 증감을 고려해 평일과 토요일, 일요일&공휴일로 나누어 분석.
그 결과, 강서01의 평균 이용량이 강서02에 비해 많다는 것을 확인.

  <img src="https://github.com/user-attachments/assets/4c3f61ed-2059-458a-a764-6feaa2a47b03" width="450" height="500"/>

- **정류장별 이용량 분석** : 지도 시각화를 통해 두 노선의 중첩되지 않는 부분을 확인. 
두 노선 모두 평일 출퇴근 시간에 이용량이 가장 많아 해당 시간을 기준으로 각 정류장별 이용량 분석.

  <img src="https://github.com/user-attachments/assets/3362a702-c967-4a1a-bc91-a98724f4d2c5" width="400" height="400"/>


- **DRT 도입 노선** :  강서01은 이용량이 많은 지하철역을 포함하고 있으며 강서02에 비해 이용량이 월등히 많아 그대로 운영.
  
  강서02의 중첩되지 않은 노선의 경우,

  1) 그림의 위쪽 노선은 강서01과 근접하여 강서01에 편입.


  2) 그림의 아래쪽 노선은 이용량이 적어 DRT 도입 노선으로 대체.

  <img src="https://github.com/user-attachments/assets/a4f01521-9f61-4d1f-888e-81f328fb3d8a" width="700" height="300"/>



## 3. 실현 가능성 및 기대효과
### 실현 가능성

**1. 변경된 강서01 노선** : 기존의 출퇴근시간 강서01 평균 이용객 11명에, 강서02에서 유입된 이용객을 합하여, 출퇴근 시간대 평균이 16명 이내일 것으로 예측함. 이는 마을버스의 수용 가능인원 이내임.

**2. 새로운 DRT 노선** : 출퇴근시간 평균 사용자가 12명으로, 충분히 수용할 수 있을 것으로 예상.


### 기대효과
**1. 대기 시간 감소**


<img src="https://github.com/user-attachments/assets/4273bc5b-23e0-405a-909c-a1c008536f2d" width="600" height="300"/>

A에서 B를 가는 경우

기존 최대 대기 시간: 25분
DRT 도입 시 최대 대기 시간:  DRT 10분 + 강서01 11분, 총 25분

**2. 운송 원가 감소**

<img src="https://github.com/user-attachments/assets/57ef5dd3-a422-4393-bdce-44fbdb92e6a0" width="600" height="250"/>


 DRT 이용시 강서02 2대를 1대의 DRT로 대체 가능. 
 
 이때 2024년 기준 마을버스 한 대의 하루 당 운송원가 45만 7040원. -> 하루마다 약 46만원 절감 가능. 


## 4. 한계 및 보완점
  마을 버스 공공데이터가 누락 값이 많아 사용하지 못하는 데이터 다수. 특히 승하차 인원 데이터 분석 중, 요일별 이용량에서 일부 요일에 누락 값이 확인되어 이용량 분석에 어려움을 겪음

## 5. 활용 공공데이터
* [서울시 버스노선별 정류장별 시간대별 승하차 인원 정보. (2024).](https://data.seoul.go.kr/dataList/OA-12913/S/1/datasetView.do)

* [노선 정보. (2021).](https://t-data.seoul.go.kr/dataprovide/trafficdataviewfile.do?data_id=53)

* [배차 정보 (2021).](https://t-data.seoul.go.kr/dataprovide/trafficdataviewfile.do?data_id=72)

* [서울시 버스정류소 위치정보. (2024).](https://data.seoul.go.kr/dataList/OA-15067/S/1/datasetView.do)

* [일자별-시간대별-버스노선별-구간별-승객수(API). (2024).](https://t-data.seoul.go.kr/dataprovide/trafficdataviewopenapi.do?data_id=1025)



