---
title: ReadyState 속성 (RDS) | Microsoft Docs
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: sql
ms.prod_service: drivers
ms.component: reference
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- ReadyState property [ADO]
ms.assetid: 5be75bc7-1171-4440-a37e-c8cc6b5cd865
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0d3ee96351ee6b09c259d4dc70e11c590c222962
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="readystate-property-rds"></a>ReadyState 속성 (RDS)
진행률을 나타냅니다는 [DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) 개체에 데이터를 검색 하는 대로 해당 [레코드 집합](../../../ado/reference/ado-api/recordset-object-ado.md) 개체입니다.  
  
> [!IMPORTANT]
>  Windows 8 및 Windows Server 2012 부터는 RDS 서버 구성 요소가 더 이상에 포함 Windows 운영 체제 (Windows 8 참조 및 [Windows Server 2012 호환성 설명서](https://www.microsoft.com/en-us/download/details.aspx?id=27416) 자세한 세부 정보에 대 한). RDS 클라이언트 구성 요소는 나중 버전의 Windows에서 제거 됩니다. 새 개발 작업에서는 이 기능을 사용하지 않도록 하고, 현재 이 기능을 사용하는 응용 프로그램은 수정하세요. RDS를 사용 하는 응용 프로그램을 마이그레이션해야 합니다. [WCF 데이터 서비스](http://go.microsoft.com/fwlink/?LinkId=199565)합니다.  
  
## <a name="settings-and-return-values"></a>설정 및 반환 값  
 설정 하거나 다음 값 중 하나를 반환 합니다.  
  
|Value|Description|  
|-----------|-----------------|  
|**adcReadyStateLoaded**|현재 쿼리가 계속 실행 되 고 인출 된 행이 없습니다. **DataControl** 개체의 **레코드 집합** 를 사용 하기 위해 사용할 수 없습니다.|  
|**adcReadyStateInteractive**|현재 쿼리에 의해 검색 되는 행의 초기 집합에 저장 된는 **DataControl** 개체의 **레코드 집합** 되며 사용 하기 위해 사용할 수 있습니다. 나머지 행을 계속 가져오고 있습니다.|  
|**adcReadyStateComplete**|현재 쿼리에 의해 검색 된 모든 행에 저장 되어는 **DataControl** 개체의 **레코드 집합** 되며 사용 하기 위해 사용할 수 있습니다.<br /><br /> 이 상태는 오류로 인해 작업이 중단 또는 경우에 존재는 **레코드 집합** 개체가 초기화 되지 않았습니다.|  
  
> [!NOTE]
>  이러한 상수를 사용 하는 각 클라이언트 실행 파일에 대 한 선언을 제공 해야 합니다. 잘라내기 및 RDS 라이브러리에 대 한 기본 설치 폴더에 있는 파일, Adcvbs.inc에서에서 원하는 상수 선언을 붙여넣기 수 있습니다.  
  
## <a name="remarks"></a>주의  
 사용 하 여는 [onReadyStateChange](../../../ado/reference/rds-api/onreadystatechange-event-rds.md) 의 변화를 모니터링 하는 이벤트는 **ReadyState** 비동기 쿼리 작업 중에 속성입니다. 이 속성의 값을 주기적으로 검사 보다 더 효율적입니다.  
  
 비동기 작업 중에 오류가 발생 하는 경우는 **ReadyState** 속성 변경 **adcReadyStateComplete**, [상태](../../../ado/reference/ado-api/state-property-ado.md) 속성이 에서변경**adStateExecuting** 를 **adStateClosed**, 및 **레코드 집합** 개체 [값](../../../ado/reference/ado-api/value-property-ado.md) 속성은 *Nothing* .  
  
## <a name="applies-to"></a>적용 대상  
 [DataControl 개체(RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>관련 항목:  
 [ReadyState 속성 (VBScript) 예제](../../../ado/reference/rds-api/readystate-property-example-vbscript.md)   
 [Cancel 메서드 (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [ExecuteOptions 속성(RDS)](../../../ado/reference/rds-api/executeoptions-property-rds.md)

