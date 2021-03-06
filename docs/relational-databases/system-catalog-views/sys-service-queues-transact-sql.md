---
title: sys.service_queues (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.service_queues
- service_queues
- service_queues_TSQL
- sys.service_queues_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.service_queues catalog view
ms.assetid: 9fd9fa76-6128-410c-896f-741e6050143a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 073329c4c2da31e3defb6a2e2dcaa77d6109228e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47762911"
---
# <a name="sysservicequeues-transact-sql"></a>sys.service_queues(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  서비스 큐는 데이터베이스의 각 개체에 대 한 행을 포함 **sys.objects.type** = SQ.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**\<열을 상속 >**||이 뷰가 상속 하는 열 목록은 참조 하세요 [sys.objects &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)합니다.|  
|**max_readers**|**smallint**|큐에서 허용된 최대 동시 판독기 수입니다.|  
|**activation_procedure**|**nvarchar(776)**|세 부분으로 된 활성화 프로시저 이름입니다.|  
|**execute_as_principal_id**|**int**|EXECUTE AS 데이터베이스 보안 주체의 ID입니다.<br /><br /> 기본값은 NULL이며 EXECUTE AS CALLER인 경우에도 NULL입니다.<br /><br /> 경우 지정한 보안 주체의 ID AS SELF EXECUTE AS 실행 \<사용자 >.<br /><br /> -2 = EXECUTE AS OWNER|  
|**is_activation_enabled**|**bit**|1 = 활성화가 설정됩니다.|  
|**is_receive_enabled**|**bit**|1 = 수신이 설정됩니다.|  
|**is_enqueue_enabled**|**bit**|1 = 큐에 대한 저장이 설정됩니다.|  
|**is_retention_enabled**|**bit**|1 = 대화가 끝날 때까지 메시지가 보관됩니다.|  
|**is_poison_message_handling_enabled**|**bit**|**적용 대상**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 부터 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]까지<br /><br /> 1 = 포이즌 메시지 처리가 설정됩니다.|  
  
## <a name="permissions"></a>사용 권한  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 자세한 내용은 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)을 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [개체 카탈로그 뷰 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [카탈로그 뷰&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
