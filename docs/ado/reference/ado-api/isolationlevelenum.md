---
title: IsolationLevelEnum | Microsoft Docs
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
- IsolationLevelEnum
helpviewer_keywords:
- IsolationLevelEnum enumeration [ADO]
ms.assetid: 8e17a7bc-b8a3-4ae2-b6c9-ce088ad31fdf
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1f6f18a4cd10c70369d2e0aceb226310d7a5f4ae
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="isolationlevelenum"></a>IsolationLevelEnum
에 대 한 트랜잭션 격리 수준을 지정는 [연결](../../../ado/reference/ado-api/connection-object-ado.md) 개체입니다.  
  
|상수|값|Description|  
|--------------|-----------|-----------------|  
|**adXactUnspecified**|-1|나타내지만, 지정 된 것 보다 공급자 다른 격리 수준을 사용 하는 수준을 확인할 수 없습니다.|  
|**adXactChaos**|16|보류 중인 변경 내용이 격리 수준이 더 높은 트랜잭션에서 없습니다 덮어쓸 수 있다는 것을 나타냅니다.|  
|**adXactBrowse**|256|한 트랜잭션에서 하면 볼 수 있음을 나타냅니다 커밋되지 않은 변경 내용이 다른 트랜잭션의 합니다.|  
|**adXactReadUncommitted**|256|와 동일 **adXactBrowse**합니다.|  
|**adXactCursorStability**|4096|한 트랜잭션에서 있습니다 볼 수 있음을 나타냅니다 변경 내용을 다른 트랜잭션에서 커밋 된 후에 합니다.|  
|**adXactReadCommitted**|4096|와 동일 **adXactCursorStability**합니다.|  
|**adXactRepeatableRead**|65536|한 트랜잭션에서 다른 트랜잭션의 변경 내용을 볼 수 없지만 해당 다시 쿼리하여 새로운 검색할 수 나타냅니다 **레코드 집합** 개체입니다.|  
|**adXactIsolated**|1048576|트랜잭션을 수행 하는 다른 트랜잭션의 격리를 나타냅니다.|  
|**adXactSerializable**|1048576|와 동일 **adXactIsolated**합니다.|  
  
## <a name="adowfc-equivalent"></a>해당 하는 ADO/WFC  
 패키지에 대 한 **com.ms.wfc.data**  
  
|상수|  
|--------------|  
|AdoEnums.IsolationLevel.UNSPECIFIED|  
|AdoEnums.IsolationLevel.CHAOS|  
|AdoEnums.IsolationLevel.BROWSE|  
|AdoEnums.IsolationLevel.READUNCOMMITTED|  
|AdoEnums.IsolationLevel.CURSORSTABILITY|  
|AdoEnums.IsolationLevel.READCOMMITTED|  
|AdoEnums.IsolationLevel.REPEATABLEREAD|  
|AdoEnums.IsolationLevel.ISOLATED|  
|AdoEnums.IsolationLevel.SERIALIZABLE|  
  
## <a name="applies-to"></a>적용 대상  
 [IsolationLevel 속성](../../../ado/reference/ado-api/isolationlevel-property.md)