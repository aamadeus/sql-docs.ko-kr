---
title: Reporting Services SharePoint 모드 인증 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Upgrade SharePoint Mode [Reporting Services]
- SharePoint integration
- SharePoint Mode
ms.assetid: 2c19794a-dd55-4fe5-b901-6dd93e9f6beb
caps.latest.revision: 8
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 42a05beda30c678f97740a536e6b50530010bff1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36180985"
---
# <a name="reporting-services-sharepoint-mode-authentication"></a>Reporting Services SharePoint 모드 인증
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 마법사의 **Reporting Services SharePoint 모드 인증** 페이지를 사용하여 현재 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 설치에서 사용되는 서비스 계정의 자격 증명을 지정할 수 있습니다. 자격 증명은 새 SharePoint 응용 프로그램 풀을 만드는 데 사용됩니다. 또한 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 서비스 응용 프로그램이 새로 만들어집니다. 서비스 응용 프로그램 이름에는 이전 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 인스턴스 이름이 포함됩니다.  
  
## <a name="options"></a>변수  
  
-   **SSRS 응용 프로그램 풀 계정 이름:** 옵션은 읽기 전용입니다. 값은 업그레이드할 기존 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 설치의 현재 값으로 자동으로 채워집니다.  
  
-   응용 프로그램 풀 계정에 암호가 필요 하지 않은 경우 **SSRS 응용 프로그램 풀 계정 암호:** 옵션이 비활성화 됩니다. “NT Authority\NetworkSerivce”를 예로 들 수 있습니다. 응용 프로그램 풀 계정에 암호가 필요하지 않은 경우 올바른 암호를 입력할 때까지 업그레이드를 계속할 수 없습니다.  
  
 자세한 내용은 참조 [Upgrade and Migrate Reporting Services](http://go.microsoft.com/fwlink/?LinkID=245628) (http://go.microsoft.com/fwlink/?LinkID=245628)합니다.  
  
## <a name="see-also"></a>관련 항목  
 [Reporting Services 업그레이드 및 마이그레이션](http://go.microsoft.com/fwlink/?LinkID=245628)  
  
  