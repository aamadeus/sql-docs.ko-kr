---
title: 메타 데이터 검색 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: ec3c0f4f-f838-43ce-85f2-cf2761e2aac5
caps.latest.revision: 13
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1d367bf34e57cd20e91a7adee5f186be95be8423
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36093957"
---
# <a name="metadata-discovery"></a>메타데이터 검색
  메타 데이터 검색 개선 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 허용 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 전에 지정 된 쿼리 실행에서 반환 된 해당 열 또는 매개 변수 메타 데이터는 동일 하거나 메타 데이터와 호환 되도록 네이티브 클라이언트 응용 프로그램 형식 쿼리를 실행 합니다. 쿼리 실행 후 반환된 메타데이터가 쿼리를 실행하기 전에 지정한 메타데이터 형식과 호환되지 않는 경우 오류가 발생합니다.  
  
 bcp 및 ODBC 함수와 IBCPSession 및 IBCPSession2 인터페이스에서는 이제 쿼리 출력 작업에서 메타데이터를 검색하지 않도록 지연된 읽기(지연된 메타데이터 검색)을 지정할 수 있습니다. 이로 인해 성능이 향상되고 메타데이터 검색 오류가 발생하지 않습니다.  
  
 사용 하 여 응용 프로그램을 개발 하는 경우 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client에 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 서버 버전에 연결 하지만 이전의 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], 메타 데이터 검색 기능이 서버 버전에 해당 됩니다.  
  
## <a name="remarks"></a>Remarks  
 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]에서 다음 bcp 함수의 기능이 개선되어 메타데이터 검색 기능이 향상되었습니다.  
  
-   [bcp_columns](../../native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md)  
  
-   [bcp_control](../../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)  
  
-   [bcp_getcolfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-getcolfmt.md)  
  
-   [bcp_readfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md)  
  
-   [bcp_setcolfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-setcolfmt.md)  
  
 사용 하 여 메타 데이터 형식을 지정 하는 경우 성능 향상을도 나타납니다 [bcp_setbulkmode](../../native-client-odbc-extensions-bulk-copy-functions/bcp-setbulkmode.md)합니다.  
  
 [bcp_control](../../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) 에 있는 새 *eOption* bcp_readfmt의 동작을 제어: `BCPDELAYREADFMT`합니다.  
  
 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]에서 다음 ODBC 함수의 기능이 개선되어 메타데이터 검색 기능이 향상되었습니다.  
  
-   [SQLNumResultCols](../../native-client-odbc-api/sqlnumresultcols.md)  
  
-   [SQLDescribeCol](../../native-client-odbc-api/sqldescribecol.md)  
  
-   [SQLNumParams](../../native-client-odbc-api/sqlnumparams.md)  
  
-   [SQLDescribeParam](../../native-client-odbc-api/sqldescribeparam.md)  
  
 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]에서 다음 OLE DB 멤버 함수의 기능이 개선되어 메타데이터 검색 기능이 향상되었습니다.  
  
-   IColumnsInfo::GetColumnInfo  
  
-   IColumnsRowset::GetColumnsRowset  
  
-   Icommandwithparameters:: Getparameterinfo (참조 [ICommandWithParameters](../../native-client-ole-db-interfaces/icommandwithparameters.md) 자세한 내용은)  
  
 IBCPSession::BCPSetBulkMode를 사용 하 여 메타 데이터 형식 지정 하는 경우에 성능이 향상 될 됩니다.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 다음과 같은 두 개의 저장 프로시저가 추가되어 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client에서 메타데이터 검색 기능이 향상되었습니다.  
  
-   sp_describe_first_result_set  
  
-   sp_describe_undeclared_parameters  
  
## <a name="see-also"></a>관련 항목  
 [SQL Server Native Client 기능](sql-server-native-client-features.md)  
  
  