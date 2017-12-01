---
title: "준비 된 문의 테이블 반환 매개 변수 메타 데이터 | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-table-valued-parameters
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: table-valued parameters (ODBC), metadata for prepared statements
ms.assetid: fd2fc705-2e98-4011-9822-c7e6cca4a535
caps.latest.revision: "13"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 99cf2abce3eef4f79bafdf26724f26f90171d09d
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="table-valued-parameter-metadata-for-prepared-statements"></a>준비된 문의 테이블 반환 매개 변수 메타데이터
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  응용 프로그램 SQLNumParams 및 SQLDescribeParam 통해 준비 된 프로시저 호출에 대 한 메타 데이터를 가져올 수 있습니다. 테이블 반환 매개 변수에 대 한 *DataTypePtr* SQL_SS_TABLE로 설정 합니다. 추가 메타 데이터는 SQL_CA_SS_TYPE_NAME, SQL_CA_SS_CATALOG_NAME 및 SQL_CA_SS_SCHEMA_NAME에 대 한 SQLGetDescField를 통해 사용할 수 있습니다.  
  
 SQL_CA_SS_TYPE_NAME, SQL_CA_SS_CATALOG_NAME 및 sql_ca_ss_schema_name은 사용 하 여 SQLColumns 테이블 반환 매개 변수와 연결 된 테이블 형식에 대해 열 메타 데이터를 가져옵니다. 이 경우 SQLColumns를 호출 하기 전에 SQL_SOPT_SS_NAME_SCOPE는 sql_ss_name_scope_table_type으로 설정 되어야 합니다. 그리고 응용 프로그램이 테이블 반환 매개 변수 열 메타데이터 검색을 마치면 SQL_SOPT_SS_NAME_SCOPE를 기본값인 SQL_SS_NAME_SCOPE_TABLE로 다시 설정해야 합니다.  
  
 SQL_CA_SS_TYPE_NAME , SQL_CA_SS_CATALOG_NAME 및 SQL_CA_SS_SCHEMA_NAME을 CLR 사용자 정의 형식 매개 변수에 사용할 수도 있습니다.  
  
 저장 프로시저 호출이 아닌 준비된 문의 테이블 반환 매개 변수 메타데이터는 가져올 수 없습니다. 이렇게 하려고 하면 응용 프로그램에서 SQLSTATE 42000이고 메시지가 "구문 오류 또는 액세스 위반입니다."인 SQL_ERROR가 반환됩니다.  
  
## <a name="see-also"></a>관련 항목:  
 [테이블 반환 매개 변수 사용 &#40; ODBC &#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  