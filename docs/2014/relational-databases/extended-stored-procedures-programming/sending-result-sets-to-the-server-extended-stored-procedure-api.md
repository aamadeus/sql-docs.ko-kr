---
title: 결과 집합 (확장 저장된 프로시저 API) 서버에 보내기 | Microsoft Docs
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
helpviewer_keywords:
- extended stored procedures [SQL Server], sending result sets
- result sets [SQL Server], extended stored procedures
ms.assetid: 9d54673d-ea9d-4ac6-825a-f216ad8b0e34
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 090f0030063abfc0246b816d4143468eb7e4e52f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36093768"
---
# <a name="sending-result-sets-to-the-server-extended-stored-procedure-api"></a>서버로 결과 집합 보내기(확장 저장 프로시저 API)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] 대신 CLR 통합을 사용하십시오.  
  
 결과 집합을 보낼 때 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], 확장된 저장된 프로시저는 다음과 같이 적절 한 API를 호출 해야 합니다.  
  
-   **srv_sendmsg** 이전 또는 이후 모든 행 (있는 경우)으로 전송 된 순서에 관계 없이 함수를 호출할 수 있습니다 **srv_sendrow**합니다. 완료 상태를 보내기 전에 클라이언트에 모든 메시지를 전송 합니다 **srv_senddone**합니다.  
  
-   클라이언트로 보내는 각 행에 대해 한 번씩 **srv_sendrow** 함수를 호출합니다. 메시지, 상태 값 하기 전에 클라이언트에 모든 행을 보내야 합니다 또는 완료 상태 **srv_sendmsg**, **srv_status** 의 인수 **srv_pfield**, 또는 **srv_senddone**합니다.  
  
-   정의 된 모든 열에 있던 행을 보내는 **srv_describe** 응용 프로그램이 정보 오류 메시지를 발생 시키고 클라이언트에 FAIL을 반환 합니다. 이 경우 행이 전송되지 않습니다.  
  
## <a name="see-also"></a>관련 항목  
 [확장 저장 프로시저 만들기](creating-extended-stored-procedures.md)  
  
  