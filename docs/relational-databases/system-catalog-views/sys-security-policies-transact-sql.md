---
title: sys.security_policies (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server 2016 Preview
f1_keywords:
- SYS.SECURITY_POLICIES_TSQL
- SECURITY_POLICIES_TSQL
- SYS.SECURITY_POLICIES
- SECURITY_POLICIES
dev_langs: TSQL
helpviewer_keywords:
- sys.security_policies catalog view
- security_policies catalog view
ms.assetid: 35362f5b-e601-4049-9e1d-c5307e823831
caps.latest.revision: "9"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9e30a903e31ce8ba7951f9756a8fd258375fb8e2
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2017
---
# <a name="syssecuritypolicies-transact-sql"></a>sys.security_policies (Transact SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  데이터베이스의 각 보안 정책에 대 한 행을 반환합니다.  
  
|열 이름|데이터 형식|설명|  
|-----------------|---------------|-----------------|  
|name|**sysname**|데이터베이스 내에서 고유한 보안 정책의 이름입니다.|  
|object_id|**int**|보안 정책의 ID입니다.|  
|principal_id|**int**|데이터베이스에 등록된 보안 정책 소유자의 ID입니다. 소유자가 스키마를 통해 결정되는 경우 NULL입니다.|  
|schema_id|**int**|개체가 상주하는 스키마의 ID입니다.|  
|parent_object_id|**int**|정책이 속하는 개체의 ID입니다. 0이어야 합니다.|  
|형식|**vachar(2)**|해야 **SP**합니다.|  
|type_desc|**nvarchar (60)**|**SECURITY_POLICY**합니다.|  
|create_date|**datetime**|보안 정책이 만들어진 UTC 날짜입니다.|  
|modify_date|**datetime**|보안 정책이 마지막으로 수정된 UTC 날짜입니다.|  
|is_ms_shipped|**bit**|항상 false입니다.|  
|is_enabled|**bit**|보안 정책 사양 상태:<br /><br /> 0 = 사용 안 함<br /><br /> 1 = 사용|  
|is_not_for_replication|**bit**|정책이 NOT FOR REPLICATION 옵션으로 생성되었습니다.|  
|uses_database_collation|**bit**|동일한 데이터 정렬을 데이터베이스로 사용합니다.|  
|is_schemabinding_enabled|**bit**|보안 정책에 대 한 Schemabinding 상태:<br /><br /> 0 또는 NULL = 사용<br /><br /> 1 = 사용 안 함|  
  
## <a name="permissions"></a>Permissions  
 보안 주체는 **ALTER ANY SECURITY POLICY** 이 카탈로그 뷰에으로 있는 사용자의 모든 개체에 대 한 액세스 권한이 **VIEW DEFINITION** 개체에 합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [행 수준 보안](../../relational-databases/security/row-level-security.md)   
 [sys.security_predicates&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-security-predicates-transact-sql.md)   
 [CREATE SECURITY POLICY&#40;Transact-SQL&#41;](../../t-sql/statements/create-security-policy-transact-sql.md)   
 [보안 카탈로그 뷰&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [카탈로그 뷰&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [보안 주체&#40;데이터베이스 엔진&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  