---
title: "배포 에이전트 보안 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.security.DA.f1"
helpviewer_keywords: 
  - "배포 에이전트 보안 대화 상자"
ms.assetid: de40cc21-2e58-4464-9be7-b5b90c925e9b
caps.latest.revision: 25
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 25
---
# 배포 에이전트 보안
  **배포 에이전트 보안** 대화 상자를 사용하여 배포 에이전트를 실행하는 Windows 계정을 지정할 수 있습니다. 배포 에이전트는 밀어넣기 구독을 위한 배포자 또는 끌어오기 구독을 위한 구독자에서 실행됩니다. [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 계정으로 에이전트 프로세스가 실행되기 때문에 이 계정을 *프로세스 계정*이라고도 합니다. 이 대화 상자에서 사용 가능한 추가 옵션은 대화 상자에 액세스하는 방법에 따라 달라집니다.  
  
-   새 구독 마법사에서 이 대화 상자에 액세스하는 경우 배포 에이전트를 구독자(밀어넣기 구독의 경우) 또는 배포자(끌어오기 구독의 경우)에 연결하는 컨텍스트도 지정할 수 있습니다. Windows 계정을 가장하거나 지정한 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 계정의 컨텍스트에서 연결을 설정할 수 있습니다.  
  
-   대화 상자에서 액세스 하는 경우는 **구독 속성** 대화 상자에 배포 에이전트 연결의 속성 단추를 클릭 하 여 사용 하는 컨텍스트를 지정 합니다 (**...**)에 **구독자 연결** 또는 **배포자 연결** 해당 대화 상자의 행 합니다. 에 액세스 하는 방법에 대 한 자세한 내용은 **구독 속성** 대화 상자, 참조 [뷰와 밀어넣기 구독 속성을 수정](../../relational-databases/replication/view-and-modify-push-subscription-properties.md) 하는 방법과: [뷰와 끌어오기 구독 속성을 수정](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)합니다.  
  
 모든 계정이 유효해야 하며 각 계정에 대해 올바른 암호를 지정해야 합니다. 계정 및 암호의 유효성은 에이전트를 실행할 때 검사합니다.  
  
## 옵션  
 **프로세스 계정**  
 배포 에이전트를 실행하는 Windows 계정을 입력합니다.  
  
-   밀어넣기 구독의 경우 계정이 다음 조건을 만족해야 합니다.  
  
    -   At 최소 수의 멤버는 **db_owner** 배포 데이터베이스에서 고정된 데이터베이스 역할입니다.  
  
    -   PAL(게시 액세스 목록)의 멤버여야 합니다.  
  
    -   스냅숏 공유에 대해 읽기 권한이 있어야 합니다.  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이외 구독자에 대한 구독인 경우에는 구독자에 대한 OLE DB 공급자의 설치 디렉터리에 대해 읽기 권한이 있어야 합니다.  
  
-   끌어오기 구독의 경우 계정이 적어도의 구성원 이어야는 **db_owner** 구독 데이터베이스에서 고정된 데이터베이스 역할입니다.  
  
 연결을 설정할 때 프로세스 계정을 가장하면 추가 사용 권한이 필요합니다. 아래의 **배포자에 연결** 및 **구독자에 연결** 섹션을 참조하십시오.  
  
 **프로세스 계정** 끌어오기 구독에 대해 지정할 수 없습니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], 배포 에이전트의 인스턴스에서 실행 되지 않기 때문에 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]합니다.  
  
 **암호** 및 **암호 확인**  
 Windows 계정의 암호를 입력합니다.  
  
 **배포자에 연결**  
 밀어넣기 구독의 경우 배포자에 연결은 항상에 지정한 계정을 가장 하 여 설정 됩니다는 **프로세스 계정** 텍스트 상자입니다.  
  
 끌어오기 구독의 경우 배포 에이전트를 배포자에 연결할 때 **프로세스 계정** 입력란에 지정한 계정을 가장할지, 아니면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 계정을 사용할지를 선택합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 계정을 사용하도록 선택한 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인과 암호를 입력합니다.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 계정을 사용하는 것보다 Windows 계정을 가장하도록 선택하는 것이 좋습니다.  
  
 연결에 사용할 Windows 계정 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 계정은 다음 조건을 만족해야 합니다.  
  
-   PAL의 멤버여야 합니다.  
  
-   스냅숏 공유에 대해 읽기 권한이 있어야 합니다.  
  
 **구독자에 연결**  
 끌어오기 구독의 경우 구독자에 연결은 항상에 지정한 계정을 가장 하 여 설정 됩니다는 **프로세스 계정** 텍스트 상자입니다.  
  
 밀어넣기 구독의 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구독자 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이외 구독자에 대한 옵션이 다음과 같이 다릅니다.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구독자의 경우 배포 에이전트를 구독자에 연결할 때 **프로세스 계정** 입력란에 지정한 계정을 가장할지, 아니면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 계정을 사용할지를 선택합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 계정을 사용하도록 선택한 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인과 암호를 입력합니다.  
  
    > [!NOTE]  
    >  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 계정을 사용하는 것보다 Windows 계정을 가장하도록 선택하는 것이 좋습니다.  
  
     Windows 계정 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구독자에 대 한 연결에 사용 되는 계정에 최소한 속해야의 **db_owner** 구독 데이터베이스에서 고정된 데이터베이스 역할입니다.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이외 구독자의 경우 배포 에이전트를 구독자에 연결할 때 사용할 데이터베이스 로그인을 구독자에서 지정합니다. 해당 로그인에는 구독 데이터베이스에서 개체를 만들 권한이 있어야 합니다. 비-구성에 대 한 자세한 내용은[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구독자 참조 [비-SQL Server 구독자에 대 한 구독을 만들](../../relational-databases/replication/create-a-subscription-for-a-non-sql-server-subscriber.md)합니다.  
  
 **추가 연결 옵션**  
 이 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이외 구독자에 대해서만 사용할 수 있습니다. 연결 문자열 형식으로 구독자에 대한 연결 옵션을 지정하십시오. Oracle에서는 추가 옵션을 지정할 필요가 없습니다. 각 옵션은 세미콜론으로 구분해야 합니다. 다음은 IBM DB2 연결 문자열의 예입니다. 이 예에서는 읽기 쉽도록 줄 바꿈을 넣었습니다.  
  
```  
Provider=DB2OLEDB;Initial Catalog=MY_SUBSCRIBER_DB;Network Transport Library=TCP;Host CCSID=1252;  
PC Code Page=1252;Network Address=MY_SUBSCRIBER;Network Port=50000;Package Collection=MY_PKGCOL;  
Default Schema=MY_SCHEMA;Process Binary as Character=False;Units of Work=RUW;DBMS Platform=DB2/NT;  
Persist Security Info=False;Connection Pooling=True;  
```  
  
 이 문자열의 옵션 대부분은 구성 중인 DB2 서버와만 관련이 있지만 **Process Binary as Character** 옵션은 항상 **False**로 설정해야 합니다. 구독 데이터베이스를 식별하려면 **Initial Catalog** 옵션 값을 지정해야 합니다. 자세한 내용은 [IBM DB2 Subscribers](../../relational-databases/replication/non-sql/ibm-db2-subscribers.md)을 참조하세요.  
  
## 참고 항목  
 [복제의 로그인 및 암호 관리](../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)   
 [복제 에이전트 보안 모델](../../relational-databases/replication/security/replication-agent-security-model.md)   
 [복제 에이전트 개요](../../relational-databases/replication/agents/replication-agents-overview.md)   
 [복제 보안을 위한 최선의 구현 방법](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [게시 구독](../../relational-databases/replication/subscribe-to-publications.md)  
  
  