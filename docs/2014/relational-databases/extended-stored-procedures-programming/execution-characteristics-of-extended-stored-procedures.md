---
title: 확장된 저장된 프로시저의 실행 특징 | Microsoft Docs
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
- extended stored procedures [SQL Server], executing
- executing extended stored procedures [SQL Server]
ms.assetid: 6fe1f7e8-cc02-49df-8a2a-d47a96ec3567
caps.latest.revision: 33
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f88d9bb01d8604ec49538b6d4ff4cc6f3557d7bc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36079750"
---
# <a name="execution-characteristics-of-extended-stored-procedures"></a>확장 저장 프로시저의 실행 특징
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] 대신 CLR 통합을 사용하십시오.  
  
 확장 저장 프로시저 실행에는 다음과 같은 세 가지 특징이 있습니다.  
  
-   보안 컨텍스트 내에서 확장된 저장된 프로시저 함수는 실행 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]합니다.  
  
-   확장 저장 프로시저 함수는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 프로세스 공간에서 실행됩니다.  
  
-   확장 저장 프로시저 실행과 연결되는 스레드는 클라이언트 연결에 사용되는 스레드와 같은 것입니다.  
  
    > [!IMPORTANT]  
    >  시스템 관리자는 확장 저장 프로시저를 서버에 추가하고 다른 사용자에게 실행 권한을 부여하기 전에 각 확장 저장 프로시저를 철저히 검토하여 유해 코드 또는 악성 코드가 포함되어 있는지 확인해야 합니다.  
  
-  
  
 DLL 될 때까지 서버 주소 공간에 로드 된 상태로 확장 저장 프로시저 DLL이 로드, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 중지 또는 관리자가 DBCC를 사용 하 여 명시적으로 DLL을 언로드하기 *DLL_name* (FREE).  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 EXECUTE 문을 사용하여 확장 저장 프로시저를 저장 프로시저처럼 사용할 수 있습니다.  
  
```  
EXECUTE @retval = xp_extendedProcName @param1, @param2 OUTPUT  
```  
  
## <a name="parameters"></a>매개 변수  
 @ *retval*  
 반환 값입니다.  
  
 @ *param1*  
 입력 매개 변수입니다.  
  
 @ *param2*  
 입/출력 매개 변수입니다.  
  
> [!CAUTION]  
>  확장 저장 프로시저는 성능 향상과 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기능 확장을 제공합니다. 그러나 확장 저장 프로시저 DLL과 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 같은 주소 공간을 공유하므로 문제가 있는 프로시저가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 작동에 부정적인 영향을 줄 수 있습니다. 확장 저장 프로시저 DLL에서 throw하는 예외는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 처리되지만 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 영역에 손상을 줄 수 있습니다. 보안 예방 조치로서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 시스템 관리자만 확장 저장 프로시저를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 추가할 수 있습니다. 이러한 프로시저는 설치하기 전에 철저히 테스트해야 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [확장 저장된 프로시저 프로그래밍](database-engine-extended-stored-procedures-programming.md)   
 [SQL Server에 설치된 확장 저장 프로시저 쿼리](querying-extended-stored-procedures-installed-in-sql-server.md)  
  
  