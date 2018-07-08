---
title: BackupRemotePartitions 요소 (XMLA) | Microsoft Docs
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
- BackupRemotePartitions Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.backupremotepartitions
- http://schemas.microsoft.com/analysisservices/2003/engine#BackupRemotePartitions
- urn:schemas-microsoft-com:xml-analysis#BackupRemotePartitions
helpviewer_keywords:
- BackupRemotePartitions element
ms.assetid: bd68bcf9-b324-4fa8-b6e5-1f5531f9992c
caps.latest.revision: 12
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: c32fd50514e96fee8de289666d8e559a78fe985b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36186388"
---
# <a name="backupremotepartitions-element-xmla"></a>BackupRemotePartitions 요소(XMLA)
  결정 여부 부모 [백업](../xml-elements-commands/backup-element-xmla.md) 명령 개체에 연결 된 원격 파티션을 백업할 합니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<Backup>  
   ...  
   <BackupRemotePartitions>...</BackupRemotePartitions>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|Description|  
|--------------------|-----------------|  
|데이터 형식 및 길이|Boolean|  
|기본값|False|  
|카디널리티|0-1: 한 번만 나타날 수 있는 선택적 요소입니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|-------------|  
|부모 요소|[백업](../xml-elements-commands/backup-element-xmla.md)|  
|자식 요소|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Remarks  
 `BackupRemotePartitions`가 `True`로 설정되면 `Locations` 명령에 하나 이상의 `Location` 요소를 포함하는 `Backup` 요소가 포함되어야 합니다. 그렇지 않으면 오류가 발생합니다. 백업 및 원격 파티션을 복원 하는 방법에 대 한 자세한 내용은 참조 [Backing Up, Restoring, and Synchronizing &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)합니다.  
  
## <a name="see-also"></a>관련 항목  
 [Locations 요소 &#40;XMLA&#41;](locations-element-xmla.md)   
 [Location 요소 &#40;XMLA&#41;](location-element-xmla.md)   
 [속성 &#40;XMLA&#41;](xml-elements-properties.md)  
  
  