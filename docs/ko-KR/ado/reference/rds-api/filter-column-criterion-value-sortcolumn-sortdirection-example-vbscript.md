---
title: Rds. 설정 DataControl 서버와 HTML 테이블 (VBScript)에 바인딩 | Microsoft Docs
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- FilterColumn property [ADO], VBScript example
- FilterCriterion property [ADO], VBScript example
- SortDirection property [RDS], VBScript example
- Reset method [ADO], VBScript example
- SortColumn property [RDS], VBScript example
- FilterValue property [ADO], VBScript example
ms.assetid: 8a74802f-34d6-4676-bf94-07df5f8bff66
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c983513f3c1851b3d22e38ea06856b13be117335
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="filtercolumn-filtercriterion-filtervalue-sortcolumn-and-sortdirection-properties-and-reset-method-example-vbscript"></a>FilterColumn, FilterCriterion, FilterValue, SortColumn, 및 SortDirection 속성 및 Reset 메서드 예제 (VBScript)
> [!IMPORTANT]
>  Windows 8 및 Windows Server 2012 부터는 RDS 서버 구성 요소가 더 이상에 포함 Windows 운영 체제 (Windows 8 참조 및 [Windows Server 2012 호환성 설명서](https://www.microsoft.com/en-us/download/details.aspx?id=27416) 자세한 세부 정보에 대 한). RDS 클라이언트 구성 요소는 나중 버전의 Windows에서 제거 됩니다. 새 개발 작업에서는 이 기능을 사용하지 않도록 하고, 현재 이 기능을 사용하는 응용 프로그램은 수정하세요. RDS를 사용 하는 응용 프로그램을 마이그레이션해야 합니다. [WCF 데이터 서비스](http://go.microsoft.com/fwlink/?LinkId=199565)합니다.  
  
 다음 코드를 설정 하는 방법을 보여 줍니다는 [.rds입니다 DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) **서버** designtime 및 데이터 원본을 사용 하 여 테이블 데이터 인식 HTML에 바인딩 매개 변수입니다. 메모장 이나 다른 텍스트 편집기에 다음 코드를 잘라내어 하십시오로 저장 **FilterColumnVBS.asp**합니다.  
  
```  
<!-- BeginFilterColumnVBS -->  
<HTML>  
<HEAD>  
<META name="VI60_DefaultClientScript" Content="VBScript">  
  
<META NAME="GENERATOR" Content="Microsoft Visual Studio 6.0">  
<TITLE>FilterColumn, FilterCriterion, FilterValue, SortColumn, and SortDirection   
Properties and Reset Method Example (VBScript)</TITLE>  
</HEAD>  
<BODY>  
<h1>FilterColumn, FilterCriterion, FilterValue, SortColumn, and SortDirection   
Properties and Reset Method Example (VBScript)</h1>  
  
<OBJECT classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33"  
   ID=RDS HEIGHT=1 WIDTH=1>  
   <PARAM NAME="SQL" VALUE="Select FirstName, LastName, Title, ReportsTo, Extension from Employees">  
   <PARAM NAME="SERVER" VALUE="<%=Request.ServerVariables("SERVER_NAME")%>">  
   <PARAM NAME="CONNECT" VALUE="Provider=SQLOLEDB;Initial Catalog=Northwind;Integrated Security=SSPI">  
</OBJECT>  
  
Sort Column: <SELECT NAME="cboSortColumn">   
              <OPTION VALUE=""></OPTION>  
                  <OPTION VALUE=ID>ID</OPTION>  
                  <OPTION VALUE=FirstName>FirstName</OPTION>  
                  <OPTION VALUE=LastName>LastName</OPTION>  
                  <OPTION VALUE=Title>Title</OPTION>  
                  <OPTION VALUE=Title>ReportsTo</OPTION>  
                  <OPTION VALUE=Phone>Extension</OPTION>  
             </SELECT>  
             <br>  
Sort Direction: <SELECT NAME="cboSortDir">   
              <OPTION VALUE=""></OPTION>  
                  <OPTION VALUE=TRUE>Ascending</OPTION>  
                  <OPTION VALUE=FALSE>Descending</OPTION>  
                </SELECT>  
<HR WIDTH="25%">  
Filter Column: <SELECT NAME="cboFilterColumn">   
              <OPTION VALUE=""></OPTION>  
                  <OPTION VALUE=FirstName>FirstName</OPTION>  
                  <OPTION VALUE=LastName>LastName</OPTION>  
                  <OPTION VALUE=Title>Title</OPTION>  
                  <OPTION VALUE=Room>ReportsTo</OPTION>  
                  <OPTION VALUE=Phone>Extension</OPTION>  
             </SELECT>  
             <br>  
Filter Criterion: <SELECT NAME="cboCriterion">   
                    <OPTION VALUE=""></OPTION>  
                    <OPTION VALUE="=">=</OPTION>  
                    <OPTION VALUE=">">></OPTION>  
                    <OPTION VALUE="<"><</OPTION>  
                    <OPTION VALUE=">=">>=</OPTION>  
                    <OPTION VALUE="<="><=</OPTION>  
                    <OPTION VALUE="<>"><></OPTION>  
                  </SELECT>   
              <br>  
Filter Value: <INPUT NAME="txtFilterValue">  
<HR WIDTH="25%">  
<INPUT TYPE=BUTTON NAME=Clear VALUE="CLEAR ALL">    
<INPUT TYPE=BUTTON NAME=SortFilter VALUE="APPLY">  
  
<HR>  
<TABLE DATASRC=#RDS ID="DataTable">  
<THEAD>  
  <TR>  
    <TH>FirstName</TH>  
    <TH>LastName</TH>  
    <TH>Title</TH>  
    <TH>Reports To</TH>  
    <TH>Extension</TH>  
  </TR>  
</THEAD>  
<TBODY>  
  <TR>  
    <TD><SPAN DATAFLD="FirstName"></SPAN></TD>  
    <TD><SPAN DATAFLD="LastName"></SPAN></TD>  
    <TD><SPAN DATAFLD="Title"></SPAN></TD>  
    <TD><SPAN DATAFLD="ReportsTo"></SPAN></TD>  
    <TD><SPAN DATAFLD="Extension"></SPAN></TD>  
  </TR>  
</TBODY>  
</TABLE>  
  
<Script Language="VBScript">  
<!--  
Const adFilterNone = 0  
  
Sub SortFilter_OnClick  
   Dim vCriterion  
   Dim vSortDir  
   Dim vSortCol  
   Dim vFilterCol  
  
   ' The value of SortColumn will be the   
   ' value of what the user picks in the  
   ' cboSortColumn box.  
   vSortCol = cboSortColumn.options(cboSortColumn.selectedIndex).value  
  
   If(vSortCol <> "") then  
      RDS.SortColumn = vSortCol  
   End If  
  
   ' The value of SortDirection will be the   
   ' value of what the user specifies in the  
   ' cboSortdirection box.  
  
   If (vSortCol <> "") then  
      vSortDir = cboSortDir.options(cboSortDir.selectedIndex).value  
      If (vSortDir = "") then  
         MsgBox "You must select a direction for the sort."  
         Exit Sub  
      Else  
         If vSortDir = "Ascending" Then vSortDir = "TRUE"  
         If vSortDir = "Descending" Then vSortDir = "FALSE"  
         RDS.SortDirection = vSortDir  
      End If  
   End If  
  
   ' The value of FilterColumn will be the   
   ' value of what the user specifies in the  
   ' cboFilterColumn box.  
   vFilterCol = cboFilterColumn.options(cboFilterColumn.selectedIndex).value  
  
   If(vFilterCol <> "") then  
      RDS.FilterColumn = vFilterCol  
   End If  
  
   ' The value of FilterCriterion will be the   
   ' text value of what the user specifies in the  
   ' cboCriterion box.  
   vCriterion = cboCriterion.options(cboCriterion.selectedIndex).value  
   If (vCriterion <> "") Then  
      RDS.FilterCriterion = vCriterion  
   End If  
  
   ' txtFilterValue is a rich text box  
   ' control. The value of FilterValue will be the   
   ' text value of what the user specifies in the  
   ' txtFilterValue box.  
   If (txtFilterValue.value <> "") Then  
      RDS.FilterValue = txtFilterValue.value  
   End If  
  
   ' Execute the sort and filter on a client-side  
   ' Recordset based on the specified sort and filter  
   ' properties. Calling Reset refreshes the result set  
   ' that is displayed in the data-bound controls to  
   ' display the filtered, sorted recordset.  
   RDS.Reset  
End Sub  
  
Sub Clear_onClick()  
   'clear the HTML input controls  
   cboSortColumn.selectedIndex = 0  
   cboSortDir.selectedIndex = 0  
   cboFilterColumn.selectedIndex = 0  
   cboCriterion.selectedIndex = 0  
   txtFilterValue.value = ""  
  
   'clear the filter  
   RDS.FilterCriterion = ""  
   RDS.Reset(FALSE)  
End Sub  
-->  
</Script>  
  
</BODY>  
</HTML>  
<!-- EndFilterColumnVBS -->  
```  
  
## <a name="see-also"></a>관련 항목:  
 [DataControl 개체 (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)   
 [FilterColumn 속성 (RDS)](../../../ado/reference/rds-api/filtercolumn-property-rds.md)   
 [FilterCriterion 속성 (RDS)](../../../ado/reference/rds-api/filtercriterion-property-rds.md)   
 [FilterValue 속성 (RDS)](../../../ado/reference/rds-api/filtervalue-property-rds.md)   
 [Reset 메서드 (RDS)](../../../ado/reference/rds-api/reset-method-rds.md)   
 [SortColumn 속성 (RDS)](../../../ado/reference/rds-api/sortcolumn-property-rds.md)   
 [SortDirection 속성(RDS)](../../../ado/reference/rds-api/sortdirection-property-rds.md)

