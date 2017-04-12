---
title: "게시 속성, FTP 스냅숏 및 인터넷 | Microsoft Docs"
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
  - "sql13.rep.newpubwizard.pubproperties.internetsynchronization.f1"
ms.assetid: 8e0198c3-5e4e-418c-9920-78ccbbfc1323
caps.latest.revision: 25
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 25
---
# 게시 속성, FTP 스냅숏 및 인터넷
  이 페이지에서는 다음 작업을 수행할 수 있습니다.  
  
-   FTP(파일 전송 프로토콜)를 통해 스냅숏을 배달하는 속성을 설정합니다. 자세한 내용은 참조 [FTP를 통해 스냅숏 전송](../../relational-databases/replication/transfer-snapshots-through-ftp.md)합니다. FTP를 사용하여 스냅숏을 배달하려면 FTP 서버를 설정해야 합니다. 자세한 내용은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 설명서를 참조하십시오.  
  
    > [!NOTE]  
    >  FTP 설정을 변경하면 새 스냅숏을 생성해야 합니다.  
  
-   HTTPS(Secure Hypertext Transfer Protocol)를 통해 구독을 동기화하도록 허용하는 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전의 병합 복제에 대한 웹 동기화 속성을 설정합니다. 웹 동기화를 사용하려면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 인터넷 정보 서비스(IIS) 서버를 구성해야 합니다. 자세한 내용은 [Web Synchronization for Merge Replication](../../relational-databases/replication/web-synchronization-for-merge-replication.md)을 참조하세요.  
  
## 옵션  
 **FTP를 통해 스냅숏 파일 액세스**  
 선택 **구독자가 FTP (파일 전송 프로토콜)를 사용 하 여 스냅숏 파일을 다운로드 하려면**, 지정 **FTP 서버 이름**, **포트 번호**, **FTP 루트 폴더의 경로**, **로그인**, 및 **암호**, 구독자가 스냅숏 전달에 FTP를 사용할 수 있도록 합니다.  
  
 이 옵션을 사용하면 구독자는 FTP를 사용하여 스냅숏 파일을 검색할 수 있지만 반드시 그럴 필요는 없습니다. 이 옵션을 선택하면 새 구독 마법사는 구독자가 FTP를 통해 스냅숏 파일을 검색하는 것을 기본값으로 설정합니다. 설정을 변경하려면 **구독 속성** 대화 상자를 사용합니다. 구독자가 FTP를 통해 스냅숏 파일에 액세스할 수 있도록 허용하는 경우 **게시 속성** 대화 상자의 **스냅숏** 페이지에서 FTP 폴더를 스냅숏 파일의 위치로 지정합니다. 이렇게 하면 새 스냅숏이 생성될 때 스냅숏 에이전트가 FTP 폴더의 파일을 자동으로 업데이트합니다. 위치가 FTP 폴더로 설정되어 있지 않으면 새 스냅숏을 생성할 때 파일을 수동으로 업데이트해야 합니다. 자세한 내용은 참조 [FTP를 통해 스냅숏 배달](../../relational-databases/replication/publish/deliver-a-snapshot-through-ftp.md)합니다.  
  
 **웹 동기화**  
 병합 복제에 대해서만 사용할 수 있습니다. **구독자가 웹 서버에 연결하여 동기화하도록 허용**을 선택하고 병합 구독자가 웹 동기화를 사용할 수 있는 웹 서버 주소를 지정합니다. 웹 서버는 SSL(Secure Sockets Layer)을 사용해야 하고 웹 주소는 https://server.domain.com/synchronize와 같이 정규화된 주소여야 합니다. 자세한 내용은 [Configure Web Synchronization](../../relational-databases/replication/configure-web-synchronization.md)을 참조하세요.  
  
## 참고 항목  
 [게시 만들기](../../relational-databases/replication/publish/create-a-publication.md)   
 [게시 속성 보기 및 수정](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [끌어오기 구독 속성 보기 및 수정](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [밀어넣기 구독 속성 보기 및 수정](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)   
 [초기 스냅숏 만들기 및 적용](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)   
 [데이터 및 데이터베이스 개체 게시](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  