---
title: Isolation 요소 (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Isolation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Isolation element
ms.assetid: 28c98c6f-668e-4547-8d25-127cc3995a7d
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: cdcbf79ccd1281c9f3dbaa109b3c77214ced22bf
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36081929"
---
# <a name="isolation-element-assl"></a>Isolation 요소(ASSL)
  파생 된 요소에 대 한 격리 수준을 나타냅니다는 [DataSource](../data-type/datasource-data-type-assl.md) 데이터 형식입니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<DataSource>  
   ...  
   <Isolation>...</Isolation>  
   ...  
</DataSource>  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|Description|  
|--------------------|-----------------|  
|데이터 형식 및 길이|String(열거형)|  
|기본값|*ReadCommitted*|  
|카디널리티|0-1: 한 번만 나타날 수 있는 선택적 요소입니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|-------------|  
|부모 요소|[DataSource](../data-type/datasource-data-type-assl.md)|  
|자식 요소|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Remarks  
 이 요소의 값은 다음 표에 있는 문자열 중 하나로 제한됩니다.  
  
|값|Description|  
|-----------|-----------------|  
|*ReadCommitted*|다른 트랜잭션에 의해 수정되었지만 커밋되지 않은 데이터를 문이 읽을 수 없도록 지정합니다. 이렇게 하면 더티 읽기를 방지할 수 있습니다. 다른 트랜잭션은 현재 트랜잭션 내의 개별 문 간에 데이터를 변경할 수 있으며, 이로 인해 반복할 수 없는 읽기 또는 가상 데이터가 발생합니다. 이 값은 `Isolation` 요소의 기본값입니다.|  
|*스냅숏*|트랜잭션의 문이 읽은 데이터가 트랜잭션 시작 시와 트랜잭션별로 데이터 버전의 일관성이 유지되도록 지정합니다. 트랜잭션은 시작되기 전에 커밋된 데이터 수정 내용만 볼 수 있습니다. 현재 트랜잭션이 시작된 후 다른 트랜잭션에서 수정한 데이터는 현재 트랜잭션에서 실행되는 문에 표시되지 않습니다. 따라서 트랜잭션의 문이 트랜잭션 시작 당시 커밋된 데이터의 스냅숏을 가져오는 것처럼 보입니다.|  
  
## <a name="see-also"></a>관련 항목  
 [속성 &#40;ASSL&#41;](properties-assl.md)  
  
  