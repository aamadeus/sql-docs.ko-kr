---
title: "STGeometryN (geometry 데이터 형식) | Microsoft Docs"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STGeometryN_TSQL
- STGeometryN (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STGeometryN (geometry Data Type)
ms.assetid: 348c7047-3442-4590-8879-fe841e79058c
caps.latest.revision: 19
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: fe227cc574662025aa43016ca3f053ad36bf0678
ms.contentlocale: ko-kr
ms.lasthandoff: 09/01/2017

---
# <a name="stgeometryn-geometry-data-type"></a>STGeometryN(geometry 데이터 형식)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

지정한 기 하 도형을 반환는 **기 하 도형 컬렉션**합니다.
  
## <a name="syntax"></a>구문  
  
```  
  
.STGeometryN ( expression )  
```  
  
## <a name="arguments"></a>인수  
 *expression*  
 이 **int** 1과 수의 식 **기 하 도형** 인스턴스에 **geometrycollection**합니다.  
  
## <a name="return-types"></a>반환 형식  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]반환 형식: **기 하 도형**  
  
 CLR 반환 형식: **SqlGeometry**  
  
## <a name="remarks"></a>주의  
 이 메서드가 반환 **null** 매개 변수가의 결과 보다 크면 `STNumGeometries()` throw 됩니다는 **ArgumentOutOfRangeException** 경우는 *식* 매개 변수가 1 보다 작은 경우  
  
## <a name="examples"></a>예  
 다음 예제에서는 한 `MultiPoint``geometry collection` 사용 하 여 `STGeometryN()` 두 번째 찾으려고 `geometry` 컬렉션의 인스턴스.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('MULTIPOINT(0 0, 13.5 2, 7 19)', 0);  
SELECT @g.STGeometryN(2).ToString();  
```  
  
## <a name="see-also"></a>관련 항목:  
 [Geometry 인스턴스의 OGC 메서드](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

