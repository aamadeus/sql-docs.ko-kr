---
title: sys.dm_os_stacks (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_os_stacks
- dm_os_stacks_TSQL
- sys.dm_os_stacks
- sys.dm_os_stacks_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_os_stacks dynamic management view
ms.assetid: a69b06c4-28f0-4535-8fa1-9f132db4d916
caps.latest.revision: "23"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9e3e292fbafbee9586d377f133af7f9d3ee520d5
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmosstacks-transact-sql"></a>sys.dm_os_stacks(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  이 동적 관리 뷰는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 내부에서 다음 용도로 사용됩니다.  
  
-   완료되지 않은 할당과 같은 디버그 데이터를 추적합니다.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 요소가 특정 호출이 실행되었다고 가정하는 위치에서 이 구성 요소가 사용하는 논리를 가정하거나 유효성을 검사합니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**stack_address**|**varbinary (8)**|이 스택 할당의 고유한 주소입니다. Null을 허용하지 않습니다.|  
|**frame_index**|**int**|각 줄 함수를 나타냅니다. 특정 작업에 대해 프레임 인덱스로 오름차순 정렬 될 때 호출 **stack_address**, 전체 호출 스택을 반환 합니다. Null을 허용하지 않습니다.|  
|**frame_address**|**varbinary (8)**|함수 호출 주소입니다. Null을 허용하지 않습니다.|  
  
## <a name="remarks"></a>주의  
 **sys.dm_os_stacks** 는 기호 서버와 다른 구성 요소 정보를 올바르게 표시 하려면 서버에 있어야 합니다.  
  
## <a name="permissions"></a>Permissions  
[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], 필요 `VIEW SERVER STATE` 권한.   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] 프리미엄 계층 필요는 `VIEW DATABASE STATE` 데이터베이스에는 권한이 있습니다. [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] 표준 및 기본 계층 필요는 **서버 관리자** 또는 **Azure Active Directory 관리자** 계정.  
  

## <a name="see-also"></a>관련 항목:  
  [SQL Server 운영 체제 관련 동적 관리 뷰 &#40; Transact SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  