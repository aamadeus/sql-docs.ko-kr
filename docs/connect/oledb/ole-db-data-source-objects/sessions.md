---
title: 세션 | Microsoft Docs
description: OLE DB Driver for SQL Server에에서 대 한 세션
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-data-source-objects
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- sessions [OLE DB]
- OLE DB Driver for SQL Server, sessions
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 93bc1dfd43cd0f049c335ea3d17812f4b38939ab
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2018
---
# <a name="sessions"></a>세션
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  OLE DB Driver for SQL Server 세션의 인스턴스를 단일 연결을 나타내는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]합니다.  
  
 OLE DB Driver for SQL Server 세션 데이터 원본에 대 한 트랜잭션 공간으로 구분 해야 합니다. 특정 세션 개체에서 만들어진 모든 명령 개체는 해당 세션 개체의 로컬 또는 분산 트랜잭션에 참여합니다.  
  
 초기화된 데이터 원본에서 만든 첫 번째 세션 개체는 초기화 시 설정된 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 연결을 받습니다. 세션 개체의 인터페이스에 있는 모든 참조가 해제되면 데이터 원본에서 만든 다른 세션 개체가 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 대한 연결을 사용할 수 있습니다.  
  
 데이터 원본에서 만든 추가 세션 개체는 데이터 원본에 지정된 대로 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 대한 고유한 연결을 설정합니다. 응용 프로그램이 해당 세션 중에 만들어진 개체 참조를 모두 해제하면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 대한 연결이 삭제됩니다.  
  
 다음 예제에서는에 연결 하는 OLE DB Driver for SQL Server를 사용 하는 방법을 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터베이스:  
  
```  
int main()  
{  
    // Interfaces used in the example.  
    IDBInitialize*      pIDBInitialize      = NULL;  
    IDBCreateSession*   pIDBCreateSession   = NULL;  
    IDBCreateCommand*   pICreateCmd1        = NULL;  
    IDBCreateCommand*   pICreateCmd2        = NULL;  
    IDBCreateCommand*   pICreateCmd3        = NULL;  
  
    // Initialize COM.  
    if (FAILED(CoInitialize(NULL)))  
    {  
        // Display error from CoInitialize.  
        return (-1);  
    }  
  
    // Get the memory allocator for this task.  
    if (FAILED(CoGetMalloc(MEMCTX_TASK, &g_pIMalloc)))  
    {  
        // Display error from CoGetMalloc.  
        goto EXIT;  
    }  
  
    // Create an instance of the data source object.  
    if (FAILED(CoCreateInstance(CLSID_MSOLEDBSQL, NULL,  
        CLSCTX_INPROC_SERVER, IID_IDBInitialize, (void**)  
        &pIDBInitialize)))  
    {  
        // Display error from CoCreateInstance.  
        goto EXIT;  
    }  
  
    // The InitFromPersistedDS function   
    // performs IDBInitialize->Initialize() establishing  
    // the first application connection to the instance of SQL Server.  
    if (FAILED(InitFromPersistedDS(pIDBInitialize, L"MyDataSource",  
        NULL, NULL)))  
    {  
        goto EXIT;  
    }  
  
    // The IDBCreateSession interface is implemented on the data source  
    // object. Maintaining the reference received maintains the   
    // connection of the data source to the instance of SQL Server.  
    if (FAILED(pIDBInitialize->QueryInterface(IID_IDBCreateSession,  
        (void**) &pIDBCreateSession)))  
    {  
        // Display error from pIDBInitialize.  
        goto EXIT;  
    }  
  
    // Releasing this has no effect on the SQL Server connection  
    // of the data source object because of the reference maintained by  
    // pIDBCreateSession.  
    pIDBInitialize->Release();  
    pIDBInitialize = NULL;  
  
    // The session created next receives the SQL Server connection of  
    // the data source object. No new connection is established.  
    if (FAILED(pIDBCreateSession->CreateSession(NULL,  
        IID_IDBCreateCommand, (IUnknown**) &pICreateCmd1)))  
    {  
        // Display error from pIDBCreateSession.  
        goto EXIT;  
    }  
  
    // A new connection to the instance of SQL Server is established to support the  
    // next session object created. On successful completion, the  
    // application has two active connections on the SQL Server.  
    if (FAILED(pIDBCreateSession->CreateSession(NULL,  
        IID_IDBCreateCommand, (IUnknown**) &pICreateCmd2)))  
    {  
        // Display error from pIDBCreateSession.  
        goto EXIT;  
    }  
  
    // pICreateCmd1 has the data source connection. Because the  
    // reference on the IDBCreateSession interface of the data source  
    // has not been released, releasing the reference on the session  
    // object does not terminate a connection to the instance of SQL Server.  
    // However, the connection of the data source object is now   
    // available to another session object. After a successful call to   
    // Release, the application still has two active connections to the   
    // instance of SQL Server.  
    pICreateCmd1->Release();  
    pICreateCmd1 = NULL;  
  
    // The next session created gets the SQL Server connection  
    // of the data source object. The application has two active  
    // connections to the instance of SQL Server.  
    if (FAILED(pIDBCreateSession->CreateSession(NULL,  
        IID_IDBCreateCommand, (IUnknown**) &pICreateCmd3)))  
    {  
        // Display error from pIDBCreateSession.  
        goto EXIT;  
    }  
  
EXIT:  
    // Even on error, this does not terminate a SQL Server connection   
    // because pICreateCmd1 has the connection of the data source   
    // object.  
    if (pICreateCmd1 != NULL)  
        pICreateCmd1->Release();  
  
    // Releasing the reference on pICreateCmd2 terminates the SQL  
    // Server connection supporting the session object. The application  
    // now has only a single active connection on the instance of SQL Server.  
    if (pICreateCmd2 != NULL)  
        pICreateCmd2->Release();  
  
    // Even on error, this does not terminate a SQL Server connection   
    // because pICreateCmd3 has the connection of the   
    // data source object.  
    if (pICreateCmd3 != NULL)  
        pICreateCmd3->Release();  
  
    // On release of the last reference on a data source interface, the  
    // connection of the data source object to the instance of SQL Server is broken.  
    // The example application now has no SQL Server connections active.  
    if (pIDBCreateSession != NULL)  
        pIDBCreateSession->Release();  
  
    // Called only if an error occurred while attempting to get a   
    // reference on the IDBCreateSession interface of the data source.  
    // If so, the call to IDBInitialize::Uninitialize terminates the   
    // connection of the data source object to the instance of SQL Server.  
    if (pIDBInitialize != NULL)  
    {  
        if (FAILED(pIDBInitialize->Uninitialize()))  
        {  
            // Uninitialize is not required, but it fails if an  
            // interface has not been released. Use it for  
            // debugging.  
        }  
        pIDBInitialize->Release();  
    }  
  
    if (g_pIMalloc != NULL)  
        g_pIMalloc->Release();  
  
    CoUninitialize();  
  
    return (0);  
}  
```  
  
 세션 개체의 인스턴스를 SQL Server 용 OLE DB Driver 연결 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 지속적으로 만들고 세션 개체를 해제 하는 응용 프로그램에 대 한 상당한 오버 헤드가 생성할 수 있습니다. SQL Server 세션 개체에 대 한 OLE DB 드라이버를 효율적으로 관리 하 여 오버 헤드를 최소화할 수 있습니다. OLE DB Driver for SQL Server 응용 프로그램을 유지할 수는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 개체의 인터페이스를 하나 이상에 대 한 참조를 유지 관리 하 여 활성 세션 개체의 연결 합니다.  
  
 예를 들어 명령 만들기 개체 참조 풀을 유지 관리하면 풀에 포함된 이러한 세션 개체에 대해 활성 연결이 유지됩니다. 풀 유지 관리 코드로 전달 유효한 세션 개체를 필요한 대로 **IDBCreateCommand** 인터페이스 포인터를 세션이 필요한 응용 프로그램 메서드를 합니다. 응용 프로그램 메서드에 더 이상 세션이 필요하지 않으면 메서드에서 명령 만들기 개체에 대한 응용 프로그램 참조를 해제하는 대신 인터페이스 포인터를 다시 풀 유지 관리 코드로 반환합니다.  
  
> [!NOTE]  
>  앞의 예제에는 **IDBCreateCommand** 때문에 인터페이스를 사용는 **ICommand** 구현는 **GetDBSession** 메서드, 개체가 작성 된 세션을 확인할 수 있도록 하는 명령 또는 행 집합 범위 내의 유일한 메서드입니다. 따라서 명령 개체를 사용해야만 응용 프로그램이 추가 세션을 만들 수 있는 데이터 원본 개체 포인터를 검색할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [데이터 원본 개체 & #40; OLE db& #41;](../../oledb/ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  