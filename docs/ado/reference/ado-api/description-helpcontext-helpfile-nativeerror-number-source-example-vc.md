---
title: "오류 개체 속성 예제 (VC + +) | Microsoft Docs"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Number property [ADO], VC++ example
- HelpContext property [ADO], VC++ example
- NativeError property [ADO], VC++ example
- SQLState property [ADO], VC++ example
- Source property [ADO], VC++ example
- HelpFile property [ADO], VC++ example
- Description property [ADO], VC++ example
ms.assetid: 5321fc0f-cd0c-4e2a-a5bc-0008fba86b59
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 99f335ba08109973dcab4be118903588b7c9fdca
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="description-helpcontext-helpfile-nativeerror-number-source-and-sqlstate-properties-example-vc"></a>설명, HelpContext, 도움말 파일, NativeError, 숫자, 소스 및 SQLState 속성 예제 (VC + +)
이 예제에서는 오류를 트리거합니다.를 트래핑 하 고 표시 된 [설명](../../../ado/reference/ado-api/description-property.md), [HelpContext](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md), [HelpFile](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md), [NativeError](../../../ado/reference/ado-api/nativeerror-property-ado.md), [ 숫자](../../../ado/reference/ado-api/number-property-ado.md), [소스](../../../ado/reference/ado-api/source-property-ado-error.md), 및 [SQLState](../../../ado/reference/ado-api/sqlstate-property.md) 결과 속성 [오류](../../../ado/reference/ado-api/error-object.md) 개체입니다.  
  
```  
// BeginDescriptionCpp.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
// Function declarations  
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};  
void DescriptionX();  
void PrintProviderError(_ConnectionPtr pConnection);  
void PrintComError(_com_error &e);  
  
int main() {  
   if (FAILED(::CoInitialize(NULL)))  
      return -1;  
  
   DescriptionX();  
   ::CoUninitialize();  
}  
  
void DescriptionX() {  
   // Define ADO object pointers. Initialize pointers on define. These are in the ADODB::  namespace  
   _ConnectionPtr pConnection = NULL;  
   ErrorPtr errorLoop = NULL;  
  
   // Define Other Variables  
   HRESULT hr = S_OK;  
  
   try {  
      // Intentionally trigger an error.  open connection  
      TESTHR(pConnection.CreateInstance(__uuidof(Connection)));  
  
      if (FAILED(hr = pConnection->Open("Nothing", "", "", adConnectUnspecified))) {  
         _com_issue_error(hr);  
         exit(1);  
      }  
  
      // Cleanup object before exit.  
      pConnection->Close();  
   }  
   catch(_com_error) {  
      // Pass a connection pointer.  
      PrintProviderError(pConnection);  
   }  
}  
  
void PrintProviderError(_ConnectionPtr pConnection) {  
   // Define Other Variables  
   HRESULT hr = S_OK;  
   _bstr_t strError;  
   ErrorPtr pErr = NULL;  
  
   try {  
      // Enumerate Errors collection and display properties of each Error object.  
      long nCount = pConnection->Errors->Count;  
  
      // Collection ranges from 0 to nCount - 1.  
      for ( long i = 0 ; i < nCount ; i++ ) {  
         pErr = pConnection->Errors->GetItem(i);  
         printf("Error #%d\n", pErr->Number);  
         printf(" %s\n", (LPCSTR)pErr->Description);  
         printf(" (Source: %s)\n", (LPCSTR)pErr->Source);  
         printf(" (SQL State: %s)\n", (LPCSTR)pErr->SQLState);  
         printf(" (NativeError: %d)\n", (LPCSTR)pErr->NativeError);  
  
         if ((LPCSTR)pErr->GetHelpFile() == NULL)  
            printf("\tNo Help file available\n");  
         else {  
            printf("\t(HelpFile: %s\n)" ,pErr->HelpFile);  
            printf("\t(HelpContext: %s\n)" , pErr->HelpContext);  
         }  
      }  
   }  
  
   catch(_com_error &e) {  
      // Notify the user of errors if any.  
      PrintComError(e);  
   }  
}  
  
void PrintComError(_com_error &e) {  
   // Notify the user of errors if any.  
   _bstr_t bstrSource(e.Source());  
   _bstr_t bstrDescription(e.Description());  
  
   // Print Com errors.  
   printf("Error\n");  
   printf("\tCode = %08lx\n", e.Error());  
   printf("\tCode meaning = %s", e.ErrorMessage());  
   printf("\tSource = %s\n", (LPCSTR) bstrSource);  
   printf("\tDescription = %s\n", (LPCSTR) bstrDescription);  
}  
```  
  
## <a name="see-also"></a>관련 항목:  
 [Description 속성](../../../ado/reference/ado-api/description-property.md)   
 [Error 개체](../../../ado/reference/ado-api/error-object.md)   
 [HelpContext, 도움말 파일 속성](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [HelpContext, 도움말 파일 속성](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [NativeError 속성 (ADO)](../../../ado/reference/ado-api/nativeerror-property-ado.md)   
 [Number 속성 (ADO)](../../../ado/reference/ado-api/number-property-ado.md)   
 [Source 속성 (ADO 오류)](../../../ado/reference/ado-api/source-property-ado-error.md)   
 [SQLState 속성](../../../ado/reference/ado-api/sqlstate-property.md)
