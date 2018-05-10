---
title: BeginTrans, CommitTrans 및 RollbackTrans 메서드 예제 (VC + +) | Microsoft Docs
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
- BeginTrans method [ADO], VC++ example
- RollbackTrans method [ADO], VC++ example
- CommitTrans method [ADO], VC++ example
ms.assetid: 4ac19647-73e7-4edf-9913-25c8fd927e36
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7b4d10ed949380ad8cb6a83c77a9191f100f2b2c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="begintrans-committrans-and-rollbacktrans-methods-example-vc"></a>BeginTrans, CommitTrans 및 RollbackTrans 메서드 예제 (VC + +)
에 있는 모든 심리학 책의 책 종류를 변경 하는이 예제는 ***타이틀*** 데이터베이스의 테이블입니다. 후의 [BeginTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) 메서드 시작에 대 한 모든 변경 내용을 격리 하는 트랜잭션을 ***타이틀*** 테이블은 [CommitTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) 메서드는 변경 내용을 저장 합니다. 사용할 수는 [롤백](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) 메서드를 사용 하 여 저장 하는 변경 내용을 취소 하는 [업데이트](../../../ado/reference/ado-api/update-method.md) 메서드.  
  
## <a name="example"></a>예제  
  
```  
// BeginBeginTransCpp.cpp  
// compile with: /EHsc /c  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
#include <stdio.h>  
#include <ole2.h>  
#include <conio.h>  
#include <assert.h>  
#include <malloc.h>  
#include "icrsint.h"  
  
// extracts only title and type   
class CTitlesRs : public CADORecordBinding {  
   BEGIN_ADO_BINDING(CTitlesRs)  
  
   //Column title is the 2nd field in the recordset    
   ADO_VARIABLE_LENGTH_ENTRY2(2, adVarChar, m_szT_title, sizeof(m_szT_title), lT_titleStatus, FALSE)  
  
   // Column type is the 3rd field in the recordset    
   ADO_VARIABLE_LENGTH_ENTRY2(3, adVarChar, m_szT_type, sizeof(m_szT_type), lT_typeStatus, TRUE)  
   END_ADO_BINDING()  
  
public:  
   CHAR m_szT_title[150];  
   ULONG lT_titleStatus;  
   CHAR m_szT_type[40];  
   ULONG lT_typeStatus;  
};  
  
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };  
void BeginTransX();  
void PrintProviderError(_ConnectionPtr pConnection);  
  
int main() {  
   if (FAILED(::CoInitialize(NULL)))  
      return -1;  
  
   BeginTransX();  
  
   ::CoUninitialize();  
}  
  
void BeginTransX() {  
   // Define ADO object pointers, initialize pointers on define.  These are in the ADODB::  namespace.  
   _RecordsetPtr rstTitles = NULL;  
   _ConnectionPtr pConnection = NULL;  
   char * token1, * token2;  
  
   // Define Other Variables  
   HRESULT hr = S_OK;    
   IADORecordBinding *picRs = NULL;   // Interface Pointer declared  
   CTitlesRs titlrs;  
   _bstr_t strTitle;   
   _bstr_t strMessage;  
   LPSTR p_TempStr = NULL;  
   char chKey;  
   int i = 0;  
  
   try {  
      // open connection.  
      _bstr_t strCnn("Provider='sqloledb';Data Source='My_Data_Source'; Initial Catalog='pubs';Integrated Security='SSPI';");  
  
      TESTHR(pConnection.CreateInstance(__uuidof(Connection)));  
  
      TESTHR(pConnection->Open(strCnn, "", "", adConnectUnspecified));  
  
      rstTitles.CreateInstance(__uuidof(Recordset));    
  
      rstTitles->CursorType = adOpenDynamic;  
      rstTitles->LockType = adLockPessimistic;  
  
      // open Titles table  
      TESTHR(rstTitles->Open("titles", _variant_t((IDispatch*)pConnection,true),  
         adOpenDynamic, adLockPessimistic,adCmdTable));  
  
      rstTitles->MoveFirst();  
      pConnection->BeginTrans();  
  
      // Open an IADORecordBinding interface pointer which   
      // we'll use for Binding Recordset to a class  
      TESTHR(rstTitles->QueryInterface(__uuidof(IADORecordBinding), (LPVOID*)&picRs));  
  
      // Bind the Recordset to a C++ Class here      
      TESTHR(picRs->BindToRecordset(&titlrs));  
  
      // Loop through recordset, prompt user to change the type for a specified title.  
      // Allocate memory to p_TempStr string pointer.  
      p_TempStr = (LPSTR) malloc(sizeof(titlrs.m_szT_type));  
  
      // Check for null string.  
      assert(p_TempStr != NULL);  
  
      while (VARIANT_FALSE == rstTitles->EndOfFile) {  
         // Set the final character of the destination string to NULL.  
         p_TempStr[sizeof(titlrs.m_szT_type)-1] = '\0';  
  
         // The source string will get truncated if its length is   
         // longer than the length of the destination string minus one.  
         strncpy_s(p_TempStr, sizeof(titlrs.m_szT_type), strtok_s(titlrs.m_szT_type," ", &token1), sizeof(titlrs.m_szT_type) - 1);  
  
         // Compare type with psychology  
         if (!strcmp(p_TempStr,"psychology")) {   
            strTitle = titlrs.m_szT_title;  
            strMessage = "Title: " + strTitle + "\n Change type to Self help?(y/n)";  
  
            // Change the title for specified employee  
            printf("%s\n", (LPCSTR)strMessage);  
            do {  
               chKey = _getch();  
            } while (chKey != 'y' && chKey !='n');  
  
            if (chKey == 'y') {  
               // Set last character of destination string to NULL.  
               titlrs.m_szT_type[sizeof(titlrs.m_szT_type)-1] = '\0';  
  
               // Copy "self_help" title field.  The source string will get truncated   
               // if its length is longer than length of destination string, minus one.  
               strncpy_s(titlrs.m_szT_type, _countof(titlrs.m_szT_type), "self_help", sizeof(titlrs.m_szT_type) - 1);  
  
               picRs->Update(&titlrs);  
            }  
         }  
         rstTitles->MoveNext();  
      }  
      // Ask if the User wants to commit to all the changes made above  
      printf("\n\n Save all changes(y/n)?");  
  
      do {  
         chKey = _getch();  
      } while (chKey != 'y' && chKey !='n');  
  
      if (chKey == 'y')  
         // Save the changes to the title table  
         pConnection->CommitTrans();  
      else  
         // Unsave the changes to the title table  
         pConnection->RollbackTrans();  
  
      // Print current data in recordset.  
      rstTitles->Requery(0);  
  
      // Move to the first record of the title table  
      rstTitles->MoveFirst();  
      printf("\n\nPress any key to continue...");  
      _getch();  
  
      // Clear the screen for the next display     
      // system("cls");   
  
      // Open IADORecordBinding interface pointer again for binding Recordset to a class.  
      TESTHR(rstTitles->QueryInterface( __uuidof(IADORecordBinding), (LPVOID*)&picRs));  
  
      // Rebind the Recordset to a C++ Class.  
      TESTHR(picRs->BindToRecordset(&titlrs));  
  
      while (!rstTitles->EndOfFile) {  
         i = i + 1;  
         if (i % 23 == 0) {  
            printf("\nPress any key to continue...");  
            _getch();  
  
            // Clear the screen for the next display  
            // system("cls");   
         }  
         printf("%s -  %s\n", titlrs.m_szT_title, titlrs.m_szT_type);  
         rstTitles->MoveNext();  
      }  
      // Restore original data becasue this is a demonstration.  
      rstTitles->MoveFirst();  
  
      while (VARIANT_FALSE == rstTitles->EndOfFile) {  
         // Set the final character of the destination string to NULL.  
         p_TempStr[sizeof(titlrs.m_szT_type)-1] = '\0';  
  
         // The source string will get truncated if its length is   
         // longer than the length of the destination string minus one.  
         strncpy_s(p_TempStr, sizeof(titlrs.m_szT_type), titlrs.m_szT_type, sizeof(titlrs.m_szT_type) - 1);  
  
         p_TempStr = strtok_s(p_TempStr," ", &token2);  
  
         if (!strcmp(p_TempStr,"self_help")) {  
            // Set final character of destination string to NULL.  
            titlrs.m_szT_type[sizeof(titlrs.m_szT_type)-1] = '\0';  
  
            // The source string will get truncated if its length is longer than the length   
            // of the destination string minus one.  
            strncpy_s(titlrs.m_szT_type, _countof(titlrs.m_szT_type), "psychology", sizeof(titlrs.m_szT_type) - 1);  
            picRs->Update(&titlrs);  
         }  
         rstTitles->MoveNext();    
      }  
   }  
   catch(_com_error &e) {  
      // Notify the user of errors if any.  
      _bstr_t bstrSource(e.Source());  
      _bstr_t bstrDescription(e.Description());  
  
      PrintProviderError(pConnection);  
  
      printf("Source : %s\n", (LPCSTR)bstrSource);  
      printf("Description : %s\n", (LPCSTR)bstrDescription);  
   }  
  
   // Deallocate the memory  
   if (p_TempStr)  
      free(p_TempStr);  
   // Clean up objects before exit.  
   // Release the IADORecordset Interface here  
   if (picRs)  
      picRs->Release();  
  
   if (rstTitles)  
      if (rstTitles->State == adStateOpen)  
         rstTitles->Close();  
   if (pConnection)  
      if (pConnection->State == adStateOpen)  
         pConnection->Close();  
};  
  
void PrintProviderError(_ConnectionPtr pConnection) {  
   // Print Provider Errors from Connection object.  
   // pErr is a record object in the Connection's Error collection.  
   ErrorPtr pErr = NULL;  
   long nCount = 0;  
   long i = 0;  
  
   if ( (pConnection->Errors->Count) > 0) {  
      nCount = pConnection->Errors->Count;  
      // Collection ranges from 0 to nCount -1.  
      for (i = 0 ; i < nCount ; i++) {  
         pErr = pConnection->Errors->GetItem(i);  
         printf("Error number: %x\t%s\n", pErr->Number, (LPCSTR) pErr->Description);  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>관련 항목:  
 [BeginTrans, CommitTrans 및 RollbackTrans 메서드 (ADO)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)   
 [Update 메서드](../../../ado/reference/ado-api/update-method.md)