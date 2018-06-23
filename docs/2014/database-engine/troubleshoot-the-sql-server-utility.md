---
title: SQL Server 유틸리티 문제 해결 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f5f47c2a-38ea-40f8-9767-9bc138d14453
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0bc94d8644d1a0015829b730d5556b967c6b8c93
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36092250"
---
# <a name="troubleshoot-the-sql-server-utility"></a>SQL Server 유틸리티 문제 해결
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 유틸리티 문제 해결에는 SQL Server 인스턴스를 UCP에 등록하는 작업의 실패 해결, UCP에서 관리되는 인스턴스 목록 뷰에 회색 아이콘으로 표시되는 실패한 데이터 수집 문제 해결, 성능 병목 현상 완화, 리소스 상태 문제 해결 등이 포함됩니다. 로 식별 되는 리소스 상태 문제를 완화 하는 방법에 대 한 자세한 내용은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] UCP 참조 [SQL Server 리소스 상태 문제를 해결 &#40;SQL Server 유틸리티&#41;](../relational-databases/manage/troubleshoot-sql-server-resource-health-sql-server-utility.md)합니다.  
  
## <a name="failed-operation-to-enroll-an-instance-of-sql-server-into-a-sql-server-utility"></a>SQL Server 유틸리티에 SQL Server 인스턴스를 등록하는 작업 실패  
 인스턴스에 연결 하는 경우 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 사용 하 여 등록할 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인증 및 UCP가 위치한 도메인이 아닌 다른 Active Directory 도메인에 속하는 프록시 계정을 지정 하면 인스턴스 유효성 검사는 성공 하지만 다음 오류 메시지와 함께 등록 작업이 실패합니다.  
  
 Transact-SQL 문 또는 일괄 처리를 실행하는 동안 예외가 발생했습니다. (Microsoft.SqlServer.ConnectionInfo)  
  
 추가 정보: Windows NT 그룹/사용자 '\<DomainName\AccountName>'에 대한 정보를 가져올 수 없습니다. 오류 코드 0x5. (Microsoft SQL Server, 오류: 15404)  
  
 이 문제는 다음과 같은 예제 시나리오에서 발생합니다.  
  
1.  UCP가 "Domain_1"의 멤버입니다.  
  
2.  단방향 도메인 트러스트 관계가 설정되어 있습니다. 즉, "Domain_2"는 "Domain_1"을 트러스트하지 않지만 "Domain_1"은 "Domain_2"를 트러스트합니다.  
  
3.  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 유틸리티에 등록할 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스도 "Domain_1"의 멤버입니다.  
  
4.  등록 작업 중 “sa”를 사용하여 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 연결하고 등록합니다. "Domain_2"의 프록시 계정을 지정합니다.  
  
5.  유효성 검사는 성공하지만 등록이 실패합니다.  
  
 위와 같은 예제에서 이 문제를 해결하는 방법은 “sa”를 사용하고 "Domain_1"의 프록시 계정을 제공하여 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 연결한 후 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 유틸리티에 등록하는 것입니다.  
  
## <a name="failed-wmi-validation"></a>WMI 유효성 검사 실패  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에서 WMI가 올바르게 구성되지 않을 경우 UCP 만들기 및 관리되는 인스턴스 등록 작업 시 경고가 표시되지만 작업이 중지되지는 않습니다. 또한 변경 하는 경우는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트 계정 구성을 있도록 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트가 필요한 WMI 클래스의 해당된 관리 되는 인스턴스에 대 한 데이터 수집에 대 한 권한을 갖지 못하게 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] UCP에 업로드 하려면 실패 합니다. 그러면 UCP에 회색 아이콘이 표시됩니다.  
  
 데이터 수집이 실패하면 해당 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 관리되는 인스턴스의 UCP 목록 뷰에 회색 상태 아이콘이 표시됩니다. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 관리되는 인스턴스의 작업 기록에는 sysutility_mi_collect_and_upload가 2단계(PowerShell 스크립트에서 수집된 단계 데이터)에서 실패했다고 표시됩니다.  
  
 이 경우 다음과 같은 오류 메시지만 출력됩니다.  
  
 셸 변수 "ErrorActionPreference"가 Stop: Access denied로 설정되어 있으므로 명령 실행이 중지되었습니다.  
  
 오류: \<날짜-시간 (MM/DD/YYYY h:mm: ss) >: cpu 속성을 수집 하는 동안 예외가 발생 했습니다.  WMI 쿼리가 실패했을 수 있습니다.  경고.  
  
 이 문제를 해결하려면 다음 구성 설정을 확인하십시오.///  
  
-   Windows Server 2003에서 SQL Server 에이전트 서비스의 관리 되는 인스턴스에서 성능 모니터링 하는 Windows 그룹의 일부 여야 합니다 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]합니다.  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 관리되는 인스턴스에서 WMI 서비스가 설정되고 구성되어 있어야 합니다.  
  
-   WMI 저장소의 관리 되는 인스턴스에서 손상 되었을 수 있습니다 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]합니다.  
  
-   누락 되거나 손상의 관리 되는 인스턴스에서 성능 라이브러리가 되었을 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]합니다.  
  
 지정된 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스가 UCP에 데이터를 보고하도록 올바르게 구성되어 있는지 확인하려면 다음 클래스를 지정된 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에서 사용할 수 있으며 SQL Server 에이전트 서비스 계정에서 액세스할 수 있는지 확인합니다.  
  
-   Win32_MountPoint  
  
-   Win32_PerfRawData_PerfProc_Process  
  
-   Win32_PerfRawData_PerfOS_Processor  
  
-   Win32_Processor  
  
-   Win32_Volume  
  
-   Win32_LogicalDisk  
  
 각 클래스의 Get-WmiObject PowerShell cmdlet을 사용하여 해당 클래스에 액세스할 수 있는지 확인할 수 있습니다. 관리 되는 인스턴스에서 다음 cmdlet을 실행 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:  
  
```  
Get-WmiObject Win32_MountPoint -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_PerfRawData_PerfProc_Process -ErrorAction Stop| Out-Null  
Get-WmiObject Win32_PerfRawData_PerfOS_Processor -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_Processor -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_Volume -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_LogicalDisk -ErrorAction Stop | Out-Null  
```  
  
 WMI 문제 해결에 대 한 자세한 내용은 참조 [WMI 문제 해결](http://go.microsoft.com/fwlink/?LinkId=178250)합니다. 이러한 SQL Server 유틸리티 작업의 쿼리는 로컬로 실행할 수 있으므로 DCOM 및 원격 문제 해결 정보에는 영향을 주지 않습니다.  
  
## <a name="failed-data-collection"></a>데이터 수집 실패  
 경우 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 유틸리티 데이터 수집 이벤트가 실패 하면 다음 가능성을 고려 하십시오.  
  
-   관리되는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]인스턴스에 있는 "유틸리티 정보" 컬렉션 집합의 속성은 변경하면 안 되며, 데이터 컬렉션은 유틸리티 에이전트 작업에 의해 제어되므로 데이터 컬렉션을 수동으로 설정/해제하면 안 됩니다.  
  
-   WMI 유효성 검사가 실패했거나 지원되지 않는지 확인합니다. 자세한 내용은 이 항목 앞부분의 "WMI 유효성 검사 실패" 섹션을 참조하십시오.  
  
-   관리 되는 인스턴스 목록 보기에는 데이터의 데이터를 새로 고칩니다 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 유틸리티 뷰포인트는 자동으로 새로 고쳐지지 않습니다. 데이터를 새로 고치려면 마우스 오른쪽 단추로 클릭는 **관리 되는 인스턴스** 에서 노드는 **유틸리티 탐색기 탐색** 창에서 다음을 선택 **새로 고침**, 마우스 오른쪽 단추로 클릭 하거나는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스 목록 보기에서 이름을 선택한 다음 선택 **새로 고침**합니다. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 UCP를 등록한 후에 최대 30분이 지나야 유틸리티 탐색기 내용 창의 대시보드와 뷰포인트에 데이터가 표시되기 시작합니다.  
  
-   인스턴스를 확인 하려면 SQL Server 구성 관리자를 사용 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 실행 되 고 있습니다.  
  
-   데이터 수집 또는 데이터 업로드 작업이 제한 시간 문제로 인해 실패하면 MSDB 데이터베이스에서 dbo.fn_sysutility_mi_get_collect_script() 함수를 업데이트합니다. 특히 "Invoke-BulkCopyCommand()" 함수에 아래 줄을 추가합니다.  
  
    ```  
    $bulkCopy.BulkCopyTimeout=180  
    ```  
  
     기본 제한 시간 값은 30초입니다.  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스가 클러스터링되지 않은 경우 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트 서비스가 실행 중이고 이 서비스가 UCP와 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 관리되는 인스턴스에서 자동으로 시작되도록 설정되어 있는지 확인합니다.  
  
-   관리 되는 인스턴스에서 데이터 수집을 실행 하는 유효한 계정이 사용 되 고 있는지 확인 하십시오. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]합니다. 예를 들어 암호가 만료되었을 수 있습니다. 프록시 암호가 만료된 경우 다음과 같이 SSMS에서 암호 자격 증명을 업데이트합니다.  
  
    1.  SSMS **개체 탐색기**에서 **보안** 노드를 확장한 다음 **자격 증명** 노드를 확장합니다.  
  
    2.  마우스 오른쪽 단추로 클릭 **UtilityAgentProxyCredential_\<GUID >** 선택 **속성**합니다.  
  
    3.  자격 증명 속성 대화 상자에서 필요에 따라 자격 증명을 업데이트는 **UtilityAgentProxyCredential_\<GUID >** 자격 증명입니다.  
  
    4.  **확인** 을 클릭하여 변경 내용을 확인합니다.  
  
-   관리 되는 인스턴스 및 UCP에서 TCP/IP를 사용할지 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]합니다. TCP/IP를 설정 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 구성 관리자.  
  
-   UCP에서 SQL Server Browser 서비스가 시작되어야 하며 자동으로 시작하도록 구성되어 있어야 합니다. 조직에서 SQL Server Browser 서비스 사용을 금지하는 경우 다음 단계를 사용하여 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 관리되는 인스턴스가 UCP에 연결하는 것을 허용하십시오.  
  
    1.  관리 되는 인스턴스에서 Windows 작업 표시줄에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], 클릭 **시작**, 클릭 **실행...** .  
  
    2.  입력란에 "cliconfg.exe"를 입력하고 **확인**을 클릭합니다.  
  
    3.  "SQL 클라이언트 구성 유틸리티 EXE"를 시작하도록 허용하라는 메시지가 표시되면 "**계속**"을 클릭합니다.  
  
    4.  **SQL Server 클라이언트 네트워크 유틸리티** 대화 상자에서 **별칭** 탭을 선택하고 **추가…** 를 클릭합니다.  
  
    5.  **네트워크 라이브러리 구성 추가** 대화 상자에서 다음을 수행합니다.  
  
    6.  네트워크 라이브러리 목록에서 TCP/IP를 지정합니다.  
  
    7.  UCP의 **서버 별칭** 입력란에 ComputerName\InstanceName을 지정합니다.  
  
    8.  UCP의 **서버 이름** 입력란에 ComputerName을 지정합니다.  
  
    9. **동적으로 포트 확인** 확인란의 선택을 취소합니다.  
  
    10. **포트 번호** 입력란에 UCP가 수신하는 포트 번호를 지정합니다.  
  
    11. **확인** 을 클릭하여 변경 내용을 저장합니다.  
  
    12. 관리 되는 각 인스턴스에 대해 이러한 단계를 반복 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 하는 SQL Server Browser 서비스가 해제 되어 없는 UCP에 연결 합니다.  
  
-   확인 하는 관리 되는 인스턴스가 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 네트워크에 연결 합니다.  
  
-   이름은 같지만 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 관리되는 인스턴스의 대/소문자 설정이 다른 데이터베이스가 있는 경우 데이터베이스와 해당 뷰포인트 간의 식별이 잘못되어 데이터 수집이 실패할 수 있습니다. 예를 들어 "MYDATABASE"라는 데이터베이스가 "MyDatabase"라는 데이터베이스의 상태를 보여 줄 수 있습니다. 이 시나리오에서는 오류가 발생하지 않습니다. 또한 UCP에 표시되는 다른 객체에서 데이터베이스 파일 및 파일 그룹 이름 등의 대/소문자가 일치하지 않아 데이터 수집이 실패할 수도 있습니다.  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 관리되는 인스턴스가 Windows Server 2003 컴퓨터에서 호스팅되는 경우 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트 서비스 계정이 성능 모니터 사용자 보안 그룹이나 로컬 관리자 그룹에 속해야 합니다. 그렇지 않으면 액세스 거부 오류가 발생하고 데이터베이스 수집이 실패합니다. 추가 하는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트 서비스 계정을 성능 모니터 사용자 보안 그룹에는 다음 단계를 따르십시오.  
  
    1.  **컴퓨터 관리**, **로컬 사용자 및 그룹**, **그룹**을 차례로 엽니다.  
  
    2.  **성능 모니터 사용자** 를 마우스 오른쪽 단추로 클릭하고 **그룹에 추가**를 선택합니다.  
  
    3.  **추가**를 클릭합니다.  
  
    4.  SQL Server 에이전트 서비스가 실행되고 있는 계정을 입력하고 **확인**을 클릭합니다.  
  
    5.  사용자를 이 그룹에 추가하기 전에 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 이미 UCP가 등록된 경우 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트 서비스를 다시 시작합니다.  
  
## <a name="see-also"></a>관련 항목  
 [SQL Server 유틸리티 기능 및 태스크](../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [SQL Server 리소스 상태 문제 해결&#40;SQL Server 유틸리티&#41;](../relational-databases/manage/troubleshoot-sql-server-resource-health-sql-server-utility.md)  
  
  