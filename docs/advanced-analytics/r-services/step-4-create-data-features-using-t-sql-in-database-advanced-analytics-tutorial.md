---
title: "4단계: T-SQL을 사용하여 데이터 기능 만들기(데이터베이스 내 고급 분석 자습서) | Microsoft Docs"
ms.custom: ""
ms.date: "04/19/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
  - "TSQL"
ms.assetid: 5b2f4c44-6192-40df-abf1-fc983844f1d0
caps.latest.revision: 10
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 10
---
# 4단계: T-SQL을 사용하여 데이터 기능 만들기(데이터베이스 내 고급 분석 자습서)
데이터 탐색을 여러 번 수행한 후 데이터에서 몇 가지 유용한 정보를 수집했으며 *기능 엔지니어링*으로 넘어갈 준비가 되었습니다. 원시 데이터에서 기능을 만드는 이 프로세스는 고급 모델링 분석에서 중요한 단계입니다.  
  
이 단계에서는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 함수를 사용하여 원시 데이터에서 기능을 만드는 방법을 알아봅니다. 그런 다음 저장 프로시저에서 해당 함수를 호출하여 기능 값이 포함된 테이블을 만듭니다.  
  
## 함수 정의  
원래 데이터에 보고된 거리 값은 보고된 미터 거리를 기반으로 하며 지리적 거리 또는 이동한 거리를 나타내지 않을 수도 있습니다. 따라서 원본 NYC Taxi 데이터 집합에서 사용할 수 있는 좌표를 통해 승하차 지점 사이의 직접 거리를 계산해야 합니다. 이렇게 하려면 사용자 지정 [!INCLUDE[tsql](../../includes/tsql-md.md)] 함수에 [Haversine 수식](https://en.wikipedia.org/wiki/Haversine_formula)을 사용합니다.  
  
사용자 지정 T-SQL 함수 _fnCalculateDistance_를 사용하여 Haversine 수식을 통해 거리를 계산하고 두 번째 사용자 지정 T-SQL 함수 _fnEngineerFeatures_를 사용하여 모든 기능이 포함된 테이블을 만듭니다.  
  
#### FnCalculateDistance를 사용하여 여정 거리를 계산하려면  
  
1.  이 연습을 위한 준비 과정에서 _fnCalculateDistance_ 함수를 다운로드하고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 등록한 상태여야 합니다. 코드 검토  
  
    [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 **프로그래밍 기능**, **함수**, **스칼라 반환 함수**를 차례로 확장합니다.   
    _fnCalculateDistance_를 마우스 오른쪽 단추로 클릭하고 **수정**을 선택하여 새 쿼리 창에서 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트를 엽니다.  
  
    ```  
    CREATE FUNCTION [dbo].[fnCalculateDistance] (@Lat1 float, @Long1 float, @Lat2 float, @Long2 float)  
    -- User-defined function that calculates the direct distance between two geographical coordinates.  
    RETURNS float  
    AS  
    BEGIN  
      DECLARE @distance decimal(28, 10)  
      -- Convert to radians  
      SET @Lat1 = @Lat1 / 57.2958  
      SET @Long1 = @Long1 / 57.2958  
      SET @Lat2 = @Lat2 / 57.2958  
      SET @Long2 = @Long2 / 57.2958  
      -- Calculate distance  
      SET @distance = (SIN(@Lat1) * SIN(@Lat2)) + (COS(@Lat1) * COS(@Lat2) * COS(@Long2 - @Long1))  
      --Convert to miles  
      IF @distance <> 0  
      BEGIN  
        SET @distance = 3958.75 * ATAN(SQRT(1 - POWER(@distance, 2)) / @distance);  
      END  
      RETURN @distance  
    END  
    GO  
  
    ```  
  
    -   함수는 스칼라 반환 함수이며, 미리 정의된 형식의 단일 데이터 값을 반환합니다.  
  
    -   여정 승하차 위치에서 얻은 위도 및 경도 값을 입력으로 사용합니다. Haversine 수식은 위치를 라디안으로 변환하고 해당 값을 사용하여 두 위치 사이의 직접 거리(마일)를 계산합니다.  
  
모델 학습에 사용할 수 있는 테이블에 계산 값을 추가하려면 다른 함수 _fnEngineerFeatures_를 사용합니다.  
  
#### _fnEngineerFeatures_를 사용하여 기능을 저장하려면  
  
1.  이 연습을 위한 준비 과정에서 만들어진 사용자 지정 T-SQL 함수 _fnEngineerFeatures_의 코드를 검토합니다.  
  
    이 함수는 여러 열을 입력으로 사용하고 여러 기능 열이 있는 테이블을 출력하는 테이블 반환 함수입니다.  이 함수는 모델 작성에 사용할 기능 집합을 만드는 데 사용됩니다. _fnEngineerFeatures_ 함수는 이전에 만든 T-SQL 함수 _fnCalculateDistance_를 호출하여 승하차 위치 사이의 직접 거리를 가져옵니다.  
  
    ```  
    CREATE FUNCTION [dbo].[fnEngineerFeatures] (  
    @passenger_count int = 0,  
    @trip_distance float = 0,  
    @trip_time_in_secs int = 0,  
    @pickup_latitude float = 0,  
    @pickup_longitude float = 0,  
    @dropoff_latitude float = 0,  
    @dropoff_longitude float = 0)  
    RETURNS TABLE  
    AS  
      RETURN  
      (  
      -- Add the SELECT statement with parameter references here  
      SELECT  
        @passenger_count AS passenger_count,  
        @trip_distance AS trip_distance,  
        @trip_time_in_secs AS trip_time_in_secs,  
        [dbo].[fnCalculateDistance](@pickup_latitude, @pickup_longitude, @dropoff_latitude, @dropoff_longitude) AS direct_distance  
  
      )  
    GO  
  
    ```  
  
2.  이 함수가 작동하는지 확인하려면 함수를 사용하여 미터 거리가 0이지만 승하차 위치가 서로 다른 여정의 지리적 거리를 계산합니다.  
  
    ```  
        SELECT tipped, fare_amount, passenger_count,(trip_time_in_secs/60) as TripMinutes,  
        trip_distance, pickup_datetime, dropoff_datetime,   
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) AS direct_distance  
        FROM nyctaxi_sample  
        WHERE pickup_longitude != dropoff_longitude and pickup_latitude != dropoff_latitude and trip_distance = 0  
        ORDER BY trip_time_in_secs DESC  
    ```  
  
    확인한 것처럼 미터에서 보고된 거리가 항상 지리적 거리와 일치하는 것은 아닙니다. 이 때문에 기능 엔지니어링이 중요합니다.  
  
다음 단계에서는 이러한 데이터 기능을 사용하여 R을 통해 Machine Learning 모델을 학습하는 방법을 알아봅니다.  
  
## 다음 단계  
[5단계: T-SQL을 사용하여 모델 학습 및 저장](../../advanced-analytics/r-services/step-5-train-and-save-a-model-using-t-sql.md)  
  
## 이전 단계  
[3단계: 데이터 탐색 및 시각화](../../advanced-analytics/r-services/step-3-explore-and-visualize-the-data-in-database-advanced-analytics-tutorial.md)  
  
## 참고 항목  
[SQL 개발자를 위한 데이터베이스 내 고급 분석&#40;자습서&#41;](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md)  
[SQL Server R Services 자습서](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)  
  
  
  