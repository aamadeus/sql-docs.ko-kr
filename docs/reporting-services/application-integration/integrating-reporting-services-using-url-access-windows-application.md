---
title: "Windows 응용 프로그램에서 URL 액세스 사용 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Windows applications [Reporting Services]
- Web Browser controls [Reporting Services]
- Windows Forms [Reporting Services]
- browser controls [Reporting Services]
- URL access [Reporting Services], Windows applications
ms.assetid: a4b222e5-0cbd-409c-92c4-046a674db8ac
caps.latest.revision: 48
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 6174bfd45317faf9b6c8c7131dd1c5026d3a4d51
ms.contentlocale: ko-kr
ms.lasthandoff: 06/22/2017

---
# <a name="integrating-reporting-services-using-url-access---windows-application"></a>URL 액세스-Windows 응용 프로그램을 사용 하 여 Reporting Services 통합
  보고서 서버에 대한 URL 액세스는 웹 환경에 최적화되어 있지만, URL 액세스를 사용하여 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 보고서를 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 응용 프로그램에 포함시킬 수도 있습니다. 하지만 Windows Forms와 관련된 URL 액세스의 경우에는 웹 브라우저 기술을 사용해야 합니다. URL 액세스 및 Windows Forms에서 다음과 같은 통합 시나리오를 사용할 수 있습니다.  
  
-   웹 브라우저를 프로그래밍 방식으로 시작하여 Windows Form 응용 프로그램에서 보고서를 표시합니다.  
  
-   Windows Form에서 <xref:System.Windows.Forms.WebBrowser> 컨트롤을 사용하여 보고서를 표시합니다.  
  
## <a name="starting-internet-explorer-from-a-windows-form"></a>Windows Form에서 Internet Explorer 시작  
 <xref:System.Diagnostics.Process> 클래스를 사용하여 컴퓨터에서 실행 중인 프로세스에 액세스할 수 있습니다. <xref:System.Diagnostics.Process> 클래스는는 유용한 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 시작, 중지, 제어 및 응용 프로그램을 모니터링 하기 위한 구문입니다. 보고서 서버 데이터베이스에 특정 보고서를 보려면 시작할 수 있습니다는 **IExplore** 프로세스를 보고서에는 URL에 전달 합니다. 다음 코드 예제를 사용하면 사용자가 Windows Form에서 단추를 클릭할 때 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer를 시작하고 특정 보고서 URL을 전달할 수 있습니다.  
  
```vb  
Private Sub viewReportButton_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles viewReportButton.Click  
   ' Build the URL access string based on values supplied by a user  
   Dim url As String = serverUrlTextBox.Text + "?" & reportPathTextBox.Text & _  
   "&rs:Command=Render" & "&rs:Format=HTML4.0"  
  
   ' If the user does not select the toolbar check box,  
   ' turn the toolbar off in the HTML Viewer  
   If toolbarCheckBox.Checked = False Then  
      url += "&rc:Toolbar=False"  
   End If  
   ' load report in the Web browser  
   Try  
      System.Diagnostics.Process.Start("IExplore", url)  
   Catch  
      MessageBox.Show("The system could not start the specified report using Internet Explorer.", _  
      "An error has occurred", MessageBoxButtons.OK, MessageBoxIcon.Error)  
   End Try  
End Sub 'viewReportButton_Click  
```  
  
```csharp  
// Sample click event for a Button control on a Windows Form  
private void viewReportButton_Click(object sender, System.EventArgs e)  
{  
   // Build the URL access string based on values supplied by a user  
   string url = serverUrlTextBox.Text + "?" + reportPathTextBox.Text +  
      "&rs:Command=Render" + "&rs:Format=HTML4.0";  
  
   // If the user does not check the toolbar check box,  
   // turn the toolbar off in the HTML Viewer  
   if (toolbarCheckBox.Checked == false)  
      url += "&rc:Toolbar=False";  
  
   // load report in the Web browser  
   try  
   {  
      System.Diagnostics.Process.Start("IExplore", url);  
   }  
  
   catch (Exception)  
   {  
      MessageBox.Show(  
         "The system could not open the specified report using Internet Explorer.",   
         "An error has occurred", MessageBoxButtons.OK, MessageBoxIcon.Error);  
   }  
}  
```  
  
## <a name="embedding-a-browser-control-on-a-windows-form"></a>Windows Form에 브라우저 컨트롤 포함  
 보고서를 외부 웹 브라우저에서 보고 싶지 않으면 <xref:System.Windows.Forms.WebBrowser> 컨트롤을 사용하여 웹 브라우저를 Windows Form의 일부로 완벽하게 포함할 수 있습니다.  
  
###### <a name="to-add-the-webbrowser-control-to-your-windows-form"></a>WebBrowser 컨트롤을 Windows Form에 추가하려면  
  
1.  새 Windows 응용 프로그램에서 만든 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] 또는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]합니다.  
  
2.  찾을 <xref:System.Windows.Forms.WebBrowser> 컨트롤에 **도구 상자** 대화 상자.  
  
     경우는 **도구 상자** 은 표시 되지 않는 액세스할 수를 클릭 하 여는 **보기** 메뉴 항목을 선택 하면 **도구 상자**합니다.  
  
3.  끌어서는 <xref:System.Windows.Forms.WebBrowser>Windows Form의 디자인 화면으로 제어 합니다.  
  
     <xref:System.Windows.Forms.WebBrowser>webBrowser1 라는 컨트롤은 폼에 추가  
  
 지시는 <xref:System.Windows.Forms.WebBrowser> 컨트롤을 호출 하 여 URL 해당 **탐색** 메서드. 다음 예에서 볼 수 있는 것처럼 런타임에 특정 URL 액세스 문자열을 <xref:System.Windows.Forms.WebBrowser> 컨트롤에 할당할 수 있습니다.  
  
```vb  
Dim url As String = "http://localhost/reportserver?/" & _  
                    "AdventureWorks2012 Sample Reports/" & _  
                    "Company Sales&rs:Command=Render"  
WebBrowser1.Navigate(url)  
```  
  
```csharp  
string url = "http://localhost/reportserver?/" +  
             "AdventureWorks2012 Sample Reports/" +  
             "Company Sales&rs:Command=Render";  
webBrowser1.Navigate(url);  
```  
  
## <a name="see-also"></a>참고 항목  
 [응용 프로그램에 Reporting Services 통합](../../reporting-services/application-integration/integrating-reporting-services-into-applications.md)   
 [URL 액세스를 사용 하 여 Reporting Services 통합](../../reporting-services/application-integration/integrating-reporting-services-using-url-access.md)   
 [SOAP를 사용 하 여 Reporting Services 통합](../../reporting-services/application-integration/integrating-reporting-services-using-soap.md)   
 [ReportViewer 컨트롤을 사용 하 여 Reporting Services 통합](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls.md)   
 [URL 액세스 &#40; Ssrs&#41;](../../reporting-services/url-access-ssrs.md)  
  
  