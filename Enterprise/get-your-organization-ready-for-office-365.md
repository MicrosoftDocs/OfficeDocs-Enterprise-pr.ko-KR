---
title: 조직에서 Office 365 Enterprise를 사용할 수 있도록 준비
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 712fced7-f9d0-4fde-8b79-286262a5d0bc
description: fasttrack 배포를 옵트아웃 했으며 기본 배포 단계에서 필요한 사항을 찾지 못하는 경우에는이 작업을 시작 합니다.
ms.openlocfilehash: a15bd73efe2fd2e2dfd13b3a444f77b9d0bfc764
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487744"
---
# <a name="get-your-organization-ready-for-office-365-enterprise"></a>조직에서 Office 365 Enterprise를 사용할 수 있도록 준비

## <a name="what-do-you-need-to-do-to-get-ready-for-office-365"></a>Office 365을 준비 하기 위해 수행 해야 하는 작업은 무엇 인가요?

대부분의 조직은 Office 365을 준비 하기 위해 필요한 작업을 수행 하지 않아도 됩니다. 웹에 있는 응용 프로그램은 사용자가 계정을 사용 하는 즉시 사용할 수 있습니다. 다른 조직에는 추가 계획을 세우는 데 필요한 위치, 보안 관행 또는 기타 요구 사항이 있습니다. 엔터프라이즈 수준 조직의 경우 Office 365을 시작 하려면 아래의 검사 목록 항목을 참조 하세요.
  
Office 365를 설치하는 데 도움이 필요하면 [FastTrack](https://fasttrack.microsoft.com/office)이 Office 365를 배포하는 가장 쉬운 방법이며 로그인하여 [Office 365 서비스 배보 관리자](deployment-advisors-for-office-365.md)를 사용할 수도 있습니다.
  
|**시작 하려면 하나 이상의 항목을 선택 합니다.**||
|:-----|:-----|
| [Office의 시스템 요구 사항](https://products.office.com/office-system-requirements) |-Microsoft Office Professional, Office 365, office 365 ProPlus 및 Windows, Mac, iOS 및 Android 용 Office 응용 프로그램에는 모두 특정 시스템 요구 사항이 있습니다. 하드웨어 및 소프트웨어가 최소 시스템 요구 사항을 충족 하는지 확인 합니다.|
|**대부분** 의 고객은 온-프레미스 디렉터리를 Office 365에 연결 합니다. [네트워크에서 idfix를 설치 및 실행](https://www.microsoft.com/download/details.aspx?id=36832)하 여 디렉터리 준비에 대 한 시작을 확인 하세요. <br> [AAD Connect advisor](https://aka.ms/aadconnectpwsync) 및 [Azure AD Premium 설정 가이드](https://aka.ms/aadpguidance) 를 사용 하 여 사용자 지정 된 설정 지침을 확인 하세요. <br> |- [사용자 계정의 유효성을 검사](https://support.office.com/article/Prepare-to-provision-users-through-directory-synchronization-to-Office-365-01920974-9e6f-4331-a370-13aea4e82b3e)하기 위해 디렉터리에 대 한 자동화 된 검사가 자동으로 동기화 됩니다. <br> -디렉터리 개체를 변경 하 고 변경 내용을 자동화 하기 위한 서비스를 제공 합니다. <br> - [idfix 도구 사용에 대 한 자세한 내용](prepare-directory-attributes-for-synch-with-idfix.md) |
|[네트워크 성능 지침](https://aka.ms/tune) 을 **읽고** 도구를 사용 하 여 사용자에 게 최상의 환경을 제공 하는 데 필요한 연결성 및 성능 구성을 확인 합니다.  <br> | -office 365에 연결할 수 있는지 확인 하 고, 아웃 바운드 트래픽을 필터링 하거나 검사 하는 경우 조직에 대 한 [Office 365 끝점을 관리](https://support.office.com/article/Managing-Office-365-endpoints-99cab9d4-ef59-4207-9f2b-3728eb46bf9a) 하는 방법을 이해 하는 것이 좋습니다.  <br>  - 보다 예측 가능한 환경을 위해 [네트워크 용량을 모델링 및 테스트 하 고](https://support.office.com/article/Network-and-migration-planning-for-Office-365-f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132) [Office 365 회로에 대 한 Azure express](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd) 주소로 이동 합니다.   |
|[계획 검사 목록을](https://support.office.com/article/Deployment-planning-checklist-for-Office-365-5fa4f6ef-35ad-4840-91c1-4834df3df5a0) **사용** 하 여 고유한 배포 계획을 작성 하는 것이 적절 한 방법입니다.  <br> | 자세한 내용은 계획에 도움이 되는 참조 또는 방법 정보에 대 한 링크를 계획 해야 할 수 있습니다. |
|[Exchange Server 대규모 항목 스크립트](https://gallery.technet.microsoft.com/Exchange-Server-Large-Item-b9546cc6) 를 **사용** 하 여 마이그레이션할 수 없는 메일 항목을 찾습니다.  <br> | -Exchange 웹 서비스를 사용 하 여 사용자가 지정한 파일 크기에 대해 사서함을 가장, 액세스, 검색 하 고, 결과를 CSV 파일로 덤프 합니다. [스크립트 사용 방법에 대 한 자세한 지침](https://blogs.technet.com/b/mikehall/archive/2013/06/27/large-mail-item-script.aspx)을 읽으십시오. |
|**** 모든 사용자가 새 서비스 및 응용 프로그램을 사용 하기 시작할 수 있도록 계획 하는 데 도움이 되는 [Microsoft 배포 전문가](https://go.microsoft.com/fwlink/?LinkId=517115) 를 활용 합니다.  <br> [Office 365 서비스에 대 한 배포 마법사](https://support.office.com/article/Deployment-wizards-for-Office-365-services-165f46e8-3533-4d76-be57-97f81ebd40f2) 를 사용 하 여 사용자 지정 된 설정 지침을 확인 하세요.  <br> | -온 보 딩 센터는 고객과 파트너 조직과 직접 연동 됩니다. 오늘 전화를 제공 합니다. |
|[Office 365 성공 센터의 서식 파일과 리소스](https://www.microsoft.com/fasttrack/resources) 를 **사용** 하 여 배포 및 온 보 딩 계획을 조직의 사용자와 공유 합니다.  <br> | -Office 365로의 전환 전, 중 및 이후 모든 사용자와 통신 하는 것이 중요 합니다.  <br> -서식 파일, 가이드 및 유인물을 사용 하 여 통신을 향상 시킬 수 있습니다. |
|office [365 네트워크 연결 원리](https://aka.ms/o365networkingprinciples) 문서를 **읽고** office 365 트래픽을 안전 하 게 관리 하 고 가능한 최적의 성능을 얻는 데 필요한 연결 원칙을 이해 합니다.  <br> | -이 문서는 Office 365 네트워크 연결을 안전 하 게 최적화 하기 위한 가장 최근 지침을 이해 하는 데 도움이 됩니다. |
   
Office 365을 보다 광범위 한 클라우드 전략과 통합 하는 데 도움이 되는 리소스를 더 원하십니까? [Microsoft 클라우드 IT 아키텍처 리소스](https://docs.microsoft.com/en-us/office365/enterprise/microsoft-cloud-it-architecture-resources)는 다음과 같습니다.
  
## <a name="want-to-talk-with-support"></a>지원 서비스에 문의 하 고 싶으십니까?

여기에서 비즈니스 제품 지원에 [문의](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) 하는 것이 도움이 됩니다.
