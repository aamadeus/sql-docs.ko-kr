---
title: 날짜 및 시간 기능 향상 | Microsoft Docs
description: SQL Server 용 OLE DB 드라이버에서 날짜 및 시간 개선
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 884a1ada21be273821fba192bde933bb245072ff
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2018
---
# <a name="date-and-time-improvements"></a>날짜 및 시간 기능 향상
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  이 항목에서는 OLE DB 드라이버에 추가 된 날짜 및 시간 데이터 형식에 대 한 SQL Server 지원에 대 한 설명 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]합니다.  
  
 날짜/시간 기능 향상에 대 한 자세한 내용은 참조 [날짜 및 시간 기능 향상 &#40;OLE DB&#41;](../../oledb/ole-db-date-time/date-and-time-improvements-ole-db.md)합니다.  
  
 이 기능을 보여 주는 예제 응용 프로그램에 대한 자세한 내용은 [SQL Server 데이터 프로그래밍 예제](http://msftdpprodsamples.codeplex.com/)를 참조하십시오.  
  
## <a name="usage"></a>사용법  
 다음 섹션에서는 새 date 및 time 형식을 사용하는 다양한 방법에 대해 설명합니다.  
  
### <a name="use-date-as-a-distinct-data-type"></a>고유 데이터 형식으로 Date 사용  
 부터는 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], 날짜/시간 형식에 대 한 향상 된 지원을 통해 DBTYPE_DBDATE OLE DB 유형을 사용 하는 것이 효율적입니다.  
  
### <a name="use-time-as-a-distinct-data-type"></a>고유 데이터 형식으로 Time 사용  
 OLE DB에는 정밀도가 1초인 시간(DBTYPE_DBTIME)만 포함하는 데이터 형식이 이미 있습니다.
  
 새 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 100 나노초까지 정확한 time 데이터 형식은 소수 자릿수 초입니다. SQL Server 용 OLE DB 드라이버에서 새 형식 그러려면: DBTYPE_DBTIME2 합니다. 소수 자릿수 초가 없는 시간을 사용하도록 작성된 기존 응용 프로그램은 time(0) 열을 사용할 수 있습니다. 응용 프로그램 메타 데이터의 반환 형식을 사용 하지 않는 한 기존 OLE DB DBTYPE_TIME 형식과 해당 구조체는 제대로 작동 해야 합니다.  
  
### <a name="use-time-as-a-distinct-data-type-with-extended-fractional-seconds-precision"></a>확장된 초 소수 부분 자릿수의 고유 데이터 형식으로 Time 사용  
 프로세스 제어 및 제조 응용 프로그램과 같은 일부 응용 프로그램에는 정밀도가 최대 100나노초인 시간 데이터를 처리하는 기능이 필요합니다. 새 OLE DB에서 이러한 목적 형식은 DBTYPE_DBTIME2 합니다.  
  
### <a name="use-datetime-with-extended-fractional-seconds-precision"></a>확장된 초 소수 부분 자릿수의 Datetime 사용  
 OLE DB에는 정밀도가 최대 1나노초인 형식이 이미 정의되어 있습니다. 그러나 이 형식은 기존 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 응용 프로그램에서 이미 사용되고 있고 이러한 응용 프로그램에서는 1/300초의 정밀도만 허용합니다. 새 **datetime2(3)** 형식은 기존 datetime 형식과 직접 호환되지 않습니다. 이 형식이 응용 프로그램의 동작에 영향을 미칠 수 있는 경우 응용 프로그램에서 새 DBCOLUMN 플래그를 사용하여 실제 서버 유형을 확인해야 합니다.    
  
### <a name="use-datetime-with-extended-fractional-seconds-precision-and-timezone"></a>확장된 초 소수 부분 자릿수 및 표준 시간대의 Datetime 사용  
 일부 응용 프로그램에는 표준 시간대 정보가 포함된 datetime 값이 필요합니다. 이것은 새 DBTYPE_DBTIMESTAMPOFFSET 형식에서 지원 됩니다.
  
### <a name="use-datetimedatetimedatetimeoffset-data-with-client-side-conversions-consistent-with-existing-conversions"></a>기존 변환과 일관된 클라이언트 쪽 변환이 포함된 Date/Time/Datetime/Datetimeoffset 데이터 사용  
 변환에서 제공 하는 모든 날짜 및 시간 형식 간 변환을 포함 하도록 일관 된 방식으로 확장 됩니다 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [SQL Server 기능용 OLE DB 드라이버](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  