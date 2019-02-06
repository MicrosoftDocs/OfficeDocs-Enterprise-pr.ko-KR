---
title: PowerShell을 사용하여 Office 365 그룹 관리
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MOE150
- MED150
- MBS150
- BSA160
- BCS160
ms.assetid: aeb669aa-1770-4537-9de2-a82ac11b0540
description: 마지막 업데이트 된-18 년 4 월, 2018
ms.openlocfilehash: 518f845099a72d9addac13388d1b281ca63ee408
ms.sourcegitcommit: e56f830ccff8d74d9edbff4a46a9ee1d613291ed
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/05/2019
ms.locfileid: "29741221"
---
# <a name="manage-office-365-groups-with-powershell"></a>PowerShell을 사용하여 Office 365 그룹 관리

 *마지막 업데이트 된-18 년 4 월, 2018* 
  
이 문서는 Microsoft PowerShell에서 그룹에 대 한 일반적인 관리 작업을 수행 하는 단계를 제공 합니다. 또한 그룹에 대 한 PowerShell cmdlet 목록을 제공 합니다. SharePoint 사이트를 관리 하는 방법에 대 한 정보를 [관리 팀 사이트 및 PowerShell을 사용 하 여 통신 사이트를](https://support.office.com/article/52ecc2ab-88c3-486e-b8ff-ef6a968ccd87)참조 하십시오.
  
## <a name="common-tasks-for-managing-office-365-groups"></a>Office 365 그룹을 관리 하기 위한 일반 작업

- [Outlook에서 배포 목록을 Office 365 그룹으로 업그레이드](https://support.office.com/article/787d7a75-e201-46f3-a242-f698162ff09f)
    
- [Office 365 그룹을 만들 수 있는 사용자 관리](https://support.office.com/article/4c46c8cb-17d0-44b5-9776-005fced8e618)
    
- [Office 365 그룹에 대한 게스트 액세스 관리](https://support.office.com/article/7c713d74-a144-4eab-92e7-d50df526ff96)
    
- [Azure Active Directory에서 동적으로 그룹 관리](https://go.microsoft.com/fwlink/?linkid=847632)
    
- Office 365 그룹에 수백 또는 수천 사용자를 추가 [추가 UnifiedGroupLinks cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=616191)을 사용 합니다.
    
### <a name="link-to-your-office-365-groups-usage-guidelines"></a>Office 365 그룹 사용 지침에 연결
<a name="BK_LinkToGuideLines"> </a>

때 사용자가 [Outlook에서 그룹 만들기](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102)를 표시할 수 있습니다 조직의 사용 지침에 대 한 링크입니다. 예: 경우 필요한 특정 접두사 또는 그룹 이름에 추가할 접미사입니다.
  
Azure Active Directory PowerShell을 사용 하 여 사용자에 게 Office 365 그룹에 대 한 조직의 사용 지침을 가리키도록 합니다. [그룹 설정을 구성 하기 위한 Azure Active Directory cmdlet](https://go.microsoft.com/fwlink/?LinkID=827484) 아웃 확인 하 고 사용 현황 지침은 하이퍼링크를 정의 하는 **디렉터리 수준에서 설정 만들기의** 에서 단계를 수행 합니다. 한번 AAD cmdlet을 실행, 사용자의 표시 됩니다 지침에 대 한 링크를 만들거나 Outlook에서 그룹을 편집 하는 경우. 
  
![사용 현황 지침 링크를 사용 하 여 새 그룹 만들기](./../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![조직의 Office 365 그룹 지침을 보려면 그룹 사용 지침을 클릭 합니다.](./../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
### <a name="allow-users-to-send-as-the-office-365-group"></a>Office 365 그룹으로 사용자가 보내기 하도록 허용
<a name="BK_LinkToGuideLines"> </a>

Exchange 관리 센터에도 수행할 수 있습니다. [사람 이름으로 보내기 또는 그룹을 대신 하 여 보낼 허용 구성원](https://support.office.com/article/0ad41414-0cc6-4b97-90fb-06bec7bcf590)을 참조 하십시오.
  
Office 365 그룹 "다른 사람 이름으로 보내기"를 사용 하도록 설정 하려면이 설정을 구성 하려면 [Add-recipientpermission](https://go.microsoft.com/fwlink/p/?LinkId=723960) 및 [Get RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=733239) cmdlet을 사용 합니다. 이 설정을 사용 하면 한 후 Office 365 그룹 사용자를 보내고 Office 365 그룹으로 전자 메일에 회신 Outlook 또는 Outlook 웹에서 사용할 수 있습니다. 사용자는 새 전자 메일을 만들고 "다른 이름으로 보내기" 필드 그룹의 전자 메일 주소를 변경 하려면 그룹에 이동할 수 있습니다. 
  
> [!NOTE]
> 메시지 그룹에 전송 되 고 그룹 대화에 표시 되도록 "사람 이름으로 보내기" 전자 메일을 작성 하는 경우 **참조** 필드에 그룹 전자 메일 주소를 추가 해야 합니다. 
  
이 시간에 사서함 정책을 업데이트 하는 유일한 방법은 [PowerShell](https://technet.microsoft.com/en-us/library/cc482986.aspx)을 통해 됩니다.
  
- 이 명령을 사용 하 여 그룹 별칭을 설정 합니다.
    
  ```
  $groupAlias = "TestSendAs"
  ```

- 사용자 별칭을 설정 하려면이 명령을 사용 합니다.
    
  ```
  $userAlias = "User"
  ```

- 이 명령을 사용 하 여 받는 사람 세부 정보를 가져오는데 Get-recipient cmdlet에는 groupalias를 전달 합니다.
    
  ```
  $groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias
  ```

- 다음 대상 받는 사람 이름 (그룹 이름) Add-recipientpermission cmdlet에 전달 해야 합니다. 사용자에 대 한 sendas 사용 권한을 부여지 것입니다 useralias-트러스트를 받 매개 변수에 할당 됩니다.
    
  ```
  Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
  ```

- Cmdlet가 실행 되 면 사용자가 Outlook 또는 Outlook 웹에 있는 그룹 전자 메일 주소에서 **** 필드를 추가 하 여 그룹으로 보낼으로 이동할 수 있습니다. 
    
### <a name="create-classifications-for-office-groups-in-your-organization"></a>조직에서 Office 그룹에 대 한 분류 만들기
<a name="BKMK_CreateClassification"> </a>

조직에서 사용자가 Office 365 그룹을 만들 때 설정할 수 있는 분류를 만들 수 있습니다. 예, 자신이 만든 그룹에 "표준", "Secret" 및 "위쪽 비밀"를 설정 하는 사용자를 허용할 수 있습니다. 기본적으로 설정 되지 않은 그룹 분류 하 고를 설정 하 여 사용자에 대 한 순서 대로 만들어야 합니다. PowerShell Azure Active Directory를 사용 하 여 사용자에 게 Office 365 그룹에 대 한 조직의 사용 지침을 가리키도록 합니다.
  
[그룹 설정을 구성 하기 위한 Azure Active Directory cmdlet](https://go.microsoft.com/fwlink/?LinkID=827484) 아웃 확인 하 고 Office 365 그룹에 대 한 분류를 정의 하는 **디렉터리 수준에서 설정 만들기의** 에서 단계를 수행 합니다. 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

사용할 수 있는 각 분류에 대 한 설명을 연결 하기 위해 설정을 정의 하려면 *ClassificationDescriptions* 특성입니다. 
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description", where Classification matches the strings in the ClassificationList.
```

예를 들면 다음과 같습니다.
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

프로그램 분류를 설정 하려면 위의 Azure Active Directory cmdlet을 실행 한 후 특정 그룹에 대 한 분류를 설정 하려는 경우 [집합 UnifiedGroup](https://go.microsoft.com/fwlink/?LinkID=616189) cmdlet을 실행 합니다. 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

또는 분류를 사용 하 여 새 그룹 만들기.
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

에 대 한 자세한 내용은 Exchange Online PowerShell을 사용 하 여 [Exchange online PowerShell을 사용 하](https://go.microsoft.com/fwlink/?LinkID=402831) 고 [Connect to Exchange Online PowerShell](https://go.microsoft.com/fwlink/?LinkID=722415) 체크아웃 합니다. 
  
이러한 설정을 사용 하도록 설정 된 후 그룹 소유자가 수는 분류 드롭다운 메뉴의 웹 서버 및 Outlook에는 Outlook에서 선택 하 고 그룹 **편집** 페이지에서 저장 합니다. 
  
![Office 365 그룹 분류를 선택 합니다.](./../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
### <a name="hide-office-365-groups-from-gal"></a>GAL에서 Office 365 그룹 숨기기
<a name="BKMK_CreateClassification"> </a>

Office 365 그룹 전체 주소 목록 (gal 전체) 및 조직의 다른 목록에 표시할지 여부를 지정할 수 있습니다. 예, 주소 목록에 표시 되려면 원하지 않는 법률 부서 그룹을 설치한 경우 GAL에 나타나지 않게 해당 그룹을 중지할 수 있습니다. 다음과 같은 주소 목록에서 그룹을 숨기려면 Set-Unified 그룹 commandlet을 실행 합니다.
  
```
  Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

### <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a>Office 365 그룹에 메시지를 보내려고 내부 사용자만 허용
<a name="BKMK_CreateClassification"> </a>

다른 조직에서 사용자가 Office 365 그룹에 전자 메일을 보낼 수 하지 않을 경우에 해당 그룹에 대 한 설정을 변경할 수 있습니다. 내부 사용자만 그룹에 전자 메일을 보낼 수 있습니다. 외부 사용자가 해당 그룹에 메시지를 전송 하려고 하는 경우 거부 됩니다.
  
다음과 같이이 설정을 업데이트 하려면 집합 UnifiedGroup commandlet을 실행 합니다.
  
```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

### <a name="add-mailtips-to-the-office-365-groups"></a>Office 365 그룹에 메일 설명을 추가합니다
<a name="BKMK_CreateClassification"> </a>

보낸사람을 Office 365 그룹에 전자 메일을 보낼 하려고 때마다 메일 설명은 자신을 표시할 수 있습니다.
  
그룹에 메일 설명을 추가 하려면 Set-Unified 그룹 commandlet을 실행 합니다.
  
```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

메일 설명, 함께 설정할 수도 있습니다 MailTipTranslations 보려면 추가 언어를 지정 하는 메일 설명은 합니다. 스페인어 번역을 한 후 다음 명령을 실행 하려는 경우를 가정해 보겠습니다.
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

### <a name="change-display-name-of-the-office-365-group"></a>Office 365 그룹의 표시 이름 변경
<a name="BKMK_CreateClassification"> </a>

표시 이름에는 Office 365 그룹의 이름을 지정합니다. Exchange 관리 센터 또는 o365 관리 포털에이 이름을 확인할 수 있습니다. 그룹의 표시 이름을 편집 하거나 집합 UnifiedGroup 명령을 실행 하 여 기존 Office 365 그룹에 표시 이름을 할당 수 있습니다.
  
```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

### <a name="manage-user-photos-in-office-365-groups"></a>Office 365 그룹에서 사용자 사진 관리
<a name="BKMK_CreateClassification"> </a>

| |
|**cmdlet 이름**|**설명**|
|:-----|:-----|
|[Get-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |사용 하는 계정에 연결 된 사용자 사진에 대 한 정보를 볼 수 있습니다. Active Directory에 저장 된 사용자 사진  <br/> |
|[집합 UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |계정을 사용 하 여 사용자 사진에 연결 하는 데 사용 됩니다. Active Directory에 저장 된 사용자 사진  <br/> |
|[UserPhoto 제거](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |Office 365 그룹에 대 한 사진 제거  <br/> |
   
### <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a>Outlook에 대 한 Office 365 그룹의 기본 설정을 공용 또는 개인으로 변경
<a name="BKMK_CreateClassification"> </a>

Office 365 Outlook에서 그룹으로 개인 기본적으로 만들어집니다. 조직이 기본적으로 (또는를 Private) 공용으로 만들어야 하는 Outlook에 대 한 Office 365 그룹을 하려는 경우에이 PowerShell cmdlet 구문을 사용 합니다.
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
Private로 설정:
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
설정을 확인 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
자세한 내용은 [Set-organizationconfig](https://go.microsoft.com/fwlink/?linkid=871816) 및 [Get-organizationconfig](https://go.microsoft.com/fwlink/?linkid=871817)를 참조 하십시오.
  
## <a name="office-365-groups-cmdlets"></a>Office 365 그룹 cmdlet

Office 365 그룹에는 다음 cmdlet은 사용할 수 최근에 했습니다. 이 사용할 수 없는 경우 Office 365 구독 업데이트 되지 않은이 기능을 가진 아직 합니다. 메시지 센터 및 [Office 365 로드맵](http://roadmap.office.com/en-us)확인 합니다.
  
| |
|**cmdlet 이름**|**설명**|
|:-----|:-----|
|[Get-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |이 cmdlet을 사용 하면 기존 Office 365 그룹을 조회 하 고 그룹 개체의 속성을 보려면  <br/> |
|[Set-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |특정 Office 365 그룹의 속성을 업데이트 합니다.  <br/> |
|[New-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |새 Office 365 그룹을 만듭니다. 이 cmdlet은 최소한의 매개 변수 집합을 제공, 설정에 대 한 확장 된 속성 값을 사용 하 여 집합 UnifiedGroup 새 그룹을 만든 후  <br/> |
|[Remove-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |기존 Office 365 그룹 삭제  <br/> |
|[Get-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |Office 365 그룹 멤버 자격 및 소유자 정보를 검색  <br/> |
|[Add-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |추가 백 또는 다양 한 사용자 또는 기존 Office 365 그룹에 새 소유자  <br/> |
|[Remove-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |기존 Office 365 그룹에서 소유자 및 구성원을 제거 합니다.  <br/> |
   
## <a name="for-more-information"></a>자세한 내용

- [PowerShell을 사용 하 여](https://technet.microsoft.com/en-us/library/cc482986.aspx)
    
- [사서함에는 Outlook Web App 사서함 정책 적용 또는 제거](https://technet.microsoft.com/en-us/library/dd876884%28v=exchg.150%29.aspx)
    
- [Office 365 그룹 명명 정책을](https://support.office.com/article/6ceca4d3-cad1-4532-9f0f-d469dfbbb552)
    

