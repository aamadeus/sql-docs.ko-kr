---
title: SQL Server Native Client ODBC 데이터 원본 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ODBC data sources, about data sources
- ODBC data sources, names
- data sources [SQL Server Native Client]
- names [ODBC]
- ODBC applications, data sources
- SQL Server Native Client ODBC driver, data sources
- ODBC data sources
ms.assetid: a6a50fd0-d439-43fd-b76f-16ec02f478c5
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3b74f989db617c2fcd86e0d823b9bb563c7dcda1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36088364"
---
# <a name="sql-server-native-client-odbc-data-sources"></a>SQL Server Native Client ODBC 데이터 원본
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DSN(데이터 원본 이름)은 ODBC 응용 프로그램이 특정 서버의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 연결하는 데 필요한 모든 정보가 포함된 ODBC 데이터 원본을 식별합니다. ODBC 데이터 원본 이름은 다음 두 가지 방법으로 정의할 수 있습니다.  
  
-   클라이언트 컴퓨터에서 관리 도구 제어판을 열고 두 번 클릭 **데이터 원본 (ODBC)** 합니다. DSN을 만드는 데 사용하는 ODBC 데이터 원본 관리자가 열립니다.  
  
-   ODBC 응용 프로그램에서 호출 [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)합니다.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 원본에는 다음 항목이 포함됩니다.  
  
-   데이터 원본의 이름입니다.  
  
-   특정 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결하는 데 필요한 정보  
  
-   특정 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서 사용할 기본 데이터베이스(옵션)  
  
-   사용할 ANSI 옵션, 성능 통계 기록 여부 등의 설정(옵션)  
  
 ODBC 응용 프로그램이 반드시 데이터 원본을 통해 연결해야 하는 것은 아니지만 이와 같은 연결 정보를 ODBC 연결 함수에 제공해야 합니다. 그렇지 않으면 드라이버가 DSN에서 연결 정보를 찾습니다.  
  
## <a name="see-also"></a>관련 항목  
 [SQL Server와 통신 &#40;ODBC&#41;](communicating-with-sql-server-odbc.md)  
  
  