---
title: STGeometryType(geometry 데이터 형식) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STGeometryType_TSQL
- STGeometryType (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STGeometryType (geometry Data Type)
ms.assetid: 224cdc83-aa83-4ad4-bb82-b7481031e910
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3c91ae4decb540d80e371153504121ee22bf3ccc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47663461"
---
# <a name="stgeometrytype-geometry-data-type"></a>STGeometryType(geometry 데이터 형식)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

**geometry** 인스턴스로 표현된 OGC(Open Geospatial Consortium) 형식 이름을 반환합니다.
  
## <a name="syntax"></a>구문  
  
```  
  
.STGeometryType ( )  
```  
  
## <a name="return-types"></a>반환 형식  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 반환 형식: **nvarchar(4000)**  
  
 CLR 반환 형식: **SqlString**  
  
## <a name="remarks"></a>Remarks  
 `STGeometryType()`에 의해 반환될 수 있는 OGC 형식 이름은 **Point**, **LineString**, **CircularString**, **CompoundCurve**, **Polygon, CurvePolygon**, **GeometryCollection**, **MultiPoint**, **MultiLineString** 및  **MultiPolygon**입니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 `Polygon` 인스턴스를 만들고 `STGeometryType()`을 사용하여 이 인스턴스가 다각형인지 확인합니다.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0))', 0);  
SELECT @g.STGeometryType();  
```  
  
## <a name="see-also"></a>참고 항목  
 [geometry 인스턴스의 OGC 메서드](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

