---
title: 바인딩 및 변환 (OLE DB) | Microsoft Docs
description: 바인딩 및 변환 (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-date-time
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- conversions [OLE DB]
- bindings [OLE DB]
- OLE DB, bindings and conversions
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 67c60756f004d339ebd466ce8835c6f549cc7d2a
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2018
---
# <a name="conversions-ole-db"></a>변환 (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  이 섹션에서는 간을 변환 하는 방법을 설명 **datetime** 및 **datetimeoffset** 값입니다. 이 섹션에 설명된 변환은 OLE DB에서 이미 제공하거나 OLE DB의 일관된 확장입니다.  
  
 OLE DB에서 날짜와 시간에 대한 리터럴 및 문자열 형식은 일반적으로 ISO를 따르며 클라이언트 로캘에 종속되지 않습니다. 한 가지 예외는 OLE Automation이 표준인 DBTYPE_DATE이지만 그러나 없기 때문에 OLE DB Driver for SQL Server만 클라이언트에서 데이터를 전송 하는 경우 형식을 변환, OLE DB 드라이버 강제로 DBTYPE_DATE와 문자열 형식 간의 변환 SQL Server에 대 한 응용 프로그램에 방법이 없습니다. 이러한 경우를 제외하면 문자열에는 다음과 같은 형식이 사용됩니다. 여기서 대괄호 안의 텍스트는 선택적 요소를 나타냅니다.  
  
-   형식은 **datetime** 및 **datetimeoffset** 문자열:  
  
     *yyyy*-*mm*-*dd*[ *hh*:*mm*:*ss*[.*9999999*][ ± *hh*:*mm*]]  
  
-   형식은 **시간** 문자열:  
  
     *hh*:*mm*:*ss*[.*9999999*]  
  
-   형식은 **날짜** 문자열:  
  
     *yyyy*-*mm*-*dd*  
  
> [!NOTE]  
>  이전 버전의 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client와 SQLOLEDB에서는 OLE 변환을 구현했으며 이 경우 표준 변환은 실패했습니다. OLE DB Driver for SQL Server와 동일한 동작을 따릅니다 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client입니다. 결과적으로, OLE DB 드라이버에서 SQL Server에 대해 수행 하는 변환 중 일부는 OLE DB 사양과에서 다릅니다.  
  
 문자열에서 변환을 시작하면 공백 및 필드 너비를 보다 융통성 있게 사용할 수 있습니다. 자세한 내용은의 "데이터 형식:: 문자열 및 리터럴" 섹션을 참조 하십시오. [OLE DB 날짜 및 시간 기능 향상에 대 한 데이터 형식 지원](../../oledb/ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md)합니다.  
  
 일반적인 변환 규칙은 다음과 같습니다.  
  
-   문자열을 날짜/시간 형식으로 변환하면 문자열이 먼저 ISO 리터럴로 구문 분석됩니다. 구문 분석이 실패하면 문자열은 시간 구성 요소가 있는 OLE 날짜 리터럴로 구문 분석됩니다.  
  
-   시간 구성 요소가 없지만 받는 사람이 시간을 저장할 수 있는 경우 시간이 0으로 설정됩니다. 날짜 구성 요소가 없지만 받는 사람이 날짜를 저장할 수 있는 경우, ISO 변환을 사용하면 날짜가 현재 날짜로 설정되고 OLE 변환을 사용하면 날짜가 1899-12-30으로 설정됩니다.  
  
-   클라이언트에서 사용하는 데이터 형식에는 표준 시간대가 없지만 서버에서 표준 시간대를 저장할 수 있는 경우 클라이언트의 데이터는 클라이언트 표준 시간대를 기준으로 하는 것으로 간주합니다.  
  
-   서버에는 표준 시간대가 없지만 클라이언트에 표준 시간대 정보가 있는 경우 UTC 표준 시간대가 사용됩니다. 이는 서버 동작과는 다릅니다.  
  
-   시간 구성 요소가 있지만 받는 사람이 시간을 저장할 수 없는 경우 시간 구성 요소는 무시됩니다.  
  
-   날짜 구성 요소가 있지만 받는 사람이 날짜를 저장할 수 없는 경우 날짜 구성 요소는 무시됩니다.  
  
-   클라이언트에서 서버로 변환할 때 초 또는 소수 자릿수 초가 잘리는 경우 DB_E_ERRORSOCCURRED가 반환되고 DBSTATUS_E_DATAOVERFLOW 상태가 설정됩니다.  
  
-   서버에서 클라이언트로 변환할 때 초 또는 소수 자릿수 초가 잘리는 경우 DBSTATUS_S_TRUNCATED가 설정됩니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [클라이언트에서 서버로 수행되는 변환](../../oledb/ole-db-date-time/conversions-performed-from-client-to-server.md)  
 사이 수행 하는 날짜/시간 변환에 설명 SQL Server 용 OLE DB Driver로 작성 된 클라이언트 응용 프로그램 및 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] (또는 이상).  
  
 [서버에서 클라이언트로 수행되는 변환](../../oledb/ole-db-date-time/conversions-performed-from-server-to-client.md)  
 사이 수행 하는 날짜/시간 변환에 설명 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] (또는 이상) SQL Server 용 OLE DB Driver로 작성 된 클라이언트 응용 프로그램 및입니다.  
  
## <a name="see-also"></a>관련 항목:  
 [날짜 및 시간 기능 향상 & #40; OLE db& #41;](../../oledb/ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  