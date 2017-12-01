---
title: "APS 도메인 관리자 (APS) 만들기"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ed52bf78-2b0a-4252-98a7-8c2805e22d3d
caps.latest.revision: "7"
ms.openlocfilehash: 5ec32cd93b7fece9e12076fa82eea147bf13b81b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="create-an-aps-domain-administrator"></a>APS 도메인 관리자 만들기
일부 작업에는 분석 플랫폼 시스템 도메인 관리자 권한이 필요 합니다. 이 추가 기기 도메인 관리자를 만드는 방법을 설명 합니다.  
  
## <a name="create-a-domain-administrator"></a>도메인 관리자 만들기  
APS 노드를 모두 실행 하는 사용자를 구성할 수 있는 충분 한 권한이 **APS Configuration Manager** (`dwconfig.exe`)의 구성원 이어야 합니다는 **Domain Admins** 그룹입니다. 시작 하 고 중지할 APS 서비스, 사용자의 구성원 이어야 합니다는 **PdwControlNodeAccess** 그룹입니다.  
  
#### <a name="to-add-a-user-to-the-domain-admins-group"></a>Domain Admins 그룹에 사용자를 추가 하려면  
  
1.  로그 활성 AD 노드로  **(*appliance_domain*-AD01 * * 또는  ***appliance_domain*-AD02**) 기존 어플라이언스 도메인을 사용 하 여 관리자 계정입니다.  
  
2.  시작 메뉴에서 **실행**을 클릭합니다. 에 **열려** 상자에서 입력 **dsa.msc**합니다. **확인**을 클릭합니다.  
  
3.  에 **Active Directory 사용자 및 컴퓨터** 프로그램 마우스 오른쪽 단추로 클릭 **사용자**, 가리킨 **새로**, 클릭 하 고 **사용자**합니다.  
  
4.  에 **새 개체 – 사용자** 대화 상자에서 새 사용자에 대 한 설명을 채운 다음 클릭 **다음**합니다.  
  
    암호 대화 상자를 완료 한 다음 클릭 **다음**합니다.  
  
    > [!WARNING]  
    > SQL Server PDW는 도메인 관리자 또는 로컬 관리자 암호에 달러 기호 ($) 문자를 지원 하지 않습니다. 달러 기호를 포함 하는 암호를 유효 하 고 사용할 수 있도록 하지만 업그레이드 및 유지 관리 작업을 차단할 수 있습니다.  
  
    새 사용자 설명을 확인 한 다음 클릭 **마침**합니다.  
  
5.  사용자 목록에서 사용자 속성 대화 상자를 열려면 새 사용자를 두 번 클릭 합니다.  
  
6.  에 **소속** 탭을 클릭 **추가**합니다.  
  
    형식 **Domain Admins; PdwControlNodeAccess** 클릭 하 고 **이름 확인**합니다. **확인**을 클릭합니다.  
  
    이렇게 하면 새 사용자를 추가 **Domain Admins** 그룹 및 **PdwControlNodeAccess** 그룹입니다. **확인**을 클릭합니다.  
  
## <a name="see-also"></a>관련 항목:  
[구성 관리자 &#40; 시작 분석 플랫폼 시스템 &#41;](launch-the-configuration-manager.md)  
  