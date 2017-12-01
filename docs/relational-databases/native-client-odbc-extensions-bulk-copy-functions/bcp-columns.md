---
title: bcp_columns | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-extensions-bulk-copy-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: bcp_columns
apilocation: sqlncli11.dll
apitype: DLLExport
helpviewer_keywords: bcp_columns function
ms.assetid: 5376f6fe-9508-439a-8c66-778d77f19ac3
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 86f3a722b11761f2d195cd0490c1b9adb5479bed
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="bcpcolumns"></a>bcp_columns
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서의 대량 복사에 사용하기 위해 사용자 파일에서 찾는 총 열 수를 설정합니다. [bcp_setbulkmode](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-setbulkmode.md) bcp_columns 대신 사용할 수 있습니다 및 [bcp_colfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md)합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
RETCODE bcp_columns (  
        HDBC hdbc,  
        INT nColumns);  
```  
  
## <a name="arguments"></a>인수  
 *hdbc*  
 대량 복사가 가능한 ODBC 연결 핸들입니다.  
  
 *nColumns*  
 사용자 파일에 포함된 총 열 수입니다. 데이터 대량 복사 하려면에서 사용자 파일을 준비 하는 경우에 프로그램 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블 및 사용자 파일의 모든 열을 복사 하지 않으려는 설정 해야 *nColumns* 사용자 파일 열의 총 수입니다.  
  
## <a name="returns"></a>반환 값  
 SUCCEED 또는 FAIL  
  
## <a name="remarks"></a>주의  
 후에이 함수를 호출할 수 있습니다 [bcp_init](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) 유효한 파일 이름으로 호출 합니다.  
  
 기본값과는 다른 사용자 파일 형식을 사용하려는 경우에만 이 함수를 호출해야 합니다. 기본 사용자 파일 형식에 대 한 설명에 대 한 자세한 내용은 참조 **bcp_init**합니다.  
  
 호출한 후 **bcp_columns**를 호출 해야 [bcp_colfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md)완전히 사용자 지정 파일 형식 정의를 사용자 파일의 각 열에 대 한 합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [대량 복사 함수](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  