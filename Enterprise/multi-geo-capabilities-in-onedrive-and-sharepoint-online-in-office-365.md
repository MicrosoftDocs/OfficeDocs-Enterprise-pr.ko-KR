---
title: "OneDrive 및 Office 365의에서 SharePoint Online의 다중-지리적으로 분산 기능"
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 1/24/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: "OneDrive 및 SharePoint Online에서 다중-지리적으로 분산 기능을 조직 여러 지리적 위치 및/또는 기존 테 넌 트 내의 국가에 해당 Office 365 현재 상태를 확장할 수 있습니다."
ms.openlocfilehash: d53da13d5a6a6d5add9da69a3bca9fcdfa39bbd0
ms.sourcegitcommit: 38d43444cf5e03527aa75f670efb2de0f48f847d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/28/2018
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365"></a>OneDrive 및 Office 365의에서 SharePoint Online의 다중-지리적으로 분산 기능

OneDrive 및 SharePoint Online에서 다중-지리적으로 분산 기능을 조직 여러 지리적 위치 및/또는 기존 테 넌 트 내의 국가에 해당 Office 365 현재 상태를 확장할 수 있습니다. 이 기능은 현재 미리 보기 중입니다. OneDrive 다중-지리적으로 분산 미리 보기에 대 한 다중 National 회사를 등록 하 여 Microsoft 계정 팀에 게 연락 합니다.
  
와 OneDrive 다중-지리적으로 분산을 프로 비전 하 고 저장 나머지 부분에서 데이터 데이터 residency 요구를 충족 하기 위해 선택한 지리적 위치에 하 고 수 동시에 직원을 현대 생산성 경험 부족 글로벌 롤 잠금을 해제 합니다.
  
다중-지리적으로 분산 기능 조직을 활용 하는 방법을 다음과 같습니다.
  
- 여러 지리적 위치에 해당 하는 단일 Office 365 테 넌 하나의 글로벌 연결 된 조직으로 작동 합니다.
    
- 만들고 지정 된 지리적 위치 내 나머지에서 데이터를 호스트 하 여 데이터 residency 요구를 충족 합니다.
    
- 위성 사용자에 게 권한 부여는 동일한 현대 생산성 경험 중앙 위치 사용자가 절감할 수 있었습니다.
    
- 사용 하면 사용자가 자신의 콘텐츠에 대 한 액세스는 그대로 유지 되는 동안 자신의 역할 변경 됨에 따라 여러 지리적 위치에 걸친 이동 합니다.
    
- 지리적으로 분산 위치 마다 공유 정책에 및 각 사이트 마다 데이터 손실 방지 정책을 조정할 수 있습니다.
    
- EDiscovery 관리자 당 지리적 위치를 지정 하 고 관리 하는 사용자의 지리적 위치에 맞게 조정 하는 경우를 허용 합니다.
    
- 추가 지리적 위치에 대 한 고유 URL 네임 스페이스 (예: ContosoEUR.sharepoint.com)를 선택 합니다.
    
- Office 365 geo 다중 테 넌 트를 지역 온-프레미스 데이터를 통합 합니다.
    
자세한 내용은 및 데모를 보려면 [Office 365의 소개 (영문) 다중-지리적으로 분산 기능 및 구성 하는 방법](https://youtu.be/3d9-Vt2fArk) 및[다중-지리적으로 분산 개요 포스터 (영문)를](https://technet.microsoft.com/library/dn782272.aspx)참조 합니다.
  
다중-지리적으로 분산 구성에서 Office 365 테 넌 트 (기본 위치) 하는 중앙 위치 및 위성 지리적 위치를 하나 이상으로 구성 됩니다. 다중-지리적으로 분산의 핵심 개념은 하는 단일 테 넌 시가에 걸쳐 하나 여러 지리적 위치입니다. 다중-지리적으로 분산 테 넌 트의 지리적 위치, 그룹 및 사용자 정보에 대 한 정보에서 Azure Active Directory (AAD) 마스터입니다. 테 넌 트 정보는 중앙에서 마스터 이며 각 지리적 위치에 동기화를 하기 때문에 공유 하 고 회사의 모든 사용자와 관련 된 경험 글로벌 인식 기능을 포함 합니다.
  
## <a name="sample-multi-geo-tenant-configuration"></a>샘플 geo 다중 테 넌 트 구성

다중-지리적으로 분산 테 넌 트를 사용 하 여 Contoso, 북미의 중앙 위치와로 확장할 수 있습니다 위성 지리적으로 분산 및 위치에 유럽, 오스트레일리아 단일 조직 우산 아래에서 Contoso.com의 합니다. 유럽으로 설정 하는 기본 데이터 위치와 사용자는 북미에서 자신의 기본 설정된 데이터의 위치와 사용자는 자신의 OneDrive 미국에서를 가지게 하는 동안 유럽에서 자신의 OneDrive를 갖게 됩니다.
  
![Contoso에 대 한 지리적 위치와 다른 사용 가능한 지리적 위치를 보여주는 거두었으며, 맵](images/df317ccc-2e53-411d-9211-a5aee63ca1e5.png)
  
## <a name="get-multi-geo-features-in-three-simple-steps"></a>간단한 세 단계를 확인할 수 있는 다중-지리적으로 분산 기능

다중-지리적으로 분산을 구성 하는 것은 쉽습니다.
  
1. 다중-지리적으로 분산에 대 한 Office 365 테 넌 트를 사용 하도록 설정 합니다.
    
2. 위성 위치를 추가 합니다.
    
3. 적절 한 위치에 대 한 사용자 계정을 구성 합니다.
    
## <a name="multi-geo-status-and-availability"></a>다중-지리적으로 분산 상태와 연락 가능성

OneDrive 다중-지리적으로 분산 이러한 지역 및 국가에서 현재 제공 됩니다.
  
- 아시아 태평양
    
- 오스트레일리아
    
- 캐나다
    
- 유럽 연합 (EMEA)
    
- 인도
    
- 일본
    
- 영국
    
- 미국 (북미)
    
- 대한민국
    
> [!NOTE]
> 인도 및 대한민국은 현재만 라이선스 및 이러한 지리적 위치에 대금 청구 주소와 고객을 위해 사용할 수 있습니다. 
  
예정 된 지리적 위치:
  
- 프랑스
    
사용 가능한 서비스:
  
- 미리 보기에서 온라인-exchange
    
- 비즈니스용 OneDrive-미리 보기
    
- SharePoint Online-개발
    

