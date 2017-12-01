---
title: sys.sysconfigures (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sysconfigures
- sysconfigures
- sys.sysconfigures_TSQL
- sysconfigures_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sys.sysconfigures compatibility view
- sysconfigures system table
ms.assetid: 146bf10a-c898-4676-a2a1-673fb1cee7a2
caps.latest.revision: "39"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4e2151437e11f60107ddbe2cbfc64cc1b6f155df
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/27/2017
---
# <a name="syssysconfigures-transact-sql"></a>sys.sysconfigures(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  사용자가 설정한 각 구성 옵션당 한 개의 행을 포함합니다. **sysconfigures** 의 가장 최근 시작 하기 전에 정의 된 구성 옵션이 포함 되어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], 그 이후에 설정 된 동적 구성 옵션입니다.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**값**|**int**|사용자 수정이 가능한 변수 값입니다. RECONFIGURE가 실행된 경우에만 [!INCLUDE[ssDE](../../includes/ssde-md.md)]에서 사용합니다.|  
|**구성**|**int**|구성 변수 번호입니다.|  
|**주석**|**nvarchar(255)**|구성 옵션에 대한 설명입니다.|  
|**상태**|**smallint**|옵션의 상태를 표시하는 비트맵입니다. 가능한 값은 다음과 같습니다.<br /><br /> 0 = 정적. 서버가 다시 시작될 때 설정이 적용됩니다.<br /><br /> 1 = 동적. RECONFIGURE 문이 실행될 때 변수가 적용됩니다.<br /><br /> 2 = 고급. 변수가 표시 됩니다 경우에만 **고급 옵션 표시** 설정 됩니다. 서버가 다시 시작될 때 설정이 적용됩니다.<br /><br /> 3 = 동적 및 고급입니다.|  
  
## <a name="see-also"></a>관련 항목:  
 [시스템 뷰 &#40; 시스템 테이블 매핑 Transact SQL &#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [호환성 뷰&#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  