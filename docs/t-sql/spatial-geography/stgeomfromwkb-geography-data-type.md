---
title: "STGeomFromWKB (geography 데이터 형식) | Microsoft Docs"
ms.custom: 
ms.date: 07/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STGeomFromWKB_TSQL
- STGeomFromWKB (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STGeomFromWKB method
ms.assetid: 79d39d88-5440-49a7-9247-190eafce3f4f
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 22841fbeff43f2d81d3760057d501004e44de534
ms.contentlocale: ko-kr
ms.lasthandoff: 09/01/2017

---
# <a name="stgeomfromwkb-geography-data-type"></a>STGeomFromWKB(geography 데이터 형식)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

반환 된 **geography** Open Geospatial Consortium (OGC) wkb (WELL-KNOWN Binary) 표현의 인스턴스.
  
이 **geography** 데이터 형식 메서드 지원 **FullGlobe** 인스턴스 또는 반구 보다 큰 공간 인스턴스.
  
## <a name="syntax"></a>구문  
  
```  
  
STGeomFromWKB ( 'WKB_geography' , SRID )  
```  
  
## <a name="arguments"></a>인수  
 *WKB_geography*  
 WKB 표현입니다는 **geography** 인스턴스를 반환 합니다. *WKB_geography* 는 **varbinary (max)** 식입니다.  
  
 *SRID*  
 **int** spatial 나타내는 식 참조의 ID (SRID)는 **geography** 인스턴스를 반환 합니다.  
  
## <a name="return-types"></a>반환 형식  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]반환 형식: **geography**  
  
 CLR 반환 형식: **SqlGeography**  
  
## <a name="remarks"></a>주의  
 OGC 형식은 **geography** 에서 반환한 인스턴스 `STGeomFromText()` 해당 WKB 입력으로 설정 됩니다.  
  
 이 메서드에서 throw 한 **FormatException** 입력이 잘못 된 경우.  
  
 이 메서드는 throw **ArgumentException** 입력에 대척점 가장자리를 포함 하는 경우.  
  
## <a name="examples"></a>예  
 다음 예에서는 `STGeomFromWKB()`를 사용하여 `geography` 인스턴스를 만듭니다.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromWKB(0x010200000002000000D7A3703D0A975EC08716D9CEF7D34740CBA145B6F3955EC08716D9CEF7D34740, 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>관련 항목:  
 [OGC 정적 지리 메서드](../../t-sql/spatial-geography/ogc-static-geography-methods.md)  
  
  
