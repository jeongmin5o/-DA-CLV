# CLV

- 사용자가 앱 사용을 중단할 때까지 **기업이 해당 고객에게서 벌어들이는 수입을 의미**
- 고객의 생애 가치는 > 고객을 확보하는 데 소요되는 비용보다 더 많아야 합니다. 
- 이 수치가 너무 낮으면 마케팅에 너무 많은 비용을 지출하거나 효과적으로 사용하지 않고 있다는 것을 보여주며, 
- 반대로 너무 높으면 마케팅에 충분한 비용을 지출하지 않고 있기 때문에 더 많은 예산을 투자하면 효과적으로 더 빠르게 성장할 수 있다는 것을 보여줌


## CLV 어떻게 계산해?

계산하는 것은 2가지 방법이 있다.


  
### 1️⃣ 현재 고객 데이터를 공식에 대입하여 CLV 도출  -> 현재 고객의 가치 단순 측정
    
    ▶️ (기본) 데이터 프레임 생성
    1) 각 고객별 TOTAL PRICE 구하기 
      = 평균 주문 총액 * 1년 평균 구매 횟수 * 평균 유지 시간(년)
    2) 고객 ID 기준으로 TOTAL_TRANSACTION, TOTAL_UNIT, TOTAL_PRICE 구하기
      TOTAL_TRANSACTION: 영수증 번호(청구서) 중복값 제거한 갯수 
      TOTAL_UNIT: 구매수량의 합
      TOTAL_PRICE:  TOTAL_PRICE의 합 

    ▶️ 각 지표 계산
    1) Average Order Value(평균주문금액) = total_price / total_transaction0
    2) Purchase Frequency(구매빈도) =  (total_transaction / total_number_of_customers
    3) Repeat Rate & Churn Rate(반복률 및 이탈률)
      repeat_rate = 2개 이상 TOTAL_TRANSACTION 갯수/ 전체 갯수
      Churn Rate = 1 - 반복률

    4) Profit Margin(이익마진)  = total_price * 0.10
    5) Customer Value(고객 가치) = average_order_value * purchase_frequency
    6) Customer Lifetime Value(고객 평생가치_CLTV) = (customer_value / churn_rate) x profit_margin



### 2️⃣ lieftime 패키지를 통해서 고객 CLV 예측값 도출  -> 미래 고객의 가치 확인
**Lifetime package**

liffetimes 패키지는 아래 두가지의 전제를 갖는다

    1. 사용자는 “살아있을 때(alive)” 상호 작용한다
    2. 연구중인 사용자는 일정 기간 후에 “사망(die)” 할 수 있다.

이커머스에서 lifetime package를 활용해보면,고객의 반복 구매를 예측할 수 있다.

**alive = 적극적 구매
die = 제품에 무관심**


    ▶️ 기본적인 변수 설명
    Recency = 마지막 구매 이후 경과 시간 [주간]
    T = 첫 번째 구매가 이루어진 분석 날짜 이전의 시간 [주간]
    빈도 = 반복 구매의 총 횟수
    money_value = 구매당 평균 수입

** 에러! **
📝Try adding a larger penalizer to see if that helps convergence.
Recency = 0 인경우 에러메세지가 뜬다!
그러니 Recency가 0인 값은 제외하고 보던가, Recency 구하는 현재 날짜를 하루 뒤로 

### 해석 방법


참고한 블로그 : https://2innnnn0.github.io/geultto/python_lifetime_1/

https://python.plainenglish.io/customer-lifetime-value-calculation-clv-296827dc949e

https://python.plainenglish.io/how-to-predict-customer-lifetime-value-clv-in-python-bg-nbd-and-gamma-gamma-method-154a590b5175
