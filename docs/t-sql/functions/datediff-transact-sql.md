---
title: DATEDIFF(Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DATEDIFF_TSQL
- DATEDIFF
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- DATEDIFF function [SQL Server]
- time [SQL Server], crossed boundaries
- differences in date and time [SQL Server]
- counting crossed date time boundaries [SQL Server]
- date and time [SQL Server], DATEDIFF
- dates [SQL Server], crossed boundaries
- boundary differences date and time [SQL Server]
- functions [SQL Server], time
- functions [SQL Server], date and time
- interval dates [SQL Server]
- time [SQL Server], functions
- crossing date time boundaries [SQL Server]
- calculating dates times [SQL Server]
ms.assetid: eba979f2-1a8d-4cce-9d75-b74f9b519b37
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 40e1027474bc84f3e30862ee43a61b3d199e8549
ms.sourcegitcommit: b58d514879f182fac74d9819918188f1688889f3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/02/2018
ms.locfileid: "50970464"
---
# <a name="datediff-transact-sql"></a>DATEDIFF(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

> [!div class="nextstepaction"]
> [SQL Server 문서 개선에 참여해주세요.](https://80s3ignv.optimalworkshop.com/optimalsort/36yyw5kq-0)

이 기능은 지정된 *startdate*와 *enddate* 사이에 지정된 datepart 경계의 수(부호 있는 정수 값으로)를 반환합니다.
  
*startdate*와 *enddate* 값 간의 더 큰 차이를 처리하는 함수는 [DATEDIFF_BIG &#40;Transact-SQL&#41;](../../t-sql/functions/datediff-big-transact-sql.md)를 참조하세요. 모든 [!INCLUDE[tsql](../../includes/tsql-md.md)]의 날짜 및 시간 데이터 형식 및 함수에 대한 개요는 [날짜 및 시간 데이터 형식 및 함수&#40;Transact-SQL&#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)을 참조하세요.
  
![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>구문  
  
```sql
DATEDIFF ( datepart , startdate , enddate )  
```  
  
## <a name="arguments"></a>인수  
*datepart*  
겹쳐지는 범위의 유형을 지정하는 *startdate*와 *enddate* 부분입니다. `DATEDIFF`은 해당하는 사용자 정의 변수 항목을 허용하지 않습니다. 이 표에서는 올바른 *datepart* 인수가 모두 나열되어 있습니다.
  
|*datepart*|약어|  
|---|---|
|**year**|**yy, yyyy**|  
|**quarter**|**qq, q**|  
|**month**|**mm, m**|  
|**dayofyear**|**dy, y**|  
|**day**|**dd, d**|  
|**week**|**wk, ww**|  
|**hour**|**hh**|  
|**minute**|**mi, n**|  
|**second**|**ss, s**|  
|**millisecond**|**ms**|  
|**microsecond**|**mcs**|  
|**nanosecond**|**ns**|  
  
*startdate*  
다음 값 중 하나를 확인할 수 있는 식입니다.

+ **date**
+ **datetime**
+ **datetimeoffset**
+ **datetime2** 
+ **smalldatetime**
+ **time**
  
모호성을 피하려면 4자리 연도를 사용하세요. 두 자리 연도 값에 대한 정보는 [두 자리 연도 구분 서버 구성 옵션 구성](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md)을 참조하세요.
  
*enddate*  
*startdate*를 참조하세요.
  
## <a name="return-type"></a>반환 형식  
 **int**  
  
## <a name="return-value"></a>반환 값  
  
-   각 특정 *datepart* 및 해당 *datepart*에 대한 약어는 동일한 값을 반환합니다.  
  
**int**에 대한 범위를 벗어난 반환 값의 경우(-2,147,483,648 to +2,147,483,647) `DATEDIFF`에서 오류를 반환합니다.  **밀리초**의 경우 *startdate*와 *enddate*의 최대 차이는 24일, 20시간, 31분 및 23.647초입니다. **초**의 경우 최대 차이는 68년입니다.
  
*startdate* 및 *enddate* 모두에 시간 값만 할당되고 *datepart*가 시간 *datepart*가 아니면 `DATEDIFF`는 0을 반환합니다.
  
`DATEDIFF`은 반환 값을 계산하기 위해 *startdate* 또는 *enddate*의 표준 시간대 오프셋 구성 요소를 사용하지 않습니다.
  
[smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md)은 분 단위까지만 정확하므로 *startdate* 또는 *enddate*에 **smalldatetime** 값이 있는 경우 반환 값에서 초와 밀리초는 항상 0으로 설정됩니다.
  
날짜 데이터 형식의 변수에 시간 값만 할당된 경우 `DATEDIFF`은 누락된 날짜 부분 값을 기본값인 1900-01-01로 설정합니다. 시간 또는 날짜 데이터 형식의 변수에 날짜 값만 할당될 경우 `DATEDIFF`은 누락된 시간 부분 값을 기본값인 00:00:00으로 설정합니다. *startdate* 또는 *enddate* 중 하나는 시간 부분만 있고 다른 하나는 날짜 부분만 있는 경우 `DATEDIFF`는 누락된 시간 및 날짜 부분을 기본값으로 설정합니다.
  
*startdate*와 *enddate*가 날짜 데이터 형식이 다르고 한 쪽의 시간 부분 또는 소수 자릿수 초의 전체 자릿수가 다른 쪽보다 많을 경우 `DATEDIFF`는 다른 쪽의 누락된 부분을 0으로 설정합니다.
  
## <a name="datepart-boundaries"></a>datepart 범위  
다음 명령문은 동일한 *startdate*와 동일한 *endate* 값을 가집니다. 이러한 날짜는 서로 인접하며 차이는 .0000001초입니다. 각 문에서 *startdate*와 *endate* 사이의 차이는 해당 *datepart*에서 하나의 달력 또는 시간 범위를 넘어섭니다. 각 문은 1을 반환합니다. *startdate* 및 *enddate*의 연도 값이 다르지만 달력 주 값이 동일한 경우 `DATEDIFF`는 *datepart* **week**에 대해 0을 반환합니다.
  
```sql
SELECT DATEDIFF(year,        '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(quarter,     '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(month,       '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(dayofyear,   '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(day,         '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(week,        '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(hour,        '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(minute,      '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(second,      '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(millisecond, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
```
  
## <a name="remarks"></a>Remarks  
SELECT, WHERE, HAVING, GROUP BY 및 ORDER BY 절에서 `DATEDIFF`를 <list>사용합니다.
  
`DATEDIFF`는 문자열 리터럴을 **datetime2** 형식으로 암시적으로 캐스팅합니다. 즉 `DATEDIFF`는 데이터가 문자열로 전달될 때 형식 YDM을 지원하지 않습니다. YDM 형식을 사용하려면 문자열을 **datetime** 또는 **smalldatetime** 형식으로 명시적으로 캐스팅해야 합니다.
  
SET DATEFIRST를 지정해도 `DATEDIFF`에는 영향을 주지 않습니다. `DATEDIFF`은 항상 일요일을 한 주의 첫 날로 사용하여 함수가 결정적으로 작동하게 합니다.
  
## <a name="examples"></a>예  
이러한 예에서는 여러 유형의 식을 *startdate* 및 *enddate* 매개 변수에 대한 인수로 사용합니다.
  
### <a name="a-specifying-columns-for-startdate-and-enddate"></a>1. startdate 및 enddate에 대한 열 지정  
이 예에서는 테이블의 두 열 사이에 겹쳐지는 날짜 범위의 수를 계산합니다.
  
```sql
CREATE TABLE dbo.Duration  
    (startDate datetime2, endDate datetime2);  
    
INSERT INTO dbo.Duration(startDate, endDate)  
    VALUES ('2007-05-06 12:10:09', '2007-05-07 12:10:09');  
    
SELECT DATEDIFF(day, startDate, endDate) AS 'Duration'  
    FROM dbo.Duration;  
-- Returns: 1  
```  
  
### <a name="b-specifying-user-defined-variables-for-startdate-and-enddate"></a>2. startdate 및 enddate에 대한 사용자 정의 변수 지정  
이 예에서는 사용자 정의 변수가 *startdate* 및 *enddate* 인수로 작용합니다.
  
```sql
DECLARE @startdate datetime2 = '2007-05-05 12:10:09.3312722';  
DECLARE @enddate   datetime2 = '2007-05-04 12:10:09.3312722';   
SELECT DATEDIFF(day, @startdate, @enddate);  
```  
  
### <a name="c-specifying-scalar-system-functions-for-startdate-and-enddate"></a>3. startdate 및 enddate에 대한 스칼라 시스템 함수 지정  
이 예에서는 스칼라 시스템 함수를 *startdate* 및 *enddate* 인수로 사용합니다.
  
```sql
SELECT DATEDIFF(millisecond, GETDATE(), SYSDATETIME());  
```  
  
### <a name="d-specifying-scalar-subqueries-and-scalar-functions-for-startdate-and-enddate"></a>4. startdate 및 enddate에 대한 스칼라 하위 쿼리 및 스칼라 함수 지정  
이 예에서는 스칼라 하위 쿼리 및 스칼라 함수를 *startdate* 및 *enddate* 인수로 사용합니다.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT DATEDIFF(day,
    (SELECT MIN(OrderDate) FROM Sales.SalesOrderHeader),  
    (SELECT MAX(OrderDate) FROM Sales.SalesOrderHeader));  
```  
  
### <a name="e-specifying-constants-for-startdate-and-enddate"></a>5. startdate 및 enddate에 대한 상수 지정  
이 예에서는 문자 상수를 *startdate* 및 *enddate* 인수로 사용합니다.
  
```sql
SELECT DATEDIFF(day,
   '2007-05-07 09:53:01.0376635',
   '2007-05-08 09:53:01.0376635');  
```  
  
### <a name="f-specifying-numeric-expressions-and-scalar-system-functions-for-enddate"></a>6. enddate에 대한 숫자 식 및 스칼라 시스템 함수 지정  
이 예에서는 `(GETDATE() + 1)` 숫자 식, `GETDATE` 스칼라 시스템 함수 및 `SYSDATETIME`을 *enddate* 인수로 사용합니다.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT DATEDIFF(day, '2007-05-07 09:53:01.0376635', GETDATE() + 1)   
    AS NumberOfDays  
    FROM Sales.SalesOrderHeader;  
GO  
USE AdventureWorks2012;  
GO  
SELECT DATEDIFF(day, '2007-05-07 09:53:01.0376635', DATEADD(day, 1, SYSDATETIME())) AS NumberOfDays  
    FROM Sales.SalesOrderHeader;  
GO  
```  
  
### <a name="g-specifying-ranking-functions-for-startdate"></a>7. startdate에 대한 순위 함수 지정  
이 예제에서는 순위 함수를 *startdate* 인수로 사용합니다.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT p.FirstName, p.LastName  
    ,DATEDIFF(day, ROW_NUMBER() OVER (ORDER BY   
        a.PostalCode), SYSDATETIME()) AS 'Row Number'  
FROM Sales.SalesPerson s   
    INNER JOIN Person.Person p   
        ON s.BusinessEntityID = p.BusinessEntityID  
    INNER JOIN Person.Address a   
        ON a.AddressID = p.BusinessEntityID  
WHERE TerritoryID IS NOT NULL   
    AND SalesYTD <> 0;  
```  
  
### <a name="h-specifying-an-aggregate-window-function-for-startdate"></a>8. startdate에 대한 집계 창 함수 지정  
이 예에서는 집계 창 함수를 *startdate* 인수로 사용합니다.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT soh.SalesOrderID, sod.ProductID, sod.OrderQty, soh.OrderDate,
    DATEDIFF(day, MIN(soh.OrderDate)   
        OVER(PARTITION BY soh.SalesOrderID), SYSDATETIME()) AS 'Total'  
FROM Sales.SalesOrderDetail sod  
    INNER JOIN Sales.SalesOrderHeader soh  
        ON sod.SalesOrderID = soh.SalesOrderID  
WHERE soh.SalesOrderID IN(43659, 58918);  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>예제: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 및 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
이러한 예에서는 여러 유형의 식을 *startdate* 및 *enddate* 매개 변수에 대한 인수로 사용합니다.
  
### <a name="i-specifying-columns-for-startdate-and-enddate"></a>9. startdate 및 enddate에 대한 열 지정  
이 예에서는 테이블의 두 열 사이에 겹쳐지는 날짜 범위의 수를 계산합니다.
  
```sql
CREATE TABLE dbo.Duration 
    (startDate datetime2, endDate datetime2);
    
INSERT INTO dbo.Duration (startDate, endDate)  
    VALUES ('2007-05-06 12:10:09', '2007-05-07 12:10:09');  
    
SELECT TOP(1) DATEDIFF(day, startDate, endDate) AS Duration  
    FROM dbo.Duration;  
-- Returns: 1  
```  
  
### <a name="j-specifying-scalar-subqueries-and-scalar-functions-for-startdate-and-enddate"></a>10. startdate 및 enddate에 대한 스칼라 하위 쿼리 및 스칼라 함수 지정  
이 예에서는 스칼라 하위 쿼리 및 스칼라 함수를 *startdate* 및 *enddate* 인수로 사용합니다.
  
```sql
-- Uses AdventureWorks  
  
SELECT TOP(1) DATEDIFF(day, (SELECT MIN(HireDate) FROM dbo.DimEmployee),  
    (SELECT MAX(HireDate) FROM dbo.DimEmployee))   
FROM dbo.DimEmployee;  
  
```  
  
### <a name="k-specifying-constants-for-startdate-and-enddate"></a>11. startdate 및 enddate에 대한 상수 지정  
이 예에서는 문자 상수를 *startdate* 및 *enddate* 인수로 사용합니다.
  
```sql
-- Uses AdventureWorks  
  
SELECT TOP(1) DATEDIFF(day,
    '2007-05-07 09:53:01.0376635',
    '2007-05-08 09:53:01.0376635') FROM DimCustomer;  
```  
  
### <a name="l-specifying-ranking-functions-for-startdate"></a>12. startdate에 대한 순위 함수 지정  
이 예제에서는 순위 함수를 *startdate* 인수로 사용합니다.
  
```sql
-- Uses AdventureWorks  
  
SELECT FirstName, LastName,
    DATEDIFF(day, ROW_NUMBER() OVER (ORDER BY   
        DepartmentName), SYSDATETIME()) AS RowNumber  
FROM dbo.DimEmployee;  
```  
  
### <a name="m-specifying-an-aggregate-window-function-for-startdate"></a>13. startdate에 대한 집계 창 함수 지정  
이 예에서는 집계 창 함수를 *startdate* 인수로 사용합니다.
  
```sql
-- Uses AdventureWorks  
  
SELECT FirstName, LastName, DepartmentName,
    DATEDIFF(year, MAX(HireDate)  
        OVER (PARTITION BY DepartmentName), SYSDATETIME()) AS SomeValue  
FROM dbo.DimEmployee  
```  
  
## <a name="see-also"></a>관련 항목:
[DATEDIFF_BIG&#40;Transact-SQL&#41;](../../t-sql/functions/datediff-big-transact-sql.md)  
[CAST 및 CONVERT&#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  


