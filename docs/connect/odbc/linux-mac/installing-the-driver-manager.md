---
title: Installing the Driver Manager (ODBC Driver for SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 02/14/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Driver Manager, installing
ms.assetid: 7c4b6fb4-f45a-4973-adb9-a4d83f0a2a7a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b5ffb878e0d30ce7f905ce74647e8db8c2983501
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51605823"
---
# <a name="installing-the-driver-manager"></a>드라이버 관리자 설치
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

이 문서에서는 SQL Server Linux 및 macOS에 대 한 모든 버전의 Microsoft ODBC 드라이버를 사용 하 여 사용할 unixODBC 드라이버 관리자를 설치 하는 지침이 포함 되어 있습니다.  

> [!IMPORTANT]  
> unixODBC 드라이버 관리자를 설치하기 전에 컴퓨터에 설치된 드라이버 관리자 패키지를 삭제합니다. unixODBC 드라이버 관리자를 설치하면 기존 드라이버 관리자에 오류가 발생할 수 있습니다.  

## <a name="installing-the-driver-manager-for-microsoft-odbc-driver-13-131-and-17"></a>Microsoft ODBC Driver 13, 13.1 및 17용 드라이버 관리자 설치
드라이버 관리자 종속성은 자동으로 해결 패키지 관리 시스템에서의 지침에 따라 Microsoft ODBC Driver 13.1, 13, 17 for Linux 또는 macOS에서 SQL Server를 설치할 때 [Microsoft ODBC Driver 설치 SQL Server Linux 또는 macOS에 대 한](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)합니다. 

## <a name="installing-the-driver-manager-for-microsoft-odbc-driver-11-for-sql-server"></a>Microsoft ODBC Driver 11 for SQL Server용 드라이버 관리자 설치  

(SUSE 및 Red Hat Linux만 해당)

**설치 스크립트 사용**  
  
> [!IMPORTANT]  
> 이러한 지침은 Red Hat Linux용 설치 파일인 `msodbcsql-11.0.2270.0.tar.gz`를 참조합니다. SUSE Linux용 미리 보기를 설치하는 경우 파일 이름은 `msodbcsql-11.0.2260.0.tar.gz`입니다.  

드라이버 관리자를 설치하려면  
  
1.  루트 권한이 있는지 확인합니다.  
  
2.  [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ODBC Driver 다운로드가 `msodbcsql-11.0.2270.0.tar.gz`라는 파일을 배치한 디렉터리로 이동합니다. Linux 버전과 일치하는 \*.tar.gz 파일이 있는지 확인합니다. 파일을 추출하려면 **tar xvzf msodbcsql-11.0.2270.0.tar.gz** 명령을 실행합니다.  

3.  `msodbcsql-11.0.2270.0` 디렉터리로 변경하면 `build_dm.sh`라는 파일이 나타납니다. 실행할 수 있습니다 `build_dm.sh` unixODBC 드라이버 관리자를 설치 합니다.

4.  사용 가능한 옵션 목록을 보려면 **./build_dm.sh --help** 명령을 실행합니다.  
  
5.  설치 준비가 되고 컴퓨터가 FTP를 통해 외부 사이트에 액세스할 수 있는 경우 **./build_dm.sh** 명령을 실행합니다.

컴퓨터가 FTP를 통해 외부 사이트에 액세스할 수 없는 경우 `unixODBC-2.3.0.tar.gz`를 가져옵니다. 가져올 수 있습니다 `unixODBC-2.3.0.tar.gz` 에서 [ https://www.unixodbc.org ](https://www.unixodbc.org/)합니다. 페이지 왼쪽에서 다운로드** 링크를 클릭하여 다운로드 페이지로 이동합니다. 그런 다음 적절한 링크를 클릭하여 unixODBC-2.3.0(unixODBC-2.3.1 아님)을 다운로드합니다. unixODBC-2.3.1은 이 릴리스의 [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 지원되지 않습니다. UnixODBC 드라이버 관리자 설치를 시작 하려면 다음 명령을 실행 합니다. **./build_dm.sh --download-url=file://unixODBC-2.3.0.tar.gz**합니다.  

6.  **YES**를 입력하여 파일의 압축 해제를 진행합니다. 이 부분의 프로세스를 완료하려면 최대 5분까지 걸릴 수 있습니다.  

7.  스크립트가 실행을 중지한 후 화면의 지침을 따라 unixODBC 드라이버 관리자를 설치합니다.

이제 드라이버를 설치할 준비가 되었습니다. 자세한 내용은 [Microsoft ODBC Driver for SQL Server Linux 및 macOS 설치](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)합니다.  

**수동 설치**

설치 스크립트가 완료할 수 없는 경우 적절한 드라이버 관리자를 직접 구성하고 빌드합니다.

1.  이전에 설치된 unixODBC 버전(예: unixODBC 2.2.11)을 제거합니다. Red Hat Enterprise Linux 5 또는 6에서 **yum remove unixODBC** 명령을 실행합니다. SUSE Linux enterprise **zypper 제거 unixODBC**합니다.  
  
2.  [https://www.unixodbc.org](https://www.unixodbc.org/)으로 이동하여 페이지 왼쪽에서 **다운로드** 링크를 클릭하여 다운로드 페이지로 이동합니다. 그런 다음 적절한 링크를 클릭하여 unixODBC-2.3.0.tar.gz 파일을 컴퓨터에 저장합니다. UnixODBC-2.3.1은 이 릴리스의 [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 지원되지 않습니다.  
  
3.  Linux 컴퓨터에서 명령을 실행 합니다. **tar xvzf unixODBC-2.3.0.tar.gz**합니다.  
  
4.  unixODBC-2.3.0 디렉터리로 변경합니다.  
  
5.  명령 프롬프트에서 명령을 실행 합니다. **CPPFLAGS = "-DSIZEOF_LONG_INT 8 ="** 합니다.  
  
6.  명령 프롬프트에서 명령을 실행 합니다. **export CPPFLAGS**합니다.  
  
7.  명령 프롬프트에서 명령을 실행: **"./configure --prefix=/usr --libdir=/usr/lib64 --sysconfdir=/etc --enable-gui=no --enable-drivers=no --enable-iconv --with-iconv-char-enc=UTF8 --with-iconv-ucode-enc=UTF16LE"**.  
  
8.  명령 프롬프트(루트로 로그인)에서 **make** 명령을 실행합니다.  
  
9. 명령 프롬프트(루트로 로그인)에서 **make install** 명령을 실행합니다.  

이제 드라이버를 설치할 준비가 되었습니다. 자세한 내용은 [Microsoft ODBC Driver for SQL Server Linux 및 macOS 설치](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)합니다.  
  
## <a name="see-also"></a>참고 항목
[Linux 및 macOS 기반 SQL Server용 Microsoft ODBC Driver 설치](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)

[이 버전의 드라이버에서 알려진 문제](../../../connect/odbc/linux-mac/known-issues-in-this-version-of-the-driver.md)

[릴리스 정보](../../../connect/odbc/linux-mac/release-notes.md)
