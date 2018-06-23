---
title: 게시 속성, 에이전트 보안 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.rep.newpubwizard.pubproperties.agentsecurity.f1
ms.assetid: 03945aac-66f2-4370-b5d1-c1de694bc4c1
caps.latest.revision: 20
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 2b72ec15e139ee164e74589ce70db4e193972ee0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36182990"
---
# <a name="publication-properties-agent-security"></a>게시 속성, 에이전트 보안
  **게시 속성** 대화 상자의 **에이전트 보안** 페이지를 사용하여 다음 에이전트를 실행하고 복제 토폴로지의 컴퓨터에 연결할 때 사용되는 계정의 설정에 액세스할 수 있습니다.  
  
-   모든 게시에 대한 스냅숏 에이전트입니다.  
  
-   모든 트랜잭션 게시에 대한 로그 판독기 에이전트입니다. 트랜잭션 복제에 대해 게시된 각 데이터베이스에 하나의 로그 판독기 에이전트가 있습니다. 로그 판독기 에이전트 설정을 변경하면 데이터베이스의 모든 트랜잭션 게시에 영향을 줍니다.  
  
-   지연 업데이트 구독을 허용하는 트랜잭션 게시에 대한 큐 판독기 에이전트 각 배포 데이터베이스에 대해 하나의 큐 판독기 에이전트가 있습니다. 큐 판독기 에이전트 설정을 변경하면 같은 배포 데이터베이스를 사용하는 지연 업데이트 구독이 있는 모든 트랜잭션 게시에 영향을 줍니다. 큐 판독기 에이전트 보안 설정에 대한 자세한 내용은 [복제 보안 설정 보기 및 수정](security/view-and-modify-replication-security-settings.md)을 참조하세요.  
  
 각 에이전트에 필요한 보안 설정 및 사용 권한에 대한 자세한 내용은 [Replication Agent Security Model](security/replication-agent-security-model.md)을 참조하십시오.  
  
## <a name="options"></a>변수  
 **보안 설정** 또는 **에이전트 만들기**  
 에이전트 작업이 생성된 경우 **보안 설정** 을 클릭하여 에이전트 보안 설정을 변경할 수 있는 대화 상자에 액세스합니다. 에이전트 작업이 생성되지 않은 경우 **에이전트 만들기** 를 클릭하여 새 에이전트를 만들고 보안 설정을 지정합니다.  
  
## <a name="see-also"></a>관련 항목  
 [Create a Publication](publish/create-a-publication.md)   
 [게시 속성 보기 및 수정](publish/view-and-modify-publication-properties.md)   
 [데이터 및 데이터베이스 개체 게시](publish/publish-data-and-database-objects.md)   
 [Replication Security Best Practices](security/replication-security-best-practices.md)   
 [보안 및 보호&#40;복제&#41;](security/security-and-protection-replication.md)  
  
  