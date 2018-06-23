---
title: SQL Server 가져오기 및 내보내기 마법사 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- exporting data
- mapping files [Integration Services]
- SQL Server Import and Export Wizard
- SSIS packages, creating
- packages [Integration Services], copying
- Integration Services packages, creating
- packages [Integration Services], creating
- SQL Server Integration Services packages, creating
- Import and Export Wizard
- copying data [Integration Services]
- importing data, SSIS packages
- sources [Integration Services], copying data
ms.assetid: c0e4d867-b2a9-4b2a-844b-2fe45be88f81
caps.latest.revision: 87
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 3e320ff0fdb834ca242739a76fb9e0b1242e3579
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36183067"
---
# <a name="sql-server-import-and-export-wizard"></a>SQL Server 가져오기 및 내보내기 마법사
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사를 만드는 가장 간단한 방법을 제공는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 원본에서 데이터를 대상으로 복사 하는 패키지입니다.  
  
> [!NOTE]  
>  64비트 컴퓨터의 경우 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에서는 64비트 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사(DTSWizard.exe)를 설치합니다. 그러나 Access 또는 Excel 등의 일부 데이터 원본은 32비트 공급자만 제공합니다. 이러한 데이터 원본을 사용하려면 32비트 버전의 마법사를 설치하여 실행해야 합니다. 마법사의 32 비트 버전을 설치 하려면 클라이언트 도구를 선택 하거나 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 설치 중입니다.  
  
 시작 메뉴, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 명령 프롬프트에서 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 가져오기 및 내보내기 마법사를 시작할 수 있습니다. 자세한 내용은 참조 [SQL Server 가져오기 및 내보내기 마법사](start-the-sql-server-import-and-export-wizard.md)합니다.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사에서에서 복사할 수 데이터를 모든 데이터 소스를 관리 되는 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 데이터 공급자 또는 네이티브 OLE DB 공급자를 사용할 수 있습니다. 사용 가능한 공급자 목록에는 다음 데이터 원본이 포함됩니다.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   플랫 파일  
  
-   Microsoft Office Access  
  
-   Microsoft Office Excel  
  
 일부 마법사 기능은 마법사를 시작하는 환경에 따라 다르게 작동합니다.  
  
-   시작 하는 경우는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 선택 하 여 패키지를 즉시 실행 하는 **즉시 실행** 확인란 합니다. 기본적으로 이 확인란이 선택되어 있으므로 패키지가 즉시 실행됩니다.  
  
     패키지를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 저장할지, 아니면 파일 시스템에 저장할지를 결정할 수도 있습니다. 패키지를 저장하도록 선택할 경우에는 패키지 보호 수준도 지정해야 합니다. 패키지 보호 수준에 대 한 자세한 내용은 참조 [Access Control for Sensitive Data in Packages](../security/access-control-for-sensitive-data-in-packages.md)합니다.  
  
     이후에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사가 패키지를 만들고 데이터를 복사를 사용할 수 있습니다는 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 열고 태스크, 변환 및 이벤트 기반 논리를 추가 하 여 저장 된 패키지를 변경 합니다.  
  
    > [!NOTE]  
    >  [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], 마법사로 만든 패키지를 저장 하는 옵션이 제공 되지 않습니다.  
  
-   시작 하는 경우는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사에서는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트에서 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], 패키지 마법사 완료의 일환으로 실행할 수 없습니다. 대신 마법사를 시작한 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트에 패키지가 추가됩니다. 그런 다음 패키지를 실행하거나 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 태스크, 변환 및 이벤트 기반 논리를 추가하여 패키지를 확장할 수 있습니다.  
  
 자세한 내용은 참조 [SQL Server 가져오기 및 내보내기 마법사](start-the-sql-server-import-and-export-wizard.md)합니다.  
  
## <a name="permissions-required-by-the-import-and-export-wizard"></a>가져오기 및 내보내기 마법사에 필요한 권한  
 완료 하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사 성공적으로 적어도 다음 권한이 있어야 합니다.  
  
-   원본 및 대상 데이터베이스나 파일 공유에 연결할 수 있는 권한. [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], 서버 및 데이터베이스 로그인 권한이 필요 합니다.  
  
-   원본 데이터베이스나 파일의 데이터를 읽을 수 있는 권한. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], 원본 테이블 및 보기에 대 한 SELECT 권한이 필요 합니다.  
  
-   대상 데이터베이스나 파일에 데이터를 쓸 수 있는 권한. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], 대상 테이블에 대 한 INSERT 권한이 필요 합니다.  
  
-   새 대상 데이터베이스나 테이블 또는 파일을 만들려는 경우 새 데이터베이스나 테이블 또는 파일을 만들 수 있는 권한. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 CREATE DATABASE 또는 CREATE TABLE 권한이 필요합니다.  
  
-   Msdb 데이터베이스 또는 파일 시스템에 쓸 수 있는 권한 마법사로 만든 패키지를 저장 하려는 경우 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], msdb 데이터베이스에 대 한 INSERT 권한이 필요 합니다.  
  
## <a name="mapping-data-types-in-the-import-and-export-wizard"></a>가져오기 및 내보내기 마법사에서 데이터 형식 매핑  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사는 최소한의 변환 기능을 제공 합니다. 새로운 대상 테이블 및 파일에서 열의 이름, 데이터 형식 및 데이터 형식 속성을 설정하는 것 이외의 열 수준 변환은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사에서 지원되지 않습니다.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사는 매핑을 사용 하는 파일만 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 다른 한 데이터베이스 버전 또는 시스템에서 데이터 유형을 매핑하기 위해 제공 합니다. 예를 들어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 Oracle로 매핑할 수 있습니다. XML 형식의 매핑 파일은 기본적으로 C:\Program Files\Microsoft SQL Server\100\DTS\MappingFiles에 설치됩니다. 비즈니스에서 데이터 형식 간에 다른 매핑을 필요로 하는 경우 매핑을 업데이트하여 마법사가 수행하는 매핑에 적용할 수 있습니다. 예를 들어, 원하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **nchar** 데이터 형식에 매핑되도록 db2 **그래픽** 데이터 형식 대신 DB2 **VARGRAPHIC** 데이터 형식에서 데이터를 전송할 때 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 변경 DB2에 **nchar** 사용 하려면 SqlClientToIBMDB2.xml 매핑 파일의 매핑 **그래픽** 대신 **VARGRAPHIC 합니다.**  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에는 가장 일반적으로 사용되는 원본과 대상 조합 간 매핑이 포함되어 있으므로 새 매핑 파일을 Mapping Files 디렉터리에 추가하여 추가 원본 및 대상을 지원할 수 있습니다. 새 매핑 파일은 게시된 XSD 스키마를 따라야 하며 원본과 대상의 고유한 조합 간에 매핑해야 합니다.  
  
> [!NOTE]  
>  기존 매핑 파일을 편집 하거나 폴더에 새 매핑 파일을 추가할 경우 해야 닫았다가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사 또는 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 인식 되도록 하려면 새롭거나 변경 된 파일에 대 한 합니다.  
  
## <a name="external-resources"></a>외부 리소스  
  
-   비디오, [(SQL Server 비디오) SQL Server 데이터 내보내기](http://go.microsoft.com/fwlink/?LinkID=200975), technet.microsoft.com  
  
-   CodePlex 샘플 [ODBC에서 사용 하 여 플랫 파일 마법사 내보내기 자습서: 단원 패키지](http://go.microsoft.com/fwlink/?LinkId=217657), msftisprodsamples.codeplex.com  
  
  