---
title: POWER (Transact SQL) | Microsoft Docs
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
- POWER_TSQL
- POWER
dev_langs:
- TSQL
helpviewer_keywords:
- POWER function
ms.assetid: 0fd34494-90b9-4559-8011-a8c1b9f40239
caps.latest.revision: 41
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: cb1f3ca862c070888a8e8cb5265f582dcf47d4aa
ms.contentlocale: ko-kr
ms.lasthandoff: 09/01/2017

---
# <a name="power-transact-sql"></a>POWER(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  지정된 식을 거듭제곱한 값을 반환합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
POWER ( float_expression , y )  
```  
  
## <a name="arguments"></a>인수  
 *float_expression*  
 이 [식](../../t-sql/language-elements/expressions-transact-sql.md) 형식의 **float** 또는 암시적으로 변환할 수 있는 형식의 **float**합니다.  
  
 *y*  
 구할 거듭제곱입니다 *float_expression*합니다. *y* 제외한 정확한 수치 또는 근사치 숫자 데이터 형식 범주의 식일 수 있습니다는 **비트** 데이터 형식입니다.  
  
## <a name="return-types"></a>반환 형식  
 전송과 같은 유형을 반환 *float_expression*합니다. 예를 들어 경우는 **10 진수**(2, 0)으로 제출 됩니다 *float_expression*, 반환 된 결과 **10 진수**(2, 0).  
  
## <a name="examples"></a>예  
  
### <a name="a-using-power-to-return-the-cube-of-a-number"></a>1. POWER를 사용하여 숫자의 세제곱 반환  
 다음 예에서는 3의 승수로 거듭 제곱한 수(숫자의 세제곱)를 보여줍니다.  
  
```  
DECLARE @input1 float;  
DECLARE @input2 float;  
SET @input1= 2;  
SET @input2 = 2.5;  
SELECT POWER(@input1, 3) AS Result1, POWER(@input2, 3) AS Result2;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result1                Result2  
---------------------- ----------------------  
8                      15.625  
  
(1 row(s) affected)  
```  
  
### <a name="b-using-power-to-show-results-of-data-type-conversion"></a>2. POWER를 사용하여 데이터 형식 자동 변환 표시  
 다음 예제와 방법을 *float_expression* 예기치 않은 결과 반환할 수 있는 데이터 형식을 유지 합니다.  
  
```  
SELECT   
POWER(CAST(2.0 AS float), -100.0) AS FloatResult,  
POWER(2, -100.0) AS IntegerResult,  
POWER(CAST(2.0 AS int), -100.0) AS IntegerResult,  
POWER(2.0, -100.0) AS Decimal1Result,  
POWER(2.00, -100.0) AS Decimal2Result,  
POWER(CAST(2.0 AS decimal(5,2)), -100.0) AS Decimal2Result;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
FloatResult            IntegerResult IntegerResult Decimal1Result Decimal2Result Decimal2Result  
---------------------- ------------- ------------- -------------- -------------- --------------  
7.88860905221012E-31   0             0             0.0            0.00           0.00  
```  
  
### <a name="c-using-power"></a>3. POWER 사용  
 다음 예에서는 `POWER`에 대한 `2` 결과를 반환합니다.  
  
```  
DECLARE @value int, @counter int;  
SET @value = 2;  
SET @counter = 1;  
  
WHILE @counter < 5  
   BEGIN  
      SELECT POWER(@value, @counter)  
      SET NOCOUNT ON  
      SET @counter = @counter + 1  
      SET NOCOUNT OFF  
   END;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
-----------   
2             
  
(1 row(s) affected)  
  
-----------   
4             
  
(1 row(s) affected)  
  
-----------   
8             
  
(1 row(s) affected)  
  
-----------   
16            
  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>예: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 및[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-using-power-to-return-the-cube-of-a-number"></a>D: POWER를 사용 하 여 숫자의 세제곱 반환 하는  
 다음 예제에서는 반환 `POWER` 에 대 한 결과 `2.0` 3 제곱 합니다.  
  
```  
SELECT POWER(2.0, 3);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `------------`  
  
 `8.0`  
  
## <a name="see-also"></a>관련 항목:  
 [decimal 및 numeric&#40; Transact SQL &#41;](../../t-sql/data-types/decimal-and-numeric-transact-sql.md)   
 [float 및 real &#40; Transact SQL &#41;](../../t-sql/data-types/float-and-real-transact-sql.md)   
 [int, bigint, smallint 및 tinyint &#40; Transact SQL &#41;](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)   
 [수치 연산 함수 &#40; Transact SQL &#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)   
 [money 및 smallmoney &#40; Transact SQL &#41;](../../t-sql/data-types/money-and-smallmoney-transact-sql.md)  
  
  

