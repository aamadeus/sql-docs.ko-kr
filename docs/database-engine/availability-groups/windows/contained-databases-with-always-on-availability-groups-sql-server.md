---
title: Always On 가용성 그룹이 있는 포함된 데이터베이스(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], interoperability
- contained database, AlwaysOnAvailabilityGroups
ms.assetid: cacce3ae-e940-4566-8298-6607c4268e74
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3a1252614ee29436ac15ba3e783e22a834abe0f5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47826971"
---
# <a name="contained-databases-with-always-on-availability-groups-sql-server"></a>Always On 가용성 그룹에 포함된 데이터베이스(SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  이 항목에서는 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 의 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]에서 포함된 데이터베이스를 사용하는 방법에 대한 정보를 제공합니다.  
  
 **항목 내용:**  
  
-   [필수 구성 요소](#Prerequisites)  
  
-   [관련 작업](#RelatedTasks)  
  
##  <a name="Prerequisites"></a> 사전 요구 사항  
  
-   포함된 데이터베이스를 가용성 그룹에 추가하기 전에 가용성 그룹에 대한 가용성 복제본을 호스팅하는 모든 서버 인스턴스에서 **contained database authentication** 서버 옵션이 **1** 로 설정되어 있는지 확인합니다. 자세한 내용은 [contained database authentication 서버 구성 옵션](../../../database-engine/configure-windows/contained-database-authentication-server-configuration-option.md) 및 [서버 구성 옵션&#40;SQL Server&#41;](../../../database-engine/configure-windows/server-configuration-options-sql-server.md)에서 포함된 데이터베이스를 사용하는 방법에 대한 정보를 제공합니다.  
  
##  <a name="RelatedTasks"></a> 관련 태스크  
  
-   [서버 구성 옵션&#40;SQL Server&#41;](../../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
## <a name="see-also"></a>참고 항목  
 [Always On 가용성 그룹 개요&#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [포함된 데이터베이스](../../../relational-databases/databases/contained-databases.md)  
  
  
