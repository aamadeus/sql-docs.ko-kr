---
title: "max full-text crawl range 서버 구성 옵션 | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "탐색 [전체 텍스트 검색]"
  - "max full-text crawl range 옵션"
ms.assetid: a49de86b-0891-4dcd-89c0-ead30aab00e0
caps.latest.revision: 24
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 24
---
# max full-text crawl range 서버 구성 옵션
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **max full-text crawl range** 옵션을 사용하여 CPU 사용률을 최적화함으로써 전체 탐색 중에 탐색 성능을 개선할 수 있습니다. 이 옵션을 사용하면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 전체 인덱스 탐색 중에 사용해야 하는 파티션의 수를 지정할 수 있습니다. 예를 들어 CPU가 여러 개 있고 사용률이 최적 상태가 아닌 경우 이 옵션의 최대값을 늘릴 수 있습니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 이 옵션 외에도 테이블의 행 수 및 CPU 수와 같은 여러 요소를 감안하여 실제 사용되는 파티션 수를 지정합니다.  
  
 이 옵션의 기본값은 4이고 최소값은 1이며 최대값은 256입니다. 이 옵션을 변경하면 이후의 탐색에만 영향을 미칩니다. 실행 중인 탐색 작업은 변경된 옵션 설정의 영향을 받지 않습니다.  
  
 **max full-text crawl range** 옵션은 고급 옵션입니다. **sp_configure** 시스템 저장 프로시저를 사용하여 설정을 변경하면 **show advanced options**를 1로 설정할 때만 **max full-text crawl range**를 변경할 수 있습니다. 이 설정은 서버를 다시 시작하지 않아도 즉시 적용됩니다.  
  
## 참고 항목  
 [RECONFIGURE&#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [서버 구성 옵션&#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  