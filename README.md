# 시계열 데이터분석
## 카카오 주가 분석 및 예측(한국 금 ETF와의 비교분석)

<img src= 'https://github.com/DianaKang0123/time_series_project/assets/156397873/b4e0dac8-febd-4098-877e-ab461ddfd876' width='250'>

---

### 📈 목차
1. 국내 금 ETF 와 비교분석
2. 카카오 주가 분석
3. ARIMA를 통한 카카오 주가 예측
4. Prophet를 통한 카카오 주가 예측

---

## 1️⃣ 국내 금 ETF VS KAKAO
<img width="413" alt="kakao_vs_gold" src="https://github.com/DianaKang0123/time_series_project/assets/156397873/0f72270c-3f5d-4289-a0fe-dfc07c830612">

### 🤓 두 종목의 금액 그래프 비교 결과
- 두 그래프 모두 우연변동 시계열이지만 KAKAO의 경우 2020년 이후 상승, 2021년 말부터 하락하는 모습을 보인다.

<img width="440" alt="kakao_vs_gold_Variance" src="https://github.com/DianaKang0123/time_series_project/assets/156397873/518cd559-6a15-4735-afd5-af8b25ddfdb4">

### 🤓 두 종목간의 분산 그래프 비교 결과
- GOLD는 전연도의 걸쳐 비교적 분산이 꽤 일정한 모습을 보인다. 이는 가격변동이 크지 않다는 것을 나타낸다.
- 반면, KAKAO는 2020년도 이후 분산이 급격하게 커지는 모습을 보이며, 이는 해당시기에 가격의 변동이 크다는 것을 나타낸다.

<img width="322" alt="rate" src="https://github.com/DianaKang0123/time_series_project/assets/156397873/e7848265-65a0-47a0-be02-9a54fcdd7e68">

### 🤓변동성 그래프 확인 결과
- GOLD보다 KAKAO의 변동성이 더 높은 것을 알 수 있다.

## 1-1 수익률을 계산
#### 로그, SHIFT를 통해서 다음날의 가격과 비교한 수익률 계산 후 시각화

<img width="439" alt="variance_compare" src="https://github.com/DianaKang0123/time_series_project/assets/156397873/3206992a-870c-4a0c-a2e1-231676bb0071">

### 🤓 수익률 로그 그래프의 비교결과
- 카카오의 수익률의 분포가 금 ETF에 비하여 큰 폭으로 변동하는 것을 확인
- 카카오 주식이 금 ETF에 비하여 시장에서 더 큰 변동성을 보이고 있다.

### 수익률 분포 그래프 확인

<img width="393" alt="histogram" src="https://github.com/DianaKang0123/time_series_project/assets/156397873/ca25ba60-dade-41d8-aed2-b9494c7aed23">

### 🤓 수익률 분포 그래프 확인 결과
- 기존 데이터 프레임의 분포의 경우 정규분포를 따르지 않음을 확인할 수 있다.
- 로그를 취할때와 취하지 않을떄 모두 첨도가 높은 정규분포를 보인다.
- KAKAO의 경우 1에 해당하는 값이 500과 가까운 높은 값을 보이기 떄문에 고른 분포를 위하여 log를 취한는 것이 좋아 보인다.

## 1-2 두 종목의 연관성을 확인
#### VIF 사용

<img width="250" alt="vif" src="https://github.com/DianaKang0123/time_series_project/assets/156397873/c7f36239-e731-4029-8e85-bd25f07ff9d7">

### 🤓 두 종목간의 다중공선성 확인 결과
- 두 종목은 독립적이다.

### 일자별 누적 수익률

<img width="446" alt="rate_stack_by_day" src="https://github.com/DianaKang0123/time_series_project/assets/156397873/ad3fd1b1-9485-48c9-b820-c10465297487">
<img width="449" alt="rate_stack_by_month" src="https://github.com/DianaKang0123/time_series_project/assets/156397873/2f650ec2-0022-48e9-ba2b-5868192cc04c">

### 🤓 주가변동 관련 이슈
- 2014년 5월 다음과의 합병 소식 10월 다음과 합병법인 출범

<img width="286" alt="kakao2014" src="https://github.com/DianaKang0123/time_series_project/assets/156397873/f0e0b726-997f-4011-bf4b-9adb98a91e53">

- 2017년 카카오뱅크 출시. 코스닥에서 유가증권시장으로 이전으로 주가상승

<img width="254" alt="kakao2017" src="https://github.com/DianaKang0123/time_series_project/assets/156397873/75d45fdf-1e1d-41c6-95af-ef9e926eba99">
<img width="299" alt="kakaobank2017" src="https://github.com/DianaKang0123/time_series_project/assets/156397873/0f23a866-68f9-49bc-b659-1d509bfaaddf">

- 2020년 언텍트 시대 카카오 플랫폼, 콘텐츠 사업, 카카오페이, 카카오 모빌리티 등의 실적으로 주가상승

- 2021년 4월 카카오 주식 액면분할

<img width="490" alt="kakao2021" src="https://github.com/DianaKang0123/time_series_project/assets/156397873/53457b2e-ca68-4817-9783-c19341d02c38">

- 2021년 9월 빅테크 흐름 규제, 데이터센터 화재, 스톡옵션 먹튀로 하락세

<img width="446" alt="kakaorun" src="https://github.com/DianaKang0123/time_series_project/assets/156397873/decd0f4c-2447-44d3-aa55-91455adb2f56">
<img width="635" alt="kakaosorry" src="https://github.com/DianaKang0123/time_series_project/assets/156397873/37380edb-4140-4fc2-a11d-50b5faa4f6c9">

## 2️⃣ ARIMA
## 2-1 이동 평균 (MA)

<img width="469" alt="mc_window2" src="https://github.com/DianaKang0123/time_series_project/assets/156397873/8f72d8c4-424c-4451-b120-6cbc4f06ae99">

### 🤓 각 집계함수 적용 결과
- 평균과 중앙값이 거의 비슷하게 나타나므로 정규분포를 따르는 값임을 알 수 잇따.
- 이에따라 최소값, 평균, 최대값을 통한 그래프를 시각화 한다.

<img width="470" alt="mc_window20" src="https://github.com/DianaKang0123/time_series_project/assets/156397873/65118de5-fd7b-439a-b8f0-b1085a82ea6a">
<img width="468" alt="diff_variance" src="https://github.com/DianaKang0123/time_series_project/assets/156397873/717f83de-58dd-4cff-a253-4d751a8fca26">

### 🤓 이동평균 집계함수 그래프 확인 결과
- 이동 평균의 window사이즈를 작게 주었을 경우 최소값과 최댁값, 평균의 차이가 근소한 것을 확인 할 수 있다.
- 해당 그래프로 데이터의 세부적인 변동을 확인할 수 있다.
- 이동 평균의 window 사이즈를 크게 주어 데이터의 전반적인 변동성을 줄이고, 그래프를 뽑아 보았을 때,
- 결과적으로 분산이 상대적으로 일정한 모습을 확인할 수 있다.
- 2022년 12월쯤 diff 그래프의 수치가 급격히 상승하는 부분또한 window사이즈를 크게하여 rolling 하였으므로 최댓갑과 최소값의 폭이 적게 나타난다.
- 즉, 이전보다 이상치에 덜 민감해 졌음을 알 수 있다.

## 2-2 SMA(Simple Moving Average)

<img width="470" alt="sma" src="https://github.com/DianaKang0123/time_series_project/assets/156397873/ef06440e-4262-4898-b918-d0dc41a5a114">
<img width="493" alt="buy_or_sell" src="https://github.com/DianaKang0123/time_series_project/assets/156397873/abcbbead-9a50-4f0f-91f6-3453c31fbfd7">

### 🤓 SMA를 통한 주가 분석 그래프 확인 결과
- 2014년부터 SMA를 통한 그래프르 시각화 한 결과,
- 2015년 1분기(매도) 데드 크로스가 나타나며, 단기 이동 평균선이 장기 이동 평균선 아래에 위치한다.
- 2017년 1분기(매수) 골든 크로스가 나타나며 이후 단기 이동 평균선이 장기 이동 평균선 위로 위치한다.
- 2018년 1분기(매도) 데드크로스가 나타나며 해당 기간 후 단기 이동 평균선이 장기 이동 평균선 아래에 위치한다.
- 2019년 1분기(매수) 골든 크로스가 나타나며, 골든 크로스 이후 2022년 데드 크로스가 나타나기 전까지 단기 이동 평균이 장기보다 위에 위치한다.
- 2022년의 시작에 나타난 데드 크로스 이후 2024년도까지 장기 이동 평균이 단기 이동평균보다 위에 위치한다.

## 3️⃣ 카카오 주가 예측

![kakao_df](https://github.com/DianaKang0123/time_series_project/assets/156397873/8faa58b2-f7df-47dd-8809-45b38cf4707d)

### 3-1 acf와 pacf 확인 (lag(시차) = 20) 및 전처리

<img width="468" alt="acf" src="https://github.com/DianaKang0123/time_series_project/assets/156397873/a5ba894d-d33e-4404-b92e-2e0014398e5e">
<img width="461" alt="pacf_20" src="https://github.com/DianaKang0123/time_series_project/assets/156397873/d88bae28-4344-4913-be70-87725d15b0ce">

### 3-2 MA적용 전후 분포 확인

<img width="491" alt="diff_diff_window" src="https://github.com/DianaKang0123/time_series_project/assets/156397873/c8b9fe02-1f78-43d6-a1f2-c9cb796e078e">

### 3-3 데이터 세트 분할

<img width="266" alt="y_train_test" src="https://github.com/DianaKang0123/time_series_project/assets/156397873/c0bd06cb-d808-480e-9fd0-9c7838ac6ac8">

### 3-4 영가설 검증 및 모델 훈련 

<img width="305" alt="summary" src="https://github.com/DianaKang0123/time_series_project/assets/156397873/d8105242-73f3-4302-9f4b-cc843e5ec85f">

- Prob(통계량):
    - Q : 잔차가 백색잡음 시계열을 따른다는 영가설이 0.76으로 참이므로 잔차들은 서로 독립이고 동일한 분포를 보인다.
    - H : 잔차가 이분산성을 띄지 않는다는 영가설이 0.00으로 거짓이므로 잔차의 분산은 시간에 따라 일정하지 않은 모습을 보인다.
    - JB: 잔차가 정규성을 따른다는 영가설이 0.00으로 거짓이므로 평균과 분산이 일정하지 않다고 볼 수 있다.
- Skew (왜도)와 Kurtosis (첨도):
    - Skew는 -0.26으로 대칭성을 나타내며 0에 근접한 수치로 데이터는 왼쪽으로 살짝 치우치게 나타나고 데이터의 양의 방향으로 꼬리가 두껍게 나타난다.
    - Kurtosis는 10.73으로 뾰족한 정도가 높으며, 분포가 안정적인 형태를 보인다.
 
<img width="487" alt="model_graph" src="https://github.com/DianaKang0123/time_series_project/assets/156397873/27a2d052-868d-4d4a-8f68-621c3a9bbb1e">

### 🤓 모델의 그래프 확인 결과
- 표준화 잔차가 비교적 고른 분포를 보인다.
- 히스토그램의 경우 정규분포를 보이지만 첨도가 높게 나타난다.
- 정규 Q-Q 플롯의 경우 잔차가 대부분 정규분포를 따르지만 양극단의 값은 정규분포에서 벗어나 있음을 보여준다.

<img width="467" alt="prediction" src="https://github.com/DianaKang0123/time_series_project/assets/156397873/0cbc6ea2-fe9f-4a3a-bc66-0f785b50fb27">

### MAPE(Mean Absolute Percentage Error) 및 예측 그래프 확인 결과
- MAPE (%) : 1.5990%
- 해당 예측은 예측값을 누적으로 처리하여 고르게 감소하는 그래프를 보였으며, 이러한 오류를 방지하기 위하여 predict_one_step 함수를 사용
- predict 에서 return 한 값을 다시 그래프로 나타낸 결과 실제값과 예측값이 비슷한 것을 확인
- 하지만 이 경우 실제값이 있어야만 하며, 미래를 예측하기 힘들기 때문에 prophet을 사용하여 예측

### 3-5 Prophet을 통한 예측 (2022-06~)

<img width="492" alt="prophet_y" src="https://github.com/DianaKang0123/time_series_project/assets/156397873/3652622c-d7ff-4957-9ffb-4cd5c5bb68a4">


<img width="476" alt="prophet_prediction" src="https://github.com/DianaKang0123/time_series_project/assets/156397873/8f585e6d-2a60-42fd-b713-739ad57ac415">


<img width="494" alt="forcast" src="https://github.com/DianaKang0123/time_series_project/assets/156397873/5f88c9fd-f18c-4e5d-9cd4-68c02427fefd">

<img width="494" alt="forcast" src="https://github.com/DianaKang0123/time_series_project/assets/156397873/13bd0421-0ef8-483b-b07a-a175cb3370b5">

### 3-6 훈련데이터를 분할 하여 예측 진행
### 최적의 파라미터 조합  
<img width="242" alt="best_param" src="https://github.com/DianaKang0123/time_series_project/assets/156397873/6ed37b78-61a9-4e31-9752-ba1385f1a318">

<img width="453" alt="param_prediction" src="https://github.com/DianaKang0123/time_series_project/assets/156397873/22d37a77-1d20-41f5-a612-ead15b4000a1">

### 🤓 예측 그래프 확인 결과
- 카카오의 주식은 2024년 6월 17일 현시점을 기준으로 하락하는 모습을 보인다.
- 예측 최댓값 경우 2024년 9월 경까지 하락 후 반등하는 모습을 보이지만
- 예측 최솟값의 경우 꾸준한 하락세를 보인다. 

<img width="492" alt="final_prediction" src="https://github.com/DianaKang0123/time_series_project/assets/156397873/3b209ffd-332d-448c-9444-d0facd9309da">
<img width="492" alt="final_prediction" src="https://github.com/DianaKang0123/time_series_project/assets/156397873/f050a2c9-2934-4323-a103-07aa40d628d8">

## 🚩 결론

- 카카오 주식 예측의 경우 현 시점 이후로 하락 하는 추세를 보인다.
- 요일별 주가는 금요일이 제일 높은 금액으로 나타나며, 수요일이 가장 낮게 나타난다.
- 연간 그래프를 보면 2월 말 경이 가장 높은 수치를 보이며 10월 말 경이 가장 낮은 수치를 나타낸다.
- 카카오의 경우 2021년 10월 경 최고점을 찍은 후 꾸준히 하락하는 것으로 보여진다.
- 하지만 현재 카카오가 서비스 전반에 생성형 AI를 접목하여 AI 비서 서비스를 고도화 하는 등 해당 기술에 대한 기대감이 있는 상태이다.
- 이러한 상태가 적용될 경우 그래프의 최대치의 흐름을 따라 갈 가능성을 시사한다.
> <img width="284" alt="NEWS1" src="https://github.com/DianaKang0123/time_series_project/assets/156397873/e590064d-4f3c-4a36-bd57-dcb3a1257ce5">
> 
> 기사 원본 https://www.mk.co.kr/news/it/11039824
>
>  <img width="285" alt="news2" src="https://github.com/DianaKang0123/time_series_project/assets/156397873/60a1ab39-62da-44b9-8ea5-69267743c542">
>  
> 기사 원본 https://www.etnews.com/20240613000216

