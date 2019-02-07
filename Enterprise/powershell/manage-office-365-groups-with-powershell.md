---
title: PowerShell을 사용하여 Office 365 그룹 관리
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BSA160
- BCS160
ms.assetid: aeb669aa-1770-4537-9de2-a82ac11b0540
description: Microsoft PowerShell에서 Office 365 그룹에 대 한 일반적인 관리 작업을 수행 하는 방법에 알아봅니다.
ms.openlocfilehash: 6d7841595315507b0b7f28f6b86f9349705f1d8b
ms.sourcegitcommit: 662d75796991bac4e959348ded4999008875422e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2019
ms.locfileid: "29760060"
---
# <a name="manage-office-365-groups-with-powershell"></a><span data-ttu-id="45666-103">PowerShell을 사용하여 Office 365 그룹 관리</span><span class="sxs-lookup"><span data-stu-id="45666-103">Manage Office 365 Groups with PowerShell</span></span>

 <span data-ttu-id="45666-104">*마지막 업데이트 된-18 년 4 월, 2018*</span><span class="sxs-lookup"><span data-stu-id="45666-104">*Last updated 18 April, 2018*</span></span> 
  
<span data-ttu-id="45666-p101">이 문서는 Microsoft PowerShell에서 그룹에 대 한 일반적인 관리 작업을 수행 하는 단계를 제공 합니다. 또한 그룹에 대 한 PowerShell cmdlet 목록을 제공 합니다. SharePoint 사이트를 관리 하는 방법에 대 한 정보를 [PowerShell을 사용 하 여 SharePoint Online 관리 사이트](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="45666-p101">This article provides the steps for doing common management tasks for Groups in Microsoft PowerShell. It also lists the PowerShell cmdlets for Groups. For info about managing SharePoint sites, see [Manage SharePoint Online sites using PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).</span></span>

## <a name="link-to-your-office-365-groups-usage-guidelines"></a><span data-ttu-id="45666-108">Office 365 그룹 사용 지침에 연결</span><span class="sxs-lookup"><span data-stu-id="45666-108">Link to your Office 365 Groups usage guidelines</span></span>
<span data-ttu-id="45666-109"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="45666-109"></span></span>

<span data-ttu-id="45666-p102">때 사용자가 [Outlook에서 그룹 만들기 또는 편집](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx)을 표시할 수 있습니다 조직의 사용 지침에 대 한 링크입니다. 예: 경우 필요한 특정 접두사 또는 그룹 이름에 추가할 접미사입니다.</span><span class="sxs-lookup"><span data-stu-id="45666-p102">When users [create or edit a group in Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), you can show them a link to your organization's usage guidelines. For example, if you require a specific prefix or suffix to be added to a group name.</span></span>
  
<span data-ttu-id="45666-p103">Azure Active Directory PowerShell을 사용 하 여 사용자에 게 Office 365 그룹에 대 한 조직의 사용 지침을 가리키도록 합니다. [그룹 설정을 구성 하기 위한 Azure Active Directory cmdlet](https://go.microsoft.com/fwlink/?LinkID=827484) 아웃 확인 하 고 사용 현황 지침은 하이퍼링크를 정의 하는 **디렉터리 수준에서 설정 만들기의** 에서 단계를 수행 합니다. 한번 AAD cmdlet을 실행, 사용자의 표시 됩니다 지침에 대 한 링크를 만들거나 Outlook에서 그룹을 편집 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="45666-p103">Use the Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups. Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the usage guideline hyperlink. Once you run the AAD cmdlet, user's will see the link to your guidelines when they create or edit a group in Outlook.</span></span> 
  
![사용 현황 지침 링크를 사용 하 여 새 그룹 만들기](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![조직의 Office 365 그룹 지침을 보려면 그룹 사용 지침을 클릭 합니다.](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
## <a name="allow-users-to-send-as-the-office-365-group"></a><span data-ttu-id="45666-117">Office 365 그룹으로 사용자가 보내기 하도록 허용</span><span class="sxs-lookup"><span data-stu-id="45666-117">Allow users to Send as the Office 365 Group</span></span>
<span data-ttu-id="45666-118"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="45666-118"></span></span>
  
<span data-ttu-id="45666-p104">Office 365 그룹 "다른 사람 이름으로 보내기"를 사용 하도록 설정 하려면이 설정을 구성 하려면 [Add-recipientpermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission) 및 [Get RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient) cmdlet을 사용 합니다. 이 설정을 사용 하면 한 후 Office 365 그룹 사용자를 보내고 Office 365 그룹으로 전자 메일에 회신 Outlook 또는 Outlook 웹에서 사용할 수 있습니다. 사용자는 새 전자 메일을 만들고 "다른 이름으로 보내기" 필드 그룹의 전자 메일 주소를 변경 하려면 그룹에 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45666-p104">If you want to enable your Office 365 groups to "Send As", use the [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission) and the [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient) cmdlets to configure this. Once you enable this setting, Office 365 group users can use Outlook or Outlook on the web to send and reply to email as the Office 365 group. Users can go to the group, create a new email, and change the "Send As" field to the group's email address.</span></span> 

<span data-ttu-id="45666-122">([Exchange 관리 센터에서이 수행할 수도 있습니다](https://docs.microsoft.com/en-us/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group).)</span><span class="sxs-lookup"><span data-stu-id="45666-122">([You can also do this in the Exchange Admin Center](https://docs.microsoft.com/en-us/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group).)</span></span>
  
<span data-ttu-id="45666-p105">다음을 사용 하 여 스크립트를 대체 \* \<GroupAlias\> \* 업데이트 하 고, 하려는 그룹의 별칭을 가진 및 \* \<UserAlias\> \* 사용 권한을 부여 하려면 원하는 사용자의 별칭을 가진 합니다. 이 스크립트를 실행 하려면 [Exchange Online PowerShell 연결](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="45666-p105">Use the following script, replacing *\<GroupAlias\>* with the alias of the group that you want to update, and *\<UserAlias\>* with the alias of the user to whom you want to grant permssions. [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) to run this script.</span></span>

```PowerShell
$groupAlias = "<GroupAlias>"

$userAlias = "<UserAlias>"


$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

<span data-ttu-id="45666-125">Cmdlet가 실행 되 면 사용자가 Outlook 또는 Outlook 웹에 있는 그룹 전자 메일 주소에서 \*\*\*\* 필드를 추가 하 여 그룹으로 보낼으로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45666-125">Once the cmdlet is executed, users can go to Outlook or Outlook on the web to send as the group, by adding the group email address to the **From** field.</span></span> 

## <a name="create-classifications-for-office-groups-in-your-organization"></a><span data-ttu-id="45666-126">조직에서 Office 그룹에 대 한 분류 만들기</span><span class="sxs-lookup"><span data-stu-id="45666-126">Create classifications for Office groups in your organization</span></span>

<span data-ttu-id="45666-p106">조직에서 사용자가 Office 365 그룹을 만들 때 설정할 수 있는 분류를 만들 수 있습니다. 예, 자신이 만든 그룹에 "표준", "Secret" 및 "위쪽 비밀"를 설정 하는 사용자를 허용할 수 있습니다. 기본적으로 설정 되지 않은 그룹 분류 하 고를 설정 하 여 사용자에 대 한 순서 대로 만들어야 합니다. PowerShell Azure Active Directory를 사용 하 여 사용자에 게 Office 365 그룹에 대 한 조직의 사용 지침을 가리키도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="45666-p106">You can create classifications that the users in your organization can set when they create an Office 365 group. For example, you can allow users to set "Standard", "Secret", and "Top Secret" on groups they create. Group classifications aren't set by default and you need to create it in order for your users to set it. Use Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups.</span></span>
  
<span data-ttu-id="45666-131">[그룹 설정을 구성 하기 위한 Azure Active Directory cmdlet](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) 아웃 확인 하 고 Office 365 그룹에 대 한 분류를 정의 하는 **디렉터리 수준에서 설정 만들기의** 에서 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="45666-131">Check out [Azure Active Directory cmdlets for configuring group settings](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) and follow the steps in the **Create settings at the directory level** to define the classification for Office 365 groups.</span></span> 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

<span data-ttu-id="45666-132">사용할 수 있는 각 분류에 대 한 설명을 연결 하기 위해 설정을 정의 하려면 *ClassificationDescriptions* 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="45666-132">In order to associate a description to each classification you can use the settings attribute  *ClassificationDescriptions* to define.</span></span>
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

<span data-ttu-id="45666-133">여기서 분류는 ClassificationList에서 문자열을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="45666-133">where Classification matches the strings in the ClassificationList.</span></span>

<span data-ttu-id="45666-134">예제:</span><span class="sxs-lookup"><span data-stu-id="45666-134">Example:</span></span>
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

<span data-ttu-id="45666-135">프로그램 분류를 설정 하려면 위의 Azure Active Directory cmdlet을 실행 한 후 특정 그룹에 대 한 분류를 설정 하려는 경우 [집합 UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="45666-135">After you run the above Azure Active Directory cmdlet to set your classification, run the [Set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) cmdlet if you want to set the classification for a specific group.</span></span> 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

<span data-ttu-id="45666-136">또는 분류를 사용 하 여 새 그룹 만들기.</span><span class="sxs-lookup"><span data-stu-id="45666-136">Or create a new group with a classification.</span></span>
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

<span data-ttu-id="45666-137">에 대 한 자세한 내용은 Exchange Online PowerShell을 사용 하 여 [Exchange online PowerShell을 사용 하](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) 고 [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) 체크아웃 합니다.</span><span class="sxs-lookup"><span data-stu-id="45666-137">Check out [Using PowerShell with Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) and [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) for more details on using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="45666-138">이러한 설정을 사용 하도록 설정 된 후 그룹 소유자가 수는 분류 드롭다운 메뉴의 웹 서버 및 Outlook에는 Outlook에서 선택 하 고 그룹 **편집** 페이지에서 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="45666-138">Once these settings are enabled, the group owner will be able to choose a classification from the drop down menu in Outlook on the Web and Outlook, and save it from the **Edit** group page.</span></span> 
  
![Office 365 그룹 분류를 선택 합니다.](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
## <a name="hide-office-365-groups-from-gal"></a><span data-ttu-id="45666-140">GAL에서 Office 365 그룹 숨기기</span><span class="sxs-lookup"><span data-stu-id="45666-140">Hide Office 365 Groups from GAL</span></span>
<span data-ttu-id="45666-141"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="45666-141"></span></span>

<span data-ttu-id="45666-p107">Office 365 그룹 전체 주소 목록 (gal 전체) 및 조직의 다른 목록에 표시할지 여부를 지정할 수 있습니다. 예, 주소 목록에 표시 되려면 원하지 않는 법률 부서 그룹을 설치한 경우 GAL에 나타나지 않게 해당 그룹을 중지할 수 있습니다. 다음과 같은 주소 목록에서 그룹 숨기기 Set-Unified 그룹 cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="45666-p107">You can specify whether a Office 365 group appears in the global address list (GAL) and other lists in your organization. For example, if you have a legal department group that you don't want to show up in the address list, you can stop that group from appearing in GAL. Run the Set-Unified Group cmdlet to hide the group from address list like this:</span></span>
  
```
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a><span data-ttu-id="45666-145">Office 365 그룹에 메시지를 보내려고 내부 사용자만 허용</span><span class="sxs-lookup"><span data-stu-id="45666-145">Allow only internal users to send message to Office 365 group</span></span>
<span data-ttu-id="45666-146"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="45666-146"></span></span>

<span data-ttu-id="45666-p108">다른 조직에서 사용자가 Office 365 그룹에 전자 메일을 보낼 수 하지 않을 경우에 해당 그룹에 대 한 설정을 변경할 수 있습니다. 내부 사용자만 그룹에 전자 메일을 보낼 수 있습니다. 외부 사용자가 해당 그룹에 메시지를 전송 하려고 하는 경우 거부 됩니다.</span><span class="sxs-lookup"><span data-stu-id="45666-p108">If you don't want users from other organization to send email to a Office 365 group, you can change the settings for that group. It will allow only internal users to send an email to your group. If external user try to send message to that group they will be rejected.</span></span>
  
<span data-ttu-id="45666-150">다음과 같이이 설정을 업데이트 하려면 집합 UnifiedGroup cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="45666-150">Run the Set-UnifiedGroup cmdlet to update this setting, like this:</span></span>

```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-the-office-365-groups"></a><span data-ttu-id="45666-151">Office 365 그룹에 메일 설명을 추가합니다</span><span class="sxs-lookup"><span data-stu-id="45666-151">Add MailTips to the Office 365 Groups</span></span>
<span data-ttu-id="45666-152"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="45666-152"></span></span>

<span data-ttu-id="45666-153">보낸사람을 Office 365 그룹에 전자 메일을 보낼 하려고 때마다 메일 설명은 자신에 게 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45666-153">Whenever a sender tries to send an email to an Office 365 group, a MailTip can be shown to them.</span></span>
  
<span data-ttu-id="45666-154">그룹에 메일 설명을 추가 Set-Unified 그룹 cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="45666-154">Run the Set-Unified Group cmdlet to add a mailTip to the group:</span></span>

```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

<span data-ttu-id="45666-p109">메일 설명, 함께 메일 설명은 대 한 추가 언어를 지정 하는 MailTipTranslations을 설정할 수도 있습니다. 스페인어 번역을 한 후 다음 명령을 실행 하려는 경우를 가정해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="45666-p109">Along with MailTip, you can also set MailTipTranslations, which specifies additional languages for the MailTip. Suppose you want to have the Spanish translation, then run the following command:</span></span>
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-display-name-of-the-office-365-group"></a><span data-ttu-id="45666-157">Office 365 그룹의 표시 이름 변경</span><span class="sxs-lookup"><span data-stu-id="45666-157">Change Display name of the Office 365 group</span></span>

<span data-ttu-id="45666-p110">표시 이름에는 Office 365 그룹의 이름을 지정합니다. Exchange 관리 센터 또는 Office 365 관리 포털에이 이름을 확인할 수 있습니다. 그룹의 표시 이름을 편집 하거나 집합 UnifiedGroup 명령을 실행 하 여 기존 Office 365 그룹에는 표시 이름이 할당 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45666-p110">Display name specifies the name of the Office 365 group. You can see this name in your exchange admin center or Office 365 admin portal. You can edit the display name of the group or assign a display name to an existing Office 365 group by running the Set-UnifiedGroup command:</span></span>

```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a><span data-ttu-id="45666-161">Outlook에 대 한 Office 365 그룹의 기본 설정을 공용 또는 개인으로 변경</span><span class="sxs-lookup"><span data-stu-id="45666-161">Change the default setting of Office 365 Groups for Outlook to Public or Private</span></span>
<span data-ttu-id="45666-162"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="45666-162"></span></span>

<span data-ttu-id="45666-p111">Office 365 Outlook에서 그룹으로 개인 기본적으로 만들어집니다. 조직이 기본적으로 (또는를 Private) 공용으로 만들 Office 365 그룹을 하려는 경우에이 PowerShell cmdlet 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="45666-p111">Office 365 Groups in Outlook are created as Private by default. If your organization wants Office 365 Groups to be created as Public by default (or back to Private), use this PowerShell cmdlet syntax:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
<span data-ttu-id="45666-165">Private로 설정:</span><span class="sxs-lookup"><span data-stu-id="45666-165">To set to Private:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
<span data-ttu-id="45666-166">설정을 확인</span><span class="sxs-lookup"><span data-stu-id="45666-166">To verify the setting:</span></span> 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
<span data-ttu-id="45666-167">자세한 내용은 [Set-organizationconfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig) 및 [Get-organizationconfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="45666-167">To learn more, see [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig) and [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig).</span></span>
  
## <a name="office-365-groups-cmdlets"></a><span data-ttu-id="45666-168">Office 365 그룹 cmdlet</span><span class="sxs-lookup"><span data-stu-id="45666-168">Office 365 Groups cmdlets</span></span>

<span data-ttu-id="45666-169">Office 365 그룹과 다음 cmdlet은 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45666-169">The following cmdlets can be used with Office 365 Groups.</span></span>
  
|<span data-ttu-id="45666-170">**cmdlet 이름**</span><span class="sxs-lookup"><span data-stu-id="45666-170">**Cmdlet name**</span></span>|<span data-ttu-id="45666-171">**설명**</span><span class="sxs-lookup"><span data-stu-id="45666-171">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="45666-172">Get-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="45666-172">Get-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |<span data-ttu-id="45666-173">이 cmdlet을 사용 하면 기존 Office 365 그룹을 조회 하 고 그룹 개체의 속성을 보려면</span><span class="sxs-lookup"><span data-stu-id="45666-173">Use this cmdlet to look up existing Office 365 Groups, and to view properties of the group object</span></span>  <br/> |
|[<span data-ttu-id="45666-174">Set-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="45666-174">Set-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |<span data-ttu-id="45666-175">특정 Office 365 그룹의 속성을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="45666-175">Update the properties of a specific Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="45666-176">New-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="45666-176">New-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |<span data-ttu-id="45666-p112">새 Office 365 그룹을 만듭니다. 이 cmdlet은 최소한의 매개 변수 집합을 제공, 설정에 대 한 확장 된 속성 값을 사용 하 여 집합 UnifiedGroup 새 그룹을 만든 후</span><span class="sxs-lookup"><span data-stu-id="45666-p112">Create a new Office 365 group. This cmdlet provides a minimal set of parameters, for setting values for extended properties use Set-UnifiedGroup after creating the new group</span></span>  <br/> |
|[<span data-ttu-id="45666-179">Remove-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="45666-179">Remove-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |<span data-ttu-id="45666-180">기존 Office 365 그룹 삭제</span><span class="sxs-lookup"><span data-stu-id="45666-180">Delete an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="45666-181">Get-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="45666-181">Get-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |<span data-ttu-id="45666-182">Office 365 그룹 멤버 자격 및 소유자 정보를 검색</span><span class="sxs-lookup"><span data-stu-id="45666-182">Retrieve membership and owner information for an Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="45666-183">Add-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="45666-183">Add-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |<span data-ttu-id="45666-184">추가 백 또는 다양 한 사용자 또는 기존 Office 365 그룹에 새 소유자</span><span class="sxs-lookup"><span data-stu-id="45666-184">Add hundred or thousands of users, or new owners, to an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="45666-185">Remove-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="45666-185">Remove-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |<span data-ttu-id="45666-186">기존 Office 365 그룹에서 소유자 및 구성원을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="45666-186">Remove owners and members from an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="45666-187">Get-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="45666-187">Get-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |<span data-ttu-id="45666-p113">사용 하는 계정에 연결 된 사용자 사진에 대 한 정보를 볼 수 있습니다. Active Directory에 저장 된 사용자 사진</span><span class="sxs-lookup"><span data-stu-id="45666-p113">Used to view information about the user photo associated with an account. User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="45666-190">집합 UserPhoto</span><span class="sxs-lookup"><span data-stu-id="45666-190">Set-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |<span data-ttu-id="45666-p114">계정을 사용 하 여 사용자 사진에 연결 하는 데 사용 됩니다. Active Directory에 저장 된 사용자 사진</span><span class="sxs-lookup"><span data-stu-id="45666-p114">Used to associate a user photo with an account. User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="45666-193">UserPhoto 제거</span><span class="sxs-lookup"><span data-stu-id="45666-193">Remove-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |<span data-ttu-id="45666-194">Office 365 그룹에 대 한 사진 제거</span><span class="sxs-lookup"><span data-stu-id="45666-194">Remove the photo for an Office 365 group</span></span>  <br/> |

## <a name="related-topics"></a><span data-ttu-id="45666-195">관련 항목</span><span class="sxs-lookup"><span data-stu-id="45666-195">Related topics</span></span>

[<span data-ttu-id="45666-196">Office 365 그룹에 업그레이드 메일 그룹</span><span class="sxs-lookup"><span data-stu-id="45666-196">Upgrade distribution lists to Office 365 Groups</span></span>](https://docs.microsoft.com/en-us/office365/admin/manage/upgrade-distribution-lists)

[<span data-ttu-id="45666-197">Office 365 그룹을 만들 수 있는 사용자 관리</span><span class="sxs-lookup"><span data-stu-id="45666-197">Manage who can create Office 365 Groups</span></span>](https://docs.microsoft.com/en-us/office365/admin/create-groups/manage-creation-of-groups)

[<span data-ttu-id="45666-198">Office 365 그룹에 대한 게스트 액세스 관리</span><span class="sxs-lookup"><span data-stu-id="45666-198">Manage guest access to Office 365 Groups</span></span>](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[<span data-ttu-id="45666-199">정적 그룹 멤버 자격에서 동적으로 변경</span><span class="sxs-lookup"><span data-stu-id="45666-199">Change static group membership to dynamic in</span></span>](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-change-type)
