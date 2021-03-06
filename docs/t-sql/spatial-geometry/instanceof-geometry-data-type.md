---
title: InstanceOf(geometry 데이터 형식) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- InstanceOf
- InstanceOf_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- InstanceOf (geometry Data Type)
ms.assetid: fdea1248-29a4-4bab-a60d-a1b359b5e109
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3f517a0a991d36fb0371a7f2eee5e3fb4a0dacc2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47715959"
---
# <a name="instanceof-geometry-data-type"></a>InstanceOf(geometry 데이터 형식)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

**geometry** 인스턴스가 지정된 형식과 동일한 경우 테스트하는 메서드입니다. **geometry** 인스턴스의 형식이 지정한 형식과 동일하거나 지정한 형식이 인스턴스 형식의 상위 항목이면 1을 반환하고, 그렇지 않으면 0을 반환합니다.
  
## <a name="syntax"></a>구문  
  
```  
  
.InstanceOf (geometry_type )  
```  
  
## <a name="arguments"></a>인수  
 *geometry_type*  
 **geometry** 형식 계층에 노출되는 15개의 형식 중 하나를 지정하는 **nvarchar(4000)** 문자열입니다.  
  
## <a name="return-types"></a>반환 형식  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 반환 형식: **bit**  
  
 CLR 반환 형식: **SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
 메서드에 대한 입력은 **Geometry**, **Point**, **Curve**, **LineString**, **CircularString**, **CompoundCurve**, **Surface**, **Polygon**, **CurvePolygon**, **GeometryCollection**, **MultiSurface**, **MultiPolygon**, **MultiCurve**, **MultiLineString** 및 **MultiPoint** 중 하나여야 합니다. 이 메서드는 다른 문자열이 입력에 사용되면 **ArgumentException**을 throw합니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 `MultiPoint` 인스턴스를 만들고 `InstanceOf()`를 사용하여 인스턴스가 `GeometryCollection`인지 확인합니다.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('MULTIPOINT(0 0, 13.5 2, 7 19)', 0);  
SELECT @g.InstanceOf('GEOMETRYCOLLECTION');  
```  
  
## <a name="see-also"></a>참고 항목  
 [geometry 인스턴스의 확장 메서드](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

