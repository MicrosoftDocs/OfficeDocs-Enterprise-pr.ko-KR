---
title: OneDrive 및 Office 365의 SharePoint Online에 제공되는 다중 위치 기능
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: OneDrive 및 SharePoint Online의 다중 위치 기능으로 여러 지리적 지역으로 Office 365 범위를 확장합니다.
ms.openlocfilehash: c6648dc8a0b225105e408fc082f6bb4d1a1b4930
ms.sourcegitcommit: 2f138e0733266ab4b179bbe882c734500118dde1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "24012738"
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365"></a>OneDrive 및 Office 365의 SharePoint Online에 제공되는 다중 위치 기능

OneDrive 및 SharePoint Online의 Multi-Geo 기능을 사용하여 조직은 Office 365 사용 범위를 기존 테넌트 내의 여러 지리적 지역 및/또는 국가로 확장할 수 있습니다. 또한 Microsoft 계정 팀에 연락하여 비즈니스용 OneDrive Multi-Geo에 귀하의 다국적 기업을 등록할 수 있습니다.
  
OneDrive Multi-Geo를 사용하여 데이터 상주 요구 사항을 충족하기 위해 선택한 지리적 위치에서 미사용 데이터를 프로비전 및 저장하고, 동시에 귀하의 전 세계 작업자들이 최신 생산선 환경을 활용하도록 할 수 있습니다.
  
다중 위치 기능이 조직에 유용하게 사용될 수 있는 방법은 다음과 같습니다.
  
- 단일 Office 365 테넌트가 여러 개의 지리적 위치에 걸쳐 있는 하나의 연결된 전역 조직으로 작용합니다.
    
- 지정된 지리적 위치 내에서 미사용 데이터를 생성 및 호스트하여 데이터 상주 요구 사항을 충족합니다.
    
- 중앙 위치 사용자가 사용하는 것과 동일한 최신 생산성 환경을 위성 사용자도 누릴 수 있습니다.
    
- 콘텐츠 액세스 권한을 안전하게 유지하면서 역할 변화에 맞춰 지리적 위치 간을 이동할 수 있도록 합니다.
    
- 지리적 위치별 공유 정책을 조정하고, 사이트별로 데이터 손실 방지 정책을 조정합니다.
    
- 지리적 위치별로 eDiscovery 관리자를 지정하고, 지리적 위치에 맞게 관리 방식을 조정할 수 있습니다.
    
- 추가적인 지리적 위치에 대한 고유한 URL 네임스페이스(예: ContosoEUR.sharepoint.com)를 선택합니다.
    
- 지역의 온-프레미스 데이터를 Office 365 다중 위치 테넌트에 통합합니다.
    
다중 위치 구성에서 Office 365 테넌트는 하나의 중앙 위치(기본 위치라고도 함)와 하나 이상의 위성 지리적 위치로 구성됩니다. 다중 위치의 핵심 개념은 단일 테넌트가 하나의 다중 지리적 위치에 걸쳐 있는 다중 위치 개념입니다. 다중 위치 테넌트에서 지리적 위치, 그룹 및 사용자에 대한 정보는 AAD(Azure Active Directory)에서 마스터됩니다. 테넌트 정보가 중앙에서 마스터된 후 각 지리적 위치로 동기화되므로, 회사 직원 누구든지 전역 정보를 공유하고 경험할 수 있습니다.

## <a name="video-introducing-office-365-multi-geo"></a>비디오: Office 365 Multi-Geo 소개

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE1Yk6B?autoplay=false]
  
## <a name="get-multi-geo-features-in-three-simple-steps"></a>세 가지 간단한 단계로 다중 위치 기능 설정

다중 위치 기능은 다음과 같이 간단히 구성할 수 있습니다.
  
1. 계정 팀과 협의하여 추가 하려면 계정 팀에서 작업 하는 _Office 365의 Multi-Geo 기능_ 서비스 계획을 추가합니다. 필요한 라이선스 수를 추가하는 과정이 안내됩니다.
    
2. 위성 위치를 추가합니다.
    
3. 해당 위치에 맞게 사용자 계정을 구성합니다.
    
## <a name="multi-geo-status-and-availability"></a>다중 위치 상태 및 가용성

OneDrive Multi-Geo는 현재 다음 지역 및 국가에서 제공됩니다.
  
- 아시아 태평양
    
- 오스트레일리아
    
- 캐나다
    
- EMEA(유럽 연합)

- 프랑스
    
- 일본
    
- 영국
    
- 미국(북미)
    
- 한국
      
예정된 지리적 위치:
  
- 인도
    
## <a name="getting-started"></a>시작

비즈니스용 OneDrive Multi-Geo를 시작하려는 경우 첫 번째 단계는 [비즈니스용 OneDrive Multi-Geo 환경 계획](plan-for-multi-geo.md)입니다. 다음은 [다중 위치 환경 관리 방법 알아보기](administering-a-multi-geo-environment.md) 및 [사용자가 다중 위치 환경을 경험하는 방식](multi-geo-user-experience.md)입니다. 비즈니스용 OneDrive Multi-Geo를 설정할 준비가 되면 [다중 위치에 대한 테넌트를 구성](multi-geo-tenant-configuration.md)하고 [기존 OneDrive 사이트를 새 지리적 위치로 이동](move-onedrive-between-geo-locations.md)한 후 [검색을 설정](configure-search-for-multi-geo.md)합니다.
