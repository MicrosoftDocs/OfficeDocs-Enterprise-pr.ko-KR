---
title: 디렉터리 동기화를 위한 라우팅할 수 없는 도메인을 준비 합니다.
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365E_SetupDirSyncLocalDir
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: e7968303-c234-46c4-b8b0-b5c93c6d57a7
description: Office 365와 동기화 하기 전에 온-프레미스 사용자와 연결 된 비 routale 도메인을 사용 하는 경우 취해야 할 조치에 대해 알아봅니다.
ms.openlocfilehash: 62779ba879522177ba15a491644ab42f5961ece0
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542179"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a>디렉터리 동기화를 위한 라우팅할 수 없는 도메인을 준비 합니다.
Office 365와 온-프레미스 디렉터리를 동기화 할 때 Azure Active Directory에서 확인 된 도메인을 포함 해야 합니다. 만 사용자 이름 (UPN) 온-프레미스 도메인 연관 된 동기화 됩니다. 에 있는 라우팅할 수 없는 도메인 (예: billa@contoso.local).local 같은 포함 된 모든 UPN를 동기화 하는 반면는. onmicrosoft.com 도메인 (예: billa@contoso.onmicrosoft.com). 

Active Directory에서 사용자 계정에 대 한 현재.local 도메인을 사용 하는 경우 Office 365 도메인 제대로 동기화 하기 위해 (예: billa@contoso.com) 확인 된 도메인을 사용 하도록 변경 하는 것이 좋습니다.
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a>경우에 어떻게.local 온-프레미스 도메인만가?

Azure Active Directory에 Active Directory 동기화 (영문)에 대해 사용할 수 있는 가장 최근의 도구에는 Azure AD 연결 이라고 합니다. 자세한 내용은 [Azure Active Directory를 사용 하 여 온-프레미스 id가 통합 (영문)을](https://go.microsoft.com/fwlink/p/?LinkId=624168)참조 하십시오.
  
사용자가 로그인 할 수 있도록 사용자의 UPN과 암호 동기화를 azure AD 연결 온-프레미스를 사용 하는 동일한 자격 증명으로 로그인 합니다. 그러나 Azure AD 연결 사용자가 Office 365에 의해 검증 된 도메인에만 동기화 합니다. 이 도메인도 확인 Azure Active Directory를 통해 Office 365 id가 Azure Active Directory에서 관리 되므로 것을 의미 합니다. 즉, 도메인은 유효한 인터넷 도메인 (예.com,.org,.net,.us 등) 이어야 합니다. 내부 Active Directory를 라우팅할 수 없는 도메인 (예:.local)에 사용 하 여,이 Office 365에 있는 확인 된 도메인과 일치 가능 수는 없습니다. 두 프로그램 온-프레미스 Active Directory에서에서 기본 도메인을 변경 하 여 또는 하나 이상의 UPN 접미사를 추가 하 여이 문제를 해결할 수 있습니다.
  
### <a name="change-your-primary-domain"></a>**기본 도메인을 변경 합니다.**

Office 365, 예: contoso.com에서에서 확인 한 도메인을 기본 도메인을 변경 합니다. 도메인 contoso.local 포함 된 모든 사용자가이 contoso.com으로 업데이트 됩니다. 자세한 내용은 [이름바꾸기 작동 방법 도메인을](https://go.microsoft.com/fwlink/p/?LinkId=624174)참조 하십시오. 그러나 이것은 매우 관련 된 프로세스 및를 보다 쉽게 솔루션 것 [추가 UPN 접미사 및 자신에 게 사용자를 업데이트](prepare-a-non-routable-domain-for-directory-synchronization.md#bk_register), 다음 섹션에 나와있는 것 처럼입니다.
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a>**UPN 접미사를 추가 하 고 사용자에 게 자신에 게 업데이트**

.Local 문제를 해결할 수 도메인 (또는 도메인)와 일치 하도록 Active Directory에 새 UPN 접미사 또는 접미사를 등록 하 여 Office 365에서 확인 합니다. 새 접미사를 등록 한 후 사용자는 사용자 계정이 billa@contoso.com 처럼 표시 되도록는.local 예제에 대 한 새 도메인 이름으로 바꿉니다 Upn 업데이트 합니다.
  
확인 된 도메인을 사용 하 여 Upn을 업데이트 한 후 Office 365와 온-프레미스 Active Directory 동기화 준비가 된 것입니다.
  
 **1 단계: 새 UPN 접미사를 추가 합니다.**
  
1. Active Directory 도메인 서비스 (AD DS)에서 실행 되는 서버의 서버 관리자에서 **도구** 를 선택 \> **Active Directory 도메인 및 트러스트**합니다.
    
    **또는 Windows Server 2012를 설치 하지 않은 경우**
    
    **실행** 대화 상자를 열고 Domain.msc에서 입력 한 다음 **Windows 키 + R을** 누릅니다. 하 고 **확인**을 선택 합니다.
    
    ![Active Directory 도메인 및 트러스트를 선택 합니다.](media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. **Active Directory 도메인 및 트러스트** 창에서 **Active Directory 도메인 및 트러스트를**마우스 오른쪽 단추로 클릭 한 다음 **속성**을 선택 합니다.
    
    ![ActiveDirectory 도메인 및 트러스트를 단추로 클릭 하 고 속성을 선택 합니다.](media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. **UPN 접미사** 탭에서 **대체 UPN 접미사** 상자에 입력 새 UPN 접미사 또는 접미사를 한 다음 **추가** 선택 \> **적용**합니다.
    
    ![새 UPN 접미사를 추가 합니다.](media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    추가 접미사를 완료 했으면 **확인** 을 선택 합니다. 
    
 **2 단계: 기존 사용자에 대 한 UPN 접미사를 변경 합니다.**
  
1. Active Directory 도메인 서비스 (AD DS)에서 실행 되는 서버의 서버 관리자에서 **도구** 를 선택 \> **Active Directory Active Directory 사용자 및 컴퓨터**입니다.
    
    **또는 Windows Server 2012를 설치 하지 않은 경우**
    
    다음 **확인** 을 클릭 하 고 **실행** 대화 상자를 열고에 Dsa.msc를 입력 한 다음 **Windows 키 + R을** 누릅니다.
    
2. 사용자를 선택 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 선택 합니다.
    
3. UPN 접미사 드롭다운 목록에서 **계정** 탭에서 새 UPN 접미사를 선택 하 고 **확인**을 선택 합니다.
    
    ![사용자에 대 한 새 UPN 접미사를 추가 합니다.](media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. 모든 사용자에 대해 다음이 단계를 완료 합니다.
    
    업데이트를 대량 수 또는 UPN 접미사 [를 모든 사용자에 대 한 UPN 접미사를 변경 하려면 Windows PowerShell을 사용할 수 있습니다](prepare-a-non-routable-domain-for-directory-synchronization.md#BK_Posh).
    
### <a name="you-can-also-use-windows-powershell-to-change-the-upn-suffix-for-all-users"></a>**Windows PowerShell을 사용 하 여 모든 사용자에 대 한 UPN 접미사를 변경할 수도 있습니다.**

업데이트 하는 사용자 수가 많은 경우에 Windows PowerShell을 사용 하 여 더 쉽습니다. 다음 예제에서는 contoso.com으로 모든 contoso.local 접미사를 변경 하려면 [Get ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) 및 [집합 ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) cmdlet을 사용 합니다. 

Contoso.com를 모든 contoso.local 접미사를 업데이트 하려면 다음 Windows PowerShell 명령을 실행 합니다.
    
  ```
  $LocalUsers = Get-ADUser -Filter {UserPrincipalName -like '*contoso.local'} -Properties userPrincipalName -ResultSetSize $null
  ```

  ```
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("contoso.local","contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```
Active Directory에서 Windows PowerShell을 사용 하는 방법에 대 한 자세한 내용은 [Windows PowerShell의 Active Directory 모듈](https://go.microsoft.com/fwlink/p/?LinkId=624314) 을 참조 하십시오. 

