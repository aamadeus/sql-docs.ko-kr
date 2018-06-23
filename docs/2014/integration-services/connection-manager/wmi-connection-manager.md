---
title: WMI 연결 관리자 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- connections [Integration Services], WMI
- connection managers [Integration Services], WMI
- WMI connection manager [Integration Services]
ms.assetid: fbfa4ba7-3d0d-4d6b-94ad-50741a88d03d
caps.latest.revision: 39
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 199cea31baaee58c25b50a8ef0aefed15dfab387
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36186573"
---
# <a name="wmi-connection-manager"></a>WMI 연결 관리자
  WMI 연결 관리자를 사용하면 패키지에서 WMI(Windows Management Instrumentation)를 사용하여 엔터프라이즈 환경의 정보를 관리할 수 있습니다. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 에 포함되는 웹 서비스 태스크에서는 WMI 연결 관리자가 사용됩니다.  
  
 패키지에는 WMI 연결 관리자를 추가 하면 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 는 연결 관리자를 만들고 런타임에 WMI 연결으로 확인 되는 연결 관리자 속성을 설정 하 고, 연결 관리자를 추가 하는 `Connections` 컬렉션에는 패키지입니다. `ConnectionManagerType` 연결 관리자의 속성이로 설정 되어 `WMI`합니다.  
  
## <a name="configuration-of-the-wmi-connection-manager"></a>WMI 연결 관리자 구성  
 다음과 같은 방법으로 WMI 연결 관리자를 구성할 수 있습니다.  
  
-   서버의 이름을 지정합니다.  
  
-   서버에 네임스페이스를 지정합니다.  
  
-   서버에 연결하기 위한 인증 모드를 선택합니다.  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용은 [WMI 연결 관리자 편집기](../wmi-connection-manager-editor.md)를 참조하세요.  
  
 연결 관리자를 프로그래밍 방식으로 구성 하는 방법에 대 한 정보를 참조 하십시오. <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 및 [프로그래밍 방식으로 연결 추가](../building-packages-programmatically/adding-connections-programmatically.md)합니다.  
  
## <a name="see-also"></a>관련 항목  
 [웹 서비스 태스크](../control-flow/web-service-task.md)   
 [Integration Services &#40;SSIS&#41; 연결](integration-services-ssis-connections.md)  
  
  