---
title: Office 365의 디렉터리 동기화 설정
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED15
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: Office 365와 온-프레미스 Active directory 간에 디렉터리 동기화를 설정 하는 방법에 대해 알아봅니다.
ms.openlocfilehash: 5f6e5be2a2137ee183a7d592d9a3e6b086e5be9a
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085267"
---
# <a name="set-up-directory-synchronization-for-office-365"></a>Office 365의 디렉터리 동기화 설정

Office 365에서는 클라우드 기반 사용자 id 관리 서비스 Azure Active Directory를 사용 하 여 사용자를 관리 합니다. 온-프레미스 환경을 Office 365와 동기화 하 여 온-프레미스 Active Directory를 Azure AD와 통합할 수도 있습니다. 동기화를 설정한 후에는 Azure AD 또는 온-프레미스 디렉터리 내에서 사용자 인증을 수행 하도록 결정할 수 있습니다.
  
## <a name="office-365-directory-synchronization"></a>Office 365 디렉터리 동기화

온-프레미스 조직과 Office 365 간에 동기화 된 id 또는 페더레이션 id를 사용할 수 있습니다. 동기화 된 id를 사용 하면 온-프레미스에서 사용자를 관리 하며, 온-프레미스와 클라우드에서 동일한 암호를 사용 하는 경우 Azure AD에서 인증 됩니다. 가장 일반적인 디렉터리 동기화 시나리오입니다. 통과 인증 또는 페더레이션 id를 통해 온-프레미스에서 사용자를 관리할 수 있으며 온-프레미스 디렉터리에서 인증을 받습니다. 페더레이션 id는 추가 구성을 필요로 하며 사용자가 한 번만 로그인 할 수 있도록 합니다. 자세한 내용은 [Office 365 id 및 Azure Active Directory 이해](about-office-365-identity.md)를 참조 하세요.
  
## <a name="want-to-upgrade-from-windows-azure-active-directory-sync-dirsync-to-azure-active-directory-connect"></a>Windows azure active directory 동기화 (DirSync)에서 Azure active directory Connect로 업그레이드 하 시겠습니까?

현재 DirSync를 사용 중 이며 업그레이드 하려면 [azure.com](https://azure.com) 으로 [업그레이드 지침을 참조](https://go.microsoft.com/fwlink/p/?LinkId=733240)하세요.
  
## <a name="prerequisites-for-azure-ad-connect"></a>Azure AD Connect에 대 한 필수 구성 요소

Office 365 구독을 사용 하 여 Azure AD에 대 한 무료 구독을 받을 수 있습니다. 디렉터리 동기화를 설정할 때 온-프레미스 서버 중 하나에 Azure Active directory Connect를 설치 합니다.
  
Office 365의 경우 다음을 수행 해야 합니다.
  
- 온-프레미스 도메인을 확인 합니다 (이 절차에서는이 과정을 안내 합니다.).
- office 365 테 넌 트 및 온-프레미스 Active Directory에 대 한 [office 365의 비즈니스 권한에 대해 관리자 역할 할당](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504) 을 사용 하도록 설정 합니다.

Azure AD Connect를 설치 하는 온-프레미스 서버에 대해 다음 소프트웨어가 필요 합니다.
  
|**서버 OS**|**기타 소프트웨어**|
|:-----|:-----|
|**Windows Server 2012 R2** | -PowerShell은 기본적으로 설치 되며 아무 작업도 필요 하지 않습니다.  <br> -Net 4.5.1 이상 버전은 Windows Update를 통해 제공 됩니다. 제어판에 Windows Server에 대 한 최신 업데이트를 설치 했는지 확인 합니다. |
|**windows server 2008 R2 서비스 팩 1 (SP1)** 또는 **Windows server 2012** | -PowerShell의 최신 버전은 Windows Management Framework 4.0에서 사용할 수 있습니다. [Microsoft 다운로드 센터](https://go.microsoft.com/fwlink/p/?LinkId=717996)에서 해당 파일을 검색 합니다.<br> - [Microsoft 다운로드 센터](https://go.microsoft.com/fwlink/p/?LinkId=717996)에서 .net 4.5.1 이상 버전을 사용할 수 있습니다. |
|**Windows Server 2008** | - [Microsoft 다운로드 센터](https://go.microsoft.com/fwlink/p/?LinkId=717996)에서 제공 하는 Windows Management Framework 3.0에서 지원 되는 최신 버전의 PowerShell을 사용할 수 있습니다.  <br> - [Microsoft 다운로드 센터](https://go.microsoft.com/fwlink/p/?LinkId=717996)에서 .net 4.5.1 이상 버전을 사용할 수 있습니다. |

> [!NOTE]
> azure active directory DirSync를 사용 하는 경우 온-프레미스 Active directory에서 azure active directory로 동기화 할 수 있는 메일 그룹 구성원의 최대 수는 15000입니다. Azure AD Connect의 경우 해당 번호는 5만입니다. 
  
azure AD Connect에 대 한 하드웨어, 소프트웨어, 계정 및 사용 권한 요구 사항, SSL 인증서 요구 사항 및 개체 제한을 보다 신중 하 게 검토 하 여 [azure Active Directory connect에 대 한 필수 구성 요소](https://go.microsoft.com/fwlink/p/?LinkId=716896)를 읽으십시오.
  
또한 Azure AD Connect [버전 릴리스 기록을](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) 검토 하 여 각 릴리스에서 포함 및 수정 된 항목을 확인할 수 있습니다.

## <a name="to-set-up-directory-synchronization"></a>디렉터리 동기화를 설정 하려면

1. Office 365 관리 센터에 로그인 하 고 왼쪽 탐색 창에서 **사용자** \> **활성 사용자** 를 선택 합니다.
2. Office 365 관리 센터의 **활성 사용자** 페이지에서 **더 많은** \> **디렉터리 동기화**를 선택 합니다.

    ![기타 메뉴에서 디렉터리 동기화를 선택 합니다.](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. **Active directory 준비** 페이지에서 시작 하기 위한 **Microsoft Azure Active Directory 연결 도구 다운로드** 링크를 선택 합니다. azure Active Directory connect 설치 프로세스에 대 한 자세한 내용은 [azure ad connect 및 azure ad connect Health 설치 로드맵](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap)를 참조 하세요.

## <a name="assign-licenses-to-synchronized-users"></a>동기화 된 사용자에 게 라이선스 할당

사용자를 Office 365로 동기화 한 후에는이를 만들지만, 메일 등의 office 365 기능을 사용할 수 있도록 라이선스를 할당 해야 합니다. 자세한 내용은 [비즈니스용 Office 365의 사용자에 게 라이선스 할당](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc)을 참조 하세요.

## <a name="finish-setting-up-domains"></a>도메인 설정 완료

dns 레코드를 관리 하 여 도메인 설정을 완료 하려면 [Office 365에 대 한 dns 레코드 만들기](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) 의 단계를 수행 합니다.