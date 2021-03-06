---
title: SET ANSI_NULLS(Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 12/04/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SET_ANSI_NULLS_TSQL
- ANSI_NULLS
- SET ANSI_NULLS
- ANSI_NULLS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SET ANSI_NULLS statement
- not equal to operator (<>)
- ANSI_NULLS option
- equals operator (=)
- null values [SQL Server], comparison operators
- comparison operators [SQL Server], null values
ms.assetid: aae263ef-a3c7-4dae-80c2-cc901e48c755
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c82f0b10a692f4f1d146a6916657186d17632a15
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47597472"
---
# <a name="set-ansinulls-transact-sql"></a>SET ANSI_NULLS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]의 Null 값과 함께 사용될 경우 Equals(=)와 Not Equal To(<>) 비교 연산자의 ISO 호환 동작을 지정합니다.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 이후 버전에서는 ANSI_NULLS가 ON으로 설정되고 명시적으로 이 옵션을 OFF로 설정한 응용 프로그램에서는 오류가 발생합니다. 새 개발 작업에서는 이 기능을 사용하지 않도록 하고, 현재 이 기능을 사용하는 응용 프로그램은 수정하세요.
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  

## <a name="syntax"></a>구문

```
-- Syntax for SQL Server

SET ANSI_NULLS { ON | OFF }
```

```
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse

SET ANSI_NULLS ON
```

## <a name="remarks"></a>Remarks  
 SET ANSI_NULLS 옵션이 ON인 경우, WHERE *column_name* = **NULL**을 사용하는 SELECT 문은 *column_name*에 Null 값이 있어도 0행을 반환합니다. WHERE *column_name* <> **NULL**을 사용하는 SELECT 문은 *column_name*에 Null 이외의 값이 있어도 0행을 반환합니다.  
  
 SET ANSI_NULLS 옵션이 OFF면 Equals(=)와 Not Equal(<>) 비교 연산자가 ISO 표준을 따르지 않습니다. WHERE *column_name* = **NULL**을 사용하는 SELECT 문은 *column_name*에 Null 값이 있는 행을 반환합니다. WHERE *column_name* <> **NULL**을 사용하는 SELECT 문은 열에 Null 이외의 값이 있는 행을 반환합니다. 또한 WHERE *column_name* <> *XYZ_value*를 사용하는 SELECT 문은 *XYZ_value*가 아니고 NULL이 아닌 모든 행을 반환합니다.  
  
 SET ANSI_NULLS 옵션이 ON이면, NULL 값에 대한 모든 비교가 UNKNOWN이 됩니다. ANSI_NULLS 옵션이 OFF면 데이터 값이 NULL일 때 null 값에 대한 모든 데이터의 비교가 TRUE가 됩니다. SET ANSI_NULLS를 지정하지 않으면 현재 데이터베이스의 ANSI_NULLS 옵션 설정이 적용됩니다. ANSI_NULLS 데이터베이스 옵션에 대한 자세한 내용은 [ALTER DATABASE&#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)를 참조하세요.  

 다음 표에서는 ANSI_NULLS 설정이 null과 null이 아닌 값을 사용하여 많은 부울 식의 결과에 어떤 영향을 미치는지를 보여 줍니다.  
  
|부울 식(Boolean Expression)|SET ANSI_NULLS ON|SET ANSI_NULLS OFF|  
|---------------|---------------|------------|  
|NULL = NULL|UNKNOWN|TRUE|  
|1 = NULL|UNKNOWN|FALSE|  
|NULL <> NULL|UNKNOWN|FALSE|  
|1 <> NULL|UNKNOWN|TRUE|  
|NULL > NULL|UNKNOWN|UNKNOWN|  
|1 > NULL|UNKNOWN|UNKNOWN|  
|NULL IS NULL|TRUE|TRUE|  
|1 IS NULL|FALSE|FALSE|  
|NULL IS NOT NULL|FALSE|FALSE|  
|1 IS NOT NULL|TRUE|TRUE|  

 SET ANSI_NULLS ON 옵션은 비교의 피연산자 중 하나가 NULL 변수 또는 리터럴 NULL 변수인 경우에만 해당 비교에 영향을 줍니다. 비교의 양쪽이 열 또는 복합 식인 경우에는 설정이 비교에 영향을 주지 않습니다.  
  
 ANSI_NULLS 데이터베이스 옵션이나 SET ANSI_NULLS 설정에 관계없이 스크립트가 의도했던 대로 실행되도록 하려면 Null 값을 포함할 수 있는 비교에 IS NULL과 IS NOT NULL을 사용하십시오.  
  
 분산 쿼리를 실행할 때는 SET ANSI_NULLS를 ON으로 설정해야 합니다.  
  
 계산 열이나 인덱싱된 뷰에서 인덱스를 만들거나 변경할 때는 SET ANSI_NULLS 옵션도 ON으로 설정해야 합니다. SET ANSI_NULLS 옵션이 OFF면 계산 열의 인덱스가 있는 테이블이나 인덱싱된 뷰에서 CREATE, UPDATE, INSERT, DELETE 문이 실패합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 필요한 값을 위반하는 모든 SET 옵션이 나열된 오류를 반환합니다. 뿐만 아니라 SELECT 문 실행 시 SET ANSI_NULLS 옵션이 OFF면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 계산 열이나 뷰의 인덱스 값을 무시하고 테이블이나 뷰에 이러한 인덱스가 없는 것처럼 SELECT 작업을 처리합니다.  
  
> [!NOTE]  
>  ANSI_NULLS는 계산 열이나 인덱싱된 뷰의 인덱스를 처리할 때 필요한 값으로 설정해야 하는 7가지 SET 옵션 중 하나입니다. ANSI_PADDING, ANSI_WARNINGS, ARITHABORT, QUOTED_IDENTIFIER 및 CONCAT_NULL_YIELDS_NULL은 ON으로 설정해야 하지만 NUMERIC_ROUNDABORT는 OFF로 설정해야 합니다.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]용 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 연결될 때 자동으로 ANSI_NULLS를 ON으로 설정합니다. ODBC 데이터 원본과 ODBC 연결 특성 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결하기 전에 응용 프로그램에 설정된 OLE DB 연결 속성에서 이 설정을 구성할 수 있습니다. SET ANSI_NULLS의 기본값은 OFF입니다.  
  
 SET ANSI_DEFAULTS 옵션이 ON이면 SET ANSI_NULLS 옵션이 설정됩니다.  
  
 SET ANSI_NULLS 옵션은 실행 시간 또는 런타임에 설정되며, 구문 분석 시에는 설정되지 않습니다.  
  
 이 설정에 대한 현재 설정을 보려면 다음 쿼리를 실행합니다.
  
```  
DECLARE @ANSI_NULLS VARCHAR(3) = 'OFF';  
IF ( (32 & @@OPTIONS) = 32 ) SET @ANSI_NULLS = 'ON';  
SELECT @ANSI_NULLS AS ANSI_NULLS;  
  
```  
  
## <a name="permissions"></a>Permissions  
 public 역할의 멤버 자격이 필요합니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 Equals(`=`)와 Not Equal To(`<>`) 비교 연산자를 사용하여 테이블의 `NULL` 및 Null이 아닌 값에 비교를 수행합니다. 또한 `IS NULL`이 `SET ANSI_NULLS` 설정의 영향을 받지 않는다는 것을 보여 줍니다.  
  
```  
-- Create table t1 and insert values.  
CREATE TABLE dbo.t1 (a INT NULL);  
INSERT INTO dbo.t1 values (NULL),(0),(1);  
GO  
  
-- Print message and perform SELECT statements.  
PRINT 'Testing default setting';  
DECLARE @varname int;   
SET @varname = NULL;  
  
SELECT a  
FROM t1   
WHERE a = @varname;  
  
SELECT a   
FROM t1   
WHERE a <> @varname;  
  
SELECT a   
FROM t1   
WHERE a IS NULL;  
GO  
  
-- SET ANSI_NULLS to ON and test.  
PRINT 'Testing ANSI_NULLS ON';  
SET ANSI_NULLS ON;  
GO  
DECLARE @varname int;  
SET @varname = NULL  
  
SELECT a   
FROM t1   
WHERE a = @varname;  
  
SELECT a   
FROM t1   
WHERE a <> @varname;  
  
SELECT a   
FROM t1   
WHERE a IS NULL;  
GO  
  
-- SET ANSI_NULLS to OFF and test.  
PRINT 'Testing SET ANSI_NULLS OFF';  
SET ANSI_NULLS OFF;  
GO  
DECLARE @varname int;  
SET @varname = NULL;  
SELECT a   
FROM t1   
WHERE a = @varname;  
  
SELECT a   
FROM t1   
WHERE a <> @varname;  
  
SELECT a   
FROM t1   
WHERE a IS NULL;  
GO  
  
-- Drop table t1.  
DROP TABLE dbo.t1;  
  
```  
  
## <a name="see-also"></a>참고 항목  
 [SET 문&#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SESSIONPROPERTY&#40;Transact-SQL&#41;](../../t-sql/functions/sessionproperty-transact-sql.md)   
 [=&#40;같음&#41;&#40;Transact-SQL&#41;](../../t-sql/language-elements/equals-transact-sql.md)   
 [IF...ELSE&#40;Transact-SQL&#41;](../../t-sql/language-elements/if-else-transact-sql.md)   
 [&#60;&#62; &#40;같지 않음&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/not-equal-to-transact-sql-traditional.md)   
 [SET 문&#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET ANSI_DEFAULTS &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-defaults-transact-sql.md)   
 [WHERE&#40;Transact-SQL&#41;](../../t-sql/queries/where-transact-sql.md)   
 [WHILE&#40;Transact-SQL&#41;](../../t-sql/language-elements/while-transact-sql.md)  
  
  
