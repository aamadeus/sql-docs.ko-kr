---
title: "Visual Studio.NET에서에서 Visual C# SMO 프로젝트 만들기 | Microsoft Docs"
ms.custom: 
ms.date: 08/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: Visual C# [SMO]
ms.assetid: 1e7abb16-23a0-4a18-91ad-253261e6bf84
caps.latest.revision: "43"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 2fb8a8bd7527a14df4447fd4c7a49e92647b9e09
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="how-to-create-a-visual-c-smo-project-in-visual-studio-net"></a>Visual Studio.NET에서에서 Visual C# SMO 프로젝트 만들기 하는 방법
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]이 섹션에서는 간단한 SMO 콘솔 응용 프로그램을 작성 하는 방법에 설명 합니다.  
  
 이 예에서는 프로그램이 SMO 형식을 참조할 수 있도록 네임스페이스를 가져옵니다. 가져오기는 **에이전트** 네임 스페이스는 선택 사항입니다. 이 네임스페이스는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 사용하는 프로그램을 작성하는 경우에 필요합니다. **일반적인** 네임 스페이스의 인스턴스에 보안 연결을 설정 하는 데 필요한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]합니다. **SqlClient** 네임 스페이스는 SQL 예외 오류를 처리 하는 데 사용 됩니다.  
  
### <a name="creating-a-visual-c-smo-project-in-visual-studionet"></a>Visual Studio .NET에서 Visual C# SMO 프로젝트 만들기  
  
1. Visual Studio를 시작 합니다.
  
2. 에 **파일** 메뉴를 클릭 **새로** 차례로 **프로젝트**합니다.  **새 프로젝트** 대화 상자가 나타납니다.   
  
3. 에 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **설치 됨** 창으로 이동 **템플릿**\\**Visual C#**\\**Windows** 선택한 **콘솔 응용 프로그램**합니다.  
  
4. (선택 사항) 에 **이름** 텍스트 상자에 새 응용 프로그램의 이름을 입력 합니다.  

5. 클릭 **확인** 콘솔 응용 프로그램 템플릿을 로드 합니다.  

6. 지침에 따라 [SMO 설치](installing-smo.md) 프로젝트 참조를 프로젝트 패키지를 설치 합니다.
  
7. **보기** 메뉴에서 **코드**를 클릭합니다.
    
8. 네임 스페이스 문 앞에 코드에서 다음 명령을 입력 **를 사용 하 여** 문을 SMO 네임 스페이스의 형식을 한정 하려면:
  
    ```  
    using Microsoft.SqlServer.Management.Smo;  
    using Microsoft.SqlServer.Management.Common;  
    ```  
  
15. SMO의 Microsoft.SqlServer.Management.Smo 아래에는 Microsoft.SqlServer.Management.Smo.Agent와 같은 다양한 네임스페이스가 있습니다. 이러한 네임스페이스를 필요에 따라 추가합니다.  
  
16. 이제 SMO 코드를 추가할 수 있습니다.  
  
  