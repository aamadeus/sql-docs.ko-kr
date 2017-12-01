---
title: sys.dm_hadr_cluster_networks (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_hadr_cluster_networks
- sys.dm_hadr_cluster_networks_TSQL
- sys.dm_hadr_cluster_networks
- dm_hadr_cluster_networks_TSQL
dev_langs: TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], WSFC clusters
- sys.dm_hadr_cluster_networks dynamic management view
ms.assetid: ece32b15-d63f-4f93-92b7-e2930333e97a
caps.latest.revision: "15"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 77d2eaee6ce6ac28370a2c825eece9ade0440df0
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmhadrclusternetworks-transact-sql"></a>sys.dm_hadr_cluster_networks(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  가용성 그룹의 서브넷 구성에 참여하는 모든 WSFC 클러스터 구성원에 대해 하나의 행을 반환합니다. 이 동적 관리 뷰를 사용하여 각 가용성 복제본에 대해 구성된 네트워크 가상 IP의 유효성을 검사할 수 있습니다.  
  
 기본 키: **member_name** + **network_subnet_IP** + **network_subnet_prefix_length**  
  
 > [!TIP]
 > 부터는 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)],이 동적 관리 뷰에서 Always On 장애 조치 클러스터 인스턴스 Always On 가용성 그룹 외에도 지원 합니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**member_name**|**nvarchar (128)**|WSFC 클러스터에 있는 노드의 컴퓨터 이름입니다.|  
|**network_subnet_ip**|**nvarchar(48)**|컴퓨터가 속한 서브넷의 네트워크 IP 주소입니다. IPv4 또는 IPv6 주소일 수 있습니다.|  
|**network_subnet_ipv4_mask**|**nvarchar(45)**|IP 주소가 속한 서브넷을 지정하는 네트워크 서브넷 마스크입니다. **network_subnet_ipv4_mask** WITH DHCP 절에서 DHCP < network_subnet_option > 옵션을 지정 하는 [CREATE AVAILABILITY GROUP](../../t-sql/statements/create-availability-group-transact-sql.md) 또는 [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] 문입니다.<br /><br /> NULL = IPv6 서브넷.|  
||||  
|**network_subnet_prefix_length**|**int**|컴퓨터가 속한 서브넷을 지정하는 네트워크 IP 접두사 길이입니다.|  
|**is_public**|**bit**|WSFC 클러스터에서 개인 네트워크인지 공용 네트워크인지 여부를 나타내며 다음 중 하나입니다.<br /><br /> 0 = 개인<br /><br /> 1 = 공용|  
|**is_ipv4**|**bit**|서브넷의 유형이며 다음 중 하나입니다.<br /><br /> 1 = IPv4<br /><br /> 0 = IPv6|  
  
## <a name="security"></a>보안  
  
### <a name="permissions"></a>Permissions  
 을 실행하려면 서버에 대해 VIEW SERVER STATE 권한이 필요합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [장애 조치(failover) 클러스터링 및 Always On 가용성 그룹&#40;SQL Server&#41;](../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md)   
 [가용성 그룹 모니터링&#40;Transact-SQL&#41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [sys.dm_os_cluster_nodes &#40; Transact SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-cluster-nodes-transact-sql.md)   
 [SQL Server 시스템 카탈로그 FAQ](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [카탈로그 뷰&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  