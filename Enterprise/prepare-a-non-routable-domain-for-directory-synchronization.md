---
title: 디렉터리 동기화를 위해 라우팅할 수 없는 도메인 준비
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365E_SetupDirSyncLocalDir
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: e7968303-c234-46c4-b8b0-b5c93c6d57a7
description: Microsoft 365와 동기화 하기 전에 온-프레미스 사용자와 연결 된 routale 도메인이 있는 경우 수행 해야 하는 작업에 대해 알아봅니다.
ms.openlocfilehash: a9fe6f21dd1e2d9ade6288a083f700fccac4e6e4
ms.sourcegitcommit: 20c8c98c0b32d8cf56d50cbc70f82fd5c4ce649c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45263600"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a>디렉터리 동기화를 위해 라우팅할 수 없는 도메인 준비
온-프레미스 디렉터리를 Microsoft 365와 동기화 하는 경우 Azure Active Directory (Azure AD)에서 확인 된 도메인이 있어야 합니다. 온-프레미스 도메인과 연결 된 UPN (사용자 계정 이름)만 동기화 됩니다. 하지만 예를 들어 라우팅할 수 없는 도메인을 포함 하는 UPN은 billa@contoso와 마찬가지로 billa@contoso.onmicrosoft.com와 같은 onmicrosoft.com 도메인에 동기화 됩니다. 

현재 AD DS (Active Directory 도메인 서비스)의 사용자 계정에 대해 로컬 도메인을 사용 하는 경우에는 Microsoft 365 도메인과 적절 하 게 동기화 하기 위해 확인 된 도메인 (예 billa@contoso.com)을 사용 하도록 변경 하는 것이 좋습니다.
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a>로컬 온-프레미스 도메인만 있는 경우에는 어떻게 하나요?

AD DS를 Azure AD와 동기화 하는 데 사용할 수 있는 가장 최근 도구를 Azure AD Connect 라고 합니다. 자세한 내용은 [AZURE AD와 온-프레미스 Id 통합](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad)을 참조 하세요.
  
Azure AD Connect 사용자가 온-프레미스에서 사용 하는 것과 동일한 자격 증명으로 로그인 할 수 있도록 사용자의 UPN과 암호를 동기화 합니다. 그러나 Azure AD Connect는 Microsoft 365에서 확인 한 도메인에만 사용자를 동기화 합니다. 이는 Microsoft 365 id가 Azure AD에서 관리 되므로 Azure AD에서 도메인을 확인 하는 것을 의미 합니다. 즉, 도메인은 유효한 인터넷 도메인 (예: .com, org, .net, 미국 등) 이어야 합니다. 내부 AD DS가 라우팅할 수 없는 도메인 (예: .local)을 사용 하는 경우이는 Microsoft 365에 있는 확인 된 도메인과 일치할 수도 없습니다. 온-프레미스 AD DS에서 주 도메인을 변경 하거나 하나 이상의 UPN 접미사를 추가 하 여이 문제를 해결할 수 있습니다.
  
### <a name="change-your-primary-domain"></a>**주 도메인 변경**

Microsoft 365에서 확인 한 도메인 (예: contoso.com)으로 주 도메인을 변경 합니다. 그런 다음 contoso.com으로 업데이트 되는 contoso 라는 도메인이 있는 모든 사용자입니다. 자세한 내용은 [도메인 이름 바꾸기 작동 방법을](https://go.microsoft.com/fwlink/p/?LinkId=624174)참조 하세요. 이는 매우 관련이 있는 프로세스 이며, 다음 섹션에서 보다 쉬운 솔루션을 설명 합니다.
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a>**UPN 접미사를 추가 하 고 사용자를 업데이트 합니다.**

Microsoft 365에서 확인 한 도메인 (또는 도메인)과 일치 하도록 AD DS에서 새 UPN 접미사 또는 접미사를 등록 하 여 로컬 문제를 해결할 수 있습니다. 새 접미사를 등록 한 후에는 사용자 Upn을 새 도메인 이름 (예: billa@contoso.com으로 바꿉니다.
  
확인 된 도메인을 사용 하도록 Upn을 업데이트 한 후에는 온-프레미스 AD DS를 Microsoft 365과 동기화 할 수 있습니다.
  
 **1 단계: 새 UPN 접미사 추가**
  
1. AD DS 도메인 컨트롤러의 서버 관리자에서 **도구** \> **Active Directory 도메인 및 트러스트**를 선택 합니다.
    
    **또는 Windows Server 2012이 없는 경우**
    
    **Windows 키 + R** 을 눌러 **실행** 대화 상자를 열고 도메인 .msc를 입력 한 다음 **확인**을 선택 합니다.
    
    ![Active Directory 도메인 및 트러스트를 선택 합니다.](media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. **Active Directory 도메인 및 트러스트** 창에서 **active Directory 도메인 및 트러스트**를 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 선택 합니다.
    
    ![Active Directory 도메인 및 트러스트를 마우스 오른쪽 단추로 클릭 하 고 속성을 선택 합니다.](media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. **Upn 접미사** 탭의 **대체 UPN 접미사** 상자에 새 upn 접미사 또는 접미사를 입력 한 다음 적용 **추가** 를 선택 \> **Apply**합니다.
    
    ![새 UPN 접미사 추가](media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    접미사 추가가 완료 되 면 **확인을** 선택 합니다. 
    
 **2 단계: 기존 사용자에 대 한 UPN 접미사 변경**
  
1. AD DS 도메인 컨트롤러의 서버 관리자에서 **도구** \> **Active Directory 사용자 및 컴퓨터**를 선택 합니다.
    
    **또는 Windows Server 2012이 없는 경우**
    
    **Windows 키 + R** 을 눌러 **실행** 대화 상자를 연 다음 dsa.msc를 입력 하 고 **확인** 을 클릭 합니다.
    
2. 사용자를 선택 하 고 마우스 오른쪽 단추를 클릭 한 다음 **속성**을 선택 합니다.
    
3. **계정** 탭의 UPN 접미사 드롭다운 목록에서 새 UPN 접미사를 선택한 다음 **확인**을 선택 합니다.
    
    ![사용자에 대해 새 UPN 접미사 추가](media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. 모든 사용자에 대해이 단계를 완료 합니다.
    
   
### <a name="you-can-also-use-windows-powershell-to-change-the-upn-suffix-for-all-users"></a>**Windows PowerShell을 사용 하 여 모든 사용자에 대 한 UPN 접미사를 변경할 수도 있습니다.**

업데이트 해야 하는 사용자가 많은 경우에는 Windows PowerShell을 사용 하는 것이 더 쉽습니다. 다음 예에서는 [contoso.com cmdlet을](https://go.microsoft.com/fwlink/p/?LinkId=624312) [사용 하 여](https://go.microsoft.com/fwlink/p/?LinkId=624313) 모든 contoso 접미사를 변경 합니다. 

예를 들어 다음 Windows PowerShell 명령을 실행 하 여 모든 contoso. 로컬 접미사를 contoso.com으로 업데이트할 수 있습니다.
    
  ```powershell
  $LocalUsers = Get-ADUser -Filter "UserPrincipalName -like '*contoso.local'" -Properties userPrincipalName -ResultSetSize $null
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("@contoso.local","@contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```

AD DS에서 Windows PowerShell을 사용 하는 방법에 대해 자세히 알아보려면 [Active Directory Windows powershell 모듈](https://go.microsoft.com/fwlink/p/?LinkId=624314) 을 참조 하세요. 

