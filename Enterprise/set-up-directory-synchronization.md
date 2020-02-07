---
title: Office 365에서 디렉터리 동기화 설정
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
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
description: Office 365와 온-프레미스 Active Directory 간에 디렉터리 동기화를 설정 하는 방법에 대해 알아봅니다.
ms.openlocfilehash: d549d2b56ef1d642e5dfc16b747e6eb909dd7337
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844049"
---
# <a name="set-up-directory-synchronization-for-office-365"></a>Office 365에서 디렉터리 동기화 설정

*이 문서는 Microsoft 365 Enterprise와 Office 365 Enterprise에 모두 적용됩니다.*

Office 365에서는 azure Active Directory (Azure AD) 테 넌 트를 사용 하 여 인증 및 클라우드 기반 리소스에 액세스 하기 위한 사용 권한을 위한 id를 저장 하 고 관리 합니다. 

온-프레미스 AD DS (Active Directory 도메인 서비스)를 사용 하는 경우 AD DS 사용자 계정, 그룹 및 연락처를 Office 365 구독의 Azure AD 테 넌 트와 동기화 할 수 있습니다. Office 365의 하이브리드 id입니다. 구성 요소는 다음과 같습니다.

![Office 365의 디렉터리 동기화 구성 요소](./media/about-office-365-identity/hybrid-identity.png)

Azure AD Connect는 온-프레미스 서버에서 실행 되며 AD DS를 Azure AD 테 넌 트와 동기화 합니다. 또한 디렉터리 동기화와 함께 다음과 같은 인증 옵션을 지정할 수 있습니다.

- 암호 해시 동기화 (PHS)

  Azure AD는 인증 자체를 수행 합니다.

- 통과 인증(PTA)

  Azure AD에 AD DS가 인증을 수행 합니다.

- 페더레이션 인증

  Azure AD는 클라이언트 컴퓨터에서 인증 요청을 리디렉션하여 다른 id 공급자에 게 연결 합니다.

자세한 내용은 [하이브리드 id](plan-for-directory-synchronization.md) 를 참조 하세요.
  
## <a name="1-review-prerequisites-for-azure-ad-connect"></a>1. Azure AD Connect에 대 한 필수 구성 요소 검토

Office 365 구독을 사용 하 여 무료 Azure AD 구독을 받을 수 있습니다. 디렉터리 동기화를 설정할 때 온-프레미스 서버 중 하나에 Azure AD Connect를 설치 합니다.
  
Office 365의 경우 다음 작업을 수행 해야 합니다.
  
- 온-프레미스 도메인을 확인 합니다. Azure AD Connect 마법사는이 과정을 안내 합니다.
- Office 365 테 넌 트 및 AD DS의 관리자 계정에 대 한 사용자 이름 및 암호를 가져옵니다.

Azure AD Connect를 설치 하는 온-프레미스 서버의 경우 다음이 필요 합니다.
  
|**서버 OS**|**기타 소프트웨어**|
|:-----|:-----|
|Windows Server 2012 R2 이상 | -PowerShell은 기본적으로 설치 되며 아무 작업도 필요 하지 않습니다.  <br> -Net 4.5.1 이상 버전은 Windows Update를 통해 제공 됩니다. 제어판에 Windows Server에 대 한 최신 업데이트를 설치 했는지 확인 합니다. |
|Windows Server 2008 R2 서비스 팩 1 (SP1) * * 또는 Windows Server 2012 | -PowerShell의 최신 버전은 Windows Management Framework 4.0에서 사용할 수 있습니다. [Microsoft 다운로드 센터](https://go.microsoft.com/fwlink/p/?LinkId=717996)에서 해당 파일을 검색 합니다.  <br> - [Microsoft 다운로드 센터](https://go.microsoft.com/fwlink/p/?LinkId=717996)에서 .net 4.5.1 이상 버전을 사용할 수 있습니다. |
|Windows Server 2008 | - [Microsoft 다운로드 센터](https://go.microsoft.com/fwlink/p/?LinkId=717996)에서 제공 하는 Windows Management Framework 3.0에서 지원 되는 최신 버전의 PowerShell을 사용할 수 있습니다.  <br> - [Microsoft 다운로드 센터](https://go.microsoft.com/fwlink/p/?LinkId=717996)에서 .net 4.5.1 이상 버전을 사용할 수 있습니다. |

Azure AD Connect에 대 한 하드웨어, 소프트웨어, 계정 및 사용 권한 요구 사항, SSL 인증서 요구 사항 및 개체 제한에 대 한 자세한 내용은 [Azure Active Directory Connect의 필수 구성 요소](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites) 를 참조 하세요.
  
또한 Azure AD Connect [버전 릴리스 기록을](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) 검토 하 여 각 릴리스에서 포함 및 수정 된 항목을 확인할 수 있습니다.

## <a name="2-install-azure-ad-connect-and-configure-directory-synchronization"></a>2. Azure AD Connect를 설치 하 고 디렉터리 동기화를 구성 합니다.

시작 하기 전에 다음을 확인 해야 합니다.

- Office 365 전역 관리자의 사용자 이름 및 암호
- AD DS 도메인 관리자의 사용자 이름 및 암호
- 어떤 인증 방법 (PHS, PTA, 페더레이션된)
- [AZURE AD 원활한 sso (Single sign-on)](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso) 를 사용 하 고 있는지 여부

다음 단계를 따릅니다:

1. [Microsoft 365 관리 센터](https://admin.microsoft.com) 에 로그인https://admin.microsoft.com) 하 고 왼쪽 탐색 창에서 **사용자** \> **활성 사용자** 를 선택 합니다.
2. **활성 사용자** 페이지에서 **더** (3 개의 점) \> **디렉터리 동기화**를 선택 합니다.
  
3. **Azure Active Directory 준비** 페이지에서 **다운로드 센터로 이동을 선택 하 여 Azure AD Connect 도구** 링크를 시작 하도록 설정 합니다. 
4. [AZURE Ad connect 및 AZURE Ad Connect Health 설치 로드맵](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap)의 단계를 수행 합니다.

## <a name="3-finish-setting-up-domains"></a>3. 도메인 설정 마침

DNS 레코드를 관리 하 여 도메인 설정을 완료 하려면 [Office 365에 대 한 dns 레코드 만들기](https://docs.microsoft.com/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) 의 단계를 수행 합니다.

## <a name="next-step"></a>다음 단계

[사용자 계정에 라이선스 할당](assign-licenses-to-user-accounts.md)
