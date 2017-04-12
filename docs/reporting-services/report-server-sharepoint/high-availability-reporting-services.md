---
title: "고가용성(Reporting Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "고가용성 [SQL Server], Reporting Services"
  - "고가용성 [Reporting Services]"
  - "Reporting Services, 고가용성"
ms.assetid: 50e0813f-f591-4688-9cd1-e6389a3808e5
caps.latest.revision: 16
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 16
---
# 고가용성(Reporting Services)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 보고서 서버는 응용 프로그램 데이터, 내용, 속성 및 세션 정보를 두 개의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 관계형 데이터베이스에 저장하는 상태 비저장 서버입니다. 따라서 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 기능의 가용성을 보장하는 가장 좋은 방법은 다음을 수행하는 것입니다.  
  
-    [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 고가용성 기능을 사용하여 보고서 서버 데이터베이스의 작동 시간을 최대화합니다. 장애 조치(Failover) 클러스터에서 실행되도록 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스를 구성하는 경우 보고서 서버 데이터베이스를 만들 때 해당 인스턴스를 선택할 수 있습니다.  
  
-   가능하면 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 데이터베이스 및 데이터 원본에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]을 사용하세요. 자세한 내용은 [Always On 가용성 그룹이 포함된 Reporting Services&#40;SQL Server&#41;](../../database-engine/availability-groups/windows/reporting-services-with-always-on-availability-groups-sql-server.md)를 참조하세요.  
  
-   모든 서버가 단일 보고서 서버 데이터베이스를 공유하는 확장 배포에서 여러 보고서 서버가 실행되도록 구성합니다. 확장 배포에서 서로 다른 서버에 여러 보고서 서버 인스턴스를 배포하면 보고서 서버 인스턴스 중 하나가 작동이 중단되는 경우에도 중단되지 않는 서비스를 제공할 수 있습니다.  
  
 확장 배포를 사용하면 데이터베이스를 공유할 수 있습니다. 한 보고서 서버가 작동이 중단되는 경우에도 같은 배포에 있는 다른 서버는 계속 작동됩니다.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 는 클러스터 인식형이 아닙니다. 확장 배포는 단독으로 로드 균형 조정 기능을 제공하지 않습니다. 즉, 보고서 서버의 처리 부하를 감지하고 새 처리 요청을 사용량이 가장 적은 서버로 라우팅하지 않습니다. 또한 완료 전에 실패한 처리 요청을 다시 라우팅하지 않습니다. 로드 균형 조정 기능을 사용하려면 보고서 서버를 호스팅하는 웹 서버에 대해 로드 균형 조정을 구성한 다음 확장 배포의 보고서 서버를 구성하여 이러한 보고서 서버가 모두 같은 보고서 서버 데이터베이스를 공유하도록 해야 합니다.  
  
 보고서 서버 웹 서비스 및 Windows 서비스는 완벽하게 통합되어 있으며 단일 보고서 서버 인스턴스로 함께 실행됩니다. 한 서비스에 대한 가용성을 다른 서비스와 별도로 구성할 수는 없습니다.  
  
## 관련 항목:  
 [고가용성 솔루션&#40;SQL Server&#41;](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md)   
 [확장 배포 - Reporting Services 기본 모드&#40;구성 관리자&#41;](../Topic/Scale-out%20Deployment%20%20-%20Reporting%20Services%20Native%20mode%20\(Configuration%20Manager\).md)  
  
  