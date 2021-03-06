---
title: SQL Server 2019 빅 데이터 클러스터 배포에 대 한 Azure Kubernetes Service를 구성 | Microsoft Docs
description: SQL Server 2019 빅 데이터 클러스터 (미리 보기) 배포에 대 한 Azure Kubernetes Service (AKS)를 구성 하는 방법에 알아봅니다.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 11/06/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 0eda19b4a241a066771afff1cfb682fa7234f81e
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51700408"
---
# <a name="configure-azure-kubernetes-service-for-sql-server-2019-preview-deployments"></a>SQL Server 2019 (미리 보기) 배포에 대 한 Azure Kubernetes Service 구성

이 문서에서는 SQL Server 2019 빅 데이터 클러스터 (미리 보기) 배포에 대 한 Azure Kubernetes Service (AKS)를 구성 하는 방법을 설명 합니다. 

AKS를 사용 하면 간단 하 게 생성, 구성 및 컨테이너 화 된 응용 프로그램을 실행 하는 Kubernetes 클러스터를 사용 하 여 미리 구성 된 가상 머신의 클러스터를 관리 합니다. 이 통해 배포 하 고 Microsoft Azure에서 컨테이너 기반 응용 프로그램 관리의 커뮤니티 전문 지식의 점점 본문을 하거나 기존 기술을 사용할 수 있습니다.

이 문서에서는 Azure CLI를 사용 하 여 AKS에서 Kubernetes를 배포 하는 단계를 설명 합니다. Azure 구독이 없으면 시작 하기 전에 무료 계정을 만듭니다.

> [!TIP] 
> AKS와 SQL Server 빅 데이터 클러스터를 배포 하는 샘플 python 스크립트를 참조 하세요 [빅 데이터 클러스터 Azure Kubernetes Service (AKS)에서 SQL Server 배포](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/aks)합니다.

## <a name="prerequisites"></a>필수 구성 요소

- 기본 시나리오 유효성 검사를 하는 동안 최적의 환경을 위해 AKS environment에 대 한 4 개 이상의 Vcpu 및 32GB의 메모리가 각 (마스터) 외에도 세 개 이상의 에이전트 Vm이 좋습니다. Vm에 대 한 여러 크기 옵션을 제공 하는 azure 인프라를 참조 하십시오 [여기](https://docs.microsoft.com/azure/virtual-machines/windows/sizes) 배포 하려는 지역에 대 한 선택 항목에 대 한 합니다.
  
- 이 섹션에서는 여야 합니다. Azure CLI 버전 2.0.4 실행 이상. 설치 또는 업그레이드를 참조 해야 하는 경우 [Azure CLI 2.0 설치](https://docs.microsoft.com/cli/azure/install-azure-cli)합니다. 실행 `az --version` 필요한 경우 버전을 찾으려고 합니다.

- 설치할 [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/) 1.10 버전 이상. Kubectl 클라이언트에 특정 버전을 설치 하려는 경우 참조 [curl을 통해 이진 kubectl 설치](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl)합니다. 

- Kubernetes 서버로 동일한 1.10 최소 버전 적용 됩니다. AKS를 사용 해야 `--kubernetes-version` 기본값과 다른 버전을 지정 하려면 매개 변수입니다.

> [!NOTE]
클라이언트/서버 버전 즉 기울이기는 + /-1 부 버전은 지원 합니다. Kubernetes 설명서 상태는 "클라이언트 마스터에서 둘 이상의 부 버전 불일치 해야 하지만 마스터 최대 1 개 부 버전에서 발생할 수 있습니다. 예를 들어 v1.3 마스터 v1.1, v1.2 및 v1.3 노드를 사용 하 여 작동 및 v1.2, v1.3, 및 v1.4 클라이언트를 사용 해야 합니다. " 자세한 내용은 [지원 되는 버전 및 구성 요소 기울이기 Kubernetes](https://github.com/kubernetes/community/blob/master/contributors/design-proposals/release/versioning.md#supported-releases-and-component-skew)합니다.

또한 `az aks kubernetes install-cli` 버전과 kubectl 클라이언트를 설치 하는 낮은 필요한 1.10 합니다. 올바른 버전의 kubectl 클라이언트를 설치 하는 지침은 위에 따릅니다.

## <a name="create-a-resource-group"></a>리소스 그룹 만들기

Azure 리소스 그룹은 Azure 리소스가 배포 및 관리 되는 논리적 그룹입니다. 다음 단계를 Azure에 로그인 하 고 AKS 클러스터에 대 한 리소스 그룹을 만듭니다.

> [!TIP]
> Windows를 사용 하는 경우 나머지 단계에 대해 PowerShell을 사용 합니다.

1. 명령 프롬프트에서 다음 명령을 실행 하 고 지시에 따라 Azure 구독에 로그인 합니다.

    ```bash
    az login
    ```

1. 여러 구독이 있는 경우 다음 명령을 실행 하 여 구독의 모든를 볼 수 있습니다.

   ```bash
   az account list
   ```

1. 다른 구독으로 변경 하려는 경우이 명령을 실행할 수 있습니다.

   ```bash
   az account set --subscription <subscription id>
   ```

1. 사용 하 여 리소스 그룹을 만들어야 합니다 **az 그룹 만들기** 명령입니다. 다음 예제에서는 명명 된 리소스 그룹을 만듭니다 `sqlbigdatagroup` 에 `westus2` 위치 합니다.

   ```bash
   az group create --name sqlbigdatagroup --location westus2
   ```

## <a name="create-a-kubernetes-cluster"></a>Kubernetes 클러스터 만들기

1. 사용 하 여 AKS에서 Kubernetes 클러스터 만들기는 [az aks 만들기](https://docs.microsoft.com/cli/azure/aks) 명령입니다. 다음 예제에서는 라는 Kubernetes 클러스터를 만듭니다 *kubcluster* 하나의 Linux 마스터 노드와 두 개의 Linux 에이전트 노드가 있습니다. 이전 섹션에서 사용한 동일한 리소스 그룹에서 AKS 클러스터를 만든 있는지 확인 합니다.

    ```bash
   az aks create --name kubcluster \
    --resource-group sqlbigdatagroup \
    --generate-ssh-keys \
    --node-vm-size Standard_E4s_v3 \
    --node-count 3 \
    --kubernetes-version 1.10.8
    ```

    늘리거나 변경 하 여 Kubernetes 에이전트 노드 수를 줄일 수는 `--node-count <n>` 여기서 `<n>` 입니다 하려는 에이전트 노드는 마스터 Kubernetes 노드는 포함 되지 않습니다. 되므로 위의 예에서 **4** 크기의 Vm **Standard_E4s_v3** AKS 클러스터에 사용 되는: **1** 마스터에 대 한 및 **3** 에 에이전트 노드입니다.

    몇 분 후 명령이 완료 되 고 클러스터에 대 한 JSON 형식 정보를 반환 합니다.

1. 나중에 사용할 이전 명령의 JSON 출력을 저장 합니다.

## <a name="connect-to-the-cluster"></a>클러스터에 연결

1. Kubernetes 클러스터에 연결 하도록 kubectl을 구성 하려면 다음을 실행 합니다 [az aks 자격 증명 가져오기](https://docs.microsoft.com/cli/azure/aks?view=azure-cli-latest#az-aks-get-credentials) 명령입니다. 이 단계는 자격 증명을 다운로드 하 고 kubectl CLI 사용을 구성 합니다.

   ```bash
   az aks get-credentials --resource-group=sqlbigdatagroup --name kubcluster
   ```

1. 클러스터에 대 한 연결을 확인 하려면 사용 합니다 [kubectl get](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands) 클러스터 노드의 목록을 반환 하는 명령입니다.  아래 예제에서는 출력을 보여 줍니다. 1 개 마스터 및 3 개의 에이전트 노드가 있는 경우.

   ```bash
   kubectl get nodes
   ```

## <a name="next-steps"></a>다음 단계

이 문서의 단계는 AKS에서 Kubernetes 클러스터를 구성합니다. SQL Server 2019 빅 데이터 클러스터에 배포 하려면 다음 단계가입니다.

[빠른 시작: Azure Kubernetes Service (AKS)에서 SQL Server 빅 데이터 클러스터 배포](quickstart-big-data-cluster-deploy.md)
