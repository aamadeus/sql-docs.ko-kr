---
title: "폴더 및 파일 사용 권한(Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "보안 [Master Data Services], 파일 및 폴더"
  - "폴더 [Master Data Services]"
  - "파일 [Master Data Services]"
ms.assetid: 6402d81d-7349-47b1-95ca-99b0c0f4f373
caps.latest.revision: 10
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 10
---
# 폴더 및 파일 사용 권한(Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]를 설치할 경우 폴더와 파일이 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 공유 기능에 대해 지정한 설치 경로의 파일 시스템에 설치됩니다. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 공유 기능에 기본 설치 경로를 사용하는 경우 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]의 설치 경로는 *드라이브*:\Program Files\Microsoft SQL Server\130\Master Data Services입니다. 공유 기능 설치 경로를 변경할 수 있지만 부모 폴더에서 상속된 사용 권한과 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에 대해 명시적으로 설정된 사용 권한을 알고 있어야 합니다.  
  
## 상속된 사용 권한  
 **Microsoft SQL Server** 폴더, **Master Data Services** 폴더 및 대부분의 하위 폴더와 파일은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 설치 프로그램에서 지정된 부모 폴더에서 사용 권한을 상속합니다. 기본 설치 위치를 선택할 경우 사용 권한을 상속하는 부모 폴더는 *드라이브*:\Program Files입니다. 다음 표에서는 **Program Files**의 기본 사용 권한에 대해 설명합니다.  
  
> [!NOTE]  
>  **Program Files**의 기본 사용 권한을 수정하거나 다른 설치 위치를 선택할 경우 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 폴더 및 파일은 적절하게 부모 폴더에서 사용 권한을 상속하고 사용 권한은 다음 표에 설명된 것과 다를 수 있습니다.  
  
###### Program Files 기본 사용 권한  
  
|그룹 또는 계정 이름|사용 권한|  
|---------------------------|-----------------|  
|CREATOR OWNER|특별 사용 권한|  
|SYSTEM|특별 사용 권한|  
|관리자|특별 사용 권한|  
|사용자|읽기 & 실행, 폴더 내용 보기, 읽기|  
|TrustedInstaller|폴더 내용 보기, 특별 사용 권한|  
  
## 명시적 사용 권한  
 **MDSTempDir** 폴더 및 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web.config 파일(**WebApplication** 폴더에 있음)은 사용 권한을 상속하지 않습니다. 이러한 폴더와 파일은 선택한 설치 경로에 상관없이 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]를 설치할 때 명시적으로 설정된 사용 권한을 가집니다. 이러한 사용 권한은 수정하지 마십시오.  
  
###### MDSTempDir 사용 권한  
  
|그룹 또는 계정 이름|Permissions|  
|---------------------------|-----------------|  
|SYSTEM|수정, 읽기 & 실행, 폴더 내용 보기, 읽기, 쓰기|  
|관리자|수정, 읽기 & 실행, 폴더 내용 보기, 읽기, 쓰기|  
|MDS_ServiceAccounts|수정, 읽기 & 실행, 폴더 내용 보기, 읽기, 쓰기|  
  
###### Web.config 사용 권한  
  
|그룹 또는 계정 이름|Permissions|  
|---------------------------|-----------------|  
|SYSTEM|모든 권한, 수정, 읽기 & 실행, 읽기, 쓰기|  
|관리자|모든 권한, 수정, 읽기 & 실행, 읽기, 쓰기|  
|MDS_ServiceAccounts|읽기 & 실행, 읽기|  
  
 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web.config 파일의 내용에 대한 자세한 내용은 [웹 구성 참조&#40;Master Data Services&#41;](../master-data-services/web-configuration-reference-master-data-services.md)를 참조하세요.  
  
## 참고 항목  
 [MDS(Master Data Services) 설치](../master-data-services/install-windows/install-master-data-services.md)  
  
  