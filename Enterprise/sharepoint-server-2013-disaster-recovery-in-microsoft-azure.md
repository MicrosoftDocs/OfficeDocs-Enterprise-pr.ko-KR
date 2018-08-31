---
title: Microsoft Azure에서 SharePoint Server 2013 재해 복구
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 04/17/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Deployment
ms.assetid: e9d14cb2-ff28-4a18-a444-cebf891880ea
description: '요약: Azure를 사용 하 여 온-프레미스 SharePoint 팜에 대 한 재해 복구 환경을 만들 수 있습니다. 이 문서에서는 디자인 하 고이 솔루션을 구현 하는 방법에 설명 합니다.'
ms.openlocfilehash: 56d9fa039bfe533afbc5ac7c1e060d43c0801aef
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915803"
---
# <a name="sharepoint-server-2013-disaster-recovery-in-microsoft-azure"></a>Microsoft Azure에서 SharePoint Server 2013 재해 복구

 **요약:** Azure를 사용 하 여 온-프레미스 SharePoint 팜에 대 한 재해 복구 환경을 만들 수 있습니다. 이 문서에서는 디자인 하 고이 솔루션을 구현 하는 방법에 설명 합니다.

 **SharePoint Server 2013 재해 복구 개요 비디오를 보기**
> [!VIDEO https://www.microsoft.com/videoplayer/embed/1b73ec8f-29bd-44eb-aa3a-f7932784bfd9?autoplay=false]
  
 재난이 발생 한 SharePoint 온-프레미스 환경의 경우 시스템을 신속 하 게 다시 실행 하 여 가장 높은 우선순위가 됩니다. Microsoft Azure에서 이미 실행 되 고 백업 환경을 사용 하는 경우 SharePoint 사용 하 여 재해 복구는 빠르고 쉽게 수행할 수 있습니다. 이 비디오는 SharePoint 웜 장애 조치 환경의 주요 개념에 설명 하 고 전체 자세한 내용은이 문서에서 사용할 수 있는 기능을 보완 합니다.
  
이 문서를 사용 하 여 다음과 같은 솔루션 모델: **Microsoft Azure의 SharePoint 재해 복구**합니다.
  
[![Azure에 대한 SharePoint 재해 복구 프로세스](media/SP-DR-Azure.png)](https://go.microsoft.com/fwlink/p/?LinkId=392555)
  
 [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555) |  [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554)
  
이 문서의 내용
  
- [재해 복구를 위한 Azure 인프라 서비스를 사용 하 여](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#AZ)
    
- [솔루션 설명](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#SOL)
    
- [자세한 아키텍처](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#arch)
    
- [재해 복구 로드맵](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#RDmap)
    
- [1 단계: 디자인 재해 복구 환경](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase1)
    
- [단계 2: Azure 가상 네트워크 및 VPN 연결 만들기](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase2)
    
- [Azure 가상 네트워크를 Active Directory 및 도메인 이름 서비스를 배포 하는 3 단계:](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase3)
    
- [4 단계: Azure의 SharePoint 복구 팜 배포](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase4)
    
- [5 단계: 팜 간에 DFSR를 설정 합니다.](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase5)
    
- [단계 6: 로그 복구 팜으로 전달 설정](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase6)
    
- [단계 7: 장애 조치 및 복구의 유효성을 검사합니다](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase7)
    
- [Microsoft 개념 증명 환경](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#POC)
    
- [문제 해결 팁](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Troubleshooting)
    
## <a name="use-azure-infrastructure-services-for-disaster-recovery"></a>재해 복구를 위한 Azure 인프라 서비스를 사용 하 여

대부분의 조직에서는 하지 않은 재해 복구 환경 sharepoint, 구축 및 온-프레미스를 유지 관리 비용이 매우 많이 값일 수 있습니다. Azure 인프라 서비스 주목할 옵션에 대 한 재해 복구 환경에 더욱 유연 하 고 온-프레미스 대안 보다 저렴을 제공 합니다.
  
Azure 인프라 서비스를 사용 하는 경우의 이점은 다음과 같습니다.
  
- **더 적은 비용이 많이 드는 리소스** 유지 관리 하 고 온-프레미스 재해 복구 환경에 비해 더 적은 리소스에 대 한 지불 합니다. 자원 수 선택 어떤 재해 복구 환경에 따라 달라 집니다: 정지 대기, 웜 대기 또는 핫 대기 합니다.
    
- **더 나은 리소스 유연성** 재해 발생 시 쉽게 팜을 수평 확장할 복구 SharePoint 부하 요구 사항을 충족 합니다. 리소스에는 필요 없는 경우의 수직 확장 합니다.
    
- **낮은 데이터 센터의 참여** Azure 인프라 서비스를 사용 하 여 서로 다른 영역에 보조 데이터 센터에 투자 하는 대신 합니다.
    
시작 재해 복구와 조직에 대 한 덜 복잡 한 옵션 및 고급 높은 복구 요구 사항이 조직에 대 한 옵션입니다. 정지, 웜, 및 핫 대기 환경에 대 한 정의 클라우드 플랫폼에서 호스팅되는 환경 때 약간 달라 집니다. 다음 표에서에 Azure의 SharePoint 복구 팜 만들기 (영문)에 대 한 이러한 환경에 설명 합니다.
  
**표: 복구 환경**

|**복구 환경 유형**|**설명**|
|:-----|:-----|
|핫  <br/> |완벽 하 게 한 크기의 팜을 프로 비전 된, 대기 모드에서 실행 되 고, 업데이트 된 됩니다.  <br/> |
|웜  <br/> |팜을 작성 하 고 가상 컴퓨터가 실행 중 이며 업데이트 된 합니다.  <br/> 콘텐츠 데이터베이스를 연결, 서비스 응용 프로그램을 구축 하 고 콘텐츠를 크롤링할 복구를 포함 합니다.  <br/> 팜에는 프로덕션 팜에 보다 작은 버전일 수 및 사용자층에 전체 수평 확장 합니다.  <br/> |
|콜드  <br/> |팜의 완벽 하 게, 작성 되었지만 가상 컴퓨터를 중지 합니다.  <br/> 유지 관리 하는 환경 때때로 가상 컴퓨터를 시작, 패치, 업데이트 및 환경 확인 (영문)를 포함 합니다.  <br/> 재해 발생 시 전체 환경을 다시 시작 합니다.  <br/> |
   
것은 조직의 복구 시간 목표 (RTOs) 및 복구 지점 목표 (RPOs)를 평가 하는 것이 중요 합니다. 이러한 요구 사항이 있는 환경 조직에 가장 적합 한 투자를 결정 합니다.
  
이 문서의 지침에서는 웜 대기 환경 구현 하는 방법에 설명 합니다. 또한 해당를 직접 적용할 수 콜드 대기 환경 환경의이 종류를 지원 하기 위해 추가 절차에 따라 필요는 없지만 합니다. 이 문서는 상시 대기 환경 구현 하는 방법을 설명 하지 않습니다.
  
재해 복구 솔루션에 대 한 자세한 내용은 [고가용성 및 재해 복구 개념에 SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkID=393114) 및 [SharePoint 2013에 대 한 재해 복구 전략 선택](https://go.microsoft.com/fwlink/p/?linkid=203228)을 참조 하십시오.
  
## <a name="solution-description"></a>솔루션 설명

웜 대기 재해 복구 솔루션에는 다음과 같은 환경을 해야합니다.
  
- 온-프레미스 SharePoint 프로덕션 팜
    
- Azure의 복구 SharePoint 팜
    
- 두 환경 간에 사이트 마다 VPN 연결
    
다음 그림에서는 이러한 세 요소를 보여줍니다.
  
**그림: Azure의 웜 대기 솔루션 요소**

![Azure의 SharePoint 웜 대기 솔루션 요소](media/AZarch-AZWarmStndby.png)
  
SQL Server 로그 전달 분산 파일 시스템 복제 (DFSR)와 Azure에서 복구 팜에 데이터베이스 백업과 트랜잭션 로그를 복사를 사용 합니다. 
  
- DFSR 복구 환경에 프로덕션 환경에서 로그를 전송합니다. WAN 시나리오에서는 DFSR Azure에서 직접 보조 서버로 로그를 전달 하는 보다 더 효율적입니다.
    
- Azure에서 복구 환경에서 SQL Server에 로그 재생 됩니다.
    
- 복구 작업이 수행 될 때까지 로그 전달 SharePoint 콘텐츠 데이터베이스 복구 환경에서를 연결 하지 않습니다.
    
팜 복구 하려면 다음 단계를 수행 합니다.
  
1. 로그 전달을 중지 합니다.
    
2. 기본 팜에 대 한 트래픽이 수락을 중지 합니다.
    
3. 마지막 트랜잭션 로그를 재생 합니다.
    
4. 콘텐츠 데이터베이스를 팜에 연결 합니다.
    
5. 복제 된 서비스 데이터베이스에서 서비스 응용 프로그램을 복원 합니다.
    
6. 복구 팜을 가리키도록 시스템 DNS (Domain Name) 레코드를 업데이트 합니다.
    
7. 전체 크롤링을 시작 합니다.
    
다음이 단계를 정기적으로 예행 연습 하 고 라이브 복구에 원활 하 게 실행 되는지 확인 하는 데 도움이 되도록 문서화 하는 것이 좋습니다. 콘텐츠 데이터베이스를 연결 하 고 서비스 응용 프로그램을 복원 다소 시간이 걸릴 수 및 일반적으로 일부 수동 구성을 수행 해야 합니다.
  
복구를 수행한 후이 솔루션은 다음 표에 나열 된 항목을 제공 합니다.
  
**표: 솔루션 복구 목표**

|**항목**|**설명**|
|:-----|:-----|
|사이트 및 콘텐츠  <br/> |사이트 및 콘텐츠 복구 환경에서 사용할 수 있습니다.  <br/> |
|검색의 새 인스턴스를  <br/> |이 웜 대기 솔루션에서 검색 검색 데이터베이스에서 복원 되지 않습니다. 복구 팜의 검색 구성 요소는 프로덕션 팜으로 최대한 비슷하게으로 구성 됩니다. 사이트 및 콘텐츠를 복원 후 검색 인덱스를 다시 작성 하려면 전체 크롤링 시작 됩니다. 사이트 및 콘텐츠를 사용할 수 있도록 설정 하기 위해 완료 하 고 탐색에 대 한 기다릴 필요가 없습니다.  <br/> |
|서비스  <br/> | 서비스 데이터베이스에 데이터를 저장 하는 로그 전달 데이터베이스에서 복원 됩니다. 데이터베이스에 데이터를 저장 하지 않도록 하는 서비스가 시작 하면 됩니다. <br/>  일부 서비스 데이터베이스를 복원 해야 합니다. 다음 서비스 데이터베이스에서 복원할 필요 하지 않으며 장애 조치 후 단순히 시작 될 수 있습니다. <br/>  Usage and Health Data Collection <br/>  State Service <br/>  Word 자동화 <br/>  데이터베이스를 사용 하지 않는 다른 서비스 <br/> |
   
더 복잡 한 복구 목표를 해결 하는 Microsoft Consulting Services (MCS) 또는 파트너를 사용 하 여 작업할 수 있습니다. 이 다음 표에 요약 되어있습니다.
  
**표: 기타 항목 MCS 또는 파트너 하 여 해결할 수 있는**

|**항목**|**설명**|
|:-----|:-----|
|사용자 지정 팜 솔루션 동기화 (영문)  <br/> |원칙적으로 복구 팜 구성은 프로덕션 팜으로 동일 합니다. 사용자 지정 팜 솔루션은 복제 되므로 여부와 동기화 하는 두 환경 유지 하는 것에 대 한 전체 프로세스 인지 여부를 평가 하는 컨설턴트 또는 파트너와 작업할 수 있습니다.  <br/> |
|데이터 원본 온-프레미스에 대 한 연결  <br/> |예: 백업 도메인 컨트롤러 (BDC) 연결 및 콘텐츠 원본을 검색 백엔드 데이터 시스템에 연결을 복제를 수행할 수 없습니다.  <br/> |
|검색 복원 시나리오  <br/> |엔터프라이즈 검색 배포 되는 매우 고유 하 고 복잡 한 경향이, 때문에 더 많은 투자를 필요 데이터베이스에서 검색을 복원 합니다. 컨설턴트 또는 파트너를 식별 하 고 조직 필요할 수 있는 검색 복원 시나리오를 구현를 사용 하 여 작업할 수 있습니다.  <br/> |
   
이 문서에서 제공 하는 지침에는 온-프레미스 팜에 이미 디자인 및 배포 된 가정 합니다.
  
## <a name="detailed-architecture"></a>자세한 아키텍처

원칙적으로 Azure에서 복구 팜 구성은 프로덕션 팜 온-프레미스, 다음을 비롯 한 비슷합니다.
  
- 서버 역할의 동일한 표현
    
- 동일한 구성의 사용자 지정
    
- 검색 구성 요소는 동일한 구성
    
Azure의 환경에는 프로덕션 팜 중 더 작은 버전 수 있습니다. 장애 조치 후 복구 팜 확장 하려는 경우에 각 종류의 서버 역할 처음 표현 되는 것이 중요 합니다.
  
일부 구성 장애 조치 환경에서 복제를 수행할 수 없습니다. 장애 조치 절차 및 장애 조치 팜 예상된 서비스 수준에서 제공 하을 보장 하는 환경 테스트 해야 합니다.
  
이 솔루션에는 SharePoint 팜에 대 한 특정 토폴로지를 규정 하지 않습니다. 이 솔루션의 포커스가 있는 장애 조치 팜에 대해 Azure를 사용 하 고 두 환경 간에 로그 전달 및 DFSR를 구현할 수 있습니다.
  
### <a name="warm-standby-environments"></a>웜 대기 환경

웜 대기 환경에서 모든 가상 컴퓨터 Azure 환경에서 실행 됩니다. 환경이 장애 조치 연습 또는 이벤트를 수행할 준비가 되었습니다.
  
다음 그림에서는 웜 대기 환경으로 구성 된 Azure 기반 SharePoint 팜에 온-프레미스 SharePoint 팜에서 재해 복구 솔루션을 보여줍니다.
  
**그림: 토폴로지 및 프로덕션 팜과 웜 대기 복구 팜의 핵심 요소**

![SharePoint 팜 및 웜 대기 복구 팜 토폴로지](media/AZarch-AZWarmStndby.png)
  
다음은 이 다이어그램에 대한 설명입니다.
  
- 두 환경이 나란히 표시 된: 온-프레미스 SharePoint 팜과 Azure의 웜 대기 팜 합니다.
    
- 각 환경에는 파일 공유가 있습니다.
    
- 각 팜 а를 포함합니다. 고가용성을 달성 하기 위해 각 계층에는 두 서버 또는 프런트엔드 서비스, 분산된 캐시, 백엔드 서비스 데이터베이스 등의 특정 역할에 대 한 동일 하 게 구성 된 가상 컴퓨터 포함 됩니다. 이 그림 특정 구성 요소를 호출 하는 것이 중요 하지 않습니다. 두 팜은 동일 하 게 구성 됩니다.
    
- 4 번째 계층은 데이터베이스 계층입니다. 로그 전달 보조 데이터베이스 서버는 온-프레미스 환경에서 동일한 환경에서 파일 공유에 로그를 복사 하는 하는데 사용 됩니다.
    
- DFSR은 온-프레미스 환경의 파일 공유에서 Azure 환경의 파일 공유로 파일을 복사합니다.
    
- 로그 전달은 Azure 환경의 파일 공유에서 복구 환경의 SQL Server AlwaysOn 가용성 그룹에 있는 기본 복제본으로 로그를 재생합니다.
    
### <a name="cold-standby-environments"></a>콜드 대기 환경

콜드 대기 환경에서 SharePoint 팜 가상 컴퓨터의 대부분 종료할 수 있습니다. (권장 가상 컴퓨터 마다 2 주 또는 한 달, 번 등을 시작 하는 경우에 따라 각 가상 컴퓨터의 도메인과 동기화 할 수 있도록 합니다.) Azure 복구 환경에서 다음 가상 컴퓨터 로그 전달 및 DFSR 연속 작업을 보장 하는 실행 중인 상태를 유지 해야 합니다.
  
- 파일 공유
    
- 기본 데이터베이스 서버입니다.
    
- Windows Server Active Directory 도메인 서비스 및 DNS를 실행 하는 하나 이상의 가상 컴퓨터
    
다음 그림은 파일 공유 가상 컴퓨터 및 기본 SharePoint 데이터베이스 가상 컴퓨터 실행 중인 Azure 장애 조치 환경입니다. 다른 모든 SharePoint 가상 컴퓨터는 중지 됩니다. Windows Server Active Directory 및 DNS를 실행 하는 가상 컴퓨터 표시 되지 않습니다.
  
**가상 컴퓨터를 실행 하는 포함 된 그림: 콜드 대기 복구 팜**

![Azure의 SharePoint 콜드 대기 솔루션 요소](media/AZarch-AZColdStndby.png)
  
콜드 대기 환경에 장애 조치 후 모든 가상 컴퓨터를 시작 하 고 메서드를 호출 하는 데이터베이스 서버의 고가용성을 얻을 수를 구성 해야, SQL Server AlwaysOn 가용성 그룹 등입니다.
  
여러 저장소 그룹 구현 된 경우 (데이터베이스 분산 된 하나 이상의 SQL Server 고가용성 집합)을 해당 저장소 그룹에 연결 된 로그를 수락 하려면 각 저장소 그룹에 대 한 기본 데이터베이스를 실행 해야 합니다.
  
### <a name="skills-and-experience"></a>기술 및 경험

여러 기술은이 재해 복구 솔루션에 사용 됩니다. 이러한 기술을 예상 대로 작용 하는 확인 하는데에 온-프레미스 및 Azure 환경에서 각 구성 요소를 설치 하 고 올바르게 구성 수 해야 합니다. 하는 개인 또는 팀이이 솔루션을 설정 하는 사용자가 대 한 강력한 작업 지식이 및 실습 기술을 다음 문서에 설명 된 기술을 사용 하 여는 것이 좋습니다.
  
- [분산된 파일 시스템 (DFS) 복제 서비스](https://go.microsoft.com/fwlink/p/?LinkId=392698)
    
- [Windows Server 장애 조치 (WSFC) SQL server 클러스터링](https://go.microsoft.com/fwlink/p/?LinkId=392701)
    
- [AlwaysOn 가용성 그룹(SQL Server)](https://go.microsoft.com/fwlink/p/?LinkId=392725)
    
- [백업 및 SQL Server 데이터베이스 복원](https://go.microsoft.com/fwlink/p/?LinkId=392728)
    
- [SharePoint Server 2013 설치 및 팜 배포](https://go.microsoft.com/fwlink/p/?LinkId=393119)
    
- [Microsoft Azure](https://go.microsoft.com/fwlink/p/?LinkId=392729)
    
마지막으로, 이러한 기술에 관련 된 작업을 자동화 하는 데 사용할 수 있는 기술 스크립팅 하는 것이 좋습니다. 이 솔루션에 설명 된 모든 작업을 완료 하는 사용할 수 있는 사용자 인터페이스를 사용 하는 것이 불가능 합니다. 그러나 수동 접근 시간 사용 (영문) 및 오류가 유발 될 수 있습니다와 일치 하지 않는 결과 제공 합니다.
  
Windows PowerShell 외에도 SQL Server, SharePoint Server 및 Azure 용 Windows PowerShell 라이브러리도 있습니다. T SQL에도 도움이 구성 및 재해 복구 환경을 유지 관리 시간을 단축 하는 것을 잊지 마십시오.
  
## <a name="disaster-recovery-roadmap"></a>재해 복구 로드맵

![SharePoint 재해 복구 로드맵을 시각적으로 보여줍니다.](media/Azure-DRroadmap.png)
  
이 로드맵 프로덕션 환경에 배포 된 SharePoint Server 2013 팜 이미 있다고 가정 합니다.
  
**재해 복구를 위한 테이블: 로드맵**

|**단계**|**설명**|
|:-----|:-----|
|1 단계  <br/> |재해 복구 환경을 디자인 합니다.  <br/> |
|2 단계  <br/> |Azure 가상 네트워크와 VPN 연결을 만듭니다.  <br/> |
|3 단계  <br/> |Azure 가상 네트워크를 Windows Active Directory 및 도메인 이름 서비스를 배포 합니다.  <br/> |
|4 단계  <br/> |Azure의 SharePoint 복구 팜에 배포 합니다.  <br/> |
|단계 5  <br/> |팜 간에 DFSR를 설정 합니다.  <br/> |
|단계 6  <br/> |복구 팜으로 전달 하는 로그를 설정 합니다.  <br/> |
|단계 7  <br/> | 장애 조치 및 복구 솔루션의 유효성을 검사 합니다. 다음 절차 및 기술 포함 됩니다. <br/>  로그 전달을 중지 합니다. <br/>  백업을 복원 합니다. <br/>  콘텐츠를 크롤링합니다. <br/>  서비스를 복구 합니다. <br/>  DNS 레코드를 관리 합니다. <br/> |
   
## <a name="phase-1-design-the-disaster-recovery-environment"></a>1 단계: 디자인 재해 복구 환경

SharePoint 복구 팜에 포함 하 여 재해 복구 환경을 디자인 하는 [SharePoint 2013에 대 한 Microsoft Azure 아키텍처](microsoft-azure-architectures-for-sharepoint-2013.md) 의 지침을 사용 합니다. 디자인 프로세스를 시작 하는 그래픽 [Azure의 재해 복구 솔루션을 SharePoint](https://go.microsoft.com/fwlink/p/?LinkId=392554) Visio 파일에 사용할 수 있습니다. Azure 환경에 있는 모든 작업을 시작 하기 전에 전체 환경을 디자인 하는 것이 좋습니다.
  
가상 네트워크, VPN 연결, Active Directory 및 SharePoint 팜 디자인을 위한 [SharePoint 2013에 대 한 Microsoft Azure 아키텍처](microsoft-azure-architectures-for-sharepoint-2013.md) 에서 제공 하는 지침을 외에도 Azure 환경에는 파일 공유 역할을 추가 해야 합니다.
  
로그 전달을 재해 복구 솔루션에서을 지원 하려면 파일 공유 가상 컴퓨터는 데이터베이스 역할이 있는 서브넷에 추가 됩니다. 파일 공유를 사용 하는 SQL Server AlwaysOn 가용성 그룹에 대 한 노드 과반수의 세번째 노드로 사용 됩니다. SQL Server AlwaysOn 가용성 그룹을 사용 하는 표준 SharePoint 팜에 대 한 권장 되는 구성입니다. 
  
> [!NOTE]
> SQL Server AlwaysOn 가용성 그룹에 참가할 수 있는 데이터베이스에 대 한 필수 구성 요소를 검토 하는 것이 반드시 합니다. 자세한 내용은 [필수 구성 요소, 제한 사항 및 AlwaysOn 가용성 그룹에 대 한 권장 사항을](https://go.microsoft.com/fwlink/p/?LinkId=510870)참조 하십시오. 
  
**그림: 재해 복구 솔루션에 사용 되는 파일 서버 배치**

![SharePoint 데이터베이스 서버 역할을 포함하는 동일한 클라우드 서비스에 추가된 파일 공유 VM을 보여줍니다.](media/AZenv-FSforDFSRandWSFC.png)
  
이 다이어그램에서 파일 공유 가상 컴퓨터는 데이터베이스 서버 역할을 포함 하는 Azure의 동일한 서브넷에 추가 됩니다. SQL Server 역할 등의 다른 서버 역할을 사용 하 여 설정 하는 가용성 파일 공유 가상 컴퓨터를 추가 하지 마십시오.
  
로그의 고가용성에 대 한 고려 해야하는 경우에 [SQL Server 백업 및 복원 Azure Blob 저장소 서비스](https://go.microsoft.com/fwlink/p/?LinkId=393113)를 사용 하 여 다른 접근 방식을 취하고 하는 것이 좋습니다. 이것은 blob 저장소 URL에 직접 로그를 저장 하는 Azure의 새로운 기능입니다. 이 솔루션에서이 기능을 사용 하는 방법에 대 한 지침을 포함 하지 않습니다.
  
복구 팜을 디자인할 때 염두에 성공적인 재해 복구 환경 복구 하려는 프로덕션 팜을 정확 하 게 반영 하는 합니다. 복구 팜 크기 복구 팜의 디자인, 배포 및 테스트에서 가장 중요 한 사항은 않습니다. 비즈니스 요구 사항에 따라 조직에 조직에서 팜 수평 달라 집니다. 짧은 중단 또는 성능 및 용량 요구 사항에 맞출 필요 하면 팜의 확장할 수 있을 때까지 규모가 축소 된 팜을 사용 하 여 수도 있습니다.
  
구성 복구 팜에 프로덕션 팜으로 최대한 동일 하 게 서비스 수준 계약 (SLA) 요구 사항을 충족 하 고 비즈니스를 지원 하기 위해 필요한 기능을 제공 합니다. 재해 복구 환경을 디자인할 때도 프로덕션 환경에 대 한 변경 관리 프로세스를 살펴봅니다. 프로덕션 환경으로 복구 환경 동일한 간격으로 업데이트 하 여 복구 환경에 변경 관리 프로세스를 확장 하는 것이 좋습니다. 변경 관리 프로세스의 일부로 팜 구성, 응용 프로그램 및 사용자의 상세 인벤토리를 유지 관리 하는 것이 좋습니다. 
  
## <a name="phase-2-create-the-azure-virtual-network-and-vpn-connection"></a>단계 2: Azure 가상 네트워크 및 VPN 연결 만들기

[Microsoft Azure 가상 네트워크에 연결 온-프레미스 네트워크](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md) 계획 하 고 Azure에 가상 네트워크를 배포 하는 방법 및 VPN 연결을 만드는 방법을 표시 합니다. 다음 절차를 완료 하려면 항목의 지침을 따릅니다.
  
- 가상 네트워크의 개인 IP 주소 공간을 계획 합니다.
    
- 가상 네트워크에 대 한 라우팅 인프라 변경 작업을 계획 합니다.
    
- 트래픽과 온-프레미스 VPN 장치에 대 한 방화벽 규칙을 계획 합니다.
    
- Azure에서 크로스-프레미스 가상 네트워크를 만듭니다.
    
- 온-프레미스 네트워크와 가상 네트워크 간의 라우팅을 구성 합니다.
    
## <a name="phase-3-deploy-active-directory-and-domain-name-services-to-the-azure-virtual-network"></a>Azure 가상 네트워크를 Active Directory 및 도메인 이름 서비스를 배포 하는 3 단계:

이 단계는 다음 그림에 나와있는 것 처럼 및 [SharePoint 2013에 대 한 Microsoft Azure 아키텍처](microsoft-azure-architectures-for-sharepoint-2013.md) 의 설명에 따라 Windows Server Active Directory와 DNS 하이브리드 시나리오에서 가상 네트워크에 배포를 포함 합니다.
  
**그림: 하이브리드 Active Directory 도메인 구성**

![Azure Virtual Network와 SharePoint 팜 서브넷에 배포된 두 가상 컴퓨터: 복제 도메인 컨트롤러 및 DNS 서버](media/AZarch-HyADdomainConfig.png)
  
그림에서는 두 가상 컴퓨터는 동일한 서브넷에 배포 됩니다. 이러한 가상 컴퓨터에는 각 호스팅 두 역할은: Active Directory 및 DNS 합니다.
  
Azure의 Active Directory를 배포 하기 전에 [Windows Server Active Directory를 배포에 Azure 가상 컴퓨터에 대 한 지침](https://go.microsoft.com/fwlink/p/?linkid=392681)을 제공 합니다. 이러한 지침 솔루션에 대 한 서로 다른 아키텍처 또는 다른 구성 설정의 필요 여부를 결정 하는데 도움이 됩니다.
  
Azure의 도메인 컨트롤러를 설정에 대 한 자세한 지침을 [Azure 가상 네트워크에서 복제 Active Directory 도메인 컨트롤러 설치](https://go.microsoft.com/fwlink/p/?LinkId=392687)를 참조 하십시오.
  
이 단계 전에 가상 네트워크를 가상 컴퓨터를 배포 하지 않았으므로 있습니다. Active Directory 및 DNS를 호스팅하기 위한 가상 컴퓨터는 가능성이 솔루션에 필요한 가장 큰 가상 컴퓨터 없습니다. 이러한 가상 컴퓨터를 배포 하기 전에 먼저 가상 네트워크에서 사용 하 여 계획 하는 가장 큰 가상 컴퓨터를 만듭니다. 이렇게 하면 솔루션에 필요한 가장 큰 크기를 허용 하는 Azure의 태그에 도착 있는지 확인 합니다. 이 시간에이 가상 컴퓨터를 구성할 필요가 없습니다. 만들고 별도로 설정 하기만 합니다. 이렇게 하지 않으면 하는 경우 충돌할 수 있습니다 나중에 더 큰 가상 컴퓨터를 만들려는 경우 제한 하는 시점의 문제는이 문서 작성 되었습니다. 
  
## <a name="phase-4-deploy-the-sharepoint-recovery-farm-in-azure"></a>4 단계: Azure의 SharePoint 복구 팜 배포

디자인 계획에 따라 가상 네트워크에서 SharePoint 팜에 배포 합니다. Azure의 SharePoint 역할을 배포 하기 전에 [Azure 인프라 서비스에 SharePoint 2013에 대 한 계획](https://go.microsoft.com/fwlink/p/?LinkId=400984) 을 검토할 수 있습니다.
  
이 개념 검토 환경 구축 하 여 알게 된 다음의 사례를 고려 하십시오.
  
- Azure 포털 또는 PowerShell을 사용 하 여 가상 컴퓨터를 만듭니다.
    
- Azure 및 Hyper-v에는 동적 메모리를 지원 하지 않습니다. 이 성능 및 용량 계획에 포함 해야 합니다.
    
- 자체 가상 컴퓨터 로그온에서가 아니라 Azure 인터페이스를 통해 가상 컴퓨터를 다시 시작 합니다. Azure 인터페이스를 사용 하 여 더 잘 작동 하 고는 예측 하기가 더 쉽습니다.
    
- 비용 절감을 위해 가상 컴퓨터를 종료 하려면 Azure 인터페이스를 사용 합니다. 로그온 하 고는 가상 컴퓨터를 종료 하는 경우 요금 계속 계산 합니다.
    
- 가상 컴퓨터에 대 한 명명 규칙을 사용 합니다.
    
- 가상 컴퓨터는 배포 되는 데이터 센터 위치에 주의 해야 합니다.
    
- Azure의 자동 확장 기능 SharePoint 역할에 대 한 지원 되지 않습니다.
    
- 팜에서 같은 사이트 모음 복원 됩니다 하는 항목을 구성 하지 마십시오. 
    
## <a name="phase-5-set-up-dfsr-between-the-farms"></a>5 단계: 팜 간에 DFSR를 설정 합니다.

DFSR를 사용 하 여 파일 복제를 설정 하려면 DNS 관리 스냅인을 사용 합니다. 그러나 DFSR 설치 하기 전에 온-프레미스 파일 서버 및 Azure 파일 서버에 로그온 하 고 Windows에서 서비스를 사용 하도록 설정 합니다.
  
서버 관리자 대시보드에서 다음 단계를 완료 합니다.
  
- 로컬 서버를 구성 합니다.
    
- **추가 역할 및 기능 마법사**시작 합니다.
    
- **파일 및 저장소 서비스** 노드를 엽니다.
    
- **DFS 네임 스페이스** 와 **DFS 복제**를 선택 합니다.
    
- **다음** 마법사의 단계를 완료 하려면 클릭 합니다.
    
다음 표에서 DFSR 참조 문서 및 블로그 게시물에 대 한 링크를 제공합니다.
  
**표: DFSR에 대 한 문서를 참조**

|**제목**|**설명**|
|:-----|:-----|
|[복제](https://go.microsoft.com/fwlink/p/?LinkId=392732) <br/> |복제에 대 한 링크와 함께 DFS 관리 TechNet 항목  <br/> |
|[DFS 복제: 상태 가이드](https://go.microsoft.com/fwlink/p/?LinkId=392737) <br/> |DFS 정보에 대 한 링크와 위 키  <br/> |
|[DFS 복제: 질문과 대답 (영문)](https://go.microsoft.com/fwlink/p/?LinkId=392738) <br/> |DFS 복제 TechNet 항목  <br/> |
|[합니다. Barreto 블로그 (영문)](https://go.microsoft.com/fwlink/p/?LinkId=392739) <br/> |보안 주체 프로그램 관리자가 Microsoft에서 파일 서버 팀에서 작성 된 블로그 (영문)  <br/> |
|[Microsoft-파일 캐비닛 블로그 (영문)에서 저장소 팀](https://go.microsoft.com/fwlink/p/?LinkId=392740) <br/> |파일 서비스 및 Windows Server의 저장소 기능에 대 한 블로그 (영문)  <br/> |
   
## <a name="phase-6-set-up-log-shipping-to-the-recovery-farm"></a>단계 6: 로그 복구 팜으로 전달 설정

로그 전달이이 환경에서 재해 복구를 설정 하기 위한 중요 한 요소가 있습니다. 로그 전달 보조 데이터베이스 서버 인스턴스를 기본 데이터베이스 서버 인스턴스에서 데이터베이스에 대 한 트랜잭션 로그 파일을 보낼 자동으로 사용할 수 있습니다. 로그 전달을 설정 하려면 [구성에서에서 로그 전달을 SharePoint 2013을](https://docs.microsoft.com/sharepoint/administration/configure-log-shipping)참조 하십시오. 
  
> [!IMPORTANT]
> 에서 로그 전달을 지원 SharePoint 서버는 특정 데이터베이스에 제한 됩니다. 자세한 내용은 [지원 되는 고가용성 및 재해 복구 옵션에 SharePoint 데이터베이스 (SharePoint 2013)을](https://go.microsoft.com/fwlink/p/?LinkId=393121)참조 하십시오. 
  
## <a name="phase-7-validate-failover-and-recovery"></a>단계 7: 장애 조치 및 복구의 유효성을 검사합니다

이 최종 단계의 목표 재해 복구 솔루션 계획 한 대로 작동 하는지 확인 하는 것입니다. 이 작업을 수행 하려면 프로덕션 팜 종료 되 고 대체할 수 있는으로 복구 팜 시작 되는 장애 조치 이벤트를 만듭니다. 수동으로 또는 스크립트를 사용 하 여 장애 조치 시나리오를 시작할 수 있습니다.
  
첫번째 단계 팜 서비스 또는 콘텐츠 받는 사용자 요청을 중지 하는 것입니다. DNS 항목을 사용 하지 않도록 설정 하 여 또는 프런트엔드 웹 서버를 종료 하 여 수행할 수 있습니다. 팜의 작동이 중지 "", 후 있습니다 수 장애 조치 복구 팜으로 합니다.
  
### <a name="stop-log-shipping"></a>로그 전달을 중지합니다

팜 복구 하기 전에 로그 전달을 중지 해야 합니다. 로그 전달 보조 서버 Azure에서 첫째, 중지 하 고 기본 서버 온-프레미스에 중지 합니다. 다음 스크립트를 사용 하 여 첫번째 보조 서버에서 한 주 서버에서 다음 로그 전달을 중지 합니다. 스크립트에서 데이터베이스 이름을 사용자 환경에 따라 달라질 수 있습니다.
  
```
-- This script removes log shipping from the server.
-- Commands must be executed on the secondary server first and then on the primary server.

SET NOCOUNT ON
DECLARE  @PriDB nvarchar(max)
,@SecDB nvarchar(250)
,@PriSrv nvarchar(250)
,@SecSrv nvarchar(250)

Set @PriDB= ''
SET @PriDB = UPPER(@PriDB)
SET @PriDB = REPLACE(@PriDB, ' ', '')
SET @PriDB = '''' + REPLACE(@PriDB, ',', ''', ''') + ''''

Set @SecDB = @PriDB

Exec ( 'Select  ''exec master..sp_delete_log_shipping_secondary_database '' + '''''''' + prm.primary_database +  ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_primary_secondary '' + '''''''' + prm.Primary_Database + '''''', '''''' + sec.Secondary_Server + '''''', '''''' + sec.Secondary_database + ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_primary_database '' + '''''''' + prm.primary_database +  ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_secondary_primary '' + '''''''' + prm.primary_server + '''''', '''''' + prm.primary_database +  ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

```

### <a name="restore-the-backups"></a>백업 복원

생성 된 순서에 백업은 복원 해야 합니다. 커밋되지 않은 트랜잭션이 롤백 하지 않고 다음 이전 백업을 복원 해야 특정 트랜잭션 로그 백업, 복원 하기 전에 (즉,을 사용 하 여 `WITH NORECOVERY`):
  
- 전체 데이터베이스 백업 및 마지막 차등 백업-있을 경우, 특정 트랜잭션 로그 백업을 수행 하기 전에 만든 이러한 백업을 복원 합니다. 가장 최근의 전체 또는 차등 데이터베이스 백업을 만든, 전에 데이터베이스 전체 복구 모델 또는 대량 로그 된 복구 모델 사용 합니다.
    
- 모든 트랜잭션 로그 백업-전체 데이터베이스 백업 또는 (하나 복원) 하는 경우 차등 백업 후 및 전에 특정 트랜잭션 로그 백업 수행 모든 트랜잭션 로그 백업을 복원 합니다. 로그 백업은 생성 된 로그 체인에 있는 모든 간격 없이 시퀀스에 적용 되어야 합니다.
    
사이트 렌더링 되도록 보조 서버에서 콘텐츠 데이터베이스를 복구 하려면 복구 하기 전에 모든 데이터베이스 연결을 제거 합니다. 데이터베이스를 복원 하려면 다음 SQL 문을 실행 합니다.
  
```
restore database WSS_Content with recovery

```

> [!IMPORTANT]
> 명시적으로 T-SQL을 사용 하는 경우 모호성을 제거 하려면 모든 복원 문에서 **WITH NORECOVERY** 또는 **WITH RECOVERY** 지정 — 스크립트를 작성 하는 경우이 매우 중요 합니다. 전체 및 차등 백업을 복원 되 면 SQL Server Management Studio에서 트랜잭션 로그를 복원할 수 있습니다. 또한 로그 전달을 이미 중지 되 면 때문에 콘텐츠 데이터베이스 이므로 대기 상태에서에 대 한 전체 액세스 상태를 변경 해야 합니다.
  
SQL Server Management Studio에서 **WSS_Content** 데이터베이스를 마우스 오른쪽 단추로, **작업**을 가리킨 > **복원**, 다음 **트랜잭션 로그** 를 클릭 하 고 (전체 백업, 복원 되지 않은 경우이 사용할 수 없는). 자세한 내용은[복원 트랜잭션 로그 백업 (SQL Server)을](https://go.microsoft.com/fwlink/p/?LinkId=392778)참조 하십시오.
  
### <a name="crawl-the-content-source"></a>콘텐츠 원본 크롤링

검색 서비스를 복원 하려면 각 콘텐츠 원본의 전체 크롤링을 시작 해야 합니다. 참고 온-프레미스 팜에서 검색 추천와 같은 일부 분석 정보를 잃을 있습니다. 전체 크롤링 시작, **Restore-spenterprisesearchserviceapplication** Windows PowerShell cmdlet을 사용 하 고 로그를 전달 하 고 복제 된 검색 관리 데이터베이스를 지정 하기 전에 **Search_Service__DB_<GUID>** 합니다. 이 cmdlet는 검색 구성, 스키마, 관리 속성, 규칙 및 원본에 게 제공 하 고 다른 구성 요소의 기본 집합을 만듭니다.
  
전체 크롤링을 시작 하려면 다음 단계를 완료 합니다.
  
1. SharePoint 2013 중앙 관리에서 **응용 프로그램 관리**로 이동 > **서비스 응용 프로그램** > **서비스 응용 프로그램 관리**, 다음 크롤링할 지는 검색 서비스 응용 프로그램을 클릭 합니다.
    
2. **검색 관리** 페이지에서 **콘텐츠 원본**을 클릭, 화살표를 클릭 하 고 **전체 크롤링 시작**을 클릭 한 다음 사용할 콘텐츠 원본을 가리킵니다.
    
### <a name="recover-farm-services"></a>팜 서비스 복구

다음 표에서 로그 전달 데이터베이스, 서비스를 데이터베이스가 되어 있지만 로그 전달 데이터베이스 되지 않은 서비스와 복원 하는 것을 권장 하지 않은 서비스를 복구 하는 방법을 보여줍니다.
  
> [!IMPORTANT]
> Azure 환경에는 온-프레미스 SharePoint 데이터베이스를 복원 하 이미를 설치 하지 않은 Azure에서 수동으로 하는 모든 SharePoint 서비스 복구 하지 않습니다. 
  
**표: 서비스 응용 프로그램 데이터베이스 참조 (영문)**

|**로그 전달 데이터베이스에서 이러한 서비스를 복원 합니다.**|**이러한 서비스 데이터베이스를 되었지만 해당 데이터베이스를 복원 하지 않고 이러한 서비스를 시작 하는 것이 좋습니다.**|**이러한 서비스, 데이터베이스에서 데이터를 저장 하지 않습니다. 장애 조치 후 이러한 서비스를 시작 합니다.**|
|:-----|:-----|:-----|
| 기계 번역 서비스 <br/>  Managed Metadata Service <br/>  Secure Store Service <br/>  사용자 프로필입니다. (프로필 및 공유 태그 데이터베이스 에서만 지원 됩니다. 동기화 데이터베이스 지원 되지 않습니다.) <br/>  Microsoft SharePoint Foundation 가입 설정 서비스 <br/> | Usage and Health Data Collection <br/>  State Service <br/>  Word 자동화 <br/> | Excel Services <br/>  PerformancePoint Services <br/>  PowerPoint Conversion <br/>  Visio Graphics Service <br/>  작업 관리 <br/> |
   
다음 예제에서는 데이터베이스에서 관리 되는 메타 데이터 서비스를 복원 하는 방법을 보여줍니다.
  
이 기존 Managed_Metadata_DB 데이터베이스를 사용합니다. 이 데이터베이스에서는 로그 전달 되거나, 수 있지만를 설정 했으면 서비스 응용 프로그램에 연결할 수 있어야 하므로 활성 서비스 응용 프로그램을 보조 팜에서 않습니다.
  
먼저를 사용 하 여 `New-SPMetadataServiceApplication`를 지정 하 고는 `DatabaseName` 복원된 된 데이터베이스의 이름으로 전환 합니다.
  
다음으로 구성 새 관리 되는 메타 데이터 서비스 응용 프로그램 보조 서버에서 다음과 같습니다.
  
- 이름: 관리 되는 메타 데이터 서비스
    
- 데이터베이스 서버: 선적된 트랜잭션 로그에서 데이터베이스 이름
    
- 데이터베이스 이름: Managed_Metadata_DB
    
- 응용 프로그램 풀: SharePoint 서비스 응용 프로그램 
    
### <a name="manage-dns-records"></a>DNS 레코드 관리

SharePoint 팜의를 가리키도록 DNS 레코드를 수동으로 만들어야 합니다.
  
여러 프런트엔드 웹 서버가 있는 대부분의 경우에는 팜의 프런트엔드 웹 서버 요청을 배포 하는 Windows Server 2012 또는 하드웨어 부하 분산 장치에서 네트워크 부하 분산 기능을 활용 하 것이 좋습니다. 네트워크 부하 분산 프런트엔드 웹 서버 중 하나에 실패 하는 경우 다른 서버에 대 한 요청을 분산 하 여 위험을 줄일 수 있습니다. 
  
일반적으로 네트워크 부하 분산 설정 하는 경우 클러스터는 단일 IP 주소를 할당 됩니다. 그런 다음 만들면 DNS 호스트 레코드를 DNS 공급자에서 클러스터를 가리키는 네트워크에 대 한 합니다. (이 프로젝트에 대 한는 DNS 서버에에서 배치 Azure에서 온-프레미스 데이터 센터 오류가 발생 하는 경우 복구를 위한.) DNS 레코드를 DNS 관리자에서 Active Directory에서 예, 호출을 만들 수 예를 들어, `http://sharepoint.contoso.com`, 부하 분산 된 클러스터에 대 한 IP 주소를 가리키는 합니다.
  
SharePoint 팜에 대 한 외부 액세스를 위한 클라이언트가 인트라넷에서 사용 하는 동일한 URL에는 외부 DNS 서버에 호스트 레코드를 만들 수 있습니다 (예를들어, `http://sharepoint.contoso.com`) 방화벽의 외부 IP 주소를 가리키는 합니다. (이 예제를 사용 하 여 최상의 결과 내부 DNS 서버에 대 한 신뢰할 수 있도록 분할 DNS 설정 하는 `contoso.com` 하 고 SharePoint 팜 클러스터에 직접 요청을 라우팅하는 것이 아니라 외부 DNS 서버에 요청 하는 라우팅 DNS.) 그런 다음 클라이언트에 대 한 필요 리소스를 찾을 수 있도록 외부 IP 주소 온-프레미스 클러스터의 내부 IP 주소를 매핑할 수 있습니다.
  
여기에서 서로 다른 재해 복구 시나리오의 메시지를 몇 충돌할 수 있습니다.
  
 **예제 시나리오: 온-프레미스 SharePoint 팜의 하드웨어 오류로 인해 온-프레미스 SharePoint 팜의 사용할 수 없습니다.** 이 경우 Azure SharePoint 팜에 장애 조치에 대 한 단계를 완료 한 후에 네트워크에서 부하 분산 복구 SharePoint 팜의 프런트엔드 웹 서버는 온-프레미스 팜 것과 마찬가지로 동일한 방식으로 구성할 수 있습니다. 그런 다음 복구 팜의 클러스터 IP 주소를 가리키도록 내부 DNS 공급자에서 호스트 레코드를 리디렉션할 수 있습니다. 클라이언트에서 캐시 된 DNS 레코드 하기 전에 다소 시간이 걸릴 수 있는 메모를 새로 고칠 하 고 복구 팜에를 가리킵니다.
  
 **예제 시나리오: 온-프레미스 데이터 센터를 완전히 손실 됩니다.** 이 시나리오는 자연 재해, 화재 또는 배 등으로 인해 발생할 수 있습니다. 이 경우에 엔터프라이즈에 대 한 가능성이 해야 Azure 서브넷 자체 디렉터리 서비스와 DNS를 비롯 하 여 다른 지역에 호스팅되는 보조 데이터 센터입니다. 이전 재해 시나리오와 같이 Azure SharePoint 팜을 가리키도록 내부 및 외부 DNS 레코드를 리디렉션할 수 있습니다. 다시는 점에 주의 DNS 레코드가 전파 다소 시간이 걸릴 수 있습니다.
  
[호스트 이름이 지정 된 사이트 모음 아키텍처 및 배포 (SharePoint 2013)](https://docs.microsoft.com/SharePoint/administration/host-named-site-collection-architecture-and-deployment)에서 권장 하는 대로 호스트 이름이 지정 된 사이트 모음을 사용 하는 경우에 SharePoint 팜의 고유와 동일한 웹 응용 프로그램에서 호스트 하는 여러 사이트 모음을 할 수 있습니다. DNS 이름 (예 `http://sales.contoso.com` 및 `http://marketing.contoso.com`). 이 경우 사용자 클러스터의 IP 주소를 가리키는 각 사이트 모음에 대 한 DNS 레코드를 만들 수 있습니다. 요청을 SharePoint 웹 프런트엔드 서버에 도달 하면 후 적절 한 사이트 모음에 각 요청을 라우팅 처리할 수 있습니다.
  
## <a name="microsoft-proof-of-concept-environment"></a>Microsoft 개념 증명 환경

설계 하 고이 솔루션에 대 한 개념 증명 환경을 테스트 합니다. 이 테스트 환경에 대 한 디자인 목표를 배포 하 고 고객 환경에서 찾을 수도 하는 SharePoint 팜을 복구 하는 것 이었습니다. 여러 가정 걸었지만 팜의 모든 사용자 지정 내용을 없이 기본 기능을 제공 하는 데 필요한 있는지 알고 있습니다. 토폴로지 필드 및 제품 그룹에서 모범 사례 지침을 사용 하 여 고가용성을 위해 설계 되었습니다.
  
다음 표에서 작성 하 고 온-프레미스 테스트 환경에 대해 구성 하는 Hyper-v 가상 컴퓨터를 설명 합니다.
  
**표: 온-프레미스에 대 한 가상 컴퓨터 테스트**

|**서버 이름**|**역할**|**구성**|
|:-----|:-----|:-----|
|DC1  <br/> |Active Directory와 도메인 컨트롤러입니다.  <br/> |2 개의 프로세서  <br/> Ram 4GB를 통해 512MB에서  <br/> 1 x 127 GB 하드 디스크  <br/> |
|RRAS  <br/> |라우팅 및 원격 액세스 서비스 (RRAS) 역할을 사용 하 여 구성 하는 서버입니다.  <br/> |2 개의 프로세서  <br/> 2-8 개의 2GB의 RAM  <br/> 1 x 127 GB 하드 디스크  <br/> |
|FS1  <br/> |파일 서버 백업에 대 한 공유 및 DFSR의 시작점과 끝점입니다.  <br/> |4 개의 프로세서  <br/> 2-12GB ram  <br/> 1 x 127 GB 하드 디스크  <br/> 1 x 1 TB 하드 디스크 (SAN)  <br/> 1 x 750 GB 하드 디스크  <br/> |
|SP-WFE1, SP-WFE2  <br/> |프런트엔드 웹 서버입니다.  <br/> |4 개의 프로세서  <br/> 16GB RAM  <br/> |
|S P-A P P 1을 S P-APP2 S P-APP3  <br/> |응용 프로그램 서버입니다.  <br/> |4 개의 프로세서  <br/> 2-16 2GB의 RAM  <br/> |
|SP-SQL-HA1, SP-SQL-HA2  <br/> |높은 가용성을 제공 하도록 SQL Server 2012 AlwaysOn 가용성 그룹을 사용 하 여 구성 데이터베이스 서버입니다. 이 구성은 기본 및 보조 복제본으로 SP-sql-ha1 및 HA2-s P-SQL을 사용합니다.  <br/> |4 개의 프로세서  <br/> 2-16 2GB의 RAM  <br/> |
   
다음 표에서 작성 하 고 프런트엔드 웹 및 온-프레미스 테스트 환경에 대 한 응용 프로그램 서버에 대해 구성 하는 Hyper-v 가상 컴퓨터에 대 한 드라이브 구성을 설명 합니다.
  
**표: 프런트엔드 최종 웹에 대 한 가상 컴퓨터 드라이브 요구 사항 및 온-프레미스에 대 한 응용 프로그램 서버 테스트**

|**드라이브 문자**|**크기**|**디렉터리 이름**|**Path**|
|:-----|:-----|:-----|:-----|
|C  <br/> |80  <br/> |시스템 드라이브  <br/> |<DriveLetter>:\\프로그램 파일\\Microsoft SQL Server\\  <br/> |
|E  <br/> |80  <br/> |로그 드라이브 (40GB)  <br/> |<DriveLetter>:\\프로그램 파일\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\데이터  <br/> |
|F  <br/> |80  <br/> |페이지 (36GB)  <br/> |<DriveLetter>:\\프로그램 파일\\Microsoft SQL Server\\MSSQL\\데이터  <br/> |
   
다음 표에서 만들고 온-프레미스 데이터베이스 서버 처럼 작동 하도록 구성 된 Hyper-v 가상 컴퓨터에 대 한 드라이브 구성을 설명 합니다. **데이터베이스 엔진 구성** 페이지에서 설정 하 고 다음 표에 나와있는 설정을 확인 하 고 **데이터 디렉터리** 탭에 액세스 합니다.
  
**표: 온-프레미스에 대 한 데이터베이스 서버에 대 한 가상 컴퓨터 드라이브 요구 사항 테스트**

|**드라이브 문자**|**크기**|**디렉터리 이름**|**Path**|
|:-----|:-----|:-----|:-----|
|C  <br/> |80  <br/> |데이터 루트 디렉터리  <br/> |<DriveLetter>:\\프로그램 파일\\Microsoft SQL Server\\  <br/> |
|E  <br/> |500 개  <br/> |사용자 데이터베이스 디렉터리  <br/> |<DriveLetter>:\\프로그램 파일\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\데이터  <br/> |
|F  <br/> |500 개  <br/> |사용자 데이터베이스 로그 디렉터리  <br/> |<DriveLetter>:\\프로그램 파일\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\데이터  <br/> |
|G  <br/> |500 개  <br/> |Temp DB 디렉터리  <br/> |<DriveLetter>:\\프로그램 파일\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\데이터  <br/> |
|H  <br/> |500 개  <br/> |Temp DB 로그 디렉터리  <br/> |<DriveLetter>:\\프로그램 파일\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\데이터  <br/> |
   
### <a name="setting-up-the-test-environment"></a>테스트 환경 설정

테스트 팀에서 다양 한 배포 단계 중 첫번째 온-프레미스 아키텍처에 대 한 다음 해당 Azure 환경에서 일반적으로 작동 합니다. 이 사내 프로덕션 팜에 이미 실행 중인 일반 실제 사례를 반영 합니다. 훨씬 더 중요 한 점은 현재 프로덕션 작업량, 용량 및 일반적인 성능을 알고 있어야입니다. 비즈니스 요구 사항을 충족할 수 있는 재해 복구 모델을 구축 하는 것 외에도 최소 수준의 서비스를 제공 하기 위해 복구 팜 서버를 크기를 결정 해야 합니다. 정지 또는 웜 대기 환경에서 복구 팜 일반적으로 보다 작으면 프로덕션 팜 합니다. 복구 후 팜의 안정적이 고, 프로덕션 환경에서 팜의 확장할 수 있습니다를 시작 및 종료 작업 요구 사항을 충족 합니다.
  
세 단계로 다음에 테스트 환경의 배포 되었습니다.
  
- 하이브리드 인프라 설정
    
- 서버를 구축 합니다.
    
- SharePoint 팜 배포
    
#### <a name="set-up-the-hybrid-infrastructure"></a>하이브리드 인프라 설정

이 단계는 온-프레미스 팜에 대 한 및 Azure에서 복구 팜에 대 한 도메인 환경 설정을 관여합니다. Active Directory를 구성 하는와 관련 된 일반적인 작업을 외에도 테스트 팀 라우팅 솔루션 및 두 환경 간에 VPN 연결을 구현 합니다.
  
#### <a name="provision-the-servers"></a>서버를 구축 합니다.

팜 서버 외에도 클래스는 도메인 컨트롤러에 대 한 프로 비전 서버에 필요한 된 및 RRAS 사이트 마다 VPN를 처리할 수 있는 서버를 구성 합니다. 두 파일 서버 DFSR 서비스에 대 한 프로 비전 된 및 테스터에 게 여러 클라이언트 컴퓨터를 공급 합니다.
  
#### <a name="deploy-the-sharepoint-farms"></a>SharePoint 팜 배포

SharePoint 팜 필요한 경우 환경 안정화 하 고 문제를 해결을 단순화 하기 위해 두 단계로에 구축 되었습니다. 첫 단계 동안 각 팜 서버는 필요한 기능을 지원 하기 위해 토폴로지의 각 계층에 대 한 최소 수에 배포 되었습니다.
  
SQL server가 SharePoint 2013 서버를 만들기 전에 설치 된 데이터베이스 서버를 만들었습니다. 새 배포 되었으므로 SharePoint를 배포 하기 전에 사용 가능 그룹을 작성 되었습니다. MCS 모범 사례 지침에 따라 세 그룹 작성 되었습니다. 
  
> [!NOTE]
> SharePoint 설치 하기 전에 사용 가능 그룹을 만들 수 있도록 자리 표시자 데이터베이스를 만듭니다. 자세한 내용은 [구성 SQL Server 2012 AlwaysOn 가용성 그룹에 대 한 SharePoint 2013을](https://go.microsoft.com/fwlink/p/?LinkId=517626) 참조 하십시오.
  
팜의 만든 하 고 다음과 같은 순서로 추가 서버에 참가 합니다.
  
- S P-sql-ha1 및 s P-SQL-HA2 프로 비전 합니다.
    
- AlwaysOn을 구성 하 고 팜에 대 한 세 가용성 그룹을 만듭니다. 
    
- 프로 비전 s P-a p p 1에 중앙 관리를 호스트 합니다.
    
- S P-w f e 1 및 SP WFE2 분산된 캐시 호스트를 프로 비전 합니다. 
    
**Psconfig.exe** 명령줄에서 실행 하는 경우 _skipRegisterAsDistributedCachehost_ 매개 변수를 사용 했습니다. 자세한 내용은 [피드 및 SharePoint Server 2013의 분산 캐시 서비스에 대 한 계획](https://docs.microsoft.com/sharepoint/administration/plan-for-feeds-and-the-distributed-cache-service)을 참조 하십시오. 
  
복구 환경에서 다음 단계를 반복 하는:
  
- AZ-sql-ha1 및 AZ-SQL-HA2 프로 비전 합니다.
    
- AlwaysOn을 구성 하 고 팜에 대 한 세 가용성 그룹을 만듭니다.
    
- 프로 비전 AZ-a p p 1에 중앙 관리를 호스트 합니다.
    
- AZ-w f e 1 및 AZ WFE2 분산된 캐시 호스트를 프로 비전 합니다.
    
분산된 캐시, 추가 된 테스트 사용자 및 테스트 콘텐츠를 구성 했습니다 후에 배포의 두 단계를 시작 했습니다. 이 필수 계층을 확장 하 고 팜 아키텍처에 설명 된 고가용성 토폴로지를 지원 하기 위해 팜 서버를 구성 합니다.
  
다음 표에서 가상 컴퓨터, 서브넷 및 가용성 집합 사용해 복구 팜에 대 한 설정 합니다.
  
**표: 복구 팜 인프라**

|**서버 이름**|**역할**|**구성**|**서브넷**|**가용성 집합**|
|:-----|:-----|:-----|:-----|:-----|
|spDRAD  <br/> |Active Directory와 도메인 컨트롤러  <br/> |2 개의 프로세서  <br/> Ram 4GB를 통해 512MB에서  <br/> 1 x 127 GB 하드 디스크  <br/> |sp ADservers  <br/> ||
|AZ-S P-FS  <br/> |파일 서버 백업 위한 공유 및 DFSR에 대 한 끝점  <br/> | A5 구성: <br/>  2 개의 프로세서 <br/>  14 2GB의 RAM <br/>  1 x 127 GB 하드 디스크 <br/>  1 x 135 GB 하드 디스크 <br/>  1 x 127 GB 하드 디스크 <br/>  1 x 150 GB 하드 디스크 <br/> |sp databaseservers  <br/> |DATA_SET  <br/> |
|AZ-W F E 1, AZ-WFE2  <br/> |프런트엔드 최종 웹 서버  <br/> | A5 구성: <br/>  2 개의 프로세서 <br/>  14 2GB의 RAM <br/>  1 x 127 GB 하드 디스크 <br/> |sp webservers  <br/> |WFE_SET  <br/> |
|AZ-A P P 1, AZ-APP2, AZ-APP3  <br/> |응용 프로그램 서버  <br/> | A5 구성: <br/>  2 개의 프로세서 <br/>  14 2GB의 RAM <br/>  1 x 127 GB 하드 디스크 <br/> |sp applicationservers  <br/> |APP_SET  <br/> |
|AZ-SQL-HA1, AZ-SQL-HA2  <br/> |데이터베이스 서버 및 AlwaysOn 가용성 그룹에 대 한 기본 및 보조 복제본  <br/> | A5 구성: <br/>  2 개의 프로세서 <br/>  14 2GB의 RAM <br/> |sp databaseservers  <br/> |DATA_SET  <br/> |
   
### <a name="operations"></a>작업

다음 작업을 시작은 테스트 팀 팜 환경을 안정 기능 테스트 완료 된 후 온-프레미스 복구 환경을 구성 하는 데 필요한 작업:
  
- 전체 및 차등 백업을 구성 합니다.
    
- 온-프레미스 환경 및 Azure 환경 간에 트랜잭션 로그를 전송 하는 파일 서버에서 DFSR를 구성 합니다.
    
- 기본 데이터베이스 서버에서 로그 전달 구성 합니다.
    
- 안정을,의 유효성을 검사 하 고 필요에 따라 로그 전달의 문제를 해결 합니다. 이 식별 하 고 로그 전달 또는 DFSR 파일 동기화가 실패 하면 네트워크 대기 시간 등의 문제를 발생 시킬 수 있는 모든 동작을 문서화 포함 됩니다.
    
### <a name="databases"></a>데이터베이스

장애 조치 테스트 다음 데이터베이스를 포함 합니다. 
  
- WSS_Content
    
- ManagedMetadata
    
- 프로필 DB
    
- DB 동기화
    
- 공유 DB
    
- 콘텐츠 형식 허브 (전용된 콘텐츠 형식 신디케이션 허브에 대 한 데이터베이스)
    
## <a name="troubleshooting-tips"></a>문제 해결 팁

섹션에서는 우리가 테스트 하 고 그 솔루션 하는 동안 발생 하는 문제에 설명 합니다. 
  
### <a name="using-the-term-store-management-tool-caused-the-error-the-managed-metadata-store-or-connection-is-currently-not-available"></a>용어 저장소 관리 도구를 사용 하 여 오류를 발생 시킨, "관리 되는 메타 데이터 저장소 또는 연결 현재 사용할 수 없습니다."

웹 응용 프로그램에서 사용 하는 응용 프로그램 풀 계정에 용어 저장소 사용 권한 읽기 액세스 권한이 있는지 확인 합니다.
  
### <a name="custom-term-sets-are-not-available-in-the-site-collection"></a>사용자 지정 용어 집합 사이트 모음에서 사용할 수 없습니다.

콘텐츠 사이트 모음 및 콘텐츠 형식 허브 사이 누락 된 서비스 응용 프로그램 연결을 확인 합니다. 또한 아래는 **관리 되는 메타 데이터- <site collection name> 연결** 속성 화면에서이 옵션을 사용 하도록 설정: **이 서비스 응용 프로그램은 열 관련 용어 집합에 대 한 기본 저장소 위치.**
  
### <a name="the-get-adforest-windows-powershell-command-generates-the-error-the-term-get-adforest-is-not-recognized-as-the-name-of-a-cmdlet-function-script-file-or-operable-program"></a>이 오류를 생성 하는 Get ADForest Windows PowerShell 명령, "' Get-ADForest' 용어 cmdlet, 함수, 스크립트 파일, 또는 실행할 수 있는 프로그램의 이름으로 인식 되지 않습니다."

사용자 프로필을 설정할 때 Active Directory 포리스트 이름을 해야 합니다. 추가 역할 및 기능 마법사는 Active Directory 모듈에 대 한 Windows PowerShell을 설정 했는지 확인 (아래는 **원격 서버 관리 도구 > 역할 관리 도구 > AD DS 및 AD LDS 도구** 섹션). 또한 **Get ADForest** 을 보장 하는 종속성을 로드 하는지 소프트웨어를 사용 하기 전에 다음 명령을 실행 합니다.
  
```
Import-module servermanager
Import-module activedirectory

```

### <a name="availability-group-creation-fails-at-starting-the-alwaysonhealth-xevent-session-on-server-name"></a>가용성 그룹 만들기 'AlwaysOn_health' XEvent 세션에서 시작 해 서에 실패 하면 '<server name>'

장애 조치 클러스터의 두 노드 상태에 있는지 확인 "최대" 및 하지 "일시 중지 됨" 또는 "중지 됨"입니다. 
  
### <a name="sql-server-log-shipping-job-fails-with-access-denied-error-trying-to-connect-to-the-file-share"></a>SQL Server 로그 전달 작업이 실패 하 고 액세스 거부 오류 파일 공유에 연결 하려고 합니다.

SQL Server 에이전트의 기본 자격 증명 하는 대신 네트워크 자격 증명에서 실행 되 고 있는지 확인 합니다.
  
### <a name="sql-server-log-shipping-job-indicates-success-but-no-files-are-copied"></a>SQL Server 로그 전달 작업 성공, 나타내지만 없는 파일 복사

이러한 **보조 선호**은 가용성 그룹에 대 한 기본 백업 기본 설정 하기 때문에 발생 합니다. 기본 형식은 하는 대신 사용 가능 그룹에 대 한 보조 서버에서 로그 전달 작업을 실행 하는 확인 그렇지 않은 경우 작업이 자동으로 실패 합니다. 
  
### <a name="managed-metadata-service-or-other-sharepoint-service-fails-to-start-automatically-after-installation"></a>설치 후 자동으로 시작 하도록 실패 하는 관리 되는 메타 데이터 서비스 (또는 기타 SharePoint 서비스)

서비스를 시작, 성능 및 SharePoint Server의 현재 부하에 따라 몇 분정도 걸릴 수 있습니다. 수동으로 서비스에 대 한 **시작** 을 클릭 하 고 필요에 따라 해당 상태를 모니터링할 서버 화면에서 서비스를 새로 고치는 동안 시작에 대 한 적절 한 시간을 제공 합니다. 서비스가 중지 된 설정을 변경 하거나 하는 경우에 SharePoint 진단 로깅을 사용 하도록 설정, 서비스를 다시 시작 하 고 오류에 대 한 로그를 확인 하려고 합니다. 자세한 내용은 [SharePoint 2013에서 진단 로깅을 구성](https://docs.microsoft.com/sharepoint/administration/configure-diagnostic-logging) 을 참조 하십시오.
  
### <a name="after-changing-dns-to-the-azure-failover-environment-client-browsers-continue-to-use-the-old-ip-address-for-the-sharepoint-site"></a>SharePoint 사이트에 대 한 이전 IP 주소를 사용 하 여 클라이언트 브라우저 계속 Azure 장애 조치 환경으로 DNS를 변경한 후

DNS 변경 내용을 표시 되지 않을 수도 모든 클라이언트에 게 즉시 합니다. 테스트 클라이언트에서 관리자 권한 명령 프롬프트에서 다음 명령을 수행 하 고 사이트에 액세스 하 고 다시 시도 합니다.
  
```
Ipconfig /flushdns
```

## <a name="additional-resources"></a>추가 리소스

[SharePoint 데이터베이스에 대해 지원되는 고가용성 및 재해 복구 옵션](https://docs.microsoft.com/sharepoint/administration/supported-high-availability-and-disaster-recovery-options-for-sharepoint-databas)
  
[SharePoint 2013에 대해 SQL Server 2012 AlwaysOn 가용성 그룹 구성](https://go.microsoft.com/fwlink/p/?LinkId=393122)
  
## <a name="see-also"></a>참고 항목

[클라우드 채택 및 하이브리드 솔루션](cloud-adoption-and-hybrid-solutions.md)



