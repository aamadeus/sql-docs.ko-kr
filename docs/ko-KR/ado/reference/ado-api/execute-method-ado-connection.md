---
title: Execute 메서드 (ADO 연결) | Microsoft Docs
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::Execute
- Connection15::raw_Execute
helpviewer_keywords:
- Execute method [ADO]
ms.assetid: 03c69320-96b2-4d85-8d49-a13b13e31578
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d4a9ab40fd57d19cc6b5ab3e2e25290d7511422a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="execute-method-ado-connection"></a>Execute 메서드 (ADO 연결)
지정 된 쿼리, SQL 문, 저장된 프로시저 또는 공급자 특정 텍스트를 실행합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
Set recordset = connection.Execute (CommandText, RecordsAffected, Options)  
Set recordset = connection.Execute (CommandText, RecordsAffected, Options)  
```  
  
## <a name="return-value"></a>반환 값  
 반환 된 [Recordset 개체 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) 개체 참조입니다.  
  
#### <a name="parameters"></a>매개 변수  
 *CommandText*  
 A **문자열** SQL 문, 저장된 프로시저, URL, 또는 공급자별 텍스트 실행에 포함 된 값입니다. **필요에 따라**, 테이블 이름을 공급자가 인식 SQL만 사용할 수 있습니다. 들어 테이블 이름 "고객"은 사용 되는 경우 ADO는 자동으로 앞에 추가 만들어 "선택 *에서 Customers"를 전달 하는 표준 SQL Select 구문을로 [!INCLUDE[tsql](../../../includes/tsql_md.md)] 공급자에 게 문의 합니다.  
  
 *RecordsAffected*  
 (선택 사항) A **긴** 있는 변수 공급자 작업을 영향 받는 레코드 수를 반환 합니다.  
  
 *옵션*  
 (선택 사항) A **긴** 공급자를 CommandText 인수를 평가 하는 방식을 나타내는 값입니다. 하나 이상의 비트 마스크 될 수 있습니다 [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) 또는 [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) 값입니다.  
  
 **참고** 사용은 **ExecuteOptionEnum** 값 **adExecuteNoRecords** 내부 처리를 최소화 하 여 및 Visual Basic 6.0에서 이식 하는 응용 프로그램에 대 한 성능 향상을 위해.  
  
 사용 하지 마십시오 **adExecuteStream** 와 **Execute** 의 메서드는 **연결** 개체입니다.  
  
 Execute와 adCmdFile 또는 adCmdTableDirect CommandTypeEnum 값을 사용 하지 마십시오. 사용한 옵션으로 이러한 값만 사용할 수는 [Open 메서드 (ADO 레코드 집합)](../../../ado/reference/ado-api/open-method-ado-recordset.md) 및 [Requery 메서드](../../../ado/reference/ado-api/requery-method.md) 의 메서드는 **레코드 집합**합니다.  
  
## <a name="remarks"></a>주의  
 사용 하는 **Execute** 에서 메서드는 [연결 개체 (ADO)](../../../ado/reference/ado-api/connection-object-ado.md) 메서드에 전달 하는 CommandText 인수에 지정된 된 연결에서 모든 쿼리를 실행 하는 개체입니다. 실행을 생성 하는 모든 결과 새로운 저장 됩니다 CommandText 인수는 행을 반환 하는 쿼리를 지정 하는 경우 **레코드 집합** 개체입니다. 공급자가 반환 하는 경우 명령을 위한 용도가 아닙니다 (예: SQL UPDATE 쿼리) 결과를 반환할 **아무** 옵션으로 긴 **adExecuteNoRecords** 에 지정 됩니다. 그렇지 않으면 반환을 실행 한 닫힌 **레코드 집합**합니다.  
  
 반환 된 **레코드 집합** 개체는 항상 읽기 전용, 정방향 전용 커서입니다. 필요한 경우 한 **레코드 집합** 더 많은 기능으로 개체를 먼저 만든는 **레코드 집합** 원하는 속성 설정을 사용 하 여 개체 다음 사용 하 여는 **레코드 집합** 개체의 [ Open 메서드 (ADO 레코드 집합)](../../../ado/reference/ado-api/open-method-ado-recordset.md) 메서드는 쿼리를 실행 하 고 원하는 커서 유형을 반환 합니다.  
  
 콘텐츠는 *CommandText* 인수 공급자와 관련 되며 표준 SQL 구문 또는 공급자가 지 원하는 특수 명령 형식일 수 있습니다.  
  
 이 작업이 때 ExecuteComplete 이벤트를 발생 합니다.  
  
> [!NOTE]
>  Url은 http 체계를 사용 하 여 자동으로 호출 됩니다는 [Microsoft OLE DB Provider for Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)합니다. 자세한 내용은 참조 [절대 경로 상대 Url](../../../ado/guide/data/absolute-and-relative-urls.md)합니다.  
  
## <a name="applies-to"></a>적용 대상  
 [연결 개체(ADO)](../../../ado/reference/ado-api/connection-object-ado.md)