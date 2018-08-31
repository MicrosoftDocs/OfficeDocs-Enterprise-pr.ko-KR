---
title: 조직의 Office 365 Enterprise에 대 한 준비
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 712fced7-f9d0-4fde-8b79-286262a5d0bc
description: FastTrack 배포 로그 아웃 선택할 수 없는 찾기 (영문)이 기본 배포 단계를 수행 해야 하는 경우 시작 위치입니다.
ms.openlocfilehash: 552579347ae5f4b72821d350a061f3ba8d48841b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542218"
---
# <a name="get-your-organization-ready-for-office-365-enterprise"></a>조직의 Office 365 Enterprise에 대 한 준비

## <a name="what-do-you-need-to-do-to-get-ready-for-office-365"></a>Office 365에 대 한 준비 하기 위해 수행 하 시겠습니까?

대부분의 조직에서는 Office 365에 대 한 준비 작업을 수행할 필요가 없습니다. 웹 응용 프로그램 이므로 사용자 계정을 포함 하는 즉시이 사용할 수 있습니다. 다른 조직은 더 많은 위치, 보안 사례 또는 더 많은 계획에 대 한 필요성을 만들 수 있는 다른 요구 사항은 있습니다. 엔터프라이즈 수준의 조직에 대 한 Office 365 시작 하려면 아래의 검사 목록 항목을 따릅니다.
  
도움이 필요한 경우를 설정 하는 Office 365 시작 [FastTrack](https://fasttrack.microsoft.com/office) 는 Office 365를 배포 하는 것이 가장 편리 방법도에 로그인 하 고 [Office 365 서비스에 대 한 배포 문에](deployment-advisors-for-office-365.md)사용할 수 있습니다.
  
|**시작 하기를 하나 이상 선택 합니다.**||
|:-----|:-----|
| [Office에 대 한 시스템 요구 사항](https://products.office.com/office-system-requirements) |Microsoft Office Professional, Office 365, Office 365 ProPlus 및 각 Office 응용 프로그램을 Windows, Mac, iOS, 및 Android 모두에 대 한 특정 시스템 요구 사항이 있습니다. 하드웨어 및 소프트웨어 모임에 최소 시스템 요구 사항을 확인 합니다.|
|온-프레미스 디렉터리의 Office 365에 연결 하는 **대부분** 의 고객. [설치 하 고 네트워크에 IdFix를 실행 하](https://www.microsoft.com/download/details.aspx?id=36832)여 디렉터리 준비에 쉽게 시작할을 얻습니다.<br> [Advisor AAD 연결](https://aka.ms/aadconnectpwsync) 하 고 [Azure AD 프리미엄 가이드 설정](https://aka.ms/aadpguidance) 를 사용 하 여 지침을 사용자 지정 된 집합을 가져옵니다. <br> |--에 디렉터리에 대 한 검사를 자동화 하는 중 [사용자의 유효성을 검사 계정을 동기화가 제대로](https://support.office.com/article/Prepare-to-provision-users-through-directory-synchronization-to-Office-365-01920974-9e6f-4331-a370-13aea4e82b3e)합니다. <br> -변경 내용에서 권장 하는 디렉터리 개체 및 수에 대 한 변경 내용을 자동화를 제공 합니다. <br> - [IdFix 도구를 사용 하 여 대 한 자세한 내용](prepare-directory-attributes-for-synch-with-idfix.md)은. |
|**읽기** 수를 확인 하는 도구에서 최상의 사용자 들에 게 필요한 연결 및 성능 구성 되어이 [네트워크 성능 지침](https://aka.ms/tune) 및 사용 합니다.  <br/> | -Filter 또는 아웃 바운드 검사 하는 경우 Office 365에 연결할 수 있도록 트래픽, 싶어하는 어떤 [Office 365 끝점을 관리](https://support.office.com/article/Managing-Office-365-endpoints-99cab9d4-ef59-4207-9f2b-3728eb46bf9a) 하면 조직에 대 한 것을 의미를 이해 합니다.  <br/>  - [모델 네트워크 용량을 테스트 하 고](https://support.office.com/article/Network-and-migration-planning-for-Office-365-f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132) 또는 보다 예측 가능한 환경을 [Office 365 용 Azure ExpressRoute](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd) 회로를 이동 합니다.  <br/> |
|이 [계획 검사 목록](https://support.office.com/article/Deployment-planning-checklist-for-Office-365-5fa4f6ef-35ad-4840-91c1-4834df3df5a0) 직접 배포 계획을 작성을 위한 시작 지점으로 **사용**  <br/> | -가능한 영역 심도 깊은 개요 계획 하는데 도움이 되는 참조 (영문) 또는 사용 방법 정보에 대 한 링크와 계획에 필요 합니다.  <br/> |
|**사용 하 여** [Exchange Server 큰 항목 스크립트](https://gallery.technet.microsoft.com/Exchange-Server-Large-Item-b9546cc6) 너무 커서 마이그레이션할 수 있는 메일 항목을 찾으려고 합니다.  <br/> | -를 사용 하 여 Exchange 웹 서비스를 가장, 액세스, 파일 크기를 지정 하면 및 덤프 CSV 파일의 결과 대 한 사서함을 검색 합니다. [스크립트를 사용 하는 방법에 대 한 자세한 지침](https://blogs.technet.com/b/mikehall/archive/2013/06/27/large-mail-item-script.aspx)을 읽습니다.<br/> |
|**수행** 활용 도움을 받을 수 계획에서 모든 사람을 내리도록 지원 하려면 [Microsoft 배포 전문가](https://go.microsoft.com/fwlink/?LinkId=517115) 새로운 서비스 및 응용 프로그램을 사용 하 여 시작 합니다.  <br/> [Office 365 서비스에 대 한 배포 마법사](https://support.office.com/article/Deployment-wizards-for-Office-365-services-165f46e8-3533-4d76-be57-97f81ebd40f2) 를 사용 하 여 지침을 사용자 지정 된 집합을 가져옵니다.  <br/> | 온 보 딩 센터-고객 및 파트너 조직과 직접 작동합니다. 부여한 전화 오늘 합니다.  <br/> |
|**사용 하 여** 수 있는 [서식 파일 및 Office 365 성공 센터의 리소스를](https://fasttrack.microsoft.com/office/drive-value/engage) 배포 및 온 보 딩 공유 조직에는 다른 사람들과 계획입니다.  <br/> | -전, 중, Office 365로 전환 된 후 모든 사용자와 통신 하는 것이 중요 합니다.  <br/> -통신을 향상 시키기 위해이 서식 파일, 가이드, 및 유인물을 사용 합니다.  <br/> |
|**읽기** 가능한 최고의 성능을 시작 및 안전 하 게 Office 365 트래픽을 관리 하기 위한 연결 원칙을 이해 하려면 [Office 365 네트워크 연결 원칙](https://aka.ms/o365networkingprinciples) 문서입니다.  <br/> | -이 문서는 안전 하 게 Office 365 네트워크 연결을 최적화 하는 것에 대 한 최신 지침을 이해 하는데 도움이 됩니다.  <br/> |
   
Office 365 광범위 한 클라우드 전략에 통합할 수 있도록 더 많은 리소스를 설정할지 여부 [Microsoft 클라우드 IT 아키텍처 리소스는](https://docs.microsoft.com/en-us/office365/enterprise/microsoft-cloud-it-architecture-resources)다음과 같습니다.
  
## <a name="want-to-talk-with-support"></a>지원에 게 문의 하기 싶으십니까?
도움말 비즈니스 제품에 대 한 [지원 문의](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) 필요 하세요.
