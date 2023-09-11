# RINEX_analysis_POHG_earthquake
  
 : 정밀 위치정보를 제공하는 RINEX 데이터를 분석해 지진 후 판의 이동이 실제로 좌표 변동으로 나타났는지 확인
     
#### 🚩RTK(Real Time Kinematic)란 무엇인가?
 >  높은 수준의 정확도를 확보하기 위해 후처리가 필요했던 기존 측량 방식과는 다르게, 네트워크를 통해 기준국으로부터 실시간으로 보정정보를 수신하여 cm 단위의 정확도를 확보하는 측량기술. RTK 수신기를 통하여 실시간으로 높은 정확도의 위치정보를 얻을 수 있다.
> RINEX란 이러한 GPS 데이터의 포멧을 말함.
   
---
  
### 🌏eqrthquake_POHG
 >  2011년 동일본 대지진 발생 이후 GNSS 데이터를 통해 판의 이동을 감지한 여러 논문들을 참고하여, 17년 11월 발생한 포항 대지진 이후 비슷한 양상이 있었는지 후처리 RINEX 데이터를 종합하여 판단하고자 하였다.
 >    
 >>1. 대상 기준국 및 연도
 >>    * 2017~2018년, 총 2년간의 30분 간격 RINEX 데이터를 사용
 >>    * 보현, 호미, 군위, 부산의 네 기준국을 기준으로 하였음
 >>2. 사용 데이터
 >>    + RTKLIB을 통하여 추출한 결과 데이터 중, Q값이 1인 신뢰성 높은 자료들만 사용함
 >>    + 군위의 경우 17년 10월경의 관측소 데이터가 존재하지 않는다.  
 
### 🌏trans_coordinate
 >  Ellipsoidal 좌표계와 ECEF 좌표계 간의 변환, ECEF좌표계와 ENU 좌표계 간의 변환을 지원한다.  

### 🌏true_position
 >  위의 좌표 변환 코드에서 ECEF->ENU 를 활용해, 측정 데이터와 실제 데이터를 rms값을 통해 비교할 수 있다. 결과 데이터의 신뢰성을 이를 통해 판단한다.

---

# 포항 지진 좌표분석 결과  
  
  RTKLIB 결과 데이터 .o 파일을 합쳐가며 2년간의 변동 결과를 한 눈에 보고자 했으나, 기대했던 유의미한 좌표변화는 나타나지 않았다. 실제 위치를 상수함수로 나타낸 일차함수와 시계열 분석을 통해 도시한 그래프는 겹쳐져서 거의 눈에 띄지 않았다. 이후에 두 선이 명확하게 구분되게끔 표현법에 차이를 주었다.
  2년간의 데이터의 시계열은 아래와 같다.
  
1. 군위, 보현  
![군위, 보현](https://user-images.githubusercontent.com/92227496/139863717-37db60fb-c2b8-4fb6-bd3f-d33c929ab9a1.jpg)  
  
2. 부산, 호미    
![부산, 호미](https://user-images.githubusercontent.com/92227496/139863727-43fb7ba9-8a37-4371-918d-0ae296804ca1.jpg)  


#### 분석
> - 그래프 자체가 비어있는 것은 gnssdata.or.kr 자체에서 데이터를 제공하지 않았기 때문이다.
> - 계절의 영향으로 인해 특정 구간에서 Q=1로 확정된 값이 급격히 줄어들어, 데이터가 듬성듬성한 지점이 존재함
>    (이는 장기간의 RINEX 데이터를 통해 후처리가 가능하나, 선정 관측소들은 17년 이전의 데이터가 존재하지 않았다.)
> - 전반적으로 여름에 오차범위가 커지는 모습을 볼 수 있는데, 평균 습도의 상승 때문이라고 추정함
