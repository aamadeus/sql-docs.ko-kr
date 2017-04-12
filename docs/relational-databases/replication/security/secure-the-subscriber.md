---
title: "구독자 보안 설정 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "구독 [SQL Server 복제], 보안"
  - "구독자 [SQL Server 복제], 보안"
  - "보안 [SQL Server 복제], 구독자"
ms.assetid: c8f0d62a-8b5d-4a21-9aec-223da52bb708
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 36
---
# 구독자 보안 설정
  병합 에이전트 및 배포 에이전트는 구독자에 연결합니다. 이러한 연결은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 로그인 또는 Windows 로그인의 컨텍스트에서 설정됩니다. 필요한 최소 권한만 부여하는 원칙을 따르고 모든 암호 저장소를 보호하면서 이러한 에이전트에 적절한 로그인을 제공하는 것이 중요합니다. 각 에이전트에 필요한 사용 권한에 대한 자세한 내용은 [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md)을 참조하십시오.  
  
## 배포 에이전트  
 구독당 배포 에이전트가 하나씩(독립 에이전트 - 새 게시 마법사에서 생성된 게시의 기본값임) 또는 한 쌍의 게시 데이터베이스와 구독 데이터베이스당 배포 에이전트가 하나씩(공유 에이전트) 있습니다. T  
  
 밀어넣기 구독에 대 한 연결 정보를 지정 하려면 참조 [밀어넣기 구독을 만들](../../../relational-databases/replication/create-a-push-subscription.md)합니다.  
  
 끌어오기 구독에 대 한 연결 정보를 지정 하려면 참조 [끌어오기 구독 만들기](../../../relational-databases/replication/create-a-pull-subscription.md)  
  
## 병합 에이전트  
 각 병합 구독에는 게시자 및 구독자 모두에 연결되고 모두를 업데이트하는 자체 병합 에이전트가 있습니다.  
  
 밀어넣기 구독에 대 한 연결 정보를 지정 하려면 참조 [밀어넣기 구독을 만들](../../../relational-databases/replication/create-a-push-subscription.md)합니다.  
  
 끌어오기 구독에 대 한 연결 정보를 지정 하려면 참조 [끌어오기 구독을 만들](../../../relational-databases/replication/create-a-pull-subscription.md)합니다.  
  
## 즉시 업데이트 구독  
 즉시 업데이트 구독을 구성할 때는 게시자에 연결할 때 사용할 계정을 구독자에서 지정합니다. 이 연결은 구독자에서 발생되는 트리거에 사용되고 게시자로 변경 내용을 전파합니다. 연결 유형에 대해 3가지 옵션을 사용할 수 있습니다.  
  
-   복제가 만드는 연결된 서버 - 구성 시 지정하는 자격 증명으로 연결합니다.  
  
-   복제가 만드는 연결된 서버 - 구독자에서 변경 내용을 적용하는 사용자의 자격 증명으로 연결합니다.  
  
-   이미 정의한 연결된 서버나 원격 서버  
  
> [!IMPORTANT]  
>  연결 정보를 지정 하려면 저장된 프로시저를 사용 하 여 [sp_link_publication (& a) #40; TRANSACT-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md)합니다. 사용할 수도 있습니다는 **업데이트할 수 있는 구독에 대 한 로그인** 를 호출 하는 새 구독 마법사의 페이지 **sp_link_publication**합니다. 특정 상황에서는 구독자가 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] SP1(서비스 팩 1) 이상을 실행하고 게시자가 이전 버전을 실행할 경우 이 저장 프로시저가 실패할 수 있습니다. 이 시나리오에서 저장 프로시저가 실패할 경우 게시자를 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] SP1 이상으로 업그레이드합니다.  
  
 자세한 내용은 참조 [트랜잭션 게시에 업데이트할 수 있는 구독을 만들](../../../relational-databases/replication/publish/create-an-updatable-subscription-to-a-transactional-publication.md) 및 [보기 및 복제 보안 설정 수정](../../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)합니다.  
  
> [!IMPORTANT]  
>  연결에 대해 지정된 계정에는 복제가 게시 데이터베이스에 만드는 뷰에서 데이터를 삽입, 업데이트 및 삭제할 수 있는 사용 권한만 부여하고 다른 추가 사용 권한은 부여하지 않습니다. 폼에 이름이 지정 된 게시 데이터베이스의 뷰에 대 한 권한을 부여 **syncobj_***\< HexadecimalNumber>* 각 구독자에서 구성한 계정에 있습니다.  
  
## 지연 업데이트 구독  
 지연 업데이트 구독 구성 시 보안과 관련된 다음 두 가지 영역을 유의하십시오.  
  
-   각 배포자에 대해 하나의 큐 판독기 에이전트만 있습니다. 각 배포자에 대해 지연 업데이트 구독이 설정된 하나의 게시를 구성하는 것이 좋습니다.  
  
-   큐 판독기 에이전트는 배포자, 게시자 및 각 구독자에 연결합니다.  
  
    -   에이전트를 만들 때 에이전트가 실행되고 배포자 연결에 사용되는 계정이 지정됩니다. 새 게시 마법사를 사용하는 경우에는 구독 업데이트가 설정된 게시를 만들 때 에이전트가 생성됩니다.  
  
    -   게시자에 대한 배포를 구성할 때 에이전트가 게시자 연결에 사용하는 계정이 지정됩니다. 에이전트가 실행되는 Windows 계정 또는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 계정을 지정합니다.  
  
    -   구독을 만들 때 에이전트가 구독자 연결에 사용하는 계정이 지정됩니다.  
  
    > [!IMPORTANT]  
    >  구독자 연결에 대해서는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증을 사용하고 각 구독자 연결에는 서로 다른 계정을 지정합니다. 끌어오기 구독을 사용하는 경우 복제는 항상 Windows 인증을 사용하도록 연결을 설정합니다. 끌어오기 구독에서 복제는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증을 사용하는 데 필요한 메타데이터를 구독자에서 액세스할 수 없습니다. 이 경우 구독을 구성한 후 연결에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증을 사용하도록 변경합니다.  
  
     자세한 내용은 참조 하는 방법: 만들기 (SQL Server Management Studio) 트랜잭션 게시에 대 한 업데이트 구독 및 [보기 및 복제 보안 설정 수정](../../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)합니다.  
  
## 참고 항목  
 [데이터베이스 엔진 및 #40;에 암호화 연결 사용 SQL Server 구성 관리자 및 #41;](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md)   
 [복제 보안을 위한 최선의 구현 방법](../../../relational-databases/replication/security/replication-security-best-practices.md)   
 [보안 및 보호 & #40입니다. 복제 및 #41;](../../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  