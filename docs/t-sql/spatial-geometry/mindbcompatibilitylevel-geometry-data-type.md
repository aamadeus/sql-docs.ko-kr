---
title: MinDbCompatibilityLevel(geometry 데이터 형식) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- MinDbCompatibilityLevel method (geometry)
ms.assetid: c848b974-8ccb-4c5c-a7eb-b019a9538d99
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4cd9253f02b07cebb98dd87dc5e5b8a1180c31a1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47855751"
---
# <a name="mindbcompatibilitylevel-geometry-data-type"></a>MinDbCompatibilityLevel(geometry 데이터 형식)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

**geometry** 데이터 형식 인스턴스를 인식하는 최소 데이터베이스 호환성 수준을 반환합니다.
  
## <a name="syntax"></a>구문  
  
```  
  
.MinDbCompatibilityLevel ( )  
```  
  
## <a name="return-types"></a>반환 형식  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 반환 형식: **int**  
  
 CLR 반환 형식: **int**  
  
## <a name="remarks"></a>Remarks  
 데이터베이스의 호환성 수준을 변경하기 전에 `MinDbCompatibilityLevel()`을 사용하여 공간 개체의 호환성을 테스트할 수 있습니다.  
  
## <a name="examples"></a>예  
  
### <a name="a-testing-circularstring-type-for-compatibility-with-compatibility-level-110"></a>1. 호환성 수준 110으로 CircularString 형식의 호환성 테스트  
 다음 예에서는 `CircularString` 인스턴스에 대해 이전 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버전과의 호환성을 테스트합니다.  
  
```
 DECLARE @g geometry = 'CIRCULARSTRING(3 4, 8 9, 5 6)'; 
 IF @g.MinDbCompatibilityLevel() <= 110 
 BEGIN 
 SELECT @g.ToString(); 
 END
 ```  
  
### <a name="b-testing-linestring-type-for-compatibility-with-compatibility-level-100"></a>2. 호환성 수준 100으로 LineString 형식의 호환성 테스트  
 다음 예에서는 `LineString` 인스턴스에 대해 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]과의 호환성을 테스트합니다.  
  
```
 DECLARE @g geometry = 'LINESTRING(3 4, 8 9, 5 6)'; 
 IF @g.MinDbCompatibilityLevel() <= 100 
 BEGIN 
 SELECT @g.ToString(); 
 END
``` 
  
## <a name="see-also"></a>참고 항목  
 [ALTER DATABASE 호환성 수준&#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)  
  
  

