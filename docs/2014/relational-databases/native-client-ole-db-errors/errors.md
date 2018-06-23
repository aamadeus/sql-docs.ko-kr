---
title: 오류 | Microsoft Docs
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
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- OLE/COM errors
- errors [OLE DB]
- OLE DB error handling, about error handling
- OLE DB error handling
ms.assetid: bd0612f4-96ef-4919-b0f9-b5447210fe93
caps.latest.revision: 37
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a3210cb1cd48a375e428cc6cf8a40e6f76f48b21
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36089544"
---
# <a name="errors"></a>오류
  OLE/COM 개체는 개체 멤버 함수의 HRESULT 반환 코드를 통해 오류를 보고합니다. OLE/COM HRESULT는 비트 압축 구조입니다. OLE는 구조 멤버를 역참조하는 매크로를 제공합니다.  
  
 OLE/COM 지정는 **IErrorInfo** 인터페이스입니다. 인터페이스와 같은 메서드를 노출 **GetDescription**합니다. 이 인터페이스를 사용하여 클라이언트는 OLE/COM 서버에서 오류 정보를 추출합니다. OLE DB 확장 **IErrorInfo** 단일 멤버 함수를 실행에서 여러 오류 정보 패킷의 반환을 지원 하도록 합니다.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 여러 오류를 반환합니다. 응용 프로그램 호출 하 여 한 번에 하나씩 서버 오류를 검색할 수 [imultipleresults:: Getresult](http://go.microsoft.com/fwlink/?LinkId=129630) ISQLErrorInfo IErrorRecords와 결합 합니다.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 OLE DB 레코드로 향상 된 표시 **IErrorInfo**, 사용자 지정 `ISQLErrorInfo`, 및 공급자 관련 [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) error 개체 인터페이스입니다.  
  
 오류 추적에 대 한 정보를 참조 하십시오. [데이터 액세스 추적](http://go.microsoft.com/fwlink/?LinkId=125805)합니다. 에 추가 된 오류 추적 향상 된 기능에 대 한 내용은 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], 참조 [확장 이벤트 로그의 진단 정보에 액세스](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md)합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
  
-   [반환 코드](return-codes.md)  
  
-   [오류 인터페이스의 정보](information-in-error-interfaces.md)  
  
-   [SQL Server 오류 세부 정보](sql-server-error-detail.md)  
  
-   [오류 정보 검색](retrieving-error-information.md)  
  
-   [SQL Server 메시지 결과](sql-server-message-results.md)  
  
## <a name="see-also"></a>관련 항목  
 [SQL Server Native Client&#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  