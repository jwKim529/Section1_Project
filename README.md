비디오 게임 판매량 데이터를 이용하여 게임 개발 계획 세우기
=============
사용 데이터 : Video Game Sales (https://www.kaggle.com/datasets/gregorut/videogamesales)

컬럼 정보 : 
  Rank - Ranking of overall sales
  Name - The games name
  Platform - Platform of the games release (i.e. PC,PS4, etc.)
  Year - Year of the game's release
  Genre - Genre of the game
  Publisher - Publisher of the game
  NA_Sales - Sales in North America (in millions)
  EU_Sales - Sales in Europe (in millions)
  JP_Sales - Sales in Japan (in millions)
  Other_Sales - Sales in the rest of the world (in millions)
  
데이터 전처리(Data Preprocessing) :
  - 각 컬럼의 데이터 형태 확인
  - 데이터 수 확인 및 결측치 확인, 제거
      - 발매 년도(Year)
      - 장르(Genre)
      - 공급자(Publisher)
  - 지역별 판매량 데이터를 이용하여 컬럼을 재구성
      - NA, EU, JP, Other -> SaleCountry, Sales

분석 1 : 장르/지역별로 판매량의 차이 분석
  - 데이터를 새로 추출, 이상치 제거
  - ANOVA분석 : 이원분산분석 -> 변인:장르/지역, 대상:판매량
      - p-Value가 유의수준을 넘지 못한것으로 두 변인이 대상에 영향을 주고 있다고 판단할 수 있음
        
  - barplot으로 나타내기
      - 지역별/장르별 판매량 차이를 눈으로 확인할 수 있음

분석 2 : 연도별 게임의 트렌드 분석
  
  분석 2-1 : 장르/연도별 판매량 변화 분석

  - 데이터를 새로 추출, 이상치 제거
  - 데이터 제한 : 연도별 데이터 갯수의 차이가 크며, 유의미한 데이터로서 활용할 수 있는 년도 범위가 2011~2015라고 보여져 대상 기간내의 데이터만 활용함
      - 2011년 이전, 2015년 이후의 데이터는 갯수의 차이가 큼
      - 게임 시장의 특성 상 너무 이전의 데이터는 분석에 큰 도움이 되지 않을 것이라 판단함(게임 트렌드의 변화가 매우 큼)

  - catplot으로 나타내기
      - 년도별 장르 데이터 확인
      - 장르별 데이터 확인

  - ANOVA분석 : 이원분산분석 -> 변인:장르/년도, 대상:판매량
      - p-Value가 유의수준을 넘지 못하였으므로 두 변인이 대상에 영향을 주고 있다고 판단할 수 있음

  
  
  분석 2-2 : 플랫폼/년도별 판매량 분석
  
  - 데이터를 새로 추출, 이상치 제거
  - 데이터 제한 : 2011~2015년도
  - catplot으로 나타내기
      - 년도/플랫폼별 판매량 데이터
      - 플랫폼에 따른 분석은 각 플랫폼이 독립적이지 않음 : 각 공급자의 플랫폼은 시간에 따라 새로운 기기로 변화하고 있음을 알 수 있음(Sony의 PS3->PSV->PS4 등)
      - 비디오게임의 PC시장이 축소되는 듯이 보이지만, 2022년 현재에는 다른 플랫폼 대상으로 개발/발매 이후 실적에 따라 PC에의 이식이 되는 경우가 많음

분석 3 : 판매량 순위, 각 컬럼 별 분포도 확인
  
  - 판매량 순위 1~100위 확인

  - Pie Chart
      -각 컬럼의 데이터 분포 비율 확인
      
결론 : 
개발해야 할 게임은 어떤 게임인가?

  - 장르 : 플랫폼 게임 / 슈팅 게임
  - 플랫폼 : 높은 비율의 공급자(Nintendo, Activision 등)의 플랫폼을 대상으로 개발 진행, 이후 판매실적에 따라 PC 이식 여부 결정
