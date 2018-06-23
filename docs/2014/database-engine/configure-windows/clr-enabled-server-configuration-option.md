---
title: clr enabled 서버 구성 옵션 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- assemblies [CLR integration], verifying can run
- clr enabled option
ms.assetid: 0722d382-8fd3-4fac-b4a8-cd2b7a7e0293
caps.latest.revision: 34
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1eb4bd97f6e008dbc84e7d7882b80cfff5c88f2c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36181873"
---
# <a name="clr-enabled-server-configuration-option"></a>clr enabled 서버 구성 옵션
  clr enabled 옵션을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 사용자 어셈블리를 실행할 수 있는지 여부를 지정합니다. clr enabled 옵션은 다음 값을 제공합니다.  
  
|값|Description|  
|-----------|-----------------|  
|0|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 어셈블리를 실행할 수 없습니다.|  
|1|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 어셈블리를 실행할 수 없습니다.|  
  
 이 설정의 변경 내용을 적용하려면 WOW64 서버를 다시 시작해야 합니다. 다른 서버 유형의 경우에는 서버를 다시 시작하지 않아도 됩니다.  
  
> [!NOTE]  
>  RECONFIGURE를 실행하고 clr enabled 옵션을 1에서 0으로 변경하면 사용자 어셈블리가 포함된 모든 응용 프로그램 도메인이 즉시 언로드됩니다.  
  
> [!NOTE]  
>  경량 풀링에서는 CLR(공용 언어 런타임) 실행이 지원되지 않습니다. 두 옵션, 즉 "clr enabled" 또는 "lightweight pooling" 중 하나를 해제합니다. CLR에 의존 하며 파이버 모드에서 제대로 작동 하지 않는 기능는 `hierarchy` 데이터 형식, 복제 및 정책 기반 관리 합니다.  
  
## <a name="example"></a>예제  
 다음 예에서는 먼저 clr enabled 옵션의 현재 설정을 표시한 다음 옵션 값을 1로 설정하여 옵션을 사용하도록 설정합니다. 옵션을 해제하려면 값을 0으로 설정합니다.  
  
```  
EXEC sp_configure 'clr enabled';  
EXEC sp_configure 'clr enabled' , '1';  
RECONFIGURE;  
  
```  
  
## <a name="see-also"></a>관련 항목  
 [경량 풀링 서버 구성 옵션](lightweight-pooling-server-configuration-option.md)   
 [서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [경량 풀링 서버 구성 옵션](lightweight-pooling-server-configuration-option.md)  
  
  