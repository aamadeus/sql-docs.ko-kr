---
title: 'Ibcpsession:: Bcpdone (OLE DB) | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- IBCPSession::BCPDone (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPDone method
ms.assetid: 19cd6e55-432a-450e-a15c-54d50eb53dee
caps.latest.revision: 26
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 099618fccdf11dba2acb56303e2fec2d7a496ab0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36184258"
---
# <a name="ibcpsessionbcpdone-ole-db"></a>IBCPSession::BCPDone(OLE DB)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 보낼 나머지 행을 커밋합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
HRESULT BCPDone(void);  
```  
  
## <a name="remarks"></a>Remarks  
 다른 작업이 호출 될 수는 [IBCPSession](ibcpsession-ole-db.md) 호출한 후 인터페이스는 **BCPDone** 메서드. 호출 하는 것만 가능은 [ibcpsession:: Bcpinit](ibcpsession-bcpinit-ole-db.md) 새 대량 복사 작업을 시작 하려면 메서드. 이 호출 비슷합니다는 [irowsetfastload:: Commit](irowsetfastload-commit-ole-db.md) 메서드.  
  
## <a name="return-code-values"></a>반환 코드 값  
 S_OK  
 메서드가 성공했습니다.  
  
 E_UNEXPECTED  
 예기치 않은 메서드가 호출되었습니다. 예를 들어 이 메서드를 호출하기 전에 **BCPInit** 메서드를 호출하지 않았습니다.  
  
## <a name="example"></a>예제  
 이 예제에서는 **IBCPSession** 인터페이스를 사용하는 방법을 보여 줍니다.  
  
 이 예제를 실행하기 전에 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 실행해야 합니다.  
  
```  
create table fltest(col1 int, col2 int, col3 image)  
insert into fltest values (1, 1, 0x0FF)  
insert into fltest values (2, 2, 0xF00)  
insert into fltest values (3, 3, 0xBAD)  
insert into fltest values (4, 4, 0xFAD)  
```  
  
 이 예제는 master 데이터베이스에 연결됩니다.  
  
 예제를 실행하면 프로젝트 디렉터리에 outfile.dat 파일이 생성됩니다. outfile.dat 파일에는 기본(이진) 모드로 테이블에서 복사한 데이터가 포함됩니다.  
  
 BCP를 사용하여 이 데이터를 테이블에 다시 추가할 수 있습니다. 예를 들어 다음 명령을 사용할 수 있습니다.  
  
 **bcp 마스터... outfile.dat 파일-n-T-S에서 fltest** *서버*  
  
 이 예제를 컴파일할 때 sqlncli11.lib를 지정해야 합니다.  
  
```  
#define DBINITCONSTANTS   // Defined to initialize constants in oledb.h  
#define INITGUID  
#define MAX_ROWS  100  
  
#include <windows.h>  
#include <sqlext.h>  
#include <sqlncli.h>  
#include <oledberr.h>  
#include <stdio.h>  
  
#define SAFE_RELEASE(p) { \  
   if (p) { \  
   (p)->Release(); \  
   (p)=NULL; \  
   } \  
}  
  
// DumpErrorInfo queries error interfaces, retrieving available status or error information.  
void DumpErrorInfo ( IUnknown* pObjectWithError, REFIID IID_InterfaceWithError ) {  
   // Interfaces used in the example.  
   IErrorInfo * pIErrorInfoAll = NULL;  
   IErrorInfo * pIErrorInfoRecord = NULL;  
   IErrorRecords * pIErrorRecords = NULL;  
   ISupportErrorInfo * pISupportErrorInfo = NULL;  
   ISQLErrorInfo * pISQLErrorInfo = NULL;  
   ISQLServerErrorInfo * pISQLServerErrorInfo = NULL;  
  
   // Number of error records.  
   ULONG nRecs;  
   ULONG nRec;  
  
   // Basic error information from GetBasicErrorInfo.  
   ERRORINFO errorinfo;  
  
   // IErrorInfo values.  
   BSTR bstrDescription;  
   BSTR bstrSource;  
  
   // ISQLErrorInfo parameters.  
   BSTR bstrSQLSTATE;  
   LONG lNativeError;  
  
   // ISQLServerErrorInfo parameter pointers.  
   SSERRORINFO * pSSErrorInfo = NULL;  
   OLECHAR * pSSErrorStrings = NULL;  
  
   // Hard-code a US English locale for the example.  
   DWORD MYLOCALEID = 0x0409;  
  
   // Only ask for error information if the interface supports it.  
   if (FAILED(pObjectWithError->QueryInterface(IID_ISupportErrorInfo, (void**) &pISupportErrorInfo))) {  
      wprintf(L"SupportErrorErrorInfo interface not supported\r\n");  
      return;  
   }  
  
   if (FAILED(pISupportErrorInfo->InterfaceSupportsErrorInfo(IID_InterfaceWithError))) {  
      wprintf(L"InterfaceWithError interface not supported\r\n");  
      return;  
   }  
  
   // Do not test the return of GetErrorInfo. It can succeed and return  
   // a NULL pointer in pIErrorInfoAll. Simply test the pointer.  
   GetErrorInfo(0, &pIErrorInfoAll);  
  
   if (pIErrorInfoAll != NULL) {  
      // Test to see if it's a valid OLE DB IErrorInfo interface exposing a list of records.  
      if (SUCCEEDED(pIErrorInfoAll->QueryInterface(IID_IErrorRecords, (void**) &pIErrorRecords))) {  
         pIErrorRecords->GetRecordCount(&nRecs);  
  
         // Within each record, retrieve information from each of the defined interfaces.  
         for (nRec = 0; nRec < nRecs; nRec++) {  
            // From IErrorRecords, get the HRESULT and a reference to the ISQLErrorInfo interface.  
            pIErrorRecords->GetBasicErrorInfo(nRec, &errorinfo);  
            pIErrorRecords->GetCustomErrorObject(nRec,IID_ISQLErrorInfo, (IUnknown**) &pISQLErrorInfo);  
  
            // Display the HRESULT, then use the ISQLErrorInfo.  
            wprintf(L"HRESULT:\t%#X\r\n", errorinfo.hrError);  
  
            if (pISQLErrorInfo != NULL) {  
               pISQLErrorInfo->GetSQLInfo(&bstrSQLSTATE, &lNativeError);  
  
               // Display the SQLSTATE and native error values.  
               wprintf(L"SQLSTATE:\t%s\r\nNative Error:\t%ld\r\n", bstrSQLSTATE, lNativeError);  
  
               // SysFree BSTR references.  
               SysFreeString(bstrSQLSTATE);  
  
               // Get the ISQLServerErrorInfo interface from ISQLErrorInfo before releasing the reference.  
               pISQLErrorInfo->QueryInterface( IID_ISQLServerErrorInfo, (void**) &pISQLServerErrorInfo);   
  
               pISQLErrorInfo->Release();  
            }  
  
            // Test to ensure the reference is valid, then get error information from ISQLServerErrorInfo.  
            if (pISQLServerErrorInfo != NULL) {  
               pISQLServerErrorInfo->GetErrorInfo(&pSSErrorInfo, &pSSErrorStrings);  
  
               // ISQLServerErrorInfo::GetErrorInfo succeeds even when it has nothing to return.   
               // Test the pointers before using.  
               if (pSSErrorInfo) {  
                  // Display the state and severity from the returned information.   
                  // The error message comes from IErrorInfo::GetDescription.  
                  wprintf(L"Error state:\t%d\r\nSeverity:\t%d\r\n", pSSErrorInfo->bState, pSSErrorInfo->bClass);  
  
                  // IMalloc::Free needed to release references on returned values.  
                  CoTaskMemFree(pSSErrorStrings);  
                  CoTaskMemFree(pSSErrorInfo);  
               }  
  
               pISQLServerErrorInfo->Release();  
            }  
  
            if (SUCCEEDED(pIErrorRecords->GetErrorInfo(nRec, MYLOCALEID, &pIErrorInfoRecord))) {  
               // Get the source and description (error message) from the record's IErrorInfo.  
               pIErrorInfoRecord->GetSource(&bstrSource);  
               pIErrorInfoRecord->GetDescription(&bstrDescription);  
  
               if (bstrSource != NULL) {  
                  wprintf(L"Source:\t\t%s\r\n", bstrSource);  
                  SysFreeString(bstrSource);  
               }  
  
               if (bstrDescription != NULL) {  
                  wprintf(L"Error message:\t%s\r\n", bstrDescription);  
                  SysFreeString(bstrDescription);  
               }  
  
               pIErrorInfoRecord->Release();  
            }  
         }  
         pIErrorRecords->Release();  
      }  
      else {  
         // IErrorInfo is valid; get the source and description to see what it is.  
         pIErrorInfoAll->GetSource(&bstrSource);  
         pIErrorInfoAll->GetDescription(&bstrDescription);  
  
         if (bstrSource != NULL) {  
            wprintf(L"Source:\t\t%s\r\n", bstrSource);  
            SysFreeString(bstrSource);  
         }  
  
         if (bstrDescription != NULL) {  
            wprintf(L"Error message:\t%s\r\n", bstrDescription);  
            SysFreeString(bstrDescription);  
         }  
      }  
  
      pIErrorInfoAll->Release();  
   }  
   else   
      wprintf(L"GetErrorInfo has not returned ErrorInfo.\r\n");  
  
   pISupportErrorInfo->Release();  
   return;  
}  
  
IDBCreateSession *Connect () {  
   // constant definitions  
   static LPCWSTR pwszProviderString = L"server=(local)\\dschwart3;Database=master;Trusted_Connection=yes;";  
   static LPCWSTR pwszDataSource     = NULL;  
   static LPCWSTR pwszUserID         = NULL;  
   static LPCWSTR pwszPassword       = NULL;  
  
   IDBInitialize    * pIDBInitialize      = NULL;  
   IDBProperties    * pIDBProperties      = NULL;  
   IDBCreateSession * pIDBCreateSession   = NULL;  
  
   HRESULT hr;  
  
   // Obtain the provider's clsid  
   CLSID clsidProv = CLSID_SQLNCLI10;  
  
   // Initialize COM  
   CoInitialize(NULL);  
  
   hr = CoCreateInstance(clsidProv, NULL, CLSCTX_ALL, IID_IDBInitialize,(void **)&pIDBInitialize);  
   if (!SUCCEEDED(hr))   
      return NULL;  
  
   hr = pIDBInitialize->QueryInterface(IID_IDBProperties, (void **)&pIDBProperties);  
   if (!SUCCEEDED(hr))   
      return NULL;  
  
   // Set Init properties  
   {  
      DBPROPSET rgPropSets[1];  
      ULONG     cPropSets   = 0;  
      DBPROP    rgInitProperties[10];  
  
      // Initialize Data source properties (connection info)  
      {  
         ULONG cProperties = 0;  
  
         // DBPROP_INIT_DATASOURCE  
         if (pwszDataSource) {  
            rgInitProperties[cProperties].dwPropertyID    = DBPROP_INIT_DATASOURCE;  
            rgInitProperties[cProperties].dwOptions       = DBPROPOPTIONS_REQUIRED;  
            rgInitProperties[cProperties].dwStatus        = DBPROPSTATUS_OK;  
            rgInitProperties[cProperties].colid           = DB_NULLID;  
            rgInitProperties[cProperties].vValue.vt       = VT_BSTR;  
            V_BSTR(&rgInitProperties[cProperties].vValue) = SysAllocString(pwszDataSource);                 
            cProperties++;  
         }  
  
         // DBPROP_AUTH_USERID  
         if (pwszUserID) {  
            rgInitProperties[cProperties].dwPropertyID    = DBPROP_AUTH_USERID;  
            rgInitProperties[cProperties].dwOptions       = DBPROPOPTIONS_REQUIRED;  
            rgInitProperties[cProperties].dwStatus        = DBPROPSTATUS_OK;  
            rgInitProperties[cProperties].colid           = DB_NULLID;  
            rgInitProperties[cProperties].vValue.vt       = VT_BSTR;  
            V_BSTR(&rgInitProperties[cProperties].vValue) = SysAllocString(pwszUserID);  
            cProperties++;  
         }  
  
         // DBPROP_AUTH_PASSWORD  
         if (pwszPassword) {  
            rgInitProperties[cProperties].dwPropertyID    = DBPROP_AUTH_PASSWORD;  
            rgInitProperties[cProperties].dwOptions       = DBPROPOPTIONS_REQUIRED;  
            rgInitProperties[cProperties].dwStatus        = DBPROPSTATUS_OK;  
            rgInitProperties[cProperties].colid           = DB_NULLID;  
            rgInitProperties[cProperties].vValue.vt       = VT_BSTR;  
            V_BSTR(&rgInitProperties[cProperties].vValue) = SysAllocString(pwszPassword);  
            cProperties++;  
         }  
  
         // DBPROP_INIT_PROVIDERSTRING  
         if (pwszProviderString) {  
            rgInitProperties[cProperties].dwPropertyID    = DBPROP_INIT_PROVIDERSTRING;  
            rgInitProperties[cProperties].dwOptions       = DBPROPOPTIONS_REQUIRED;  
            rgInitProperties[cProperties].dwStatus        = DBPROPSTATUS_OK;  
            rgInitProperties[cProperties].colid           = DB_NULLID;  
            rgInitProperties[cProperties].vValue.vt       = VT_BSTR;  
            V_BSTR(&rgInitProperties[cProperties].vValue) = SysAllocString(pwszProviderString);  
            cProperties++;  
         }  
  
         if (cProperties) {  
            rgPropSets[cPropSets].cProperties = cProperties;  
            rgPropSets[cPropSets].rgProperties = rgInitProperties;  
            rgPropSets[cPropSets].guidPropertySet = DBPROPSET_DBINIT;  
            cPropSets++;  
         }  
      }  
  
      // Initialize  
      hr = pIDBProperties->SetProperties(cPropSets, rgPropSets);  
      if (!SUCCEEDED(hr)) {  
         DumpErrorInfo(pIDBProperties, IID_IDBProperties);  
         return NULL;  
      }  
   }  
  
   SAFE_RELEASE(pIDBProperties);  
  
   hr = pIDBInitialize->Initialize();  
   if (!SUCCEEDED(hr)) {  
      DumpErrorInfo(pIDBInitialize, IID_IDBInitialize);  
      return NULL;  
   }  
  
   hr = pIDBInitialize->QueryInterface(IID_IDBProperties, (void **)&pIDBProperties);  
   if (!SUCCEEDED(hr)) {   
      DumpErrorInfo(pIDBInitialize, IID_IDBInitialize);  
      return NULL;  
   }  
  
   // Set SQL Server Specific properties  
   {  
      DBPROPSET rgPropSets[1];  
      ULONG cPropSets = 0;  
      DBPROP rgSqlProperties[10];  
  
      // Initialize the DBProps for fastload and BCP  
      {  
         ULONG cProperties = 0;  
  
         // SSPROP_ENABLEFASTLOAD  
         {  
            rgSqlProperties[cProperties].dwPropertyID   = SSPROP_ENABLEFASTLOAD;  
            rgSqlProperties[cProperties].dwOptions      = DBPROPOPTIONS_REQUIRED;  
            rgSqlProperties[cProperties].dwStatus       = DBPROPSTATUS_OK;  
            rgSqlProperties[cProperties].colid          = DB_NULLID;  
            rgSqlProperties[cProperties].vValue.vt      = VT_BOOL;  
            V_BOOL(&rgSqlProperties[cProperties].vValue)= VARIANT_TRUE;  
            cProperties++;  
         }  
  
         // SSPROP_ENABLEBULKCOPY  
         {  
            rgSqlProperties[cProperties].dwPropertyID   = SSPROP_ENABLEBULKCOPY;  
            rgSqlProperties[cProperties].dwOptions      = DBPROPOPTIONS_REQUIRED;  
            rgSqlProperties[cProperties].dwStatus       = DBPROPSTATUS_OK;  
            rgSqlProperties[cProperties].colid          = DB_NULLID;  
            rgSqlProperties[cProperties].vValue.vt      = VT_BOOL;  
            V_BOOL(&rgSqlProperties[cProperties].vValue)= VARIANT_TRUE;  
            cProperties++;  
         }  
  
         rgPropSets[cPropSets].cProperties = cProperties;  
         rgPropSets[cPropSets].rgProperties = rgSqlProperties;  
         rgPropSets[cPropSets].guidPropertySet = DBPROPSET_SQLSERVERDATASOURCE;  
         cPropSets++;  
      }  
  
      hr = pIDBProperties->SetProperties(cPropSets, rgPropSets);  
      if (!SUCCEEDED(hr)) {   
         DumpErrorInfo(pIDBProperties, IID_IDBProperties);  
         return NULL;  
      }  
   }  
  
   SAFE_RELEASE(pIDBProperties);  
  
   hr = pIDBInitialize->QueryInterface(IID_IDBCreateSession, (void **)&pIDBCreateSession);  
   if (!SUCCEEDED(hr)) {   
      DumpErrorInfo(pIDBInitialize, IID_IDBInitialize);  
      return NULL;  
   }  
  
   SAFE_RELEASE(pIDBInitialize);  
  
   return pIDBCreateSession;  
}  
  
void wmain() {  
   static LPCWSTR pwszTableName   = L"fltest";  
   static LPCWSTR pwszOutFileName = L"outfile.dat";  
   static LPCWSTR pwszErrFileName = L"errfile.txt";  
  
   DBROWCOUNT icRowsCopied = 0;  
  
   IDBCreateSession * pIDBCreateSession = NULL;  
   IBCPSession * pIBCPSession = NULL;  
  
   HRESULT hr;  
  
   pIDBCreateSession = Connect();  
   if (!pIDBCreateSession) {   
      printf("Failed to connect\r\n");  
      exit(1);  
   }  
  
   // get an IBCPSession interface  
   hr = pIDBCreateSession->CreateSession(NULL, IID_IBCPSession, (IUnknown**) &pIBCPSession);  
  
   if (FAILED(hr)) {  
      printf("Failed to obtain an IBCPSession interface\r\n");  
      DumpErrorInfo(pIDBCreateSession, IID_IDBCreateSession);  
      exit(1);  
   }  
  
   SAFE_RELEASE(pIDBCreateSession);  
  
   // Initialize BCP  
  
   // Here we create the mapping between file and table, identifying  
   // which is the source and which is the destination through the final parameter  
   // (here we are copying out of the table and into the file).  
   hr = pIBCPSession->BCPInit(pwszTableName, pwszOutFileName, pwszErrFileName, BCP_DIRECTION_OUT);  
  
   if (FAILED(hr)) {  
      printf("BCPInit failed.\r\n");  
      DumpErrorInfo(pIBCPSession, IID_IBCPSession);  
      exit(1);  
   }  
  
   // You can set SSPROP_ASYNCH_BULKCOPY to TRUE to improve client latency here,  
   // at which point BCPExec can return DB_S_ASYNCHRONOUS.  
   do {  
      hr = pIBCPSession->BCPExec(&icRowsCopied);  
   } while (hr == DB_S_ASYNCHRONOUS);  
  
   if (FAILED(hr)) {  
      printf("BCPExec failed.\r\n");  
      DumpErrorInfo(pIBCPSession, IID_IBCPSession);  
      exit(1);  
   }  
  
   // flush the rest of the rows and finalize the transaction -- the process is complete.  
   hr = pIBCPSession->BCPDone();  
   if (FAILED(hr)) {  
      printf("BCPDone failed.\r\n");  
      DumpErrorInfo(pIBCPSession, IID_IBCPSession);  
      exit(1);  
   }  
  
   SAFE_RELEASE(pIBCPSession);  
  
   CoUninitialize();  
}  
```  
  
## <a name="see-also"></a>관련 항목  
 [IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md)   
 [대량 복사 작업 수행](../native-client/features/performing-bulk-copy-operations.md)  
  
  