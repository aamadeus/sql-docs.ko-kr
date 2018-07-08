---
title: Polygon | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-spatial
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- geometry subtypes [SQL Server]
- Polygon geometry subtype [SQL Server]
ms.assetid: b6a21c3c-fdb8-4187-8229-1c488454fdfb
caps.latest.revision: 25
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 6a76fc29f234418e5f44586f4fb7e121c3395264
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36187374"
---
# <a name="polygon"></a>Polygon
  A `Polygon` 는 일련의 점으로 외부 경계 링과 0 개 이상의 내부 링을 정의로 저장 하는 2 차원 표면입니다.  
  
## <a name="polygon-instances"></a>Polygon 인스턴스  
 A `Polygon` 인스턴스 세 개 이상의 서로 다른 점이 있는 링에서 구성 될 수 있습니다. A `Polygon` 인스턴스가 비어 있을 수도 있습니다.  
  
 외부 및 내부 링의는 `Polygon` 해당 경계를 정의 합니다. 링 내부 공간은 `Polygon`의 내부를 정의합니다.  
  
 다음 그림에서는 예를 보여 줍니다. `Polygon` 인스턴스.  
  
 ![기하 도형 Polygon 인스턴스의 예](../../database-engine/media/polygon.gif "기하 도형 Polygon 인스턴스의 예")  
  
 그림에 대한 설명:  
  
1.  그림 1은 한 `Polygon` 인스턴스의 외부 링에서 정의한 경계가 합니다.  
  
2.  그림 2는 외부 링 및 두 개의 내부 링에서 정의한 경계가 있는 `Polygon` 인스턴스입니다. 내부 링 내의 영역이 `Polygon` 인스턴스 외부의 일부분입니다.  
  
3.  그림 3은 `Polygon` 인스턴스의 내부 링이 하나의 탄젠트 점에서 교차하므로 올바른 인스턴스입니다.  
  
### <a name="accepted-instances"></a>허용되는 인스턴스  
 허용되는 `Polygon` 인스턴스는 예외를 발생시키지 않고 `geometry` 또는 `geography` 변수에 저장할 수 있는 인스턴스입니다. 다음 증명이 `Polygon` 인스턴스:  
  
-   빈 `Polygon` 인스턴스  
  
-   허용 가능 외부 링 및 0개 이상의 허용 가능 내부 링을 포함하는 `Polygon` 인스턴스  
  
 링이 허용되려면 다음 조건을 충족해야 합니다.  
  
-   `LineString` 인스턴스가 허용 되어야 합니다.  
  
-   `LineString` 인스턴스에 4개 이상의 점이 있어야 합니다.  
  
-   `LineString` 인스턴스의 시작점 및 끝점이 같아야 합니다.  
  
 다음 예에서는 허용 된 `Polygon` 인스턴스.  
  
```  
DECLARE @g1 geometry = 'POLYGON EMPTY';  
DECLARE @g2 geometry = 'POLYGON((1 1, 3 3, 3 1, 1 1))';  
DECLARE @g3 geometry = 'POLYGON((-5 -5, -5 5, 5 5, 5 -5, -5 -5),(0 0, 3 0, 3 3, 0 3, 0 0))';  
DECLARE @g4 geometry = 'POLYGON((-5 -5, -5 5, 5 5, 5 -5, -5 -5),(3 0, 6 0, 6 3, 3 3, 3 0))';  
DECLARE @g5 geometry = 'POLYGON((1 1, 1 1, 1 1, 1 1))';  
```  
  
 `@g4` 및 `@g5`가 보여 주듯이 허용된 `Polygon` 인스턴스는 유효한 `Polygon` 인스턴스가 아닐 수 있습니다. `@g5` 도 Polygon 인스턴스가 허용될 4개의 점이 있는 링만 포함해야 함을 보여 줍니다.  
  
 다음 예에서는 `Polygon` 인스턴스가 허용되지 않으므로 `System.FormatException`이 발생합니다.  
  
```  
DECLARE @g1 geometry = 'POLYGON((1 1, 3 3, 1 1))';  
DECLARE @g2 geometry = 'POLYGON((1 1, 3 3, 3 1, 1 5))';  
```  
  
 외부 링에 대한 `LineString` 인스턴스에 점이 부족하기 때문에 `@g1`이 허용되지 않습니다. 외부 링 `LineString` 인스턴스의 시작 점이 끝 점과 같지 않기 때문에 `@g2`가 허용되지 않습니다. 다음 예에는 허용 가능한 외부 링이 있지만 내부 링은 허용되지 않습니다. 여기서도 `System.FormatException`이 발생합니다.  
  
```  
DECLARE @g geometry = 'POLYGON((-5 -5, -5 5, 5 5, 5 -5, -5 -5),(0 0, 3 0, 0 0))';  
```  
  
### <a name="valid-instances"></a>유효한 인스턴스  
 내부 링은는 `Polygon` 모두 자체 인접할 수 및 서로 다른 하나의 탄젠트 점에서 이지만 내부 링은 한 `Polygon` 교차할는 인스턴스가 유효 하지 않습니다.  
  
 다음 예에서는 유효한 `Polygon` 인스턴스.  
  
```  
DECLARE @g1 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20))';  
DECLARE @g2 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0))';  
DECLARE @g3 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0), (-10 0, 0 10, -5 -10, -10 0))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();  
```  
  
 `@g3` 이 유효합니다. 다음 예에서는 유효하지 않은 `Polygon` 인스턴스를 보여 줍니다.  
  
```  
DECLARE @g1 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (20 0, 0 10, 0 -20, 20 0))';  
DECLARE @g2 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0), (5 0, 1 5, 1 -5, 5 0))';  
DECLARE @g3 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0), (-10 0, 0 10, 0 -10, -10 0))';  
DECLARE @g4 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0), (-10 0, 1 5, 0 -10, -10 0))';  
DECLARE @g5 geometry = 'POLYGON((10 0, 0 10, 0 -10, 10 0), (-20 -20, -20 20, 20 20, 20 -20, -20 -20) )';  
DECLARE @g6 geometry = 'POLYGON((1 1, 1 1, 1 1, 1 1))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid(), @g5.STIsValid(), @g6.STIsValid();  
```  
  
 `@g1` 이 유효하지 않습니다. `@g2` 가 유효하지 않습니다. `@g3` 유효 하지 때문에 두 개의 내부 링이 여러 연속 점에서 접하기 합니다. `@g4` 가 유효하지 않습니다. `@g5` 가 유효하지 않습니다. `@g6` 이 유효하지 않습니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 구멍이 있고 SRID가 10인 단순한 `geometry``Polygon` 인스턴스를 만듭니다.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STPolyFromText('POLYGON((0 0, 0 3, 3 3, 3 0, 0 0), (1 1, 1 2, 2 1, 1 1))', 10);  
```  
  
 유효하지 않은 인스턴스는 유효한 `geometry` 인스턴스에 입력되고 변환될 수도 있습니다. 다음 `Polygon`의 예에서는 내부 및 외부 링이 겹치고 인스턴스가 유효하지 않습니다.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('POLYGON((1 0, 0 1, 1 2, 2 1, 1 0), (2 0, 1 1, 2 2, 3 1, 2 0))');  
```  
  
 다음 예에서는 유효하지 않은 인스턴스가 `MakeValid()`를 사용하여 유효하게 됩니다.  
  
```  
SET @g = @g.MakeValid();  
SELECT @g.ToString();  
```  
  
 위의 예에서 반환된 `geometry` 인스턴스는 `MultiPolygon`입니다.  
  
```  
MULTIPOLYGON (((2 0, 3 1, 2 2, 1.5 1.5, 2 1, 1.5 0.5, 2 0)), ((1 0, 1.5 0.5, 1 1, 1.5 1.5, 1 2, 0 1, 1 0)))  
```  
  
 다음은 유효하지 않은 인스턴스를 유효한 geometry 인스턴스로 변환하는 다른 예입니다. 다음 예에서는 정확하게 서로 동일한 점 세 개를 사용하여 `Polygon` 인스턴스를 만들었습니다.  
  
```tsql  
DECLARE @g geometry  
SET @g = geometry::Parse('POLYGON((1 3, 1 3, 1 3, 1 3))');  
SET @g = @g.MakeValid();  
SELECT @g.ToString()  
```  
  
 위에서 반환된 geometry 인스턴스는 `Point(1 3)`입니다.  지정한 `Polygon` 이 `POLYGON((1 3, 1 5, 1 3, 1 3))` 이면 `MakeValid()` 에서 `LINESTRING(1 3, 1 5)`를 반환합니다.  
  
## <a name="see-also"></a>관련 항목  
 [STArea&#40;geometry 데이터 형식&#41;](/sql/t-sql/spatial-geometry/starea-geometry-data-type)   
 [STExteriorRing&#40;geometry 데이터 형식&#41;](/sql/t-sql/spatial-geometry/stexteriorring-geometry-data-type)   
 [STNumInteriorRing&#40;geometry 데이터 형식&#41;](/sql/t-sql/spatial-geometry/stnuminteriorring-geometry-data-type)   
 [STInteriorRingN&#40;geometry 데이터 형식&#41;](/sql/t-sql/spatial-geometry/stinteriorringn-geometry-data-type)   
 [STCentroid&#40;geometry 데이터 형식&#41;](/sql/t-sql/spatial-geometry/stcentroid-geometry-data-type)   
 [STPointOnSurface&#40;geometry 데이터 형식&#41;](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type)   
 [MultiPolygon](../spatial/polygon.md)   
 [공간 데이터&#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md)   
 [STIsValid&#40;geography 데이터 형식&#41;](/sql/t-sql/spatial-geography/stisvalid-geography-data-type)   
 [STIsValid&#40;geometry 데이터 형식&#41;](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type)  
  
  