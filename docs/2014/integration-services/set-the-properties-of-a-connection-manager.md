---
title: 연결 관리자의 속성 설정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- connection managers [Integration Services], modifying
- modifying connection managers
ms.assetid: 54793114-2198-4d80-8091-e241d5a5d13c
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0148cca6701db9f28ed6dd7abccb1a1f00269510
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48111863"
---
# <a name="set-the-properties-of-a-connection-manager"></a>연결 관리자의 속성 설정
  **속성** 창을 사용하여 모든 연결 관리자를 구성할 수 있습니다.  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]에서 여러 유형의 연결 관리자를 수정하기 위한 사용자 지정 대화 상자도 제공합니다. 대화 상자는 연결 관리자 유형에 따라 다른 옵션들을 포함합니다.  
  
### <a name="to-modify-a-connection-manager-using-the-properties-window"></a>속성 창을 사용하여 연결 관리자를 수정하려면  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.  
  
2.  솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.  
  
3.  SSIS 디자이너에서 **제어 흐름** 탭, **데이터 흐름** 탭 또는 **이벤트 처리기** 탭을 클릭하여 **연결 관리자** 영역을 표시합니다.  
  
4.  연결 관리자를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.  
  
5.  **속성** 창에서 속성 값을 편집합니다. **속성** 창은 연결 관리자의 표준 편집기에서 구성할 수 없는 일부 속성에 대한 액세스를 제공합니다.  
  
6.  **확인**을 클릭합니다.  
  
7.  업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.  
  
### <a name="to-modify-a-connection-manager-using-a-connection-manager-dialog-box"></a>연결 관리자 대화 상자를 사용하여 연결 관리자를 수정하려면  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.  
  
2.  솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.  
  
3.  [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에서 **제어 흐름** 탭, **데이터 흐름** 탭 또는 **이벤트 처리기** 탭을 클릭하여 **연결 관리자** 영역을 표시합니다.  
  
4.  **연결 관리자** 영역에서 연결 관리자를 두 번 클릭하여 **연결 관리자** 대화 상자를 엽니다. 특정 연결 관리자 유형에 대한 설명과 각 유형에 사용할 수 있는 옵션에 대한 자세한 내용은 다음 표를 참조하십시오.  
  
    |ODBC 대상 편집기|변수|  
    |------------------------|-------------|  
    |[ADO 연결 관리자](connection-manager/ado-connection-manager.md)|[OLE DB 연결 관리자 구성](configure-ole-db-connection-manager.md)|  
    |[ADO.NET 연결 관리자](connection-manager/ado-net-connection-manager.md)|[ADO.NET 연결 관리자 구성](configure-ado-net-connection-manager.md)|  
    |[Analysis Services 연결 관리자](connection-manager/analysis-services-connection-manager.md)|[Analysis Services 연결 관리자 추가 대화 상자 UI 참조](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)|  
    |[Excel 연결 관리자](connection-manager/excel-connection-manager.md)|[Excel 연결 관리자 편집기](../../2014/integration-services/excel-connection-manager-editor.md)|  
    |[파일 연결 관리자](connection-manager/file-connection-manager.md)|[파일 연결 관리자 편집기](../../2014/integration-services/file-connection-manager-editor.md)|  
    |[다중 파일 연결 관리자](connection-manager/multiple-files-connection-manager.md)|[파일 연결 관리자 추가 대화 상자 UI 참조](connection-manager/add-file-connection-manager-dialog-box-ui-reference.md)|  
    |[플랫 파일 연결 관리자](connection-manager/flat-file-connection-manager.md)|[플랫 파일 연결 관리자 편집기&#40;일반 페이지&#41;](general-page-of-integration-services-designers-options.md)<br /><br /> [플랫 파일 연결 관리자 편집기&#40;열 페이지&#41;](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md)<br /><br /> [플랫 파일 연결 관리자 편집기&#40;고급 페이지&#41;](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md)<br /><br /> [플랫 파일 연결 관리자 편집기&#40;미리 보기 페이지&#41;](../../2014/integration-services/flat-file-connection-manager-editor-preview-page.md)|  
    |[다중 플랫 파일 연결 관리자](connection-manager/multiple-flat-files-connection-manager.md)|[다중 플랫 파일 연결 관리자 편집기 &#40;일반 페이지&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-general-page.md)<br /><br /> [다중 플랫 파일 연결 관리자 편집기 &#40;열 페이지&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-columns-page.md)<br /><br /> [다중 플랫 파일 연결 관리자 편집기 &#40;고급 페이지&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-advanced-page.md)<br /><br /> [다중 플랫 파일 연결 관리자 편집기 &#40;페이지를 미리 보기&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-preview-page.md)|  
    |[FTP 연결 관리자](connection-manager/ftp-connection-manager.md)|[FTP 연결 관리자 편집기](../../2014/integration-services/ftp-connection-manager-editor.md)|  
    |[HTTP 연결 관리자](connection-manager/http-connection-manager.md)|[HTTP 연결 관리자 편집기 &#40;Server 페이지&#41;](../../2014/integration-services/http-connection-manager-editor-server-page.md)<br /><br /> [HTTP 연결 관리자 편집기 &#40;프록시 페이지&#41;](../../2014/integration-services/http-connection-manager-editor-proxy-page.md)|  
    |[MSMQ 연결 관리자](connection-manager/msmq-connection-manager.md)|[MSMQ 연결 관리자 편집기](../../2014/integration-services/msmq-connection-manager-editor.md)|  
    |[ODBC 연결 관리자](connection-manager/odbc-connection-manager.md)|[ODBC 연결 관리자 UI 참조](../../2014/integration-services/odbc-connection-manager-ui-reference.md)|  
    |[OLE DB 연결 관리자](connection-manager/ole-db-connection-manager.md)|[OLE DB 연결 관리자 구성](configure-ole-db-connection-manager.md)|  
    |[SMO 연결 관리자](connection-manager/smo-connection-manager.md)|[SMO 연결 관리자 편집기](../../2014/integration-services/smo-connection-manager-editor.md)|  
    |[SMTP 연결 관리자](connection-manager/smtp-connection-manager.md)|[SMTP 연결 관리자 편집기](../../2014/integration-services/smtp-connection-manager-editor.md)|  
    |[SQL Server Compact Edition 연결 관리자](connection-manager/sql-server-compact-edition-connection-manager.md)|[SQL Server Compact Edition 연결 관리자 편집기 &#40;연결 페이지&#41;](../../2014/integration-services/sql-server-compact-edition-connection-manager-editor-connection-page.md)<br /><br /> [SQL Server Compact Edition 연결 관리자 편집기 &#40;모든 페이지&#41;](../../2014/integration-services/sql-server-compact-edition-connection-manager-editor-all-page.md)|  
    |[WMI 연결 관리자](connection-manager/wmi-connection-manager.md)|[WMI 연결 관리자 편집기](../../2014/integration-services/wmi-connection-manager-editor.md)|  
  
5.  업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.  
  
## <a name="see-also"></a>관련 항목  
 [Integration Services&#40;SSIS&#41; 연결](connection-manager/integration-services-ssis-connections.md)   
 [패키지에서 연결 관리자 추가, 삭제 또는 공유](../../2014/integration-services/add-delete-or-share-a-connection-manager-in-a-package.md)  
  
  
