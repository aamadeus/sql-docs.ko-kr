---
title: 보고서 찾기, 보기 및 관리(보고서 작성기 및 SSRS) | Microsoft Docs
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-builder
ms.topic: conceptual
ms.assetid: 5599300d-6bcd-4704-aba5-fa98e01c78a9
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 8e19127cd13ddb5e71ce245b4e0a832c63ecad76
ms.sourcegitcommit: c7febcaff4a51a899bc775a86e764ac60aab22eb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/30/2018
ms.locfileid: "52711014"
---
# <a name="finding-viewing-and-managing-reports-report-builder-and-ssrs-"></a>보고서 찾기, 보기 및 관리(보고서 작성기 및 SSRS)
  보고서 작성기에서는 보고서 서버 또는 SharePoint 사이트의 폴더를 탐색하여 보고서, 공유 데이터 원본, 모델 및 기타 관련 보고서 항목을 찾고 컴퓨터에서 로컬 보고서를 찾아볼 수 있습니다. 보고서를 쉽게 찾을 수 있도록 보고서 작성기에는 최근에 사용한 서버 및 사이트 목록이 유지되며 컴퓨터 파일 시스템의 바탕 화면, 내 문서 및 내 컴퓨터 폴더에 대한 직접 액세스 기능이 제공됩니다.  
  
 보고서 디자이너에서 컴퓨터를 검색하여 로컬 보고서를 찾을 수도 있습니다. 보고서 서버 또는 SharePoint 사이트에 보고서를 배포한 후 보고서 관리자를 사용하여 보고서 서버를 탐색하거나 SharePoint 사이트를 검색하여 보고서를 찾을 수 있습니다. 보고서 및 관련된 항목은 배포된 후 로컬로 사용할 수 있는 상태로 유지됩니다.  
  
> [!NOTE]  
>  보고서 작성기는 로컬 모드로 또는 보고서 서버에 연결하여 사용할 수 있습니다. 보고서 서버에 연결되어 있지 않은 경우 몇 가지 제한이 따릅니다.  
  
 보고서 작성기에서 보고서 서버 또는 SharePoint 사이트의 보고서를 찾으려면 보고서 서버 또는 SharePoint 사이트 URL을 제공해야 합니다. 보고서 작성기를 처음 설치할 때 사용할 URL을 지정할 수 있습니다. 보고서를 저장하거나 열 때 보고서 작성기는 이 서버 또는 사이트에 기본적으로 연결합니다.  
  
 보고서는 만들거나 업데이트할 때 보고서 작성기 및 보고서 디자이너에서 미리 볼 수 있으며, 게시한 후에 보고서 관리자를 사용하여 보고서 서버에서 보고 관리하거나 기본 제공 SharePoint 도구 및 기능을 사용해 Reporting Services에 통합된 SharePoint 사이트에서 보고 관리할 수 있습니다. 자세한 내용은 [보고서 작성기에서 보고서 미리 보기](../../reporting-services/report-builder/previewing-reports-in-report-builder.md) 및 [보고서 미리 보기](../../reporting-services/reports/previewing-reports.md)를 참조하세요.  
  
 보고서 작성기 및 보고서 디자이너에서 보고서를 미리 보거나 보고서 관리자 또는 SharePoint 사이트에서 보고서를 볼 때는 데이터가 새로 고쳐지며 보고서에서 사용하는 데이터 원본의 최신 데이터가 표시됩니다. 데이터를 새로 고치지 않고 보고서를 보려면 게시된 보고서의 캐시된 데이터 및 보고서 기록을 사용하면 됩니다. 보고서 작성기 및 보고서 디자이너에서 보고서를 미리 볼 때는 이러한 기능을 사용할 수 없습니다.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="FindingAndViewingReportsRB30"></a> 보고서 작성기에서 보고서 찾기 및 보기  
 작업할 보고서를 찾거나 보고서에 사용할 공유 데이터 원본, 이미지 또는 하위 보고서를 선택하려면 컴퓨터, 보고서 서버의 폴더 또는 Reporting Services와 통합된 SharePoint 사이트를 찾아봅니다.  
  
 보고서 서버의 보고서를 찾으려면 보고서 서버의 URL을 지정해야 하고 보고서 항목을 읽고 저장하려면 해당 폴더에 대한 적절한 권한이 있어야 합니다. 시스템 관리자에게 보고서 서버의 URL 및 적절한 권한을 요청하십시오.  
  
 보고서 작성기에서 보고서를 찾아 열고 나면 미리 보고 변경할 수 있습니다. 보고서를 미리 볼 때는 최신 데이터가 표시됩니다. 자세한 내용은 [Previewing Reports in Report Builder](../../reporting-services/report-builder/previewing-reports-in-report-builder.md)를 참조하세요.  
  
 보고서 작성기를 사용하면 다음 태스크를 수행할 수 있습니다.  
  
-   **보고서 찾기** 보고서를 찾을 때 보고서 작성기에 맞게 설계된 친숙한 Microsoft Office 스타일의 **파일 열기** 대화 상자를 사용할 수 있습니다. 내 보고서, 사이트 및 서버, 바탕 화면, 내 문서, 내 컴퓨터를 비롯한 보고서 서버나 파일 시스템의 폴더를 찾아볼 수 있습니다. 사이트 및 서버에는 최근에 사용한 서버 목록이 있습니다.  
  
-   **공유 데이터 원본 찾기** 공유 데이터 원본을 찾을 때 최근에 사용한 목록에서 데이터 원본을 선택하거나 보고서와 동일한 보고서 서버에 있는 다른 폴더를 찾아볼 수 있습니다.  
  
-   **보고서 보기** 보고서를 만들거나 업데이트할 때 보고서 작성기에서 보고서를 미리 볼 수 있습니다. 보고서 작성기가 보고서 서버에 연결되어 있으면 보고서 서버가 보고서를 로드하여 처리하고, 그렇지 않으면 보고서가 로컬로 처리됩니다. 보고서 작성기의 보고서 뷰어가 렌더링된 보고서를 표시합니다.  
  
 
##  <a name="ViewingAndManagingReportServer"></a> 보고서 서버에서 보고서 보기 및 관리  
 보고서 관리자를 사용하여 보고서 서버의 보고서를 보고 관리합니다. 서버의 폴더에서 보고서를 찾아 실행하여 브라우저에 표시한 다음 관리 태스크를 수행합니다.  
  
 보고서 관리자를 사용하면 다음 관리 태스크를 수행할 수 있습니다.  
  
-   보고서, 공유 데이터 원본 및 기타 보고서 항목의 속성을 보고 업데이트합니다.  
  
-   보고서를 업로드하고 보고서용으로 새 공유 데이터 원본을 만듭니다.  
  
-   보고서를 지정된 시간 및 간격에 실행하는 일정을 만듭니다.  
  
-   보고서 구독을 작성, 변경 또는 삭제합니다.  
  
-   보고서 기록을 만들고 보고서 기록에 보관할 보고서 스냅숏 수를 지정합니다.  
  
-   서버에 새 폴더를 만들어 보고서를 원하는 방식으로 구성합니다.  
  
 이러한 태스크 중 일부는 보고서 서버 관리자가 수행합니다. 보고서 서버에서 수행된 태스크에 대한 자세한 내용은 [Reporting Services 보고서 서버&#40;기본 모드&#41;](../../reporting-services/report-server/reporting-services-report-server-native-mode.md)를 참조하세요.  
  
 보고서 관리자에는 보통 폴더, 보고서, 데이터 원본, 보고서 모델과 내 보고서 폴더가 포함됩니다. 내 보고서는 소유한 보고서를 저장하고 작업하는 데 사용할 수 있는 개인 작업 영역입니다. 다른 보고서 서버 폴더는 공용 폴더이며 일반적으로 사용자가 폴더 내용을 추가하거나 수정하려면 고급 사용 권한이 있어야 합니다. 내 보고서 내에 폴더를 만들어 보고서를 더 자세하게 구성할 수 있습니다.  
  
 보고서 관리자는 Reporting Services HTML 뷰어에 보고서를 표시합니다. HTML 뷰어는 HTML 형식의 보고서를 보는 데 필요한 프레임워크를 제공하며 보고서 도구 모음, 매개 변수 섹션, 자격 증명 섹션 및 문서 구조를 포함합니다. 보고서 도구 모음은 페이지 탐색, 확대/축소, 새로 고침, 검색, 내보내기, 인쇄 및 데이터 피드 기능을 제공합니다. 보고서 도구 모음은 URL을 통해 보고서에 액세스할 때 보고서 상단의 브라우저 창에도 나타납니다. 인쇄 기능은 선택 사항이며 관리자가 설정해야 합니다. 인쇄 기능을 사용할 수 있는 경우 프린터 아이콘이 보고서 도구 모음에 표시됩니다. 다음 그림에서는 보고서 관리자 창 및 보고서 도구 모음 기능 클로즈업 화면의 보고서 도구 모음을 보여 줍니다.  
  
 ![보고서 관리자의 보고서 도구 모음](../../reporting-services/report-builder/media/hs-reportserver-blowout.gif "보고서 관리자의 보고서 도구 모음")  
보고서 관리자 창  
  
 ![보고서 도구 모음](../../reporting-services/media/ssrs-htmlviewer-toolbar.png "보고서 도구 모음")  
보고서 도구 모음  
  
 보고서를 실행한 후 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel 또는 PDF와 같은 다른 형식으로 내보낼 수 있습니다. 또한 쉼표로 구분된 값(CSV) 렌더링 확장 프로그램 등의 데이터 렌더링 확장 프로그램을 사용해 보고서를 내보낸 다음 CSV 데이터 파일을 다른 응용 프로그램의 입력으로 사용할 수도 있습니다. 보고서 내보내기에 대한 자세한 내용은 [보고서 내보내기&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-builder/export-reports-report-builder-and-ssrs.md) 및 [다른 파일 형식으로 보고서 내보내기&#40;보고서 작성기 및 SSRS&#41;](https://msdn.microsoft.com/library/b577568b-ecbd-44c3-be88-31dab6fc38a2)를 참조하세요.  
  
 보고서를 선택하여 실행하는 가장 쉬운 방법은 보고서 관리자를 연 다음 원하는 보고서를 검색하거나 직접 찾아가는 것입니다. 보고서를 여는 방법에 대한 단계별 지침은 [보고서 열기 및 닫기&#40;보고서 관리자&#41;](../../reporting-services/reports/open-and-close-a-report-report-manager.md)를 참조하세요.  
  
 보고서를 실행한 후 새로 고치면 새 데이터가 표시됩니다.  
  
### <a name="refreshing-reports"></a>보고서 새로 고침  
 보고서 데이터는 빈번하게 변경되므로 최신 데이터를 보려면 보고서를 새로 고쳐야 할 수 있습니다. 다음과 같은 3가지 방식으로 보고서를 새로 고칠 수 있습니다.  
  
|옵션|결과|  
|------------|------------|  
|브라우저 창의**새로 고침** 단추|세션 캐시에 저장된 보고서를 표시합니다. 세션 캐시는 사용자가 보고서를 열 때 생성됩니다. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 는 보고서가 열려 있는 동안 일관된 보기 상태를 유지하기 위해 브라우저 세션을 사용합니다.|  
|![보고서 도구 모음의 브라우저 새로 고침 단추](../../reporting-services/media/htmlviewer-refresh.GIF "보고서 도구 모음의 브라우저 새로 고침 단추")|보고서 도구 모음에서 **새로 고침** 단추를 클릭하면 보고서 서버에서 쿼리가 다시 실행되며 보고서가 요청 시 실행되는 경우 보고서 데이터가 업데이트됩니다. 보고서가 캐시되었거나 스냅숏일 경우 **새고 고침** 단추를 클릭하면 보고서 서버 데이터베이스에 저장된 보고서가 표시됩니다.|  
|Ctrl+F5 키 조합|보고서 도구 모음의 **새로 고침** 단추를 클릭할 때와 동일한 결과를 나타냅니다.|  
  
  
##  <a name="ViewingAndManagingSharePointSite"></a> SharePoint 사이트에서 보고서 서버 항목 보기 및 관리  
 시스템 관리자가 SharePoint 통합 모드에서 실행되도록 보고서 서버를 구성하면 SharePoint 사이트에서 보고서 및 기타 보고서 서버 항목을 보고 관리할 수 있습니다.  
  
 SharePoint 사이트에는 데이터 원본 속성, 보고서 기록, 보고서 처리 옵션, 일정, 구독 및 보고서 매개 변수를 설정하고 공유 일정을 만들 수 있는 페이지가 포함되어 있습니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 다른 도구에서와 같은 방식으로 SharePoint 사이트에서 보고서 서버 항목을 관리할 수 있습니다.  
  
 응용 프로그램 페이지에 액세스하려면 보고서의 드롭다운 메뉴에서 항목과 관련된 동작을 선택하거나 이전에 SharePoint 라이브러리에 추가했던 기타 보고서 서버 항목을 선택합니다. 항목 및 사용자 권한에 따라 보고서 작성기에서 보고서를 만들고 모델을 생성하며 모델 항목 보안을 설정할 수도 있습니다.  
  
 Reporting Services 및 SharePoint 기술에 대한 자세한 내용은 msdn.microsoft.com의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [온라인 설명서](https://go.microsoft.com/fwlink/?LinkId=154888)에서 [보고서 서버의 구성 및 관리&#40;Reporting Services SharePoint 모드&#41;](../../reporting-services/report-server-sharepoint/configuration-and-administration-of-a-report-server.md)를 참조하세요.  
  
### <a name="finding-report-server-items-on-a-sharepoint-site"></a>SharePoint 사이트에서 보고서 서버 항목 찾기  
 속성을 설정하려면 먼저 항목을 찾아야 합니다. 보고서 서버 항목은 항상 라이브러리나 라이브러리 내의 폴더에 저장됩니다.  
  
 SharePoint 사이트에 액세스하면 찾아보기 페이지와 라이브러리 도구 탭이 표시됩니다. 찾아보기 페이지에는 라이브러리와 선택한 라이브러리의 콘텐츠가 나열됩니다. 보고서, 보고서 모델 및 라이브러리의 기타 항목을 보고 폴더를 탐색하고 사이트를 검색하여 항목을 찾을 수 있습니다.  
  
 보고서 서버 항목을 SharePoint 사이트의 다른 항목과 구분하기 위해 아이콘을 사용하여 항목을 시각적으로 식별하거나 유형 위에 마우스 커서를 놓아 파일 확장명을 읽을 수 있습니다. 다음 이미지에서는 **보고서** 라이브러리의 폴더, 보고서 모델 및 보고서 정의를 보여 줍니다.  
  
 ![보고서 서버 항목이 있는 SharePoint 라이브러리](../../reporting-services/report-builder/media/rs-sharepointlibrary.gif "보고서 서버 항목이 있는 SharePoint 라이브러리")  
  
### <a name="viewing-reports"></a>보고서 보기  
 SharePoint 라이브러리에 업로드한 보고서 정의 파일(.rdl)은 Reporting Services 추가 기능을 통해 설치되는 보고서 뷰어 웹 파트를 통해 렌더링됩니다. .rdl 파일 연결은 추가 기능을 설치할 때 자동으로 정의됩니다. 보고서를 선택하면 보고서가 자동으로 웹 파트에서 열립니다. 보고서가 열리면 웹 파트에 포함되어 있는 보고서 도구 모음을 사용하여 페이지를 탐색하고 보고서에 대해 검색, 확대 및 인쇄 작업을 수행할 수 있습니다. 도구 모음에는 보고서를 Atom 데이터 피드로 내보내기 위한 데이터 피드로 내보내기 옵션과 보고서를 인쇄 및 구독하고 PDF, Word, Excel 등의 다른 형식으로 내보내기 위한 옵션이 있는 **동작** 메뉴가 있습니다. **동작** 메뉴에서 보고서 작성기를 통해 보고서를 열 수도 있습니다. 다음 이미지에서는 보고서와 **동작** 메뉴에 있는 내보내기 옵션의 옵션을 보여 줍니다.  
  
 ![rs_SharePointRunReport](../../reporting-services/report-builder/media/rs-sharepointrunreport.gif "rs_SharePointRunReport")  
  
### <a name="managing-items-through-actions"></a>동작을 통한 항목 관리  
 관리 태스크는 각 항목에 대한 드롭다운 메뉴의 동작을 통해 지원됩니다. 사용 권한에 따라 각 항목에는 SharePoint 라이브러리에 저장되어 있는 항목에 대한 표준 공통 동작이 있습니다. 이러한 동작의 예로는**속성 보기** 및 **속성 편집** 을 들 수 있습니다. 사용자 지정 동작은 항목별 관리 기능을 제공합니다. 다음 이미지에서는 보고서 정의에 대한 동작을 보여 줍니다. 보고서 정의에 대한 사용자 지정 동작의 예로는 **구독 관리** 와 **처리 옵션 관리**를 들 수 있습니다.  
  
 ![보고서 서버 항목에 대한 메뉴 명령](../../reporting-services/report-builder/media/rs-ecbforrsitems.gif "보고서 서버 항목에 대한 메뉴 명령")  
  
  
##  <a name="DeskTop"></a> 데스크톱 응용 프로그램에서 보고서 보기  
 브라우저 대신 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel과 같은 데스크톱 응용 프로그램을 보고서 뷰어로 사용할 수 있습니다. 이렇게 하려면 데스크톱 응용 프로그램 형식과 공유 폴더 대상을 지정하는 구독을 정의합니다. 그러면 보고서 서버에서 보고서를 응용 프로그램 파일로 생성하고 파일 이름 확장명을 추가한 후 하드 디스크에 파일로 저장합니다. 그런 다음 브라우저 대신 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel 또는 다른 응용 프로그램을 사용하여 보고서를 볼 수 있습니다.  
  
  
##  <a name="AboutUserSessions"></a> 사용자 세션 정보  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 는 브라우저 세션을 사용하여 보고서를 보는 동안 일관성을 유지합니다. 세션은 인증된 사용자가 아니라 브라우저 연결을 기반으로 합니다. 사용자가 새 브라우저 창에서 보고서를 열 때마다 세션이 새로 만들어집니다. 브라우저 세션이 구성되면 나중에 보고서가 보고서 서버에서 수정되더라도 세션이 시작될 때 열었던 보고서 버전으로 계속 작업하게 됩니다. 예를 들어 보고서를 오후 11시에 열면 보고서 작성자가 같은 보고서를 오후 11시 1분에 다시 게시하더라도 세션에는 오후 11시에 열었던 버전이 유지됩니다.  
  
 브라우저의 **새로 고침** 단추를 사용하여 같은 세션 내에서 보고서를 새로 고치면 원래 세션 버전의 보고서가 표시됩니다. 보고서 도구 모음의 **새로 고침** 단추를 사용하여 요청 시 실행 보고서를 새로 고치면 보고서가 다시 실행되고 새 데이터가 있는 경우 해당 데이터가 표시됩니다.  
  
 세션 정보는 보고서 서버 임시 데이터베이스에 저장됩니다. 보고서 서버는 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 세션 관리 기능을 사용하지 않습니다. 서버를 다시 시작하거나 데이터베이스 복구 작업을 수행하면 세션 상태가 복원되지 않습니다. 세션 관리에 대한 자세한 내용은 [실행 상태 식별](../../reporting-services/report-server-web-service-net-framework-soap-headers/identifying-execution-state.md)을 참조하세요.  
  
 
##  <a name="InThisSection"></a> 섹션 내용  
 다음 항목에서는 보고서 보기 및 관리에 대한 추가 정보를 제공합니다.  
  
  [보고서 찾기, 보기 및 관리](../../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)
  
 [브라우저를 사용하여 보고서 찾기 및 보기&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-builder/finding-and-viewing-reports-with-a-browser-report-builder-and-ssrs.md)  
 URL을 사용하여 보고서를 찾고 보는 방법에 대해 설명합니다.  
  
 [보고서 작성기에서 보고서 미리 보기](../../reporting-services/report-builder/previewing-reports-in-report-builder.md)  
 보고서를 만들거나 업데이트하는 동안 보고서를 미리 보는 방법에 설명합니다.  
  
## <a name="see-also"></a>참고 항목  
 [보고서 저장&#40;보고서 작성기&#41;](../../reporting-services/report-builder/saving-reports-report-builder.md)   
 [SQL Server의 보고서 작성기](../../reporting-services/report-builder/report-builder-in-sql-server-2016.md)   
 [보고서 작성기 설치 및 제거](https://msdn.microsoft.com/library/2c9a5814-17bf-4947-8fb3-6269e7caa416)  
  
  
