---
title: NumericScale 및 전체 자릿수 속성 예 (VC + +) | Microsoft Docs
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
- NumericScale property [ADO], VC++ example
- Precision property [ADO], VC++ example
ms.assetid: 55d91ba8-4d80-4df6-af8e-060a19ddc138
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8f8e653242247f73b517833cc5ba8dc195b03998
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="numericscale-and-precision-properties-example-vc"></a>NumericScale 및 전체 자릿수 속성 예 (VC + +)
사용 하 여이 예제는 [NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md) 및 [정밀도](../../../ado/reference/ado-api/precision-property-ado.md) 소수 자릿수 및 필드에 전체 자릿수를 표시 하는 속성의 ***할인*** 목차는  ***Pubs*** 데이터베이스입니다.  
  
```  
// BeginNumericScaleCpp.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
#include <ole2.h>  
#include <stdio.h>  
#include <conio.h>  
  
// Function declarations  
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };  
void NumericScaleX();  
void PrintProviderError(_ConnectionPtr pConnection);  
void PrintComError(_com_error &e);  
  
int main() {  
   if ( FAILED(::CoInitialize(NULL)) )  
      return -1;  
  
   NumericScaleX();  
   ::CoUninitialize();  
}  
  
void NumericScaleX() {  
   // Define ADO object pointers.  Initialize pointers on define.  
   // These are in the ADODB::  namespace  
   _RecordsetPtr pRstDiscounts = NULL;  
   FieldsPtr fldTemp = NULL;  
  
   // Define Other Variables  
   _variant_t Index;  
   Index.vt = VT_I2;  
  
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");  
  
   try {  
      // Open recordset.  
      TESTHR(pRstDiscounts.CreateInstance(__uuidof(Recordset)));  
      pRstDiscounts->Open("discounts", strCnn, adOpenForwardOnly, adLockReadOnly, adCmdTable);  
  
      // Display numeric scale and precision of numeric and small integer fields.  
      fldTemp = pRstDiscounts->GetFields();  
  
      for (short int intLoop = 0 ; intLoop < (int)fldTemp->GetCount() ; intLoop++ ) {  
         Index.iVal = intLoop;  
  
         if ( (fldTemp->GetItem(Index)->Type == adNumeric) ||   
            (fldTemp->GetItem(Index)->Type == adSmallInt) ) {   
            printf("Field: %s\n" , (LPCSTR)fldTemp->GetItem(Index)->GetName());  
            printf("Numeric scale: %d\n", fldTemp->GetItem(Index)->GetNumericScale());  
            printf("Precision: %d\n", fldTemp->GetItem(Index)->GetPrecision());  
         }  
      }  
   }  
   catch(_com_error &e) {      
      // Display errors, if any. Pass a connection pointer accessed from the Recordset.  
      _variant_t vtConnect = pRstDiscounts->GetActiveConnection();  
  
      // GetActiveConnection returns connect string if connection  
      // is not open, else returns Connection object.  
      switch(vtConnect.vt) {  
      case VT_BSTR:  
         PrintComError(e);  
         break;  
      case VT_DISPATCH:  
         PrintProviderError(vtConnect);  
         break;  
      default:  
         printf("Errors occured.");  
         break;  
      }  
   }  
  
   // Clean up objects before exit.  
   if (pRstDiscounts)  
      if (pRstDiscounts->State == adStateOpen)  
         pRstDiscounts->Close();  
}  
  
void PrintProviderError(_ConnectionPtr pConnection) {  
   // Print Provider Errors from Connection object.  
   // pErr is a record object in the Connection's Error collection.  
   ErrorPtr pErr = NULL;  
  
   if ( (pConnection->Errors->Count) > 0 ) {  
      long nCount = pConnection->Errors->Count;  
  
      // Collection ranges from 0 to nCount -1.  
      for ( long i = 0 ; i < nCount ; i++ ) {  
         pErr = pConnection->Errors->GetItem(i);  
         printf("\t Error number: %x\t%s", pErr->Number, pErr->Description);  
      }  
   }  
}  
  
void PrintComError(_com_error &e) {  
   _bstr_t bstrSource(e.Source());  
   _bstr_t bstrDescription(e.Description());  
  
   // Print COM errors.   
   printf("Error\n");  
   printf("\tCode = %08lx\n", e.Error());  
   printf("\tCode meaning = %s\n", e.ErrorMessage());  
   printf("\tSource = %s\n", (LPCSTR) bstrSource);  
   printf("\tDescription = %s\n", (LPCSTR) bstrDescription);  
}  
```  
  
## <a name="see-also"></a>관련 항목:  
 [NumericScale 속성 (ADO)](../../../ado/reference/ado-api/numericscale-property-ado.md)   
 [Precision 속성(ADO)](../../../ado/reference/ado-api/precision-property-ado.md)