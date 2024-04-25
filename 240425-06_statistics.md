- 추후 수정 업로드 예정 #~

# 240425-06_statistics.md
- 아래에 대한 내용을 공부, 기록, 수정, 추가한 것임
  > 통계로 데이터 분석 능숙해지기 - 김현진[1]
  > 

# 목차
```
1

1.3 기술통계
1.4 통계 실험과 유의성검정
1.5 선형회귀분석


Self Feedback   


Reference
```


## 1 [필수 강의] Part 3. 통계로 데이터 분석 능숙해지기
### 1.1 대푯값
- **산술, 기하, 조화** 평균
  + Ex 1. 산술 평균 사용 케이스
    - 독립적인 것 (세 사원의 연봉 평균)
 
  + Ex 2. 연 평균 매출 **증가율**   
    > 각 연 매출: 15억, 30억, 25억 

    - (1) 평균 : 기하 평균 사용 (증가율 때 많이 씀 )
      > **(1) ( a1 * ... * an )^(1/n)** 
    - (2) 증가율 : n배 값
      > **n배 = x2/x1배**  
      > 15억 --2배--> 30억 --5/6배--> 25억
    - = ( 2 * 0.833 )^(1/2) = 1.29 
      > x 값이 k개 -> 곱할 값은 k-1개  

  + Ex 3. 조화 평균 사용 케이스
    > 갈 때 3m/s, 올 때 1m/s -> 평균 속력   
    > : 조화 평균이 산술 평균보다 작네

    - 2ab / (a+b)

- Median(중앙값), Mode(최빈값)

### 1.2 분산도
- 분산 : sigma(x_i-m)^2/n : 편차 제곱의 평균

- Interquartile Range [IQR, 사분위 범위], outlier [이상치] 탐지

  + Quartile [사분위수] : 오름차순, 같은 갯수를 가진 네 그룹으로 나누는 세 지점
    - Q1 [1사분위수] : 25th Perentile[백분위수] : ~~ 1/4
    - Q2 [2사분위수] : 50th Perentile[백분위수] = [Median] : ~~ 1/2
    - Q3 [3사분위수] : 75th Perentile[백분위수] : ~~ 3/4
  + (0) IQR = Q3 - Q1

  + (Outliers) (x < Minimum )  
  + (1) Minimum = Q1 - 1.5 * IQR
  + (2,3,4) Q1, Q2[Median], Q3
  + (5) Maximum = Q3 + 1.5 * IQR
  + (Outliers) ( x > Maximum )

  + Ex. 길이 9인 데이터 [14, 28, 35, 42, 47, 51, 80, 130, 140]에서의 각 값
    -  (2,3,4) Q1 = 35, Q2 = 47, Q3 = 80 
       + (n - 1(자기자신))* 1/4 = 2개
       + 그룹 당 개수 = Q1~Q3을 찾기 위해 끝에서부터 통과할 개수 = 자신 제외 남은 개수/4 
       + 자기자신 1개만 빼고 생각하는 거임. Q1~Q3 다 빼는 거 아님  
         
       > 개수가 딱 안 떨어질 때는 어떻게 되는 지 모름 -> 데이터 많으면 한 개 땡기는 정도는 큰 차이 없을 것임. -> 값의 차이가 있다고 해도 애초에 사분위수를 통해 해당 백분위 정도의 위치를 볼 수 있는 것이므로 보고자 하는 것은 비슷할 것이다.
    - (0) IQR = Q3 - Q1 
    - (1,5) Minimum = Q1 -1.5 * IQR , Maximum = Q3 + 1.5 * IQR  
    

- coefficient of variation [ CV, 변동계수 ]
  + CV = 표준편차 / 평균
  + 상대적으로 얼마나 변동이 많은지
  + 단위가 다르거나, 표준편차가 비슷한 그룹끼리 비교하고 싶을 때 '일정한 기준에 따른 비교가 가능'하다
  + Ex. 각 회사 별 매출의 CV 비교 -> 변동성 및 안정성 포착

  
- Skewness [ 왜도 ]
  + 분포의 **비대칭도**를 나타내는 통계량
  + 일반적으로 치우침이 없는 데이터라고 여기는 값 : -1 ~ 1

  + 음수값 : 값들이 오른쪽으로 몰려있음 : Mean, Median, Mode
  + 양수값 : 값들이 왼쪽으로 몰려있음 : Mode, Median, Mean
  + ![image](https://github.com/journeythrunrun/journeythrunrun/assets/164328543/f278110e-cc88-4645-b059-9dbfbd99b5f8)[2]
  + ![image](https://github.com/journeythrunrun/journeythrunrun/assets/164328543/b5c0c387-78f0-4535-965b-5712d6b83bad)[3]

- Kurtosis [ 첨도 ]
  + 꼬리 부분의 길이와 중앙 부분의 **뾰족함**으로 데이터의 분포를 알 수 있음

  + Leptokurtic : 중앙 부분이 Mesokurtic보다 높고 뾰족하기 때문에 outlier가 많을 수 있음
  + Mesokurtic : 정규 분포 모양
  + Platykurtic : outlier가 없음, 데이터 다시 확인 필요

  + ![image](https://github.com/journeythrunrun/journeythrunrun/assets/164328543/ac41f725-9624-405b-a789-473444a3c4cc)[3]




### 1.3 기술통계


### 1.4 통계 실험과 유의성검정


### 1.5 선형회귀분석


## Self Feedback   
- problem) 너무 쉬운 것도 글 쓰는 거에 시간이 많이 들어가는 것 같음
  + sol) 멈춤 가능하면(& 그래프가 아주 중요하지 않으면) : **처음부터 바로 md형식으로 정리.** 필기 -> 글 이중

## Reference
[1] 통계로 데이터 분석 능숙해지기 - 김현진  
[2] https://www.quora.com/How-is-the-gender-pay-gap-calculated-in-the-US  
[3] https://www.sciencedirect.com/topics/social-sciences/kurtosis  

