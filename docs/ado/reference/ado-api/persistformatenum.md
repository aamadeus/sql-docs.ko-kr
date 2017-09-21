---
title: PersistFormatEnum | Microsoft Docs
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- PersistFormatEnum
helpviewer_keywords:
- PersistFormatEnum enumeration [ADO]
ms.assetid: ebe1a2ab-e9f1-43a2-8f94-b190c9613d70
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9c981037637b85e23e6b871116291aa8eb607c99
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="persistformatenum"></a>PersistFormatEnum
저장 하는 형식을 지정 된 [레코드 집합](../../../ado/reference/ado-api/recordset-object-ado.md)합니다.  
  
|상수|값|Description|  
|--------------|-----------|-----------------|  
|**adPersistADTG**|0|Microsoft Advanced 데이터 테이블 그램 (ADTG) 형식을 나타냅니다.|  
|**adPersistADO**|1.|ADO의 Extensible Markup Language (XML) 형식 사용될지를 나타냅니다. 이 값 adPersistXML 동일 이며 이전 버전과 호환성에 대 한 포함 합니다.|  
|**adPersistXML**|1.|Extensible Markup Language (XML) 형식을 나타냅니다.|  
|**adPersistProviderSpecific**|2|공급자가 유지할 나타냅니다는 **레코드 집합** 자체 형식을 사용 하 여 합니다.|  
  
## <a name="adowfc-equivalent"></a>해당 하는 ADO/WFC  
 패키지에 대 한 **com.ms.wfc.data**  
  
|상수|  
|--------------|  
|AdoEnums.PersistFormat.ADTG|  
|AdoEnums.PersistFormat.XML|  
  
## <a name="applies-to"></a>적용 대상  
 [Save 메서드](../../../ado/reference/ado-api/save-method.md)