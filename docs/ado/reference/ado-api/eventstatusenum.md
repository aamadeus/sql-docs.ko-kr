---
title: EventStatusEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- EventStatusEnum
helpviewer_keywords:
- EventStatusEnum enumeration [ADO]
ms.assetid: ebfd4cda-4017-4873-9d28-38b1c7db12a8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 623468be9022a722109f99022df8d8a583888c09
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47678541"
---
# <a name="eventstatusenum"></a>EventStatusEnum
이벤트 실행의 현재 상태를 지정합니다.  
  
|상수|값|Description|  
|--------------|-----------|-----------------|  
|**adStatusCancel**|4|이벤트를 발생 시킨 작업의 취소를 요청 합니다.|  
|**adStatusCantDeny**|3|작업이 보류 중인 작업의 취소를 요청할 수 없습니다 나타냅니다.|  
|**adStatusErrorsOccurred**|2|이벤트를 발생 시킨 작업 오류로 인해 실패 했음을 나타냅니다.|  
|**adStatusOK**|1|이벤트를 발생 시킨 작업에 성공 했음을 나타냅니다.|  
|**adStatusUnwantedEvent**|5|이벤트 메서드의 실행 완료 되기 전에 알림 메시지가 방지 합니다.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC 해당  
 Package: **com.ms.wfc.data**  
  
|상수|  
|--------------|  
|AdoEnums.EventStatus.CANCEL|  
|AdoEnums.EventStatus.CANTDENY|  
|AdoEnums.EventStatus.ERRORSOCCURRED|  
|AdoEnums.EventStatus.OK|  
|AdoEnums.EventStatus.UNWANTEDEVENT|  
  
## <a name="applies-to"></a>적용 대상  
  
||||  
|-|-|-|  
|[BeginTransComplete, CommitTransComplete, 및 RollbackTransComplete 이벤트 (ADO)](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|[ConnectComplete 및 Disconnect 이벤트(ADO)](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)|[EndOfRecordset 이벤트(ADO)](../../../ado/reference/ado-api/endofrecordset-event-ado.md)|  
|[ExecuteComplete 이벤트(ADO)](../../../ado/reference/ado-api/executecomplete-event-ado.md)|[FetchComplete 이벤트(ADO)](../../../ado/reference/ado-api/fetchcomplete-event-ado.md)|[InfoMessage 이벤트(ADO)](../../../ado/reference/ado-api/infomessage-event-ado.md)|  
|[WillChangeField 및 FieldChangeComplete 이벤트(ADO)](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|[WillChangeRecord 및 RecordChangeComplete 이벤트(ADO)](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|[WillChangeRecordset 및 RecordsetChangeComplete 이벤트(ADO)](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|  
|[WillConnect 이벤트(ADO)](../../../ado/reference/ado-api/willconnect-event-ado.md)|[WillExecute 이벤트(ADO)](../../../ado/reference/ado-api/willexecute-event-ado.md)|[WillMove 및 MoveComplete 이벤트(ADO)](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|
