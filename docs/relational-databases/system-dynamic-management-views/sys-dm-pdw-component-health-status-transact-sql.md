---
title: sys.dm_pdw_component_health_status (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68cc3f7a-693c-4d5d-a76b-455352af8d7f
caps.latest.revision: "6"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d87c8ef38185e3194da1d13f8a9732991023f0ab
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmpdwcomponenthealthstatus-transact-sql"></a>sys.dm_pdw_component_health_status (Transact SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  어플라이언스 구성 요소의 현재 상태에 대 한 정보를 보유합니다.  
  
|열 이름|데이터 형식|Description|범위|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**||Not NULL|  
|component_id|int|구성 요소의 ID입니다. 참조 [sys.pdw_health_components &#40; Transact SQL &#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> pdw_node_id 속성, component_id, id와 component_instance_id이이 보기에 대 한 키를 형성 합니다.|Not NULL|  
|property_id|**int**|속성의 ID입니다. 참조 [sys.pdw_health_component_properties &#40; Transact SQL &#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-component-properties-transact-sql.md).|NOT  NULL|  
|component_instance_id|**nvarchar(255)**|구성 요소의 인스턴스를 식별합니다. Component_instance_id로 CPU의 인스턴스 수 식별 하는 예를 들어 'CPU1' = 합니다.<br /><br /> pdw_node_id 속성, component_id, id와 component_instance_id이이 보기에 대 한 키를 형성 합니다.|NOT  NULL|  
|property_value|**nvarchar(255)**|현재 속성 값입니다.|NULL|  
|update_time|**datetime**|에 대 한 메트릭은 마지막으로 업데이트 되었습니다.|NOT  NULL|  
  
## <a name="see-also"></a>관련 항목:  
 [SQL 데이터 웨어하우스 및 병렬 데이터 웨어하우스 동적 관리 뷰 &#40; Transact SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  