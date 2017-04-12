---
title: "SQL 전체 텍스트 필터 데몬 시작 관리자(로그온 탭) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 13e260f9-a75f-430b-88a3-959ddcead8fe
caps.latest.revision: 9
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 9
---
# SQL 전체 텍스트 필터 데몬 시작 관리자(로그온 탭)
  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]부터는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 전체 텍스트 검색에서 SQL 전체 텍스트 필터 데몬 시작 관리자(FDHOST Launcher) 서비스가 사용됩니다. 전체 텍스트 검색을 사용할 경우 이 서비스를 실행해야 합니다. 필터 데몬 호스트 프로세스에 대한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서의 "전체 텍스트 검색 아키텍처"를 참조하십시오.  
  
 사용 하는 **로그온에** 탭은 **SQL 전체 텍스트 필터 데몬 시작 관리자 속성** 대화 상자에서 사용할 계정을 지정 하려면는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 전체 텍스트 서비스는 계정의 암호를 변경 하 고 시작 하 고 서비스를 중지 합니다. 계정의 암호를 변경하는 경우 서비스를 다시 시작해야 변경된 암호가 적용됩니다.  
  
> [!NOTE]  
>  클러스터형 인스턴스의 서비스에서 사용하는 계정 이름을 변경하는 경우 새 계정은 서비스의 설치 중에 지정한 도메인 그룹의 멤버여야 합니다. 그렇지 않으면 해당 그룹에 멤버를 추가할 수 있는 권한이 있어야 합니다. 그룹 멤버 자격을 수정할 권한이 없을 경우 도메인 관리자에게 문의하십시오.  
>   
>  서비스를 실행할 계정을 선택하는 방법은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서의 "Windows 서비스 계정 설정"을 참조하십시오.  
  
## 옵션  
 **기본 제공 계정**  
 **로컬 시스템**  
 로컬 시스템 계정을 지정합니다. 이 계정에는 암호가 필요하지 않습니다. 그러나 로컬 시스템 계정은 계정에 부여된 권한에 따라 서비스가 다른 서버와 상호 작용하지 못하도록 할 수 있습니다.  
  
 **로컬 서비스**  
 로컬 서비스 계정을 지정합니다. 이 계정에는 암호가 필요하지 않습니다. 그러나 로컬 서비스 계정은 계정에 부여된 권한에 따라 서비스가 다른 서버와 상호 작용하지 못하도록 할 수 있습니다.  
  
 **네트워크 서비스**  
 에 대 한 네트워크 서비스 계정을 사용 하지 않는 것이 좋습니다는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스입니다. 이러한 서비스에 대해서는 로컬 사용자 또는 도메인 사용자 계정이 더 적합합니다.  
  
 **계정 지정**  
 Windows 인증을 사용하는 로컬 또는 도메인 사용자 계정을 지정합니다. 서비스에 대해 최소의 권한을 가진 도메인 사용자 계정을 사용하는 것이 좋습니다.  
  
 **계정 이름**  
 로컬 또는 도메인 사용자 계정 이름을 지정합니다.  
  
 **암호**  
 계정의 암호를 입력합니다.  
  
 **암호 확인**  
 계정의 암호를 다시 입력합니다.  
  
 **시작**  
 서비스를 시작합니다.  
  
 **중지**  
 서비스를 중지합니다.  
  
 **일시 중지**  
 서비스를 일시 중지합니다. 이 서비스를 사용할 수 없습니다.  
  
 **재개**  
 일시 중지한 서비스를 다시 시작합니다.  
  
  