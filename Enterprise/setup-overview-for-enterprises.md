---
title: 조직을 위해 Office 365 Enterprise 배포
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
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
ms.custom: Adm_O365
ms.assetid: ee73dafb-be54-492e-bcfd-0fbfb5f65e94
description: 다음 개요 단계는 Office 365를 배포하고 Active Directory를 연결하며 데이터를 마이그레이션하고 조직의 사용자가 최신 버전의 Office 2016 사용을 시작할 수 있도록 설계되었습니다.
ms.openlocfilehash: 2530b170c607f635f6f1baebf1d83fa7745d23a6
ms.sourcegitcommit: 47c6156c0038745103b71f44b2a3b103c62e5d6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2019
ms.locfileid: "34102546"
---
# <a name="deploy-office-365-enterprise-for-your-organization"></a>조직을 위해 Office 365 Enterprise 배포
온 - 프레미스 인프라와 함께 Office 365 Enterprise를 배포하고 통합할 준비가 되셨나요? 다음 개요 단계는 디렉토리를 연결하며 데이터를 마이그레이션하고 조직의 사용자가 최신 버전의 Office 2016 사용을 시작할 수 있도록 설계되었습니다.
  
이 단계는 Office 365 Enterprise의 사용자 지정 배포를 시작하려는 비즈니스 및 [비영리 기관](https://go.microsoft.com/fwlink/?LinkId=627221)을 위한 단계입니다. 
  
Office 365 Enterprise가 없습니까? 중소기업을 위한 지침은 [비즈니스 용 Office 365 설정](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa)을 참조하세요. 
  
## <a name="guided-enterprise-office-365-setup-process-with-fasttrack"></a>FastTrack을 사용한 기업용 Office 365 설치 프로세스
Office 365 **[FastTrack](https://docs.microsoft.com/fasttrack)** 은 Office 365를 배포하는 가장 좋은 방법입니다. FastTrack은 가장 일반적인 배포 구성을 안내하고 단계별로 질문에 답변할 수 있습니다. 파트너로부터 자가 진단 또는 지침을 원하는 경우 [Office 365 설치 가이드](https://support.office.com/article/Set-up-Office-365-for-business-6a3a29a0-e616-4713-99d1-15eda62d04fa), [Office 365 설치 마법사](https://aka.ms/o365fasttrack) 또는 [공식 파트너를 찾으십시오](https://partnercenter.microsoft.com/en-us/pcv/search).

## <a name="self-deployment-of-office-365"></a>Office 365의 자체 배포
직접 Office 365를 배포하려는 경우 다음 배포 단계가 도움을 드립니다.

1. **[Office 365를 준비합니다](get-your-organization-ready-for-office-365.md)**. 이러한 도구와 리소스를 통해 네트워크, 디렉터리 및 최종 사용자가 Office 365를 이용할 준비를 하는 데 도움이 됩니다.

2. **로그인 하 고 Office 365에 인터넷 도메인을 추가**합니다. [Microsoft 365 관리 센터](https://portal.microsoft.com)에 로그인 하 고 **설치 > 도메인**을 클릭 한 다음 **새 도메인**을 클릭 합니다. 사용자를 추가 하거나 전자 메일을 마이그레이션하지 않고 Office 365 구독에 하나 이상의 도메인을 추가 합니다. 

>[!IMPORTANT] 
>온-프레미스 디렉토리에서 사용자를 동기화하거나 Single Sign-On을 사용하려는 경우 기본 설치 지침이 작동하지 않습니다.

3. **[디렉터리를 Office 365에 연결합니다](about-office-365-identity.md)**. ID 동기화 및/또는 Single Sign-On 구성 옵션을 안내합니다. 사용자 지정된 설정 지침을 확인하려면 [AAD Connect 관리자](https://aka.ms/aadconnectpwsync) 및 [Azure AD Premium 설정 가이드](https://aka.ms/aadpguidance)를 사용합니다.
4. **[Office 365 서비스 및 응용 프로그램을 구성합니다](configure-services-and-applications.md)**. 전자 메일, 파일 공유, 인스턴트 메시징 또는 다른 Office 365 서비스 및 응용 프로그램 중 하나를 구성하려면 여기에서 시작합니다.
5. **[데이터를 Office 365로 마이그레이션합니다](migrate-data-to-office-365.md)**. 서비스가 구성되면 데이터 마이그레이션을 시작할 수 있습니다.
6. **[사용자가 Office 365를 사용하도록 합니다](https://support.office.com/article/Get-started-with-Office-365-for-business-d6466f0d-5d13-464a-adcb-00906ae87029)**. 조직의 사용자가 Office 365와 리소스를 사용하는 데 자신감을 갖도록 돕습니다.