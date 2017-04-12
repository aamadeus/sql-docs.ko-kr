---
title: "Master Data Services 설치 및 구성 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/13/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
ms.assetid: f6cd850f-b01b-491f-972c-f966b9fe4190
caps.latest.revision: 44
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 37
---
# Master Data Services 설치 및 구성
  이 문서에서는 Windows Server 2012 R2 컴퓨터에 [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]를 설치하고, MDS 데이터베이스 및 웹 사이트를 설정하고, 샘플 모델 및 데이터를 배포하는 방법을 설명합니다. MDS([!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)])를 사용하면 조직에서 신뢰할 수 있는 버전의 데이터를 관리할 수 있습니다.   
   
[!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]에서 데이터를 구성하는 방법에 대한 개요는 [MDS(Master Data Services) 개요](../master-data-services/master-data-services-overview-mds.md) 를 참조하세요.     
  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]의 새로운 기능에 대한 자세한 내용은 [MDS&#40;Master Data Services&#41;의 새로운 기능](../master-data-services/what-s-new-in-master-data-services-mds.md)을 참조하세요.  
 
[!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]를 알아보는 데 유용한 동영상 및 기타 학습 리소스의 링크는 [Master Data Services에 대해 알아보기](../master-data-services/learn-sql-server-master-data-services.md)를 참조하세요. 
  
> **다운로드**  
>-   [!INCLUDE[ssSQL15](../includes/sssql15-md.md)]를 다운로드하려면  **[평가 센터](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**로 이동하세요.  
>-   Azure 계정이 있으세요?  계정이 있는 경우 **[여기](https://azure.microsoft.com/en-us/marketplace/partners/microsoft/sqlserver2016rtmenterprisewindowsserver2012r2/?wt.mc_id=sqL16_vm)** 로 이동하여 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  이 이미 설치된 가상 컴퓨터를 실행해 보세요.  
 
> **MDS 웹 사이트를 만들 수 없는 경우**
>>이 Microsoft 지원 문서에서 이 문제를 해결하는 방법에 대한 지침을 확인하세요.
[SQL Server 2016에서 낮은 권한 계정을 통해 MDS 웹 사이트를 만들 수 없는 경우](https://aka.ms/mdssupport) 
  
## <a name="installing-master-data-services-and-iis-roles-and-features"></a>Master Data Services 설치, IIS 역할 및 기능  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 설치 프로그램의 설치 마법사 또는 명령 프롬프트를 사용하여 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]를 설치합니다.  
  
 **[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 설치 프로그램을 사용하여 Windows Server 2012 R2 컴퓨터에 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]를 설치하려면**  
  
1.  Setup.exe를 두 번 클릭하고 설치 마법사의 단계를 따릅니다.  
  
2.  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 기능 선택 **페이지의** 공유 기능 **에서**를 선택합니다.  
  
     [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)], 어셈블리, Windows PowerShell 스냅인, 웹 응용 프로그램과 서비스의 폴더 및 파일이 설치됩니다.  
  
     ![mds_SQLServer2016Setup_FeatureSelection](../master-data-services/media/mds-sqlserver2016setup-featureselection.png "mds_SQLServer2016Setup_FeatureSelection")  
  
3.  설치 마법사를 완료합니다.  
  
4.  [!INCLUDE[winblue_server_2](../includes/winblue-server-2-md.md)]에서 **데스크톱** 의 작업 표시줄에 있는 **서버 관리자**아이콘을 클릭합니다.  
  
     ![Icon for the Server Manager in Windows Server 2012 taskbar](../master-data-services/media/mds-windowsservertaskbar-servermanagericon.png "Icon for the Server Manager in Windows Server 2012 taskbar")  
  
5.  **서버 관리자**에서 **관리** 메뉴에 있는 **역할 및 기능 추가** 를 클릭합니다.  
  
     ![In Server Manage, the Add Roles and Features menu command](../master-data-services/media/mds-servermanagerdashboard-addrolesfeaturesmenu.png "In Server Manage, the Add Roles and Features menu command")  
  
6.  **역할 및 기능 추가 마법사** 의 **설치 유형**페이지에서 기본값(**역할 기반 또는 기능 기반 설치**)을 적용하고 **다음**을 클릭합니다.  
  
7.  **서버 풀에서 서버 선택**을 클릭한 다음 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]를 설치한 서버를 클릭합니다.  
  
     ![Server Selection page on the Add Roles and Features Wizard](../master-data-services/media/mds-servermanagerdashboard-addrolesandfeatureswizard-serverselection.png "Server Selection page on the Add Roles and Features Wizard")  
  
8.  **역할** 상자에서 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 의 [!INCLUDE[winblue_server_2](../includes/winblue-server-2-md.md)]에 필요한 역할 및 역할 서비스를 클릭하고 **다음**을 클릭합니다. 다음 그림은 선택한 필수 역할 및 역할 서비스를 보여 줍니다.  
  
    > [!WARNING]  
    >  WebDAV 게시 역할 서비스를 설치하지 마세요. WebDAV 게시는 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]와 호환되지 않습니다.  
  
    > [!IMPORTANT]  
    >  **동적 콘텐츠 압축** 은 기본적으로 사용하도록 설정됩니다. 이로 인해 CPU 사용량이 증가하지만 xml 응답 크기가 크게 줄어들고 네트워크 I/O가 저장됩니다.  자세한 내용은 **MDS&#40;Master Data Services&#41;의 새로운 기능** in [What's New in Master Data Services &#40;MDS&#41;](../master-data-services/what-s-new-in-master-data-services-mds.md)를 참조하세요.  
  
    |역할 및 역할 서비스|역할 및 역할 서비스|  
    |-----------------------------|-----------------------------|  
    |![Common HTTP Features](../master-data-services/media/mds-servermanagerdashboard-commonhttpfeaturesroles.png "Common HTTP Features")|![Health Diagnostics Roles](../master-data-services/media/mds-servermanagerdashboard-healthdiagnosticsroles.png "Health Diagnostics Roles")|  
    |![Performance Roles](../master-data-services/media/mds-servermanagerdashboard-performanceroles.png "Performance Roles")|![Security Roles](../master-data-services/media/mds-servermanagerdashboard-securityroles.png "Security Roles")|  
    |![WebServer Application Development Roles](../master-data-services/media/mds-servermanagerdashboard-webserverapplicationdevelopmentroles.png "WebServer Application Development Roles")|![Management Tools](../master-data-services/media/mds-servermanagerdashboard-managementtoolsroles.png "Management Tools")|  
  
     다른 운영 체제에서 필요한 역할 및 역할 서비스 목록은 [웹 응용 프로그램 요구 사항&#40;Master Data Services&#41;](../master-data-services/install-windows/web-application-requirements-master-data-services.md)을 참조하세요.  
  
9. **기능** 상자에서 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 의 [!INCLUDE[winblue_server_2](../includes/winblue-server-2-md.md)]에 필요한 기능을 클릭하고 **다음**을 클릭합니다. 다음 그림은 선택한 필수 기능을 보여 줍니다.  
  
    |기능|기능|  
    |--------------|--------------|  
    |![Net Framework Features](../master-data-services/media/mds-servermanagerdashboard-netframeworkfeatures.png "Net Framework Features")|![Windows Process Features](../master-data-services/media/mds-servermanagerdashboard-windowsprocessfeatures.png "Windows Process Features")|  
  
     다른 운영 체제에서 필요한 기능 목록은 [웹 응용 프로그램 요구 사항&#40;Master Data Services&#41;](../master-data-services/install-windows/web-application-requirements-master-data-services.md)을 참조하세요.  
  
 설치 프로그램을 사용하여 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]를 설치하는 방법에 대한 자세한 내용은 [설치 마법사에서 SQL Server 2016 설치&#40;설치 프로그램&#41;](../database-engine/install-windows/install-sql-server-2016-from-the-installation-wizard-setup.md)를 참조하세요.  
  
 명령 프롬프트를 사용하여 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]를 설치하는 방법에 대한 자세한 내용은 [명령 프롬프트에서 SQL Server 2016 설치](../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)를 참조하세요. 명령 프롬프트를 사용하는 경우 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 는 기능 매개 변수로 사용할 수 있습니다.  
  
 사전 설치 작업에 대한 추가 정보 링크가 있는 간단한 설명은 [Master Data Services 설치](../master-data-services/install-windows/install-master-data-services.md)를 참조하세요.  
  
##  <a name="a-namesetupweba-setting-up-the-database-and-website"></a><a name="SetUpWeb"></a> 데이터베이스 및 웹 사이트 설정  
 **[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]를 사용하여 데이터베이스 및 웹 사이트를 설정하려면**  
  
1.  [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]를 시작하고 왼쪽 창에서 **데이터베이스 구성** 을 클릭합니다.  
  
2.  **데이터베이스 만들기**를 클릭한 다음 **데이터베이스 만들기 마법사** 에서 **다음**을 클릭합니다.  
  
3.  **데이터베이스 서버** 페이지에서 **인증 유형** 을 선택하고 **연결 테스트** 를 클릭하여 선택한 인증 유형에 대한 자격 증명으로 데이터베이스에 연결할 수 있는지 확인합니다.  
  
    > [!NOTE]  
    >  **현재 사용자 – 통합 보안** 을 인증 유형으로 선택할 경우 **사용자 이름** 상자는 읽기 전용이며 컴퓨터에 로그온된 Windows 사용자 계정의 이름이 표시됩니다.  
  
     ![The Database server page in the Create Database Wizard](../master-data-services/media/mds-configurationmanager-createdatabasewizard-serverpage.png "The Database server page in the Create Database Wizard")  
  
4.  **데이터베이스 이름** 필드에 이름을 입력합니다. 필요에 따라 Windows 데이터 정렬을 선택하고 **대/소문자 구분**등의 사용 가능한 옵션을 하나 이상 지정하려면 **SQL Server 기본 데이터 정렬** 확인란 선택을 취소합니다.  
  
     ![The Database page in the Create Database Wizard](../master-data-services/media/mds-configurationmanager-createdatabasewizard-databasepage.png "The Database page in the Create Database Wizard")  
  
     Windows 데이터 정렬에 대한 자세한 내용은 [Windows 데이터 정렬 이름(Transact-SQL)](https://msdn.microsoft.com/library/ms188046.aspx)을 참조하세요.  
  
5.  **사용자 이름** 필드에서 Master Data Services의 기본 슈퍼 사용자로 설정할 사용자의 Windows 계정을 지정합니다. 슈퍼 사용자는 모든 기능 영역에 액세스할 수 있으며 모든 모델을 추가, 삭제 및 업데이트할 수 있습니다.  
  
     ![The Administrator Account page in the Create Database Wizard.](../master-data-services/media/mds-configurationmanager-createdatabasewizard-adminpage.png "The Administrator Account page in the Create Database Wizard.")  
  
6.  **다음**을 클릭하여 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스에 대한 설정 요약을 본 후에 다시 **다음**을 클릭하여 데이터베이스를 만듭니다.  
  
     **데이터베이스 만들기 마법사**의 설정에 대한 자세한 내용은 [데이터베이스 만들기 마법사&#40;Master Data Services 구성 관리자&#41;](../master-data-services/create-database-wizard-master-data-services-configuration-manager.md)를 참조하세요.  
  
7.  [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]데이터베이스 구성 페이지에서 데이터베이스 선택을 클릭합니다.  
  
8.  **연결**을 클릭하고 6단계에서 만든 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스를 선택합니다.  
  
     ![Connect to Database dialog box for the Database Configuration page](../master-data-services/media/mds-configurationmanager-selectdatabasebutton-connecttodatabasedialog.png "Connect to Database dialog box for the Database Configuration page")  
  
     데이터베이스 설정을 마쳤습니다. 이제 **데이터베이스 구성** 페이지에 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에 대해 연결된 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]인스턴스, 만든 데이터베이스 및 현재 데이터베이스 버전이 표시됩니다.  
  
     ![Database Configuration page in the Configuration Manager shows a completed database setup.](../master-data-services/media/mds-configurationmanager-databaseconfig-completed.png "Database Configuration page in the Configuration Manager shows a completed database setup.")  
  
9. [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]의 왼쪽 창에서 **웹 구성** 을 클릭합니다.  
  
10. **웹 사이트** 목록 상자에서 **기본 웹 사이트**를 클릭한 다음 **만들기** 를 클릭하여 웹 응용 프로그램을 만듭니다.  
  
    > [!NOTE]  
    >  **기본 웹 사이트**를 선택할 경우 웹 응용 프로그램을 만들어야 합니다. 목록 상자에서 **새 웹 사이트 만들기** 를 선택하면 응용 프로그램이 자동으로 만들어집니다.  
  
     ![Web Configuration page in the Configuration Manager](../master-data-services/media/mds-configurationmanager-webconfig.png "Web Configuration page in the Configuration Manager")  
  
11. **응용 프로그램 풀** 섹션에서 다음 중 하나를 수행합니다.  
  
    -   데이터베이스 **관리자 계정**에 대해 5단계에서 입력한 것과 동일한 사용자 이름을 입력하고 암호를 입력한 다음 **확인**을 클릭합니다.  
  
         **또는**  
  
    -   다른 사용자 이름을 입력하고 암호를 입력한 다음 확인을 클릭합니다.  
  
         데이터베이스와 웹 응용 프로그램을 만들 때 동일한 계정을 사용해야 하는 것은 아닙니다.  
  
     ![Create Web Application dialog box, Web Configuration page](../master-data-services/media/mds-configurationmanager-webconfig-createwebapplication.png "Create Web Application dialog box, Web Configuration page")  
  
     **웹 응용 프로그램 만들기** 대화 상자에 대한 자세한 내용은 [웹 응용 프로그램 만들기 대화 상자&#40;Master Data Services 구성 관리자&#41;](../master-data-services/create-web-application-dialog-box-master-data-services-configuration-manager.md)를 참조하세요.  
  
12. **웹 구성** 페이지의 **웹 응용 프로그램** 상자에서 만든 응용 프로그램을 클릭한 다음 **데이터베이스에 응용 프로그램 연결** 섹션에서 **선택**을 클릭합니다.  
  
13. **연결**을 클릭하고 웹 응용 프로그램에 연결할 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스를 선택한 다음 **확인**을 클릭합니다.  
  
     웹 사이트 설정을 마쳤습니다. 이제 **웹 구성** 페이지에 선택한 웹 사이트, 만든 웹 응용 프로그램, 응용 프로그램과 연결된 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스가 표시됩니다.  
  
     ![The completed Web site configuration](../master-data-services/media/mds-configurationmanager-webconfig-completed.png "The completed Web site configuration")  
  
     웹 구성 페이지의 설정에 대한 자세한 내용은 [웹 구성 페이지&#40;Master Data Services 구성 관리자&#41;](../master-data-services/web-configuration-page-master-data-services-configuration-manager.md)를 참조하세요.  
  
 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]를 사용하여 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스와 연결된 웹 응용 프로그램 및 서비스에 대한 다른 설정을 지정할 수도 있습니다. 예를 들어 데이터를 로드하는 빈도나 유효성 검사 메일을 전송하는 빈도를 지정할 수 있습니다. 자세한 내용은 [시스템 설정&#40;Master Data Services&#41;](../master-data-services/system-settings-master-data-services.md)을 참조하세요.  
  
##  <a name="a-namedeploysamplea-deploying-sample-models-and-data"></a><a name="deploySample"></a> 샘플 모델 및 데이터 배포  
 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에는 다음 세 가지 샘플 모델 패키지가 포함되어 있습니다.   이러한 샘플 모델은 데이터를 포함합니다. **샘플 모델 패키지의 기본 위치는 %programfiles%\Microsoft SQL Server\130\Master Data Services\Samples\Packages입니다.**
  
-   chartofaccounts_en.pkg  
  
-   customer_en.pkg  
  
-   product_en.pkg  
  
 MDSModelDeploy 도구를 사용하여 패키지를 배포합니다. MDSModelDeploy 도구의 기본 위치는 *드라이브*\Program Files\Microsoft SQL Server\ 130\Master Data Services\Configuration입니다.  
  
 이 도구를 실행하기 위한 필수 조건에 대한 자세한 내용은 [MDSModelDeploy를 사용하여 모델 배포 패키지 배포](../master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)를 참조하세요.  
  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]의 새로운 기능을 지원하기 위한 데이터 업데이트에 대한 자세한 내용은 [샘플: 모델 배포 패키지&#40;Master Data Services&#41;](../Topic/Samples:%20Model%20Deployment%20Packages%20\(Master%20Data%20Services\).md)를 참조하세요.  
  
 **샘플 모델을 배포하려면**  
  
1.  샘플 모델 패키지를 *드라이브*\Program Files\Microsoft SQL Server\130\Master Data Services\Configuration에 복사합니다.  
  
2.  관리자: 명령 프롬프트를 열고 다음 명령을 실행하여 MDSModelDeploy.exe로 이동합니다.  
  
    ```  
    cd c:\Program Files\Microsoft SQL Server\130\Master Data Services\Configuration  
    ```  
  
3.  다음 명령을 각각 실행하여 각 샘플 모델을 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 에 배포합니다.  
  
    > [!IMPORTANT]  
    >  아래 예제에서는 `MDS1` 서비스 값을 지정합니다. **웹 사이트를 설정할 때** 기본 웹 사이트 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 를 선택한 경우 이 값을 사용합니다.  [데이터베이스 및 웹 사이트 설정](#SetUpWeb) 섹션을 참조하세요.  
    >   
    >  새 웹 사이트를 만들거나 다른 기존 웹 사이트를 선택한 경우 먼저 다음 명령을 실행하여 올바른 서비스 값을 확인합니다.  
    >   
    >  `MDSModelDeploy listservices`  
    >   
    >  반환되는 값 목록의 첫 번째 서비스 값은 모델을 배포할 때 지정합니다.  
  
     **chartofaccounts_en.pkg 샘플 모델을 배포하려면**  
  
    ```  
    MDSModelDeploy deploynew -package chartofaccounts_en.pkg -model ChartofAccounts -service MDS1  
    ```  
  
     **customer_en.pkg 샘플 모델을 배포하려면**  
  
    ```  
    MDSModelDeploy deploynew -package customer_en.pkg -model Customer -service MDS1  
    ```  
  
     **product_en.pkg 샘플 모델을 배포하려면**  
  
    ```  
    MDSModelDeploy deploynew -package product_en.pkg -model Product -service MDS1  
  
    ```  
  
     모델이 성공적으로 배포되면 **MDSModelDeploy 작업이 완료되었습니다.** 라는 메시지가 표시됩니다.  
  
     다음 그림은 product_en.pkg 샘플 모델을 배포하기 위한 명령을 보여 줍니다.  
  
     ![Command line for deploying the Product sample model](../master-data-services/media/mds-commandprompt-deployingsamplemodel-product.png "Command line for deploying the Product sample model")  
  
4.  샘플 모델을 보려면 다음을 수행합니다.  
  
    1.  설정한 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 웹 사이트로 이동합니다. [데이터베이스 및 웹 사이트 설정](#SetUpWeb) 섹션을 참조하세요.  
  
         웹 사이트 주소는 http://*서버 이름*/*웹 응용 프로그램*/입니다.  
  
    2.  **모델** 목록 상자에서 모델을 선택하고 **탐색기**를 클릭합니다.  
  
         ![MDS Web site, home page.](../master-data-services/media/mds-mdswebsite-homepage-selectsamplemodel.png "MDS Web site, home page.")  
  
## <a name="next-step"></a>다음 단계  
 데이터에 대한 새 모델 및 엔터티를 만듭니다. [모델 만들기&#40;Master Data Services&#41;](../master-data-services/create-a-model-master-data-services.md) 및 [엔터티 만들기&#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md)를 참조하세요.  
  
 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 모델 및 엔터티를 사용하여 데이터 구조를 작성하는 방법에 대한 개요는 [Master Data Services 개요&#40;MDS&#41;](../master-data-services/master-data-services-overview-mds.md)를 참조하세요.  
  
## <a name="did-this-article-help-you-were-listening"></a>이 문서가 도움이 되었나요? 여러분의 의견을 환영합니다.  
 어떤 정보를 찾고 계세요? 정보를 찾으셨나요? 여러분의 의견은 문서의 내용을 개선하는 데 많은 도움이 됩니다. [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Get%20Started%20with%20Master%20Data%20Services)에 의견을 제출해 주세요.  
  
## <a name="see-also"></a>참고 항목  
 [Master Data Services 데이터베이스](../master-data-services/master-data-services-database.md)   
 [마스터 데이터 관리자 웹 응용 프로그램](../master-data-services/master-data-manager-web-application.md)   
 [데이터베이스 구성 페이지&#40;Master Data Services 구성 관리자&#41;](../master-data-services/database-configuration-page-master-data-services-configuration-manager.md)   
 [MDS&#40;Master Data Services&#41;의 새로운 기능](../master-data-services/what-s-new-in-master-data-services-mds.md)  
  
  