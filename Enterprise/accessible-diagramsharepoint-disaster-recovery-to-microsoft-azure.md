---
title: 액세스 가능한 다이어그램-Microsoft Azure로의 SharePoint 재해 복구
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 4b855224-8e67-4efa-a3a4-908ee0ca6412
description: 이 문서는 Microsoft Azure에 대 한 SharePoint 재해 복구 라는 다이어그램의 액세스 가능한 텍스트 버전입니다.
ms.openlocfilehash: e711452f6e019ceb280d43c2e0167507a0b0ef20
ms.sourcegitcommit: b4514cd852093181dd4c27009a78aca3ca50d2e2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/08/2019
ms.locfileid: "38038237"
---
# <a name="accessible-diagram---sharepoint-disaster-recovery-to-microsoft-azure"></a>액세스 가능한 다이어그램-Microsoft Azure로의 SharePoint 재해 복구

**요약:** 이 문서는 Microsoft Azure에 대 한 SharePoint 재해 복구 라는 다이어그램의 액세스 가능한 텍스트 버전입니다.
  
이 포스터는 Azure의 복구 환경을 구축 하기 위한 아키텍처의 예를 제공 합니다. 
  
## <a name="on-premises-environment-with-an-azure-recovery-environment"></a>Azure 복구 환경을 사용 하는 온-프레미스 환경

이 다이어그램에서는 복구를 위해 Azure를 사용 하는 온-프레미스 환경의 프로덕션 환경에 사용 되는 아키텍처의 예를 보여 줍니다. 
  
### <a name="on-premises-production-environment"></a>온-프레미스 프로덕션 환경

함께 제공 되는 다이어그램에서는 서버 팜의 서버 계층 4 개가 포함 된 실제 프로덕션 환경을 보여 줍니다. 
  
#### <a name="tier-1"></a>계층 1

프런트 엔드 서비스와 쿼리 처리에는 두 가지 서버가 있습니다. 두 서버의 복제본을 제공 하는 인덱스 파티션이 있습니다. 
  
#### <a name="tier-2"></a>계층 2

이 계층에는 분산 캐시에 대 한 서버가 두 개 있습니다. 
  
#### <a name="tier-3"></a>계층 3

이 계층에는 3 대의 서버가 있습니다. 각 서버에서 제공 하는 서비스는 다음과 같습니다. 
  
- 백 엔드 서비스 
    
- 관리자 
    
- 워크플로 관리자 
    
- 크롤링 
    
- 콘텐츠 처리 
    
- 분석 
    
#### <a name="tier-4"></a>계층 4

이 계층에는 두 개의 서버가 있습니다. 두 서버에는 다음과 같은 세 가지 가용성 그룹이 있습니다. 
  
- 가용성 그룹 #1는 검색 기능을 제공 합니다. 
    
- 가용성 그룹 #2 콘텐츠, 구성 및 서비스 응용 프로그램을 제공 합니다. 
    
- 가용성 그룹 #3 콘텐츠를 제공 합니다. 
    
이 계층에는 파일 공유 서버도 있습니다. 계층 4 서버는 로그 전달을 사용 하 여이 서버와 통신 합니다. 그러면이 서버는 다음 섹션에 설명 된 대로, DFSR (분산 파일 시스템 복제)를 통해 Azure 웜 대기 모드 복구 환경의 파일 공유 서버와 통신 합니다. 
  
### <a name="azure-recovery-environment"></a>Azure 복구 환경

#### <a name="warm-standby-environment-running-virtual-machines"></a>가상 컴퓨터를 실행 하는 웜 대기 환경

함께 제공 되는 다이어그램에서는 Azure 복구 환경에서 정확히 복제 되는 온-프레미스 환경을 보여 줍니다. 이 환경의 파일 공유 서버는 DFSR을 통해 온-프레미스 환경에 연결 됩니다. DFSR은 파일 공유 서버를 통해 프로덕션 환경에서 복구 환경으로 로그를 전송 합니다. 
  
### <a name="overview"></a>개요

온-프레미스 SharePoint 2013 팜에 대 한 재해 복구 환경을 Azure에서 호스트할 수 있습니다. 
  
-  Azure 인프라 서비스는 보조 데이터 센터를 제공 합니다.
    
- 사용 하는 자원에 대해서만 결제 합니다. 
    
- 소규모 복구 팜은 확장 및 용량 목표를 충족 하기 위해 재해가 발생 한 후 확장할 수 있습니다. 
    
Azure의 복구 팜이 프로덕션 온-프레미스 팜과 가능한 동일 하 게 구성 됩니다. 
  
- 서버 역할의 표현이 동일 합니다. 
    
- 사용자 지정 내용이 동일 하 게 구성 됩니다. 
    
- 동일한 검색 기능 구성 (더 작은 버전의 프로덕션 팜이 있을 수 있음) 
    
로그 전달 및 DFSR은 데이터베이스 백업 및 트랜잭션 로그를 Azure 팜에 복사 하는 데 사용 됩니다. 
  
- DFSR은 프로덕션 환경에서 복구 환경으로 로그를 전송 하는 데 사용 됩니다. WAN 시나리오에서 DFSR은 Azure의 보조 서버로 직접 로그를 전달하는 것보다 더 효율적입니다. 
    
- Azure 기반 SQL Server 컴퓨터에 로그가 재생 됩니다. 
    
- 로그 전달 데이터베이스는 복구 작업이 수행 될 때까지 팜에 연결 되지 않습니다. 
    
장애 조치 (Failover) 절차: 
  
1. 로그 전달을 중지 합니다. 
    
2. 기본 팜에 대 한 트래픽을 수락 하지 않습니다. 
    
3. 최종 트랜잭션 로그를 재생 합니다. 
    
4. 콘텐츠 데이터베이스를 팜에 연결 합니다. 
    
5. 전체 크롤링을 시작 합니다. 
    
6. 복제 된 서비스 데이터베이스에서 서비스 응용 프로그램을 복원 합니다. 
    
이 솔루션에서 제공 하는 복구 목표는 다음과 같습니다. 
  
- 사이트 및 콘텐츠 
    
- 검색 (다시 크롤링, 검색 기록 없음) 
    
- 서비스
    
Microsoft 컨설팅 서비스 또는 파트너가 처리할 수 있는 추가 항목: 
  
- 사용자 지정 팜 솔루션 동기화 
    
- 온-프레미스 데이터 원본에 대 한 연결 (BDC (Business Data Connectivity) 및 search content sources) 
    
- 검색 복원 시나리오 
    
- RTO (복구 시간 목표) 및 RPO (복구 지점 목표) 
    
#### <a name="cold-standby-environment-running-virtual-machines"></a>가상 컴퓨터를 실행 하는 콜드 대기 환경

콜드 대기 환경은 시작 하는 데 시간이 오래 걸리지만 비용이 저렴 합니다. 
  
- 팜은 완전히 구축 되었지만 팜을 만든 후에는 가상 컴퓨터를 중지 합니다. 가상 컴퓨터를 실행 하는 경우에만 처리 비용을 지불 하지만 저장소 및 네트워크 데이터 전송 비용이 적용 됩니다. 
    
- 재해가 발생 하면 팜의 모든 가상 컴퓨터를 시작 하 고 패치를 적용 합니다. 
    
- 백업 및 트랜잭션 로그가 팜 데이터베이스에 적용 됩니다. 
    
다음 목록에서는 콜드 대기 환경에 대 한 추가 절차에 대해 설명 합니다. 
  
- 가상 컴퓨터를 정기적으로 켜서 환경을 패치, 업데이트 및 확인 합니다. 
    
- DNS 및 IP 주소를 새로 고치는 절차를 실행 합니다. 
    
- 장애 조치 (failover) 후 SQL AlwaysOn을 설정 합니다. 
    
함께 제공 되는 다이어그램에는 가상 컴퓨터에 대 한 복제 된 복구 환경이 나와 있습니다. 콜드 대기 환경으로 장애 조치 (failover) 후에는 모든 가상 컴퓨터가 시작 되 고 가용성 그룹은 재생 로그를 사용 하 여 데이터베이스 서버를 사용할 수 있게 구성 됩니다. 
  
## <a name="sharepoint-recovery-environment-in-azure"></a>Azure의 SharePoint 복구 환경

Azure에서 장애 조치 (failover) 환경 설계 및 구축 
  
- Azure에서 가상 네트워크를 만듭니다. 
    
- 사이트 간 VPN 연결을 사용 하 여 온-프레미스 네트워크를 Azure의 가상 네트워크와 연결 합니다. 이 연결은 Azure에서 동적 게이트웨이를 사용 합니다. 
    
- 하나 이상의 도메인 컨트롤러를 Azure virtual network에 배포 하 고 온-프레미스 도메인과 함께 작동 하도록이를 구성 합니다. 이러한 도메인 컨트롤러는 카탈로그 서버입니다. 
    
- 클라우드 서비스 및 가용성 집합에 대 한 SharePoint 팜을 조정 합니다. 
    
- 파일 공유를 호스트 하기 위해 SharePoint 팜과 파일 서버를 배포 합니다. 
    
- 온-프레미스 환경과 Azure 기반 복구 환경 사이에 로그 전달 및 DFSR을 설정 합니다. 
    
함께 제공 되는 다이어그램에서는 다음과 같은 기능을 가진 온-프레미스 환경과 Azure virtual network를 보여 줍니다. 
  
### <a name="on-premises-environment"></a>온-프레미스 환경

- Windows Server 2012 RRAS 
    
- Active Directory 서버 
    
VPN (가상 사설망) 게이트웨이를 통해 Azure virtual network와의 온-프레미스 네트워크 인터페이스입니다. 
  
### <a name="azure-virtual-network"></a>Azure virtual network

VPN 게이트웨이는 활성 VPN 게이트웨이 서브넷과 상호 작용 합니다. 
  
Azure virtual network에는 다음과 같은 세 가지 클라우드 서비스가 있습니다. 
  
- 첫 번째 클라우드 서비스에 가용성 집합이 있는 Active Directory 및 DNS 서버가 두 개 있습니다. 
    
- 두 번째 클라우드 서비스는 가용성 집합이 있는 두 개의 분산 캐시 서버와 세 개의 서버 집합을 사용 합니다. 가용성 집합이 포함 된 프런트 엔드 서버 2 대 가용성 집합을 포함 하는 세 백 엔드 서버
    
- 세 번째 클라우드 서비스에는 가용성 집합이 있는 데이터베이스 서버가 세 개 있습니다. 이러한 데이터베이스 서버 중 하나는 로그 전달에 대 한 파일 공유이 고, SQL Server AlwaysOn에 대 한 노드 과반수의 세 번째 노드입니다. 
    
### <a name="build-the-ad-ds-hybrid-environment"></a>AD DS 하이브리드 환경 구축

이 솔루션에 대 한 AD DS의 구성은 AD DS가 부분적으로 온-프레미스에 배포 되 고 Azure 가상 컴퓨터에 부분적으로 배포 되는 하이브리드 배포 시나리오를 구성 합니다. 
  
중요 — Azure에서 AD DS를 배포 하기 전에 Microsoft Azure 가상 컴퓨터 (https://docs.microsoft.com/windows-server/identity/ad-ds/introduction-to-active-directory-domain-services-ad-ds-virtualization-level-100)에 Windows Server Active Directory를 배포 하기 위한 지침을 읽어 보십시오. 
  
 
이 참조 아키텍처에는 도메인 컨트롤러로 구성 된 두 개의 가상 컴퓨터가 포함 되어 있습니다. 각 형식은 다음과 같이 구성 됩니다. 
  
- 크기-작음 
    
- 운영 체제-Windows Server 2012 
    
- Role-글로벌 카탈로그 서버로 지정 된 AD DS 도메인 컨트롤러입니다. 이 구성은 VPN 연결을 통해 송신 트래픽을 줄입니다. 변경 비율이 높은 다중 도메인 환경에서는 온-프레미스 도메인 컨트롤러를 구성 하 여 Azure의 글로벌 카탈로그 서버와 동기화 되지 않도록 합니다. 
    
- 데이터 디스크-Azure 데이터 디스크에 AD DS 데이터베이스, 로그 및 SYSVOL을 배치 합니다. 이를 운영 체제 디스크 또는 Azure에서 제공 하는 임시 디스크에 배치 하지 마십시오. 이는 중요 한 사항입니다. 
    
- 역할 — 도메인 컨트롤러에 Windows DNS를 설치 하 고 구성 합니다. 
    
- IP 주소-동적 IP 주소를 사용 합니다. 이렇게 하려면 Azure Virtual Network를 만들어야 합니다. 
    

