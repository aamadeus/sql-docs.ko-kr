---
title: srv_wsendmsg(확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- srv_wsendmsg
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_wsendmsg
ms.assetid: f2153076-32c9-4a52-8e1b-fc9618153543
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cee9fcd37841f8ac232bc3d85d00fb88ff199be9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36171952"
---
# <a name="srvwsendmsg-extended-stored-procedure-api"></a>srv_wsendmsg(확장 저장 프로시저 API)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] 대신 CLR 통합을 사용하세요.  
  
 클라이언트에 유니코드 메시지를 보냅니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
int srv_wsendmsg(SRV_PROC *   
srvproc  
, int   
msgnum  
, int   
severity  
, WCHAR *   
message  
, int   
msglen  
);  
  
```  
  
## <a name="arguments"></a>인수  
 *srvproc*  
 특정 클라이언트 연결에 대한 핸들인 SRV_PROC 구조에 대한 포인터입니다. 이 구조에는 확장 저장 프로시저 API 라이브러리가 응용 프로그램과 클라이언트 간 통신 및 데이터를 관리하는 데 사용하는 정보가 들어 있습니다.  
  
 *Msgnum*  
 4바이트 메시지 번호입니다.  
  
 *Severity*  
 오류의 심각도를 지정합니다. 심각도가 10보다 작거나 같으면 정보 메시지로 간주되고 그렇지 않으면 오류로 간주됩니다.  
  
 *message*  
 클라이언트로 보낼 유니코드 문자열에 대한 포인터입니다.  
  
 *msglen*  
 *message*의 길이(문자 수)를 지정합니다.  
  
## <a name="returns"></a>반환 값  
 SUCCEED 또는 FAIL  
  
## <a name="remarks"></a>Remarks  
 이 함수를 사용하여 유니코드로 메시지를 보낼 수 있습니다. **srv_sendmsg**와 비슷하지만 DBCHAR 문자열이 아니라 WCHAR 문자열 형식으로 메시지를 보냅니다. 메시지 길이는 바이트가 아니라 문자 수로 보고되며 *msglen* 은 SRV_NULLTERM일 수 없습니다.  
  
 이 함수는 다음과 같은 경우 FAIL을 반환합니다.  
  
-   지정된 *msglen* 이 0-32242의 범위를 벗어난 경우  
  
-   *msglen* 이 0으로 지정되어 있지만 메시지 포인터가 NULL인 경우  
  
-   네트워크를 통해 오류 메시지를 보낼 때 오류가 발생한 경우  
  
> [!IMPORTANT]  
>  확장 저장 프로시저의 원본 코드를 철저히 검토하고 프로덕션 서버에 DLL을 설치하기 전에 컴파일한 DLL을 테스트해야 합니다. 보안 검토 및 테스트에 대한 자세한 내용은 [Microsoft 웹 사이트](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/)를 참조하십시오.  
  
## <a name="see-also"></a>관련 항목  
 [srv_sendmsg(확장 저장 프로시저 API)](srv-sendmsg-extended-stored-procedure-api.md)  
  
  