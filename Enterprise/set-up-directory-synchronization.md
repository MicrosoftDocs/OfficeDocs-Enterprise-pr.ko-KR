---
title: Office 365의 디렉터리 동기화 설정
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: Office 365 및 온-프레미스 Active Directory 간에 디렉터리 동기화를 설정 하는 방법에 알아봅니다.
ms.openlocfilehash: e406eec08b34a694602c756235533f8b1ff6651e
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541941"
---
# <a name="set-up-directory-synchronization-for-office-365"></a>Office 365의 디렉터리 동기화 설정
Office 365 클라우드 기반 사용자 id 관리 서비스 Azure Active Directory를 사용 하 여 사용자를 관리 합니다. Office 365와 온-프레미스 환경을 동기화 하 여 Azure AD와 온-프레미스 Active Directory를 통합할 수 있습니다. 동기화를 설정한 후에 Azure AD 또는 온-프레미스 디렉터리 내에 수행 하는 사용자 인증을 결정할 수 있습니다.
  
## <a name="office-365-directory-synchronization"></a>Office 365 디렉터리 동기화
동기화 된 id 또는 온-프레미스 조직과 Office 365 간의 페더레이션된 id를 사용할 수 있습니다. 동기화 된 id를 가진 사용자가 온-프레미스, 관리 하 고 Azure AD를 사용 하는 경우 동일한 암호 클라우드에서 온-프레미스로 하 여 인증 합니다. 가장 일반적인 디렉터리 동기화 시나리오입니다. 통과 인증 또는 페더레이션 id를 관리할 수 있도록 사용자가 온-프레미스 및 온-프레미스 디렉터리에서 인증 합니다. 페더레이션된 id 추가 구성이 필요 하 고 사용자만 한 번 로그인 할 수 있습니다. 자세한 내용은 [Office 365 Id 이해 및 Azure Active Directory를](about-office-365-identity.md)읽어보십시오.
  
## <a name="want-to-upgrade-from-windows-azure-active-directory-sync-dirsync-to-azure-active-directory-connect"></a>Azure Active Directory 연결 하려면 Windows Azure Active Directory 동기화 (DirSync)에서 업그레이드 하려는 경우?
현재 디렉터리 동기화를 사용 하 고 업그레이드 하려는 경우을 향해 위에 [azure.com](https://azure.com) 에 [업그레이드 지침](https://go.microsoft.com/fwlink/p/?LinkId=733240)입니다.
  
## <a name="prerequisites-for-azure-ad-connect"></a>Azure AD에 대 한 필수 구성 요소에 연결
Office 365 구독을 Azure AD에 대 한 무료 구독을 얻을 수 있습니다. 디렉터리 동기화를 설정 하는 경우는 Azure Active Directory 연결에 설치한 온-프레미스 서버 중 하나입니다.
  
Office 365에 대 한 해야 합니다.
  
- 온-프레미스 도메인 (절차를 안내이 통해)을 확인 합니다.
- Office 365 테 넌 트에 대 한 권한이 파일 [비즈니스를 위한 Office 365의 관리 역할을 할당](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504) 하 고 온-프레미스 Active Directory 합니다. 
    
Azure AD 연결을 설치 하는 온-프레미스 서버에 대 한 다음과 같은 소프트웨어가 필요 합니다.
  
|**서버 운영 체제**|**기타 소프트웨어**|
|:-----|:-----|
|**Windows Server 2012 R2** | -PowerShell는 기본적으로 설치, 작업이 필요 하지 않습니다.  <br/> -Net 4.5.1 이후 릴리스에서 Windows Update를 통해 제공 되는 하 고 있습니다. 제어판에서 Windows 서버에 최신 업데이트를 설치한 후 있는지 확인 합니다. |
|**Windows Server 2008 R2 서비스 팩 1 (SP1)** 또는 **Windows Server 2012** | -최신 버전의 PowerShell Windows Management Framework 4.0에서 제공 됩니다. [Microsoft 다운로드 센터](https://go.microsoft.com/fwlink/p/?LinkId=717996)에서 검색.<br/> -.Net 4.5.1 및 이후 릴리스에서 [Microsoft 다운로드 센터](https://go.microsoft.com/fwlink/p/?LinkId=717996)에서 사용할 수 있습니다. |
|**Windows Server 2008** | -최신 지원 되는 버전의 PowerShell Windows Management Framework 3.0을 [Microsoft 다운로드 센터](https://go.microsoft.com/fwlink/p/?LinkId=717996)에서 사용할 수 있는에서 제공 됩니다.  <br/> -.Net 4.5.1 및 이후 릴리스에서 [Microsoft 다운로드 센터](https://go.microsoft.com/fwlink/p/?LinkId=717996)에서 사용할 수 있습니다. |
   
> [!NOTE]
> Azure Active Directory 디렉터리 동기화를 사용 하는 경우 온-프레미스 Active Directory에서 Azure Active Directory에는 동기화 할 수 있는 메일 그룹 구성원의 최대 수는 15, 000입니다. Azure AD 연결에 대 한 해당 번호가 50, 000입니다. 
  
Azure AD 연결에 대 한 하드웨어, 소프트웨어, 계정 및 권한 요구 사항, SSL 인증서 요구 사항 및 제한 개체를 더 신중 하 게 검토 하려면 [Azure Active Directory 연결에 대 한 필수 구성 요소](https://go.microsoft.com/fwlink/p/?LinkId=716896)를 읽습니다.
  
Azure AD 연결 [버전 릴리스 정보](https://go.microsoft.com/fwlink/p/?LinkId=733238) 포함 되며 각 버전에서 수정 된 기능을 검토할 수 있습니다. 

## <a name="to-set-up-directory-synchronization"></a>디렉터리 동기화를 설정 하려면
1. Office 365 관리 센터에 로그인 하 고 **사용자가** 선택 \> 왼쪽된 탐색 모음에 **현재 사용자** 입니다. 
2. Office 365 관리 센터의 **현재 사용자** 페이지에서 선택 * * 더 * * \> **디렉터리 동기화**합니다.
    
    ![더 많은 메뉴에서 디렉터리 동기화를 선택 합니다.](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. 에 * * 적합 디렉터리 동기화가? * * 페이지, **1 ~ 10**및 "조직의 크기에 따라, 것이 좋습니다 만들기 및 클라우드에서 사용자를 관리 하는에서 **11 ~ 50** 결과의 두 첫번째 선택. 디렉터리 동기화를 사용 하 여 하면 설치가 복잡 하 게 됩니다. 이동 하면 사용자를 추가 하려면 현재 사용자에 게. " 
    
    - 그러나 여전히, 디렉터리 동기화 설정 페이지의 아래쪽에 **여기에서 계속** 선택 하 여 계속할 수 있습니다. 
    
    - 두 후자의 선택 **51-250** 또는 **251 이상에서 작동할**을 선택 하는 경우 사용 하 여 동기화 설치 디렉터리 동기화를 권장 합니다. **다음** 계속을 선택 합니다. 
    
    ![디렉터리 동기화 설정을 계속 하려면 다음을 선택합니다](media/359a1eb9-99ae-4b5b-a413-4de53037cceb.png)
  
4. **동기화 클라우드와 로컬 디렉터리**정보를 확인 하 고 자세한 정보를 원하는 경우 알아보기로 이동 하는 자세한 내용 링크를 선택: [Office 365에 대 한 디렉터리 동기화를 통해 프로 비전 사용자에 게 준비](prepare-for-directory-synchronization.md)하 고 다음 **를 선택 합니다 **. 
    
5. **디렉터리를 확인해 보겠습니다** 페이지에서 자동으로 디렉터리를 검사 하는 것에 대 한 요구 사항을 검토 합니다. 요구를 충족 하는 경우 **다음** 을 선택 \> **검사를 시작**합니다. 요구 사항을 충족 수 없는 경우 **수동으로 계속**을 선택 하 여 계속할 수 있습니다.
    
    ![다음을 선택 또는 수동으로 계속는 보겠습니다 디렉터리 페이지에서 제품 키를 확인 합니다.](media/af4a6bd5-13aa-4bfa-9751-4464a32ca8db.png)
  
6. 디렉터리를 검사 하려면 선택 하는 경우 **디렉터리 동기화 설치 확인** 페이지에서 **검사 시작** 을 선택 합니다. 
    
    다운로드 하 여 검사를 실행 하는 지침을 따릅니다.
    
7. 검사가 완료 되 면 설치 마법사를 반환 하 고 **다음** 검색 결과 표시 하려면 선택 합니다. 
    
8. **도메인 소유권 확인** 페이지에서 설명 하는 대로 도메인을 확인 합니다. 자세한 지침은 [DNS 레코드를 관리 하는 경우 Office 365 용 DNS 레코드 만들기](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23)를 참조 하십시오.
    
    > [!IMPORTANT]
    > 소유 하 고 도메인을 확인 하려면 TXT 레코드를 추가한 후 도메인 마법사에서 사용자 추가 (영문)의 다음 단계로 이동 하지 마십시오. 디렉터리 동기화 하기에 대 한 사용자를 추가 합니다. 
  
    **Office 365 설치** 페이지로 돌아갑니다 하 고 **새로 고칠** 선택
    
    ![도메인을 확인 한 후 새로 고침을 선택 합니다.](media/9b5fb593-5ff7-49f0-80d0-18e36d39d669.png)
  
9. **도메인 준비가 완료** 페이지에서 **다음**을 선택 합니다.
    
10. **환경을 정리** 페이지에서 필요에 따라 Active Directory를 확인 하는 IDFix를 다운로드 하려면 지침을 따릅니다. **다음** 계속을 선택 합니다. 
    
11. 에 * * 실행 Azure Active Directory 연결 * * 페이지에서 Azure AD 연결 마법사를 설치 하려면 **다운로드** 를 선택 합니다. 
    
    > [!NOTE]
    > 이 시점에서 Azure AD 연결 마법사에서 수 있습니다. 한다고 가정해봅니다. 마지막 열 브라우저에서 Azure AD 연결 단계 완료 한 후 돌아갈 수 있도록 하는 디렉터리 동기화 마법사 페이지를 두면 있는지 확인 하십시오. 
  
    Azure AD 연결 마법사가 설치 후 자동으로 열립니다. 기본 설치 사이트 바탕 화면에서 열 수 있습니다. 자신의 시나리오에 따라 마법사 지침을 따릅니다.
    
  - 암호 해시 동기화와 디렉터리 동기화를 위해 [express 설정 사용 하 여 Azure AD 연결](https://go.microsoft.com/fwlink/p/?LinkID=698537)을 사용 합니다.
    
  - 다중 포리스트, 통과 인증, 페더레이션된 id 및 SSO 옵션을 [사용자 지정 설치의 Azure AD 연결](https://go.microsoft.com/fwlink/p/?LinkId=698430)을 사용 합니다.
    
    이러한 옵션을 사용 하 여 **Express 설정** 페이지에서 **사용자 지정** 을 선택 합니다. 
    
12. Azure AD 연결 마법사가 완료 되 면 **Office 365 설치** 마법사를 반환 하 고 **페이지 예상된 대로 작동 하는지 동기화 확인**에 지침을 따릅니다. **다음** 계속을 선택 합니다. 
    
13. 지침에 읽기는 * * 사용자 활성화를 * * 페이지 하 고 **다음**을 선택 합니다.
    
14. **모든 설치 하 고 있는** 페이지에서 **완료** 를 선택 합니다. 
    
## <a name="assign-licences-to-synchronized-users"></a>동기화 된 사용자에 게 라이센스 할당
Office 365로 사용자 동기화 한 후 만들어질 때 하지만 메일 등의 Office 365 기능을 사용 하 여 수 자신에 게 라이선스를 할당 해야 합니다. 자세한 내용은 [비즈니스를 위한 Office 365에서 사용자에 게 라이선스 할당](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc)을 참조 하십시오.
    
## <a name="finish-setting-up-domains"></a>도메인 설정이 완료
도메인 설정이 완료 [DNS 레코드를 관리 하는 경우 Office 365 용 DNS 레코드 만들기](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) 단계를 수행 합니다.