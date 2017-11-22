---
title: "실행 시 데이터 및 텍스트, ntext 또는 Image 열 | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-text-image-columns
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- columns [ODBC]
- ODBC data types, image columns
- ODBC data types, text columns
- data-at-execution
- ODBC data-at-execution
- image columns [ODBC]
ms.assetid: 67ffb1a6-f38d-4712-ba64-96bdd41ec2b2
caps.latest.revision: "29"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8ffac673c5ed91fb51c174ac60e20138753a1c1f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="data-at-execution-and-text-ntext-or-image-columns"></a>실행 시 데이터 및 text, ntext 또는 image 열
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  ODBC 실행 시 데이터는 응용 프로그램에서 바인딩된 열 또는 매개 변수에 있는 대량의 데이터를 사용할 수 있도록 하는 기능입니다. 매우 큰를 검색할 때 **텍스트**, **ntext**, 또는 **이미지** 열, 응용 프로그램 못할를 단순히 거 대 한 버퍼를 할당, 열 버퍼에 바인딩하고 인출 행입니다. 매우 큰 업데이트할 때 **텍스트**, **ntext**, 또는 **이미지** 열을 응용 프로그램 못할 수 단순히 거 대 한 버퍼를 할당할 매개 변수 표식 SQL에 바인딩 문, 다음 문을 실행 합니다. 이러한 경우에는 응용 프로그램 사용 해야 [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) 또는 [SQLPutData](../../relational-databases/native-client-odbc-api/sqlputdata.md) 실행 시 데이터 옵션에 해당 합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [text 및 image 열 관리](../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)  
  
  