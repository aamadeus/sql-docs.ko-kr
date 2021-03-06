---
title: 병렬 데이터 웨어하우스-원격 테이블 복사본을 받을 수 있는 기간을 구성 | Microsoft Docs
description: 구입 하 고 InfiniBand 네트워크를 사용 하 여 병렬 데이터 웨어하우스는 원격 테이블 복사 기능에 사용할 연결 기기 비 Windows 시스템을 구성 하는 방법을 설명 합니다. Windows 시스템 SQL Server PDW 데이터베이스에서 원격 테이블 복사본을 수신 하는 SQL Server 데이터베이스를 호스트 합니다. 기기에서 별도로 구입 이며 기기 InfiniBand 네트워크에 연결 합니다.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: ed7122f497b0bdebd893eec75606bbb6382e9a73
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/19/2018
ms.locfileid: "31538773"
---
# <a name="configure-an-external-windows-system-to-receive-remote-table-copies-using-infiniband---parallel-data-warehouse"></a>InfiniBand-병렬 데이터 웨어하우스를 사용 하 여 원격 테이블 복사본을 받을 수는 외부 Windows 시스템 구성
구입 하 고 InfiniBand 네트워크를 사용 하 여 SQL Server PDW에서 원격 테이블 복사 기능과 함께 사용 하기 위해 연결 하는 비 어플라이언스 Windows 시스템을 구성 하는 방법을 설명 합니다. Windows 시스템 SQL Server PDW 데이터베이스에서 원격 테이블 복사본을 수신 하는 SQL Server 데이터베이스를 호스트 합니다. 기기에서 별도로 구입 이며 기기 InfiniBand 네트워크에 연결 합니다.  
  
> [!NOTE]  
> InfiniBand 네트워크를 통해 연결 하 여 원격 테이블 복사본을 사용 하는 것에 대 한 필요 하지 않습니다. 이더넷 대역폭 요구 사항을 충족 하는 경우 이더넷 네트워크를 통해 연결을 수행할 수 있습니다.  
  
이 항목에서는 원격 테이블 복사본을 구성 하기 위한 구성 단계 중 하나. 목록이 모든 구성 단계에 대 한 참조 [원격 테이블 복사](remote-table-copy.md)  
  
## <a name="before-you-begin"></a>시작하기 전에  
외부 Windows 시스템을 구성 하기 전에 다음을 수행 해야 합니다.  
  
1.  구입 하거나 원격 복사본을 받을 Windows 시스템을 제공 합니다.  
  
2.  (충분 한 공간이 있는 경우) Windows 시스템 제어 랙에 랙 또는 가까이에 어플라이언스에 기기 InfiniBand 네트워크에 연결할 수 있도록 합니다.  
  
3.  InfiniBand는 케이블과 InfiniBand 네트워크 어댑터를 사용 하는 어플라이언스 하드웨어 공급 업체 로부터 구입 합니다. 내보낸된 데이터를 받을 때 두 개의 포트 내결함성에 대 한 네트워크 어댑터를 구입 하는 것이 좋습니다. 두 개의 포트 네트워크 어댑터는 것이 좋지만 필요 하지 않습니다.  
  
## <a name="HowToWindows"></a>원격 테이블 복사본을 받을 수는 외부 Windows 시스템 구성  
외부 Windows 시스템을 구성 하려면 다음 단계를 사용 합니다.  
  
1.  Windows 시스템에 InfiniBand 네트워크 어댑터를 설치 합니다.  
  
2.  InfiniBand 케이블을 사용 하 여 제어 랙에 기본 InfiniBand 스위치에 InfiniBand 네트워크 어댑터를 연결 합니다.  
  
3.  설치 하 고 InfiniBand 네트워크 어댑터에 대 한 적절 한 Windows 드라이버를 구성 합니다.  
  
    Windows 용 드라이버 InfiniBand OpenFabrics Alliance 등의 InfiniBand 공급 업체는 업계 consortium에서 개발 됩니다.  올바른 드라이버 InfiniBand 어댑터와 함께 배포 될 수 있습니다. 그렇지 않으면 www.openfabrics.org에서 드라이버를 다운로드할 수 있습니다.  
  
4.  어댑터에서 각 포트에 대 한 IP 주소를 구성 합니다. SMP 시스템은이 목적을 위해 예약 된 주소 범위에서 고정 IP 주소를 사용 해야 합니다. 다음 매개 변수에 따라 첫 번째 포트를 구성 합니다.  
  
    -   IP 네트워크 주소: 172.16.132.x  
  
    -   IP 서브넷 마스크: 255.255.128.0  
  
    -   호스트 IP 범위: 1-254  
  
    두 개의 포트 InfiniBand 네트워크 어댑터에 대해 다음 매개 변수에 따라 두 번째 포트를 구성 합니다.  
  
    -   IP 네트워크 주소: 172.16.132.x  
  
    -   IP 서브넷 마스크: 255.255.128.0  
  
    -   호스트 IP 범위: 1-254  
  
5.  두 개의 포트 어댑터를 사용 하 고, 여러 외부 Windows 시스템에 연결 된 경우, 각 시스템 각 IP 서브넷 내의 다른 호스트 번호를 할당 합니다.  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
