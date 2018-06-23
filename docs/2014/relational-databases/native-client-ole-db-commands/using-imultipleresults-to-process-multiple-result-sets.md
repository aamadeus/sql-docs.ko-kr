---
title: IMultipleResults를 사용 하 여 여러 결과 집합을 처리할 | Microsoft Docs
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
- multiple rowsets
- rowsets [OLE DB], multiple
- IMultipleResults interface
- multiple-rowset results
ms.assetid: 754d3f30-7d94-4b67-8dac-baf2699ce9c6
caps.latest.revision: 39
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ff247ff9c17183f435d5acc312121e5ee36e100b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36187195"
---
# <a name="using-imultipleresults-to-process-multiple-result-sets"></a>IMultipleResults를 사용하여 여러 결과 집합 처리
  소비자가 사용 하 여는 **IMultipleResults** 에서 반환 된 결과 처리 하는 인터페이스 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자 명령 실행 합니다. 경우는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 명령을 실행 하기 위해 전송 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 문을 실행 하 고 결과 반환 합니다.  
  
 클라이언트는 명령 실행을 통해 반환된 모든 결과를 처리해야 합니다. 때문에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자 명령 실행 수 결과로 여러 행 집합 개체를 생성, 사용 된 **IMultipleResults** 응용 프로그램 데이터 검색이 완료 되도록 인터페이스는 클라이언트가 시작한 왕복 합니다.  
  
 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문에서 여러 행 집합, 행 데이터 집합도 일부 발생는 **OrderDetails** 테이블 및 COMPUTE BY 절의 결과 집합도 있습니다.  
  
```  
SELECT OrderID, FullPrice = (UnitPrice * Quantity), Discount,  
    Discounted = UnitPrice * (1 - Discount) * Quantity  
FROM OrderDetails  
ORDER BY OrderID  
COMPUTE  
    SUM(UnitPrice * Quantity), SUM(UnitPrice * (1 - Discount) * Quantity)  
    BY OrderID  
```  
  
 소비자가 이 텍스트를 포함하는 명령을 실행하고 반환되는 결과 인터페이스로 행 집합을 요청하면 첫 번째 행 집합만 반환됩니다. 이 경우 소비자는 반환되는 행 집합에 있는 모든 행을 처리할 수 있습니다. 그러나 DBPROP_MULTIPLECONNECTIONS 데이터 원본 속성 VARIANT_FALSE 이면 및 MARS 연결에서 활성화 되지 않음을 설정 다른 명령은 세션 개체에서 실행할 수 있습니다 (의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 다른 만들지 않습니다 연결) 명령을 취소 될 때까지입니다. 연결에 MARS를 사용 하지 않는 경우는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 DBPROP_MULTIPLECONNECTIONS가 VARIANT_FALSE 고 활성 트랜잭션이 있으면 E_FAIL을 반환 하는 경우 DB_E_OBJECTOPEN 오류를 반환 합니다.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 스트림된 출력 매개 변수를 사용 하는 경우 DB_E_OBJECTOPEN 및 응용 프로그램을 호출 하기 전에 반환 된 출력 매개 변수 값을 모두 사용한 하지 반환도 **imultipleresults:: Getresults**  다음 결과 집합을 가져오도록 합니다. MARS가 설정되어 있지 않은 상태에서 연결이 행 집합을 생성하지 않는 명령 또는 서버 커서가 아닌 행 집합을 생성하는 명령을 실행 중이고 DBPROP_MULTIPLECONNECTIONS 데이터 원본 속성이 VARIANT_TRUE로 설정되어 있는 경우, 트랜잭션이 오류를 반환하는 활성 상태가 아니면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자가 동시 명령 개체를 지원하기 위해 추가 연결을 만듭니다. 트랜잭션 및 잠금은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 연결별로 관리합니다. 두 번째 연결이 생성되면 개별 연결의 명령이 잠금을 공유하지 않습니다. 한 명령이 다른 명령을 차단하지 않도록 다른 명령이 요청한 행의 잠금이 유지되도록 주의해야 합니다. MARS가 설정되어 있는 경우 연결에 여러 명령을 활성화할 수 있으며 명시적 트랜잭션이 사용 중인 경우 모든 명령이 공통 트랜잭션을 공유합니다.  
  
 소비자 명령을 취소할 수를 사용 하 여 [issabort:: Abort](../native-client-ole-db-interfaces/issabort-abort-ole-db.md) 명령 개체 및 파생된 행 집합에 대 한 모든 참조를 해제 하는 방식입니다.  
  
 사용 하 여 **IMultipleResults** 모든 인스턴스에서 소비자가 get 명령 실행 하 여 생성 된 모든 행 집합을 허용 하 고 적절 하 게 명령 실행을 취소 하 고에서 사용 하기 위해 세션 개체를 해제 하는 시기를 결정 하는 소비자 허용 다른 명령입니다.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 커서를 사용할 때 명령을 실행하면 커서가 생성됩니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 커서 생성에 대한 성공이나 실패를 반환하므로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 대한 왕복은 명령 실행 결과가 반환되면 완료됩니다. 각 **GetNextRows** 호출에 대 한 왕복 그러면가 됩니다. 따라서 여러 활성 명령 개체가 존재할 수 있으며, 이러한 각각의 개체가 서버 커서에서 인출한 결과 행 집합을 처리할 수 있습니다. 자세한 내용은 참조 [행 집합 및 SQL Server 커서](../native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md)합니다.  
  
## <a name="see-also"></a>관련 항목  
 [도구](commands.md)  
  
  