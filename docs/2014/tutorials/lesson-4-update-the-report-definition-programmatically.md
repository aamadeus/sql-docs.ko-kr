---
title: '4 단원: 보고서 정의 프로그래밍 방식으로 업데이트 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f0a1d46-6d6d-4f67-b51e-06dbbbffacf9
caps.latest.revision: 20
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: bb51cfc7677f60d729efeb1e878c4d4709943860
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36185099"
---
# <a name="lesson-4-update-the-report-definition-programmatically"></a>4단원: 프로그래밍 방식으로 보고서 정의 업데이트
  이제 보고서 서버에서 보고서 정의가 로드되었고 보고서 필드를 사용하여 해당 정의를 참조했으므로 보고서 정의를 업데이트해야 합니다. 이 예에서는 보고서의 `Description` 속성을 업데이트합니다.  
  
### <a name="to-update-the-report-definition"></a>보고서 정의를 업데이트하려면  
  
1.  Program.cs 파일에서 UpdateReportDefinition() 메서드에 대 한 코드를 바꿉니다 (의 경우 Module1.vb [!INCLUDE[vbprvb](../includes/vbprvb-md.md)])를 다음 코드로:  
  
    ```csharp  
    private void UpdateReportDefinition()  
    {  
        System.Console.WriteLine("Updating Report Definition");  
  
        // Create a list of the Items Choices for the Report. The   
        // ItemsChoiceType118 enum represents all the properties  
        // available in the report and the ItemsElementName   
        // represents the properties that exist in the current   
        // instance of the report.  
        List<ItemsChoiceType118> _reportItems =   
            new List<ItemsChoiceType118>(_report.ItemsElementName);  
  
        // Locate the index for the Description property  
        int index = _reportItems.IndexOf(  
            ItemsChoiceType118.Description);  
  
        // The Description item is of type StringLocIDType, so   
        // cast the item type first and then assign new value.  
        System.Console.WriteLine("- Old Description: " +   
            ((StringLocIDType)_report.Items[index]).Value );  
  
        // Update the Description for the Report  
        ((StringLocIDType)_report.Items[index]).Value =   
            "New Report Description";  
  
        System.Console.WriteLine("- New Description: " +   
            ((StringLocIDType)_report.Items[index]).Value );  
    }  
    ```  
  
    ```vb  
    Private Sub UpdateReportDefinition()  
  
        System.Console.WriteLine("Updating Report Definition")  
  
        'Create a list of the Items Choices for the Report. The   
        'ItemsChoiceType118 enum represents all the properties  
        'available in the report and the ItemsElementName   
        'represents the properties that exist in the current   
        'instance of the report.  
        Dim reportItems As List(Of ItemsChoiceType118) = _  
            New List(Of ItemsChoiceType118)(m_report.ItemsElementName)  
  
        'Locate the index for the Description property  
        Dim index As Integer = _  
            reportItems.IndexOf(ItemsChoiceType118.Description)  
  
        'The Description item is of type StringLocIDType, so   
        'cast the item type first and then assign new value.  
        System.Console.WriteLine("- Old Description: " & _  
            DirectCast(m_report.Items(index), StringLocIDType).Value)  
  
        'Update the Description for the Report  
        DirectCast(m_report.Items(index), StringLocIDType).Value = _  
            "New Report Description"  
  
        System.Console.WriteLine("- New Description: " & _  
            DirectCast(m_report.Items(index), StringLocIDType).Value)  
  
    End Sub  
    ```  
  
## <a name="next-lesson"></a>다음 단원  
 다음 단원에서는 업데이트된 보고서 정의를 다시 보고서 서버에 저장합니다. 참조 [5 단원: 보고서 서버에 보고서 정의 게시](../../2014/tutorials/lesson-5-publish-the-report-definition-to-the-report-server.md)합니다.  
  
## <a name="see-also"></a>관련 항목  
 [RDL 스키마에서 생성 한 클래스를 사용 하 여 보고서 업데이트 &#40;SSRS 자습서&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md)  
  
  