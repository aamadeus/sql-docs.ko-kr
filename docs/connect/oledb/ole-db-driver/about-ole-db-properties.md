---
title: OLE DB 속성에 대 한 | Microsoft Docs
description: OLE DB 속성 정보
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb-driver-for-sql-server
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, properties
- OLE DB Driver for SQL Server, properties
- properties [OLE DB]
- property values [OLE DB Driver for SQL Server]
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 038b9571202e6d01a17fbabbdb8c599823e9020f
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2018
---
# <a name="about-ole-db-properties"></a>OLE DB 속성 정보
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  소비자는 속성 값을 설정하여 특정 개체 동작을 요청합니다. 예를 들어 소비자는 속성을 사용하여 행 집합에서 노출할 인터페이스를 지정합니다. 소비자는 속성 값을 가져와서 행 집합, 세션 또는 데이터 원본 개체와 같은 개체의 기능을 확인합니다.  
  
 각 속성에는 값, 유형, 설명 및 읽기/쓰기 특성이 있고 행 집합 속성의 경우 열 단위로 지정할 수 있는지 여부는 나타내는 표시도 있습니다.  
  
 속성은 GUID와 속성 ID를 나타내는 정수로 식별됩니다. 속성 집합은 동일한 GUID를 공유하는 모든 속성의 집합입니다. 미리 정의 된 OLE DB 속성 집합 외에 OLE DB Driver for SQL Server에 공급자별 속성 집합 및 속성 구현합니다. 각 속성은 하나 이상의 속성 그룹에 속합니다. 속성 그룹은 특정 개체에 적용되는 모든 속성의 그룹입니다. 예를 들어 초기화 속성 그룹, 데이터 원본 속성 그룹, 세션 속성 그룹, 행 집합 속성 그룹, 테이블 속성 그룹, 열 속성 그룹 등이 있습니다. 이러한 각 속성 그룹에는 속성들이 있습니다.  
  
 속성 값을 설정하는 과정은 다음과 같습니다.  
  
1.  값을 설정할 속성을 결정합니다.  
  
2.  식별된 속성을 포함하는 속성 집합을 결정합니다.  
  
3.  식별한 각 속성 집합에 대해 하나씩 DBPROPSET 구조 배열을 할당합니다.  
  
4.  각 속성 집합에 대해 DBPROP 구조 배열을 할당합니다. 각 배열의 요소 수는 1단계에서 식별한 해당 속성 집합에 속한 속성의 수입니다.  
  
5.  각 속성의 DBPROP 구조를 채웁니다.  
  
6.  각 속성 집합의 DBPROPSET 구조에 정보(속성 집합 GUID, 요소 수 및 해당 DBPROP 배열에 대한 포인터)를 채웁니다.  
  
7.  속성을 설정할 메서드를 호출하고 DBPROPSET 구조의 수 및 배열을 전달합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [SQL Server 응용 프로그램에 대 한 OLE DB 드라이버 만들기](../../oledb/ole-db-driver/creating-a-oledb-driver-for-sql-server-application.md)   
 [속성 (OLE DB)](http://go.microsoft.com/fwlink/?LinkId=112207)  
  
  