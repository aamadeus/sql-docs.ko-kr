---
title: "STDistance (geometry 데이터 형식) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STDistance_TSQL
- STDistance (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STDistance (geometry Data Type)
ms.assetid: ac815bc7-5342-4cc4-af40-c80a1c4c8b68
caps.latest.revision: 24
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ddb0d02f5bf4655acd97ba83484ac1d902420d9a
ms.contentlocale: ko-kr
ms.lasthandoff: 09/01/2017

---
# <a name="stdistance-geometry-data-type"></a>STDistance(geometry 데이터 형식)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  점 간 최단 거리를 반환 합니다.는 **geometry** 인스턴스와 다른 지점 **geometry** 인스턴스.  
  
## <a name="syntax"></a>구문  
  
```  
  
.STDistance ( other_geometry )  
```  
  
## <a name="arguments"></a>인수  
 *other_geometry*  
 다른 **geometry** 인스턴스 사이의 거리를 측정 하는 인스턴스 `STDistance()` 가 호출 됩니다. 경우 *other_geometry* 는 빈 집합 `STDistance()` null을 반환 합니다.  
  
## <a name="return-types"></a>반환 형식  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]반환 형식: **float**  
  
 CLR 반환 형식: **SqlDouble**  
  
## <a name="remarks"></a>주의  
 `STDistance()`항상 경우 null을 반환의 spatial reference Id (Srid)는 **geometry** 인스턴스 일치 하지 않습니다.  
  
## <a name="examples"></a>예  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 2 0, 2 2, 0 2, 0 0))', 0);  
SET @h = geometry::STGeomFromText('POINT(10 10)', 0);  
SELECT @g.STDistance(@h);  
```  
  
## <a name="see-also"></a>관련 항목:  
 [공간 인덱스 개요](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [Geometry 인스턴스의 OGC 메서드](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  
