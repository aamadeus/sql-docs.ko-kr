---
title: SQL Server, Latches 개체 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Latches object
- SQLServer:Latches
ms.assetid: 2393ea1c-2bf3-41c3-9f37-b9761144eeca
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 3b4953b71343dfa5bae3c0622369fb9bf3722c5f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48145689"
---
# <a name="sql-server-latches-object"></a>SQL Server, Latches 개체
  Microsoft **의** SQLServer:Latches [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 개체는 래치라고 하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 내부 리소스 잠금을 모니터링하는 카운터를 제공합니다. 래치를 모니터링하면 사용자 동작 및 리소스 사용을 확인해 성능 병목 상태를 찾아낼 때 유용합니다.  
  
 이 표에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **래치** 카운터에 대해 설명합니다.  
  
|SQL Server Latches 카운터|Description|  
|---------------------------------|-----------------|  
|**Average Latch Wait Time (ms)**|기다린 래치 요청에 대한 밀리초 단위의 평균 래치 대기 시간입니다.|  
|**Latch Waits/sec**|즉시 충족시킬 수 없는 래치 요청 수입니다.|  
|**Number of SuperLatches**|현재 SuperLatches인 래치 수입니다.|  
|**SuperLatch Demotions/sec**|마지막 1초 동안 일반 래치로 강등된 SuperLatches 수 입니다.|  
|**SuperLatch Promotions/sec**|마지막 1초 동안 SuperLatches로 승격된 래치 수입니다.|  
|**Total Latch Wait Time (ms)**|마지막 1초 동안 기다렸던 래치 요청에 대한 밀리초 단위의 총 래치 대기 시간입니다.|  
  
## <a name="see-also"></a>관련 항목  
 [리소스 사용 모니터링&#40;시스템 모니터&#41;](monitor-resource-usage-system-monitor.md)  
  
  
