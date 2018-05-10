---
title: AbsolutePosition 및 앞 속성 예제 (VC + +) | Microsoft Docs
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
- C++
helpviewer_keywords:
- CursorLocation property [ADO], VC++ example
- AbsolutePosition property [ADO], VC++ example
ms.assetid: 48c07216-d199-4822-89f8-ce928d3d2b74
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f7b97df0763704bd22c8e6616859120a39949b62
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="absoluteposition-and-cursorlocation-properties-example-vc"></a>AbsolutePosition 및 앞 속성 예제 (VC + +)
이 예제에서는 방법을 [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md) 속성의 모든 레코드를 열거 하는 루프의 진행률을 추적할 수는 [레코드 집합](../../../ado/reference/ado-api/recordset-object-ado.md)합니다. 사용 하 여는 [앞](../../../ado/reference/ado-api/cursorlocation-property-ado.md) 속성을 사용 하 여 **AbsolutePosition** 클라이언트 커서를 커서를 설정 하 여 속성입니다.  
  
```  
// BeginAbsolutePositionCpp.cpp  
// compile with: /EHsc /c  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
#include <ole2.h>  
#include <stdio.h>  
#include "conio.h"   
#include "icrsint.h"  
  
// This class extracts last name.    
class CEmployeeRs : public CADORecordBinding {  
   BEGIN_ADO_BINDING(CEmployeeRs)  
      // Column lname is the 4th field in the recordset     
      ADO_VARIABLE_LENGTH_ENTRY2(4, adVarChar, m_szau_lname,   
      sizeof(m_szau_lname), lau_lnameStatus, TRUE)  
   END_ADO_BINDING()  
  
public:  
   CHAR   m_szau_lname[41];  
   ULONG  lau_lnameStatus;  
  
};  
  
//Function Declarations  
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };  
  
void AbsolutePositionX();  
void AbsolutePosition2X();  
void PrintProviderError(_ConnectionPtr pConnection);  
  
int main() {  
   if ( FAILED(::CoInitialize(NULL)) )  
      return -1;  
  
   AbsolutePositionX();  
  
   // Clear the screen for the next display     
   printf("Press any key to continue...");  
   _getch();  
   system("cls");   
  
   AbsolutePosition2X();  
  
   ::CoUninitialize();  
}  
  
void AbsolutePositionX() {  
   HRESULT hr = S_OK;    
  
   // Define ADO object pointers.  // Initialize pointers on define.  
   // These are in the ADODB:: namespace.  
   _RecordsetPtr pRstEmployees = NULL;  
  
   // Define other variables.  Interface Pointer declared.(VC++ Extensions)  
   IADORecordBinding *picRs = NULL;  
   CEmployeeRs emprs;   // C++ class object  
   _bstr_t strMessage;  
   char chKey;  
  
   // Open a recordset using a client cursor for the Employee table.  
  
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");  
  
   try {  
      // Open a recordset.  
      TESTHR(pRstEmployees.CreateInstance(__uuidof(Recordset)));  
  
      // Use client cursor to enable AbsolutePosition property.  
      pRstEmployees->CursorLocation = adUseClient;  
  
      // Explicitly pass the default Cursor type and LockType to the recordset.  
      TESTHR(pRstEmployees->Open("employee", strCnn, adOpenForwardOnly, adLockReadOnly, adCmdTable));  
  
      // Open an IADORecordBinding interface pointer for binding the recordset to a class.  
      TESTHR(pRstEmployees->QueryInterface(__uuidof(IADORecordBinding),(LPVOID*)&picRs));  
  
      // Bind the recordset to a C++ class here.     
      TESTHR(picRs->BindToRecordset(&emprs));  
  
      strMessage= "";  
  
      // Enumerate recordset  
      do {  
         // Display current record information.  
         printf("Employee : %s \n record %ld of %d",   
            emprs.lau_lnameStatus == adFldOK ?   
            emprs.m_szau_lname : "<NULL>",  
            pRstEmployees->AbsolutePosition,   
            pRstEmployees->RecordCount);  
  
         printf("\nContinue?(y/n)  :");  
  
         do {  
            chKey = _getch();  
         } while (chKey != 'y' && chKey !='n');  
  
         // Clear the Screen for the next output     
         system("cls");  
  
         if (chKey == 'n')  
            break;  
  
         strMessage = "";     
         pRstEmployees->MoveNext();     
      } while (!(pRstEmployees->EndOfFile));  
   }  
   catch(_com_error &e) {  
      // Notify the user of errors, if any.  
      _variant_t vtConnect = pRstEmployees->GetActiveConnection();  
  
      // GetActiveConnection returns connect string if connection  
      // is not open, else returns Connection object.  
      switch(vtConnect.vt) {  
      case VT_BSTR:  
         printf("Error:\n");  
         printf("Code = %08lx\n", e.Error());  
         printf("Message = %s\n", e.ErrorMessage());  
         printf("Source = %s\n", (LPCSTR) e.Source());  
         printf("Description = %s\n", (LPCSTR) e.Description());  
         break;  
      case VT_DISPATCH:  
         PrintProviderError(vtConnect);  
         break;  
      default:  
         printf("Errors occured.");  
         break;  
      }  
   }  
  
   // Clean up objects before exit.  Release the IADORecordset Interface here.   
   if (picRs)  
      picRs->Release();  
  
   if (pRstEmployees)  
      if (pRstEmployees->State == adStateOpen)  
         pRstEmployees->Close();  
}  
  
void AbsolutePosition2X() {  
   HRESULT hr = S_OK;    
  
   // Define ADO object pointers.  Initialize pointers on define.  
   // These are in the ADODB:: namespace.  
   _RecordsetPtr pRstEmployees = NULL;  
  
   // Define Other Variables.  Interface Pointer declared.(VC++ Extensions)  
   IADORecordBinding *picRs = NULL;  
   CEmployeeRs emprs;   // C++ class object  
   _bstr_t strMessage;  
  
   // Open a recordset using a client cursor for the Employee table.  
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");  
  
   try {  
      // Open a recordset.  
      TESTHR(pRstEmployees.CreateInstance(__uuidof(Recordset)));  
  
      // Use client cursor to enable Absoluteposition property.  
      pRstEmployees->CursorLocation = adUseClient;  
  
      // Explicitly pass the default Cursor type and LockType to the Recordset.  
      TESTHR(pRstEmployees->Open("employee", strCnn, adOpenStatic, adLockReadOnly, adCmdTable));  
  
      // Open an IADORecordBinding interface pointer for Binding Recordset to a class.  
      TESTHR(pRstEmployees->QueryInterface(__uuidof(IADORecordBinding),(LPVOID*)&picRs));  
  
      // Bind the Recordset to a C++ Class here.   
      TESTHR(picRs->BindToRecordset(&emprs));  
  
      long lGoToPos = 21;  
  
      pRstEmployees->AbsolutePosition = (PositionEnum)lGoToPos;  
  
      // Display current record information.  
      printf("Employee : %s \n record %ld of %d",   
         emprs.lau_lnameStatus == adFldOK ? emprs.m_szau_lname : "<NULL>", pRstEmployees->AbsolutePosition,   
         pRstEmployees->RecordCount);  
  
      printf("\nPress any key to continue:");  
      _getch();  
   }  
   catch(_com_error &e) {  
      // Notify the user of errors if any.  
      _variant_t vtConnect = pRstEmployees->GetActiveConnection();  
  
      // GetActiveConnection returns connect string if connection  
      // is not open, else returns Connection object.  
      switch(vtConnect.vt) {  
      case VT_BSTR:  
         printf("Error:\n");  
         printf("Code = %08lx\n", e.Error());  
         printf("Message = %s\n", e.ErrorMessage());  
         printf("Source = %s\n", (LPCSTR) e.Source());  
         printf("Description = %s\n", (LPCSTR) e.Description());  
         break;  
      case VT_DISPATCH:  
         PrintProviderError(vtConnect);  
         break;  
      default:  
         printf("Errors occured.");  
         break;  
      }  
   }  
  
   // Clean up objects before exit. Release the IADORecordset Interface here.    
   if (picRs)  
      picRs->Release();  
  
   if (pRstEmployees)  
      if (pRstEmployees->State == adStateOpen)  
         pRstEmployees->Close();  
}  
  
void PrintProviderError(_ConnectionPtr pConnection) {  
   // Print Provider Errors from Connection object.  
   // pErr is a record object in the Connection's Error collection.  
   ErrorPtr pErr = NULL;  
   long nCount = 0;      
   long i = 0;  
  
   if ( (pConnection->Errors->Count) > 0) {  
      nCount = pConnection->Errors->Count;  
      // Collection ranges from 0 to nCount -1.  
      for ( i = 0 ; i < nCount ; i++ ) {  
         pErr = pConnection->Errors->GetItem(i);  
         printf("\t Error number: %x\t%s", pErr->Number, (LPCSTR) pErr->Description);  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>관련 항목:  
 [AbsolutePosition 속성 (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md)   
 [앞 속성 (ADO)](../../../ado/reference/ado-api/cursorlocation-property-ado.md)   
 [레코드 집합 개체(ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)