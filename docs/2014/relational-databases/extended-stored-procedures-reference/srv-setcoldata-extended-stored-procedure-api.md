---
title: srv_setcoldata(확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- srv_setcoldata
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_setcoldata
ms.assetid: 2e19205a-25ca-4d4a-916b-d591cf2c892b
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: f56c16d1b497bffb55362eb63ed755456c6a6406
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48152473"
---
# <a name="srvsetcoldata-extended-stored-procedure-api"></a>srv_setcoldata(확장 저장 프로시저 API)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] 대신 CLR 통합을 사용하세요.  
  
 열 데이터의 현재 주소를 지정합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
int srv_setcoldata (  
SRV_PROC *  
srvproc  
,  
int   
column  
,  
void *  
data   
);  
  
```  
  
## <a name="arguments"></a>인수  
 *srvproc*  
 특정 클라이언트 연결에 대한 핸들인 SRV_PROC 구조에 대한 포인터입니다. 이 구조에는 확장 저장 프로시저 API 라이브러리가 응용 프로그램과 클라이언트 간 통신 및 데이터를 관리하는 데 사용하는 정보가 들어 있습니다.  
  
 *column*  
 주소가 지정되는 열의 번호를 나타냅니다. 열 번호는 1부터 시작됩니다.  
  
 *data*  
 열 데이터에 대한 포인터입니다. **srv_setcoldata**에 대한 다른 호출에 의해 열 데이터가 바뀌거나 **srv_senddone**이 호출될 때까지 *data*에 할당된 메모리를 해제하면 안 됩니다.  
  
## <a name="returns"></a>반환 값  
 SUCCEED 또는 FAIL  
  
## <a name="remarks"></a>Remarks  
 먼저 **srv_describe**를 사용하여 행의 각 열을 정의해야 합니다. 열 데이터 주소는 처음에 **srv_describe**를 사용하여 설정됩니다. 열 데이터의 주소가 변경되면 **srv_setcoldata**를 호출하여 데이터의 새 주소를 지정해야 하며, 변경된 각 열에 대해 개별적으로 **srv_setcoldata**를 호출해야 합니다.  
  
 **srv_setcollen**을 사용하여 열의 길이를 0으로 설정하면 Null 데이터가 표현됩니다. 데이터 주소는 무시됩니다.  
  
> [!IMPORTANT]  
>  확장 저장 프로시저의 원본 코드를 철저히 검토하고 프로덕션 서버에 DLL을 설치하기 전에 컴파일한 DLL을 테스트해야 합니다. 보안 검토 및 테스트에 대한 자세한 내용은 [Microsoft 웹 사이트](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/)를 참조하십시오.  
  
## <a name="see-also"></a>관련 항목  
 [srv_describe(확장 저장 프로시저 API)](srv-describe-extended-stored-procedure-api.md)  
  
  
