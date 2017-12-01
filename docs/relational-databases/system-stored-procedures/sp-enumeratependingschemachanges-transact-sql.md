---
title: sp_enumeratependingschemachanges (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_enumeratependingschemachanges
- sp_enumeratependingschemachanges_TSQL
helpviewer_keywords: sp_enumeratependingschemachanges
ms.assetid: df169b21-d10a-41df-b3a1-654cfb58bc21
caps.latest.revision: "23"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 63ad21e40d524e2374434d733e1cc4357d6a9b23
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2017
---
# <a name="spenumeratependingschemachanges-transact-sql"></a>sp_enumeratependingschemachanges(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  보류 중인 모든 스키마 변경의 목록을 반환합니다. 이 저장된 프로시저 사용 하 여 [sp_markpendingschemachange](../../relational-databases/system-stored-procedures/sp-markpendingschemachange-transact-sql.md), 관리자가 복제 되지 않도록 선택한 보류 중인 스키마 변경 내용을 건너뛸 수 있습니다. 이 저장 프로시저는 게시 데이터베이스의 게시자에서 실행됩니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_enumeratependingschemachanges [ @publication = ] 'publication'   
    [ , [ @starting_schemaversion = ] starting_schemaversion ]  
```  
  
## <a name="arguments"></a>인수  
 [  **@publication=** ] **'***게시***'**  
 게시의 이름입니다. *게시* 은 **sysname**, 기본값은 없습니다.  
  
 [  **@starting_schemaversion=** ] *starting_schemaversion*  
 결과 집합에 포함될 스키마 변경의 최소 번호입니다.  
  
## <a name="result-set"></a>결과 집합  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**article_name**|**sysname**|스키마 변경이 적용 되는 아티클의 이름입니다. 또는 **publication-wide** 전체 게시에 적용 되는 스키마 변경에 대 한 합니다.|  
|**스키마 버전**|**int**|보류 중인 스키마 변경 수입니다.|  
|**schematype**|**sysname**|스키마 변경의 유형을 나타내는 텍스트 값입니다.|  
|**schematext**|**nvarchar(max)**|스키마 변경 내용을 설명하는 [!INCLUDE[tsql](../../includes/tsql-md.md)]입니다.|  
|**schemastatus**|**nvarchar (10)**|스키마 변경이 아티클에 대해 보류 중인지 여부를 나타내며 다음 값 중 하나를 사용할 수 있습니다.<br /><br /> **활성** = 스키마 변경이 보류 중임<br /><br /> **비활성** = 스키마 변경이 비활성화 되어<br /><br /> **건너뛸** = 스키마 변경 내용이 복제 되지 않습니다|  
|**schemaguid**|**uniqueidentifier**|스키마 변경 내용을 식별합니다.|  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="remarks"></a>주의  
 **sp_enumeratependingschemachanges** 병합 복제에 사용 됩니다.  
  
 **sp_enumeratependingschemachanges**와 함께 사용 [sp_markpendingschemachange](../../relational-databases/system-stored-procedures/sp-markpendingschemachange-transact-sql.md), 병합 복제의 지원 가능성에 대 한 사용 및 사용 해야 경우에만 다른 수정 조치와 같은 다시 초기화 상황을 해결 하려면 실패 합니다.  
  
## <a name="permissions"></a>Permissions  
 구성원만는 **sysadmin** 고정된 서버 역할 또는 **db_owner** 고정된 데이터베이스 역할을 실행할 수 있는 **sp_enumeratependingschemachanges**합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [복제 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sysmergeschemachange &#40; Transact SQL &#41;](../../relational-databases/system-tables/sysmergeschemachange-transact-sql.md)  
  
  