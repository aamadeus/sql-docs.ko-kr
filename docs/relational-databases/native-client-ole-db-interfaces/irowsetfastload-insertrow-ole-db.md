---
title: 'Irowsetfastload:: Insertrow (OLE DB) | Microsoft Docs'
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-interfaces
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IRowsetFastLoad::InsertRow (OLE DB)
apitype: COM
helpviewer_keywords: InsertRow method
ms.assetid: 594d3461-34d2-41e7-8ad4-bd2753601ab6
caps.latest.revision: "37"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 396623230f9df9ba3466cf50c63d0a725f878d99
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="irowsetfastloadinsertrow-ole-db"></a>IRowsetFastLoad::InsertRow(OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  대량 복사 행 집합에 행을 추가합니다. 샘플을 보려면 [대량 복사 데이터를 사용 하 여 IRowsetFastLoad &#40; OLE db&#41;](../../relational-databases/native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md) 및 [BLOB 데이터를 SQL SERVER를 사용 하 여 IROWSETFASTLOAD 및 ISEQUENTIALSTREAM &#40; OLE db&#41;를 보낼](../../relational-databases/native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
HRESULT InsertRow(  
      HACCESSOR hAccessor,  
      void* pData);  
```  
  
## <a name="arguments"></a>인수  
 *hAccessor*[in]  
 대량 복사에 대한 행 데이터를 정의하는 접근자의 핸들입니다. 참조되는 접근자는 행 접근자로, 데이터 값이 포함된 소비자가 소유한 메모리를 바인딩합니다.  
  
 *pData*[in]  
 데이터 값이 포함된 소비자가 소유한 메모리에 대한 포인터입니다. 자세한 내용은 참조 [DBBINDING 구조](http://go.microsoft.com/fwlink/?LinkId=65955)합니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 S_OK  
 메서드가 성공했습니다. 모든 열의 바인딩된 상태 값은 DBSTATUS_S_OK 또는 DBSTATUS_S_NULL입니다.  
  
 E_FAIL  
 오류가 발생했습니다. 행 집합의 오류 인터페이스에서 오류 정보를 볼 수 있습니다.  
  
 E_INVALIDARG  
 *pData* 인수가 NULL 포인터로 설정 되었습니다.  
  
 E_OUTOFMEMORY  
 SQLNCLI11에서 요청을 완료하기에 충분한 메모리를 할당할 수 없습니다.  
  
 E_UNEXPECTED  
 이전에 무효화 된 대량 복사 행 집합에서 호출 되는 [irowsetfastload:: Commit](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-commit-ole-db.md) 메서드.  
  
 DB_E_BADACCESSORHANDLE  
 *hAccessor* 소비자가 제공한 인수 올바르지 않습니다.  
  
 DB_E_BADACCESSORTYPE  
 지정된 접근자는 행 접근자가 아니거나, 소비자가 소유한 메모리를 지정하지 않았습니다.  
  
## <a name="remarks"></a>주의  
 소비자 데이터를 변환 하는 오류는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 열의 데이터 형식을 사용 하면는에서 E_FAIL이 반환 된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자입니다. 데이터를 전송 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 **InsertRow** 메서드 또는 경우에 **커밋** 메서드. 소비자 응용 프로그램이 호출할 수는 **InsertRow** 메서드는 데이터 유형 변환 오류가 있는지 알림을 받기 전에 오류가 있는 데이터를 여러 번입니다. 때문에 **커밋** 메서드를 사용 하면 모든 데이터가 올바르게 지정 되어 있는지는 소비자가 소비자가 사용할 수는 **커밋** 메서드 적절 하 게 필요에 따라 데이터 유효성 검사 합니다.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자 대량 복사 행 집합은 쓰기 전용입니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자 소비자의 행 집합 쿼리를 허용 하는 없는 메서드를 노출 합니다. 처리를 종료 하는 소비자를 해제할 수 있습니다 해당 참조에는 [IRowsetFastLoad](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md) 호출 하지 않고 인터페이스는 **커밋** 메서드. 행 집합에 있는 소비자가 삽입한 행에 액세스하여 해당 값을 변경하거나 행 집합에서 개별적으로 행을 제거하는 기능은 없습니다.  
  
 대량 복사된 행은 서버에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 맞게 형식이 지정됩니다. 행 형식은 연결이나 세션에 대해 설정된 모든 옵션(예: ANSI_PADDING)의 영향을 받습니다. 이 옵션을 통해 설정 된 모든 연결에 대해 기본적으로에 설정 됩니다는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자입니다.  
  
## <a name="see-also"></a>관련 항목:  
 [IRowsetFastLoad &#40; OLE db&#41;](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md)  
  
  