---
title: "등록된 필터와 단어 분리기 보기 및 변경 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-search"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "전체 텍스트 검색 [SQL Server], 단어 분리기"
  - "전체 텍스트 검색 [SQL Server], 필터"
  - "필터 [전체 텍스트 검색]"
  - "단어 분리기 [전체 텍스트 검색]"
ms.assetid: f88c54df-b1aa-4701-807f-dc92c32363fd
caps.latest.revision: 22
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 22
---
# 등록된 필터와 단어 분리기 보기 및 변경
  시스템에 단어 분리기 또는 필터를 설치하거나 제거한 후 이러한 변경이 자동적으로 서버 인스턴스에 적용되지는 않습니다. 이 항목에서는 현재 등록되어 있는 단어 분리기 또는 필터를 보는 방법과 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 새로 설치한 단어 분리기 및 필터를 등록하는 방법에 대해 설명합니다.  
  
### 현재 등록된 단어 분리기의 언어 목록을 보려면  
  
1.  다음과 같이 [sys.fulltext_languages](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md) 카탈로그 뷰를 사용합니다.  
  
    ```  
    SELECT * FROM sys.fulltext_languages;   
    ```  
  
### 현재 등록된 필터의 목록을 보려면  
  
1.  다음과 같이 [sp_help_fulltext_system_components](../../relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql.md) 시스템 저장 프로시저를 사용합니다.  
  
    ```  
    EXEC sp_help_fulltext_system_components 'filter';    
    ```  
  
### 새로 설치한 단어 분리기 및 필터를 등록하려면  
  
1.  [sp_fulltext_service](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md) 시스템 저장 프로시저를 사용하여 다음과 같이 언어 목록을 업데이트합니다.  
  
    ```  
    exec sp_fulltext_service 'update_languages';   
    ```  
  
### 제거한 단어 분리기 및 필터를 등록 취소하려면  
  
1.  **sp_fulltext_service**를 사용하여 다음과 같이 언어 목록을 업데이트합니다.  
  
    ```  
    exec sp_fulltext_service 'update_languages'  
    ```  
  
2.  **sp_fulltext_service**를 사용하여 다음과 같이 필터 데몬 호스트 프로세스(fdhost.exe)를 다시 시작합니다.  
  
    ```  
    exec sp_fulltext_service 'restart_all_fdhosts';  
    ```  
  
### 새로 설치 시 기존 단어 분리기 또는 필터를 교체하려면  
  
1.  새로운 단어 분리기 또는 필터가 포함된 DLL 파일을 설치하려고 준비할 때 서버 인스턴스에 설치된 기존 DLL 파일과 다른 파일 이름을 사용합니다.  
  
2.  새 DLL 파일을 서버 인스턴스에 대한 표준 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DLL 파일이 포함된 디렉터리로 복사합니다. 기본 위치는  
  
     C:\Program Files\Microsoft SQL Server\MSSQL.*instance_name*\MSSQL\Binn  
  
    > [!IMPORTANT]  
    >  서명 및 검증을 거친 구성 요소만 로드하는 것이 좋습니다. 또한, 최소한의 권한을 가지고 FDHOST Launcher(MSSQLFDLauncher) 서비스를 실행하는 것이 좋습니다.  
  
3.  새 단어 분리기 또는 필터를 설치합니다.  
  
     **Microsoft Filter Pack IFilter를 설치 및 로드하려면**  
  
    -   [SQL Server에 Microsoft Filter Pack IFilter를 등록하는 방법](http://go.microsoft.com/fwlink/?LinkId=130439)  
  
4.  **sp_fulltext_service**를 사용하여 새로 설치된 단어 분리기 및 필터를 다음과 같이 서버 인스턴스에 로드합니다.  
  
    ```  
    EXEC sp_fulltext_service @action='load_os_resources', @value=1;  
    ```  
  
5.  **sp_fulltext_service**를 사용하여 다음과 같이 언어 목록을 업데이트합니다.  
  
    ```  
    EXEC sp_fulltext_service 'update_languages';  
    ```  
  
6.  **sp_fulltext_service**를 사용하여 다음과 같이 필터 데몬 호스트 프로세스(fdhost.exe)를 다시 시작합니다.  
  
    ```  
    EXEC sp_fulltext_service 'restart_all_fdhosts';   
    ```  
  
## 참고 항목  
 [전체 텍스트 필터 데몬 시작 관리자 서비스 계정 설정](../../relational-databases/search/set-the-service-account-for-the-full-text-filter-daemon-launcher.md)   
 [검색 필터 구성 및 관리](../../relational-databases/search/configure-and-manage-filters-for-search.md)   
 [검색을 위해 단어 분리기와 형태소 분석기 구성 및 관리](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)  
  
  