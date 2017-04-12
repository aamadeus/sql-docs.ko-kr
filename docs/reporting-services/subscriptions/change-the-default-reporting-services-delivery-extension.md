---
title: "기본 Reporting Services 배달 확장 프로그램 변경 | Microsoft Docs"
ms.custom: ""
ms.date: "03/20/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "보고서 관리자 [Reporting Services], 기본 배달 확장 프로그램"
ms.assetid: 5f6fee72-01bf-4f6c-85d2-7863c46c136b
caps.latest.revision: 19
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 18
---
# 기본 Reporting Services 배달 확장 프로그램 변경
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 설정을 수정하여 구독 정의 페이지의 **배달 방법** 목록에 표시될 배달 확장 프로그램을 결정할 수 있습니다. 예를 들어, 구성을 수정하여 사용자가 새 구독을 만들었을 때 전자 메일 배달 대신 기본적으로 파일 공유 전달을 선택할 수 있습니다. 또한 배달 확장 프로그램이 사용자 인터페이스에 나열되는 순서를 변경할 수 있습니다.  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 기본 모드 | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 모드  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 는 메일 및 Windows 파일 공유 배달을 포함하는 확장 프로그램입니다. 사용자 지정 배달을 지원하기 위해 사용자 지정 확장 프로그램이나 타사 확장 프로그램을 배포한 경우에는 보고서 서버에 배달 확장 프로그램이 더 있을 수 있습니다. 배달 확장 프로그램의 가용성은 보고서 서버에 배포되었는지 여부에 따라 다릅니다.  
  
## 기본 모드 보고서 서버 기본 구성  
 보고서 관리자의 **배달 방법** 목록에 표시되는 배달 확장 프로그램의 순서는 **RSReportServer.config** 파일에 배달 확장 프로그램 항목이 표시된 순서를 기반으로 합니다. 예를 들어, 다음 이미지에서는 목록에 전자 메일이 가장 먼저 표시되도록 기본 선택되어 있습니다.  
  
 ![default list of delivery extensions](../../reporting-services/subscriptions/media/ssrs-default-delivery.png "default list of delivery extensions")  
  
 다음은 기본 전달 확장 프로그램과 보고서 관리자에서의 표시 순서를 제어하는 **RSReportServer.config** 의 기본 섹션입니다. 전자 메일이 파일에 첫 번째로 표시되며 이것이 기본값입니다.  
  
```  
<DeliveryUI>  
     <Extension Name="Report Server Email" Type="Microsoft.ReportingServices.EmailDeliveryProvider.EmailDeliveryProviderControl,ReportingServicesEmailDeliveryProvider">  
          <DefaultDeliveryExtension>True</DefaultDeliveryExtension>  
               <Configuration>  
               <RSEmailDPConfiguration>  
                    <DefaultRenderingExtension>MHTML</DefaultRenderingExtension>  
               </RSEmailDPConfiguration>  
               </Configuration>  
     </Extension>  
     <Extension Name="Report Server FileShare" Type="Microsoft.ReportingServices.FileShareDeliveryProvider.FileShareUIControl,ReportingServicesFileShareDeliveryProvider"/>  
</DeliveryUI>  
```  
  
#### 보고서 관리자에서 파일 공유 배달을 기본 배달 확장 프로그램으로 구성  
  
1.  이 절차의 단계는 UI에서 파일 공유 배달이 첫 번째 옵션으로 표시되고 기본 선택 항목으로 나타나도록 구성을 수정합니다.  
  
      텍스트 편집기에서 RSReportServer.config 파일을 엽니다.  구성 파일에 대한 자세한 내용은 [RsReportServer.config Configuration File](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)을 참조하세요. 구성 변경 후에는 UI가 다음 이미지와 유사해 보입니다.  
  
     ![modified list of delivery extensions](../../reporting-services/subscriptions/media/ssrs-modified-delivery.png "modified list of delivery extensions")  
  
2.  DeliveryUI 섹션이 다음 예시와 유사하게 보이도록 수정하고 주요 변경 사항을 확인합니다.  
  
    1.  FileShare 확장 프로그램이 이메일 확장 프로그램 앞에 있습니다. 이렇게 하면 보고서 관리자에 확장 프로그램이 나열되는 순서가 변경됩니다.  
  
    2.  파일 공유 확장 프로그램에는 DefaultExtension 태그( `<DefaultDeliveryExtension>True</DefaultDeliveryExtension>` )가 포함되며 해당 확장 프로그램 종료 태그( `</Extension>`)가 추가됩니다.  
  
    3.  전자 메일 확장 프로그램은 이제 기본값으로 구성되지 않았습니다. `<DefaultDeliveryExtension>False</DefaultDeliveryExtension>`  
  
    ```  
    <DeliveryUI>  
         <Extension Name="Report Server FileShare" Type="Microsoft.ReportingServices.FileShareDeliveryProvider.FileShareUIControl,ReportingServicesFileShareDeliveryProvider">  
              <DefaultDeliveryExtension>True</DefaultDeliveryExtension>  
         </Extension>  
         <Extension Name="Report Server Email" Type="Microsoft.ReportingServices.EmailDeliveryProvider.EmailDeliveryProviderControl,ReportingServicesEmailDeliveryProvider">  
         <DefaultDeliveryExtension>False</DefaultDeliveryExtension>  
         <Configuration>  
              <RSEmailDPConfiguration>  
                   <DefaultRenderingExtension>MHTML</DefaultRenderingExtension>  
              </RSEmailDPConfiguration>  
         </Configuration>  
         </Extension>  
    </DeliveryUI>  
    ```  
  
3.  구성 파일을 저장합니다.  
  
4.  몇 분 안에 보고서 서버가 구성 파일을 다시 로드하고 새 설정이 적용됩니다. 보고서 서버 서비스를 다시 시작하여 구성 파일을 강제로 로드할 수 있습니다.  
  
     구성을 읽을 때 다음과 같은 이벤트가 Windows 이벤트 로그에 기록됩니다.  
  
     **이벤트 ID:** 109  
  
     **원본:** 보고서 서버 Windows 서비스(인스턴스 이름)  
  
     RSReportServer.config 파일 수정  
  
## SharePoint 모드 보고서 서버  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 모드는 RsrReportServer.config 파일이 아니라 SharePoint 서비스 응용 프로그램 데이터베이스에 확장 프로그램 정보를 저장합니다. SharePoint 모드에서 PowerShell을 사용하 여 배달 확장 프로그램 구성을 수정합니다.  
  
#### 기본 배달 확장 프로그램 구성  
  
1.  **SharePoint 관리 셸**을 엽니다.  
  
2.  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 응용 프로그램의 이름을 알고 있는 경우에 이 단계를 건너뛸 수 있습니다. SharePoint 팜에 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 응용 프로그램을 나열하려면 다음 PowerShell을 사용합니다.  
  
    ```  
    get-sprsserviceapplication | format-list *  
    ```  
  
3.  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 응용 프로그램 “ssrsapp”의 현재 기본 배달 확장 프로그램을 확인하려면 다음 PowerShell을 실행합니다.  
  
    ```  
    $app=get-sprsserviceapplication | where {$_.name -like "ssrsapp*"};Get-SPRSExtension -identity $app | where{$_.ServerDirectivesXML -like "<DefaultDelivery*"} | format-list *  
  
    ```  
  
4.  
  
## 관련 항목:  
 [RsReportServer.config 구성 파일](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
 [RsReportServer.config 구성 파일](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
 [Reporting Services의 파일 공유 배달](../../reporting-services/subscriptions/file-share-delivery-in-reporting-services.md)   
 [Reporting Services의 전자 메일 배달](../../reporting-services/subscriptions/e-mail-delivery-in-reporting-services.md)   
 [ 전자 메일 배달을 위한 보고서 서버 구성(SSRS 구성 관리자) ](http://msdn.microsoft.com/ko-kr/b838f970-d11a-4239-b164-8d11f4581d83)  
  
  