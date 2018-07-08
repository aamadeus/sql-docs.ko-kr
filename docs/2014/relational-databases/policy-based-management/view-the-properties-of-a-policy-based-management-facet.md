---
title: 정책 기반 관리 패싯의 속성 보기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Policy-Based Management, view facet properties
ms.assetid: 022a244c-c2e7-4467-b9a2-c7a27859be22
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1f4ecdd5b25cf790bb81f4cbabd024870c6a670e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36078580"
---
# <a name="view-the-properties-of-a-policy-based-management-facet"></a>정책 기반 관리 패싯의 속성 보기
  이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 를 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 정책 기반 관리 패싯의 속성을 보는 방법에 대해 설명합니다.  
  
 **항목 내용**  
  
-   **시작하기 전 주의 사항:**  
  
     [보안](#Security)  
  
-   **다음을 사용하여 패싯의 속성을 보려면:**  
  
     다른 도구는 [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> 시작하기 전에  
  
###  <a name="Security"></a> 보안  
  
####  <a name="Permissions"></a> Permissions  
 msdb 데이터베이스에서 PolicyAdministratorRole 역할의 멤버 자격이 필요합니다.  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio 사용  
  
#### <a name="to-view-the-properties-of-a-facet"></a>패싯의 속성을 보려면  
  
1.  **개체 탐색기**에서 더하기 기호를 클릭하여 보려는 속성이 지정된 패싯이 들어 있는 서버를 확장합니다.  
  
2.  더하기 기호를 클릭하여 **관리** 폴더를 확장합니다.  
  
3.  더하기 기호를 클릭하여 **정책 관리**를 확장합니다.  
  
4.  더하기 기호를 클릭하여 **패싯** 폴더를 확장합니다.  
  
5.  보려는 속성이 지정된 패싯을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다. **패싯 속성 –***facet_name* 대화 상자에서 사용 가능한 옵션에 대한 자세한 내용은 [패싯 속성 대화 상자, 일반 페이지](../../integration-services/general-page-of-integration-services-designers-options.md), [패싯 속성 대화 상자, 종속 정책 페이지](facet-properties-dialog-box-dependent-policies-page.md) 및 [패싯 속성 대화 상자, 종속 조건 페이지](facet-properties-dialog-box-dependent-conditions-page.md)를 참조하세요.  
  
6.  완료되면 **닫기**를 클릭합니다.  
  
  