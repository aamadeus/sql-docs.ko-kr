---
title: "데이터 컬렉션 매개 변수 구성(Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "데이터 컬렉션 [SQL Server]"
ms.assetid: 850905b6-35d2-4ed1-ab51-de64daa832b2
caps.latest.revision: 16
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 16
---
# 데이터 컬렉션 매개 변수 구성(Transact-SQL)
  사용자 지정 컬렉션 집합을 만들기 전에 먼저 데이터 컬렉션 매개 변수를 구성해야 합니다. 데이터 수집기에서 제공하는 저장 프로시저를 사용하여 이를 구성할 수 있습니다. 이 태스크를 수행하려면 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에서 쿼리 편집기를 사용하여 다음 절차를 수행해야 합니다.  
  
> [!NOTE]  
>  데이터 컬렉션 매개 변수는 한 번만 구성합니다. 구성 후 이러한 매개 변수는 생성된 추가 컬렉션 집합에 사용됩니다.  
  
### 데이터 컬렉션 매개 변수 구성  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 사용자 지정 컬렉션 집합을 만들 데이터베이스에 연결합니다.  
  
2.  쿼리 편집기에서 다음 문을 실행합니다.  
  
    ```tsql  
    USE msdb;  
    EXEC sp_syscollector_set_warehouse_instance_name N'INSTANCE_NAME';-- where instance name is the name of the SQL Server instance  
    EXEC sp_syscollector_set_warehouse_database_name N'MDW';  
    EXEC sp_syscollector_set_cache_directory N'D:\tempdata';  
    ```  
  
## 참고 항목  
 [데이터 컬렉션](../../relational-databases/data-collection/data-collection.md)   
 [데이터 수집기 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)  
  
  