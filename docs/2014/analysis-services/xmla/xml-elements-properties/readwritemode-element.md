---
title: ReadWriteMode 요소 | Microsoft Docs
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
helpviewer_keywords:
- ReadWriteMode command
ms.assetid: 379bcaca-bb7e-4934-a9e7-21f8ede2fdc7
caps.latest.revision: 13
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 88ebc7e23fc3ec4aad0d8273464636354958217a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36187277"
---
# <a name="readwritemode-element"></a>ReadWriteMode 요소
  `ReadWriteMode` 데이터베이스 속성은 데이터베이스가 `ReadWrite` 모드에 있는지 또는 `ReadOnly` 모드에 있는지를 지정합니다. 이 속성 값은 두 가지만 가능합니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<Database>  
...  
   <ddlns_100_0:ReadWriteMode>...</ddlns_100_0:ReadWriteMode>  
...  
</Database>  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|Description|  
|--------------------|-----------------|  
|데이터 형식 및 길이|String(열거형)|  
|기본값|ReadWrite|  
|카디널리티|0-1: 두 번 이상 나타날 수 있는 선택적 요소입니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|-------------|  
|부모 요소|[데이터베이스](database-element-xmla.md)|  
|자식 요소|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Remarks  
 `ReadWrite` 모드에서만 데이터베이스를 만들 수 있으며 `ReadOnly` 모드에서는 데이터베이스를 만들 수 없습니다.  
  
 `ReadWriteMode` 요소의 값은 다음 표에 나열된 문자열 중 하나로 제한됩니다.  
  
|값|Description|  
|-----------|-----------------|  
|*읽기 전용*|데이터베이스에 변경 또는 업데이트를 적용할 수 없습니다.|  
|*ReadWrite*|데이터베이스에 변경 또는 업데이트를 적용할 수 있습니다.|  
  
## <a name="see-also"></a>관련 항목  
 [Attach 요소](../xml-elements-commands/attach-element.md)   
 [Analysis Services 데이터베이스 연결 및 분리](../../multidimensional-models/attach-and-detach-analysis-services-databases.md)   
 [Analysis Services 데이터베이스 이동](../../multidimensional-models/move-an-analysis-services-database.md)   
 [Readwritemode 데이터베이스](../../multidimensional-models/database-readwritemodes.md)   
 [ReadOnly 및 ReadWrite 모드 간 Analysis Services 데이터베이스 전환](../../multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
  