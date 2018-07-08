---
title: Integration Services 서비스에 권한을 부여 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c2caa68-7834-4ea0-bd77-4f3a7c86d634
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 32b8ee36951ec828340de5c6d581f0b8d8bc919a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36180545"
---
# <a name="grant-permissions-to-integration-services-service"></a>Integration Services 서비스에 사용 권한 부여
  이전 버전의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 를 설치하면 기본적으로 Users 그룹의 모든 사용자에게 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스에 대한 액세스 권한이 부여되었지만 현재 릴리스의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]를 설치하면 사용자에게 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스에 대한 액세스 권한이 부여되지 않습니다. 이 서비스에는 기본적으로 보안이 적용됩니다. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 가 설치된 후 관리자가 서비스에 대한 액세스 권한을 부여해야 합니다.  
  
### <a name="to-grant-access-to-the-integration-services-service"></a>Integration Services 서비스에 대한 액세스 권한을 부여하려면  
  
1.  Dcomcnfg.exe를 실행합니다. Dcomcnfg.exe는 레지스트리의 특정 설정을 수정하는 사용자 인터페이스를 제공합니다.  
  
2.  **구성 요소 서비스** 대화 상자에서 구성 요소 서비스 > 컴퓨터 > 내 컴퓨터 > DCOM 구성 노드를 확장합니다.  
  
3.  마우스 오른쪽 단추로 클릭 **Microsoft SQL Server Integration Services 12.0**, 클릭 하 고 **속성**합니다.  
  
4.  **보안** 탭의 **시작 및 활성화 권한** 영역에서 **편집** 을 클릭합니다.  
  
5.  사용자를 추가하고 적절한 권한을 할당한 다음 확인을 클릭합니다.  
  
6.  액세스 권한에 대해 4-5단계를 반복합니다.  
  
7.  SQL Server Management Studio를 다시 시작합니다.  
  
8.  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스를 다시 시작합니다.  
  
  