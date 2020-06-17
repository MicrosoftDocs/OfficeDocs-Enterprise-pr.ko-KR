---
title: 조직에 Microsoft 365 Enterprise 배포
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/19/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- M365-subscription-management
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.assetid: ee73dafb-be54-492e-bcfd-0fbfb5f65e94
description: 이러한 개요 단계는 네트워크 설정, id 만들기, 엔터프라이즈 용 Microsoft 365 앱 배포, 데이터 마이그레이션, 조직의 사용자가 Microsoft 365 사용을 시작 하는 데 도움을 주기 위한 것입니다.
ms.openlocfilehash: 274cd4ae285ae97825b4d46a125cd9eeecf83312
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2020
ms.locfileid: "44735946"
---
# <a name="deploy-microsoft-365-enterprise-for-your-organization"></a>조직에 Microsoft 365 Enterprise 배포

Microsoft 365 Enterprise를 배포 하 고, 온-프레미스 인프라와 통합 하 고, 직원이 클라우드 기반 생산성 및 공동 작업을 활용할 수 있도록 준비 되었습니까?

이 문서에서는 사용자가 도움을 받을 수 있도록 할지 여부와 관계 없이 두 가지 배포 옵션을 설명 합니다. 각각의 경우에 Microsoft는 배포 성공을 위해 사용할 수 있는 안내 경로를 제공 합니다.

## <a name="guided-microsoft-365-enterprise-setup-process-with-fasttrack"></a>안내가 제공 되는 Microsoft 365 Enterprise 설치 프로세스 (FastTrack)

Microsoft 365 배포를 위한 최선의 방법은 **[microsoft 365에 대 한 Fasttrack](https://www.microsoft.com/fasttrack/microsoft-365)** 입니다. FastTrack은 가장 일반적인 배포 구성을 안내하고 단계별로 질문에 답변할 수 있습니다. 

일련의 설치 가이드에 액세스 하려면 Microsoft 365 구독에 로그인 한 다음 [설정 지침](https://aka.ms/o365fasttrack)으로 이동 합니다.

>[!Note]
>[Microsoft 파트너](https://www.microsoft.com/solution-providers/home)로부터 도움을 받을 수도 있습니다.
>

## <a name="do-it-yourself-guided-deployment-of-microsoft-365-enterprise"></a>Microsoft 365 Enterprise의 직접 실행을 안내 하는 배포

Microsoft 365 Enterprise를 직접 배포 하려면 Microsoft 365 서비스 구성 및 사용자 채택을 간소화 하는 디자인 결정을 내리기 위해 자세한 조사를 수행 해야 합니다. [계획을](get-your-organization-ready-for-office-365.md)시작 합니다.

계획을 완료 한 후에 Microsoft 365 Enterprise를 자체 배포 하려면 다음 단계를 수행 하는 것이 좋습니다.

1. [네트워크 설정](set-up-network-for-office-365.md)

   인터넷 도메인을 추가 하 고 온-프레미스 사용자의 네트워크 성능 최적화를 포함 합니다.
 
2. [Id 설정](protect-your-global-administrator-accounts.md)

   온-프레미스 AD DS (Active Directory 도메인 서비스)와 Microsoft 365 구독 간에 디렉터리 동기화를 설정 하는 id 모델 (클라우드 전용 또는 하이브리드)을 확인 하 고 하이브리드 id에 대 한 설정을 포함 합니다.

3. [보안 구현](https://docs.microsoft.com/office365/securitycompliance/security-roadmap)

   최초 30 일, 90 일 및 그 이상에서 테 넌 트 및 id에 대 한 기본 및 향상 된 보안, 위협 및 정보 보호를 구성 하 고 배포 하는 방법을 설명 합니다.
 
4. [클라이언트 소프트웨어 배포](https://docs.microsoft.com/DeployOffice/deployment-guide-microsoft-365-apps)

   장치에 Office 제품군 (Word, Excel, PowerPoint 및 기타)의 클라우드 업데이트 및 현재 버전인 office 365 ProPlus 라는 Microsoft 365 앱을 배포 하는 작업이 포함 되어 있습니다. 모든 Microsoft 365 클라이언트 라이선스에는 Microsoft 365 앱 for enterprise 라이선스가 포함 되어 있습니다.
 
5. [모바일 장치 관리 설정](https://support.office.com/article/set-up-mobile-device-management-mdm-in-office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)

   Microsoft 365 Enterprise에는 사용자의 모바일 장치를 보호 하 고 관리 하는 데 사용할 수 있는 모바일 장치 관리 기능이 포함 되어 있습니다.
 
6. [서비스 및 응용 프로그램 구성](configure-services-and-applications.md)

   데이터 마이그레이션에 대 한 정보와 Exchange Online, SharePoint Online 및 팀과 같은 주요 Microsoft 365 생산성 앱을 시작 하는 문서에 대 한 링크를 제공 합니다.
 
7. [사용자 교육](https://docs.microsoft.com/office365/admin/admin-overview/get-started-with-office-365#training-resources-for-your-users)

   사용자가 Microsoft 365를 빠르게 최대한 활용할 수 있도록 돕는 짧은 비디오가 포함 되어 있습니다.
 

>[!Note]
>이러한 단계는 Microsoft 365 Enterprise의 사용자 지정 배포를 시작 하려는 [비즈니스 및 비영리](https://go.microsoft.com/fwlink/?LinkId=627221) 에도 적용 됩니다. 
>
