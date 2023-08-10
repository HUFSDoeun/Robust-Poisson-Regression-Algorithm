# Robust Poisson Regression Algorithm
* 현 문서는 한국외국어대학교 통계학과 이석호 교수님 연구실의 학부연구원 과정의 연구 내용을 요약한다.

## 요약
* 본 연구는 포아송 분포의 평균 추정과 포아송 회귀계수 추정 과정에 손실함수 이동법을 적용하여, 보다 로버스트한 추정을 위한 알고리즘을 제시한다.
* 이 알고리즘은 이상점에 대해 이동모수($r_i$)를  추정하여, 로버스트한 성질의 추정값을 도출해낸다. 또한 다양한 조절모수 ($\lambda$)에 대한 모의실험 및 시각화를 진행하고, 평균제곱오차(Mean Squared Error)를 측정하여 이를 기준으로 최적의 조절모수를 선정한다.



### ⏳ 연구기간
* 2023.02.27 ~ 2023.08.31

### 🧑🏻‍🔬 연구원
* **김협**
  * 한국외국어대학교 통계학과 20학번 / ekwjsxl200@gmail.com
  * 모의 실험 결과 시각화, 결과 보고 정리
* **류원재** 
  * 한국외국어대학교 통계학과 18학번 / weonjae0211@gmail.com
  * 알고리즘 구현, 혼동행렬 시각화
* **이도은**
  * 한국외국어대학교 통계학과 20학번 / 202002397@hufs.ac.kr
  *  알고리즘 및 모의 실험 구현, 깃헙 구축

### ⚙️ 개발환경
* R 4.3.0

<br> <br> 

## 실행방법 및 설명 
### 1. Simulation & Algorithm
* Algorithm 1 (포아송 평균추정 알고리즘), Algorithm 2 (포아송 회귀추정 알고리즘)에 대해서 모의실험을 진행할 수 있는 함수인 robust_poisson을 정의하고 다양한 셋업에 대한 모의실험을 진행한다. 본 연구에서 설정한 셋업 이외의 다른 셋업에서 모의실험을 진행하고자 한다면, 해당 함수를 사용하여 추가적으로 모의실험을 진행할 수 있다.
  
**[매개 변수]**

-   target_type : mean (평균추정) or reg (회귀 계수 추정)
-   simul_type : simulation type (1, 2, 3)
-   n : 자료수
-   p : (회귀 계수 추정의 경우) 독립변수의 수 (default = 0)
-   pi : 이상치 발생확률
-   true_theta : 참 모수값 (평균추정의 경우 true mu, 회귀계수 추정의 경우 true beta)
-   alpha : 이상치
-   max_iter : 최대 반복횟수
-   lambda : 조절모수
-   tol : tolarence
-   simul_seed : 자료(y) 생성시 동일한 자료 를 생성해야하는경우 지정, default값 사용시 호출할 때마다 다른 자료 생성 (default = NULL)

**[output]**

-   X : (회귀추정의 경우) 모의실험으로 생성된 x값들 - 평균추정에서는 NULL값 반환
-   mu : (회귀추정의 경우) 모의실험으로 계산된 mu - 평균추정에서는 NULL값 반환
-   y : 모의 실험으로 생성된 자료
-   iter : 반복수
-   theta : 추정된 모수
-   r_vec : 이동모수
-   mse : MSE

<br> 

### 2. data
* 평균 추정과 회귀 추정에 대한 모의 실험 결과 데이터이다. 파일명에 시드 값(simul_seed), 자료 수(n), 독립변수(p)의 수가 기재되어있다.
  
     * **ex.** reg_df-set_simul_seed10_n200_p5.csv
        * 시드값 (simul_seed): 10, 자료수 (n) : 200, 독립변수 수 (p) : 5 를 셋업으로한 회귀추정 모의실험 데이터

* 100MB를 초과하는 데이터의 경우 github에서 push를 지원하지 않기 때문에 아래 dropbox에 저장하여 별도로 관리하였다.
  * https://www.dropbox.com/scl/fo/xzpmduq6x4747yjwmqia4/h?rlkey=s4gmrp1u2m3116ceip83m7uew&dl=0
<br> 

### 3. Visualization

<br> 

### 4. Confusion Matrix



