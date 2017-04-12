---
title: "데이터베이스 마스터 키 백업 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "데이터베이스 마스터 키 [SQL Server], 내보내기"
ms.assetid: 7ad9a0a0-6e4f-4f7b-8801-8c1b9d49c4d8
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# 데이터베이스 마스터 키 백업
  이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 을 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 데이터베이스 마스터 키를 백업하는 방법에 대해 설명합니다. 데이터베이스 마스터 키는 데이터베이스 내의 다른 키와 인증서를 암호화하는 데 사용됩니다. 데이터베이스 마스터 키가 삭제되거나 손상된 경우 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 해당 마스터 키를 해독하지 못할 수 있으며 해당 마스터 키를 사용하여 암호화한 데이터는 사실상 손실됩니다. 그러므로 데이터베이스 마스터 키를 백업하고 이 백업을 안전한 오프 사이트 위치에 저장해야 합니다.  
  
 **항목 내용**  
  
-   **시작하기 전에:**  
  
     [제한 사항](#Restrictions)  
  
     [보안](#Security)  
  
-   [Transact-SQL을 사용하여 데이터베이스 마스터 키를 백업하려면](#Procedure)  
  
##  <a name="BeforeYouBegin"></a> 시작하기 전 주의 사항  
  
###  <a name="Restrictions"></a> 제한 사항  
  
-   마스터 키를 열어야 하기 때문에 백업하기 전에 암호를 해독해야 합니다. 서비스 마스터 키를 사용하여 암호화된 경우 마스터 키를 명시적으로 열 필요가 없습니다. 하지만 마스터 키가 암호로만 암호화된 경우 명시적으로 열어야 합니다.  
  
-   마스터 키는 만들자 마자 백업하고 외부의 안전한 위치에 보관하는 것이 좋습니다.  
  
###  <a name="Security"></a> 보안  
  
####  <a name="Permissions"></a> 사용 권한  
 데이터베이스에 대한 CONTROL 권한이 필요합니다.  
  
##  <a name="Procedure"></a> Transact-SQL과 함께 SQL Server Management Studio 사용  
  
#### 데이터베이스 마스터 키를 백업하려면  
  
1.  [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]에서 백업할 데이터베이스 마스터 키가 들어 있는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 연결합니다.  
  
2.  백업 미디어에 데이터베이스 마스터 키를 암호화하는 데 사용할 암호를 선택합니다. 이 암호의 복잡성을 확인해야 합니다.  
  
3.  백업 키의 복사본을 저장하기 위해 이동식 백업 미디어를 가져옵니다.  
  
4.  키의 백업을 만들 NTFS 디렉터리를 식별합니다. 다음 단계에서 지정하는 파일을 만들 위치인 이 디렉터리는 매우 제한적인 ACL(액세스 제한 목록)로 보호되어야 합니다.  
  
5.  **개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.  
  
6.  표준 도구 모음에서 **새 쿼리**를 클릭합니다.  
  
7.  다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.  
  
    ```  
    -- Creates a backup of the "AdventureWorks2012" master key. Because this master key is not encrypted by the service master key, a password must be specified when it is opened.  
    USE AdventureWorks2012;   
    GO  
    OPEN MASTER KEY DECRYPTION BY PASSWORD = 'sfj5300osdVdgwdfkli7';   
  
    BACKUP MASTER KEY TO FILE = 'c:\temp\exportedmasterkey'   
        ENCRYPTION BY PASSWORD = 'sd092735kjn$&adsg';   
    GO  
    ```  
  
    > [!NOTE]  
    >  키의 경로와 암호(있는 경우)는 위에 나타난 것과 다릅니다. 둘 다 서버 및 키 설정에 대해 고유한지 확인하세요.  
  
8.  파일을 백업 미디어에 복사하고 복사본을 확인합니다.  
  
9. 백업을 안전한 오프 사이트 위치에 저장합니다.  
  
 자세한 내용은 [OPEN MASTER KEY&#40;Transact-SQL&#41;](../../../t-sql/statements/open-master-key-transact-sql.md) 및 [BACKUP MASTER KEY&#40;Transact-SQL&#41;](../../../t-sql/statements/backup-master-key-transact-sql.md)를 참조하세요.  
  
  