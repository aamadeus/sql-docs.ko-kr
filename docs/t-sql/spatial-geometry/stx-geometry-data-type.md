---
title: STX(geometry 데이터 형식) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STX (geometry Data Type)
- STX_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STX (geometry Data Type)
ms.assetid: 2aef77e8-0460-43f9-bad6-2aae6d8c36f9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 85bff3199c30a05cc5f3677f9dfabc9ceac84539
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47821721"
---
# <a name="stx-geometry-data-type"></a>STX(geometry 데이터 형식)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

**Point** 인스턴스의 X 좌표 속성입니다.
  
## <a name="syntax"></a>구문  
  
```  
  
.STX  
```  
  
## <a name="return-types"></a>반환 형식  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 형식: **float**  
  
 CLR 형식: **SqlDouble**  
  
## <a name="remarks"></a>Remarks  
 **geometry** 인스턴스가 점이 아닌 경우 이 속성의 값은 Null입니다.  
  
 이 속성은 읽기 전용입니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 `Point` 인스턴스를 만들고 `STX`를 사용하여 인스턴스의 X 좌표를 검색합니다.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT(3 8)', 0);  
SELECT @g.STX;  
```  
  
## <a name="see-also"></a>참고 항목  
 [STY&#40;geometry 데이터 형식&#41;](../../t-sql/spatial-geometry/sty-geometry-data-type.md)   
 [STSrid&#40;geometry 데이터 형식&#41;](../../t-sql/spatial-geometry/stsrid-geometry-data-type.md)   
 [geometry 인스턴스의 OGC 메서드](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

