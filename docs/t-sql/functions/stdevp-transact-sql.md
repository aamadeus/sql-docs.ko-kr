---
title: STDEVP (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STDEVP
- STDEVP_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STDEVP function [Transact-SQL]
- expressions [SQL Server], statistical standard deviation
- statistical standard deviation
ms.assetid: 29f2a906-d084-4464-abc3-4b275ed19442
caps.latest.revision: 45
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: abda0ca087c75f67e295e4ce493834f13b37e5f3
ms.contentlocale: ko-kr
ms.lasthandoff: 09/01/2017

---
# <a name="stdevp-transact-sql"></a>STDEVP(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  지정한 식에 있는 모든 값의 모집단에 대한 통계적 표준 편차를 반환합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
STDEVP ( [ ALL | DISTINCT ] expression )   
   OVER ( [ partition_by_clause ] order_by_clause )    
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
-- Aggregate Function Syntax   
STDEVP ( [ ALL | DISTINCT ] expression )  
  
-- Analytic Function Syntax   
STDEVP (expression) OVER ( [ partition_by_clause ] order_by_clause)  
```  
  
## <a name="arguments"></a>인수  
 **ALL**  
 모든 값에 함수를 적용합니다. 기본값은 ALL입니다.  
  
 DISTINCT  
 각 고유 값을 고려하도록 지정합니다.  
  
 *expression*  
 숫자는 [식](../../t-sql/language-elements/expressions-transact-sql.md)합니다. 집계 함수와 하위 쿼리는 허용되지 않습니다. *식* 제외한 정확한 수치 또는 근사치 숫자 데이터 형식 범주의 식이 **비트** 데이터 형식입니다.  
  
 통해 **(** [ *partition_by_clause* ] *order_by_clause***)**  
 *partition_by_clause* 함수가 적용 되는 파티션으로 FROM 절에서 생성 한 결과 집합을 나눕니다. 지정하지 않을 경우 쿼리 결과 집합의 모든 행이 단일 그룹으로 취급됩니다. *order_by_clause* 작업이 수행 되는 논리적 순서를 결정 합니다. *order_by_clause* 가 필요 합니다. 자세한 내용은 참조 [OVER 절 &#40; Transact SQL &#41; ](../../t-sql/queries/select-over-clause-transact-sql.md).  
  
## <a name="return-types"></a>반환 형식  
 **float**  
  
## <a name="remarks"></a>주의  
 STDEVP가 SELECT 문의 모든 항목에서 사용되는 경우 결과 집합의 각 값이 계산에 포함됩니다. STDEVP와 함께 사용할 수 있는 것은 숫자 열뿐입니다. Null 값은 무시됩니다.  
  
 STDEVP는 OVER 및 ORDER BY 절 없이 사용되는 경우 결정적 함수이고, OVER 및 ORDER BY 절과 함께 지정되는 경우 비결정적 함수입니다. 자세한 내용은 [Deterministic and Nondeterministic Functions](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md)을 참조하세요.  
  
## <a name="examples"></a>예  
  
### <a name="a-using-stdevp"></a>A: STDEVP를 사용 하 여  
 다음은 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 데이터베이스의 `SalesPerson` 테이블에 있는 모든 보너스 값의 모집단에 대한 표준 편차를 반환하는 예입니다.  
  
```  
SELECT STDEVP(Bonus)  
FROM Sales.SalesPerson;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>예: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 및[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-using-stdevp"></a>B: STDEVP을 사용 하 여  
 다음 예제에서는 반환 된 `STDEVP` 테이블의 판매 할당량 값의 `dbo.FactSalesQuota`합니다. 첫 번째 열의 모든 고유 값의 표준 편차를 포함 하 고 모든 중복 값을 포함 한 모든 값의 표준 편차를 포함 하는 두 번째 열입니다.  
  
```  
-- Uses AdventureWorks  
  
SELECT STDEVP(DISTINCT SalesAmountQuota)AS Distinct_Values, STDEVP(SalesAmountQuota) AS All_Values  
FROM dbo.FactSalesQuota;SELECT STDEVP(DISTINCT Quantity)AS Distinct_Values, STDEVP(Quantity) AS All_Values  
FROM ProductInventory;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Distinct_Values   All_Values`  
  
 `----------------  ----------------`  
  
 `397676.79         397226.44`  
  
### <a name="c-using-stdevp-with-over"></a>3. STDEVP OVER 사용  
 다음 예제에서는 반환 된 `STDEVP` 역 년의 분기별 판매 할당량 값의 합니다. `ORDER BY` 절의 `OVER`는 `STDEVP`을 정렬하고 `ORDER BY` 문의 `SELECT`는 결과 집합을 정렬합니다.  
  
```  
-- Uses AdventureWorks  
  
SELECT CalendarYear AS Year, CalendarQuarter AS Quarter, SalesAmountQuota AS SalesQuota,  
       STDEVP(SalesAmountQuota) OVER (ORDER BY CalendarYear, CalendarQuarter) AS StdDeviation  
FROM dbo.FactSalesQuota  
WHERE EmployeeKey = 272 AND CalendarYear = 2002  
ORDER BY CalendarQuarter;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Year  Quarter  SalesQuota              StdDeviation`  
  
 `----  -------  ----------------------  -------------------`  
  
 `2002  1         91000.0000             0.00`  
  
 `2002  2        140000.0000             24500.00`  
  
 `2002  3         70000.0000             29329.55`  
  
 `2002  4        154000.0000             34426.55`  
  
## <a name="see-also"></a>관련 항목:  
 [집계 함수 &#40; Transact SQL &#41;](../../t-sql/functions/aggregate-functions-transact-sql.md)   
 [절 &#40; 조치 Transact SQL &#41;](../../t-sql/queries/select-over-clause-transact-sql.md)  
  
  

