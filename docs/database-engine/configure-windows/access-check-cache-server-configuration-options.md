---
title: "access check cache 서버 구성 옵션 | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "access check cache 옵션"
ms.assetid: 0a992ea8-3ec6-4a4d-97b5-460ae7326247
caps.latest.revision: 9
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 9
---
# access check cache 서버 구성 옵션
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  데이터베이스 개체를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 액세스할 때 액세스 검사는 **access check result cache**라는 내부 구조에 캐시됩니다. **access check cache quota** 및 **access check cache bucket count** 옵션은 **access check result cache**에 사용되는 해시 버킷의 수와 항목 수를 제어합니다. 드문 경우지만 이러한 옵션을 변경하여 성능을 향상시킬 수 있습니다.  
  
 기본값 0은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 이러한 옵션을 관리함을 나타냅니다. 이러한 옵션은 Microsoft 고객 지원 서비스에서 안내하는 경우에만 변경하는 것이 좋습니다.  
  
## 참고 항목  
 [서버 구성 옵션&#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  