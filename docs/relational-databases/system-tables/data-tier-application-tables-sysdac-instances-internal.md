---
title: sysdac_instances_internal (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdac_instances_internal_TSQL
- sysdac_instances_internal
dev_langs:
- TSQL
helpviewer_keywords:
- sysdac_instances_internal
ms.assetid: d2d52cc4-3463-431a-b779-6fbfdeee1dfc
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f1e30db7b31a0a29a5e78e7fc5876f43764d66a3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47827381"
---
# <a name="data-tier-application-tables---sysdacinstancesinternal"></a>데이터 계층 응용 프로그램 테이블 - sysdac_instances_internal
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에 배포된 DAC(데이터 계층 응용 프로그램) 인스턴스마다 하나의 행을 표시합니다. 이 테이블은 msdb 데이터베이스의 dbo 스키마에 저장 됩니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|instance_id|**uniqueidentifier**|DAC 인스턴스의 식별자입니다.|  
|instance_name|**sysname**|인스턴스를 배포할 때 지정된 DAC 인스턴스의 이름입니다.|  
|type_name|**sysname**|DAC 패키지를 만들 때 지정된 DAC의 이름입니다.|  
|type_version|**nvarchar(64)**|DAC 패키지를 만들 때 지정된 DAC의 버전입니다.|  
|description|**nvarchar(4000)**|DAC 패키지를 만들 때 작성된 DAC에 대한 설명입니다.|  
|type_stream|**varbinary(max)**|DAC에 포함된 테이블 및 뷰와 같은 논리 개체의 인코딩된 표현을 포함하는 비트 스트림입니다.|  
|date_created|**datetime**|DAC 인스턴스를 만든 날짜와 시간입니다.|  
|created_by|**sysname**|DAC 인스턴스를 만든 사람의 로그인 정보입니다.|  
  
## <a name="remarks"></a>Remarks  
 이 보기에 대 한 읽기 전용 액세스는 master 데이터베이스에 연결할 권한이 있는 모든 사용자에 게 제공 합니다.  
  
## <a name="permissions"></a>사용 권한  
 sysadmin 고정 서버 역할의 멤버 자격이 필요합니다.  
  
## <a name="see-also"></a>관련 항목  
 [데이터 계층 응용 프로그램](../../relational-databases/data-tier-applications/data-tier-applications.md)   
 [dbo.sysdac_instances &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/data-tier-application-views-dbo-sysdac-instances.md)  
  
  
