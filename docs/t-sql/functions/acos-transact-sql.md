---
title: ACOS(Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ACOS
- ACOS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- cosine
- ACOS function
- arccosine
ms.assetid: 4ec6b46e-9438-4f0f-8b96-461edd84280a
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 30d32ba62d033713435ee25cdedf738271bf4a1f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47675391"
---
# <a name="acos-transact-sql"></a>ACOS(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

지정된 float 식을 코사인 값으로 가지는 각도를 라디안 단위로 반환하는 기능입니다. 이를 아크코사인이라고도 합니다.
  
![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>구문  
  
```sql
ACOS ( float_expression )  
```  
  
## <a name="arguments"></a>인수  
*float_expression*  
**float** 형식 또는 float로 암시적으로 변환할 수 있는 형식의 [식](../../t-sql/language-elements/expressions-transact-sql.md)입니다. -1.00에서 1.00까지의 값만 유효합니다. 값이 이 범위를 벗어나면 NULL이 반환되고 ASIN에서 도메인 오류가 보고됩니다.
  
## <a name="return-types"></a>반환 형식  
**float**
  
## <a name="examples"></a>예  
이 예에서는 지정된 수의 `ACOS` 값을 반환합니다.
  
```sql
SET NOCOUNT OFF;  
DECLARE @cos float;  
SET @cos = -1.0;  
SELECT 'The ACOS of the number is: ' + CONVERT(varchar, ACOS(@cos));  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
---------------------------------   
The ACOS of the number is: 3.14159   
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>관련 항목:
[수치 연산 함수&#40;Transact-SQL&#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)  
[함수](../../t-sql/functions/functions.md)
  
  

