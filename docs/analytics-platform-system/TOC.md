# 이 릴리스에 대한 정보
## [새로운 기능](whats-new-analytics-platform-system.md)

# Architecture
## [병렬 데이터 웨어하우스 개요](parallel-data-warehouse-overview.md)
## [하드웨어 구성 요소](hardware-components.md)
## [하드웨어 구성](hardware-configurations.md)
## [처리 및 저장소 용량](processing-and-storage-capacity-planning.md)
## [고가용성](high-availability.md)

# 하드웨어 백업 및 로드
## [개요](backup-and-loading-hardware.md)
## [로드 서버 획득 및 구성](acquire-and-configure-loading-server.md)
## [로드 서버 용량 계획 워크시트](loading-server-capacity-planning-worksheet.md)
## [백업 서버 획득 및 구성](acquire-and-configure-backup-server.md)
## [백업 서버 용량 계획 워크시트](backup-capacity-planning-worksheet.md)
## [InfiniBand 네트워크 어댑터 구성](configure-infiniband-network-adapters.md)

# Query
## [활성 쿼리 모니터링](monitoring-active-queries.md)

# 로드
## [개요](load-overview.md)
## [준비 데이터베이스 만들기](staging-database.md)
## [Integration Services를 사용하여 로드](load-with-ssis.md)
## [PDW 대상 어댑터를 사용하는 Integration Services 스크립트 작업 만들기](create-ssis-script-task-using-pdw-destination-adapter.md)
## [dwloader의 데이터 형식 변환 규칙](dwloader-data-type-conversion-rules.md)
## [INSERT를 사용하여 데이터 로드](load-with-insert.md)
## [dwloader 명령줄 로드 도구](dwloader.md)
## [로드 모니터링](monitor-loads.md)

# 데이터베이스 관리
## Backup 및 Restore 메서드
### [개요](backup-and-restore-overview.md)
### [TDE로 보호되는 데이터베이스 복원](restore-database-protected-by-tde.md)
## [PDW 권한](pdw-permissions.md)
### [사용 권한 부여](grant-permissions.md)
## [오류 메시지](error-messages.md)
## [잠금 동작](locking-behavior.md)
## [원격 테이블 복사](remote-table-copy.md)
### [InfiniBand를 사용하여 원격 테이블 복사본을 받도록 외부 Windows 시스템 구성](configure-an-external-windows-system-to-receive-remote-table-copies-using-infiniband.md)
### [원격 테이블 복사본을 받도록 외부 SMP SQL Server 구성](configure-an-external-smp-sql-server-to-receive-remote-table-copies.md)
### [원격 테이블 복사본에 대해 SQL Server PDW 구성](configure-sql-server-pdw-for-remote-table-copies.md)
## [시스템 데이터베이스](system-databases.md)
### [예약된 데이터베이스 이름](reserved-database-names.md)
### [tempdb 데이터베이스](tempdb-database.md)
### [master 데이터베이스](master-database.md)
## [사용자 세션](user-sessions.md)
## [워크로드 관리](workload-management.md)
### [워크로드 관리 작업](workload-management-tasks.md)

# 보안
## [투명한 데이터 암호화](transparent-data-encryption.md)
## [인증서 프로비전](provision-certificate.md)

# [어플라이언스 관리 작업](appliance-management-tasks.md)
## [어플라이언스 설치 및 구성 개요](appliance-installation-and-configuration-overview.md)
### [IHV에서 가져올 정보](information-to-obtain-from-your-ihv.md)
### [하드웨어 설치](hardware-installation.md)
## [어플라이언스 노드에 연결](connect-to-appliance-nodes.md)
## [바이러스 백신 소프트웨어](antivirus-software.md)
## [어플라이언스 구성](appliance-configuration.md)
### [PDW 및 어플라이언스 패브릭 물리적 구성 요소](pdw-and-appliance-fabric-physical-components.md)
### [Configuration Manager 시작](launch-the-configuration-manager.md)
### [어플라이언스 토폴로지](appliance-topology.md)
### [암호 재설정](password-reset.md)
### [어플라이언스 표준 시간대 구성](appliance-time-zone-configuration.md)
### [어플라이언스 네트워크 구성](appliance-network-configuration.md)
### [PDW 토폴로지](pdw-topology.md)
### [PDW 인증서 프로비전](pdw-certificate-provisioning.md)
### [PDW 방화벽 구성](pdw-firewall-configuration.md)
### [PDW 서비스 상태](pdw-services-status.md)
### [즉시 파일 초기화 구성](instant-file-initialization-configuration.md)
### [master 데이터베이스 복원](restore-the-master-database.md)
### [DSRM(Directory Services Restore Mode)의 AD 노드에 로그온하는 관리자 암호 설정](set-admin-password-for-logging-on-to-ad-nodes-in-directory-services-restore-mode.md)
### [Windows Server Update Services 구성](configure-windows-server-update-services-wsus.md)
### [외부 데이터에 대한 PolyBase 연결 구성](configure-polybase-connectivity-to-external-data.md)
### [DNS 전달자를 사용하여 비 어플라이언스 DNS 이름 확인](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md)
### [APS 도메인 관리자 만들기](create-an-aps-domain-administrator-aps.md)
### [Microsoft에 원격 분석 피드백 보내기](send-telemetry-feedback-to-microsoft-sql-server-pdw.md)
## [소프트웨어 서비스](software-servicing.md)
### [Microsoft 업데이트 다운로드 및 적용](download-and-apply-microsoft-updates.md)
### [Microsoft Update 제거](uninstall-microsoft-updates.md)
### [Analytics Platform System 핫픽스 적용](apply-analytics-platform-system-hotfixes.md)
### [Analytics Platform System 핫픽스 제거](uninstall-analytics-platform-system-hotfixes.md)
## [APS 어플라이언스 켜기 또는 끄기](power-the-aps-appliance-on-or-off.md)
## [어플라이언스 모니터링](appliance-monitoring.md)
### [관리 콘솔을 사용하여 어플라이언스 모니터링](monitor-the-appliance-by-using-the-admin-console.md)
### [시스템 뷰를 사용하여 어플라이언스 모니터링](monitor-the-appliance-by-using-system-views.md)
### [System Center Operations Manager를 사용하여 어플라이언스 모니터링](monitor-the-appliance-by-using-system-center-operations-manager.md)
#### [SCOM 관리 팩 설치](install-the-scom-management-packs.md)
#### [PDW용 SCOM 관리 팩 가져오기](import-the-scom-management-pack-for-pdw.md)
#### [Analytics Platform System을 모니터링하도록 SCOM 구성](configure-scom-to-monitor-analytics-platform-system.md)
### [어플라이언스 성능 상태 모니터링](monitor-appliance-health-state.md)
### [어플라이언스 경고 추적](track-appliance-alerts.md)
### [용량 사용률 보기](view-capacity-utilization.md)
### [폴링 주기 확인](determine-polling-frequency.md)
### [오류가 발생한 클러스터 노드 확인](determine-which-cluster-node-failed.md)
### [관리 콘솔 경고의 이해](understanding-admin-console-alerts.md)

# 참조
## [T-SQL 언어 요소](tsql-language-elements.md)
## [T-SQL 문](tsql-statements.md)
## [T-SQL 시스템 뷰](tsql-system-views.md) 