---
title: PowerShell을 사용하여 Office 365 그룹 관리
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: Admin
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
description: Microsoft PowerShell에서 Office 365 그룹에 대 한 일반적인 관리 작업을 수행 하는 방법을 알아봅니다.
ms.openlocfilehash: b2cd536630f80dec66344162669b0bbe1cf3b4cd
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069024"
---
# <a name="manage-office-365-groups-with-powershell"></a><span data-ttu-id="40ea6-103">PowerShell을 사용하여 Office 365 그룹 관리</span><span class="sxs-lookup"><span data-stu-id="40ea6-103">Manage Office 365 Groups with PowerShell</span></span>

 <span data-ttu-id="40ea6-104">*마지막 업데이트 18 4 월, 2018*</span><span class="sxs-lookup"><span data-stu-id="40ea6-104">*Last updated 18 April, 2018*</span></span> 
  
<span data-ttu-id="40ea6-105">이 문서에서는 Microsoft PowerShell의 그룹에 대 한 일반적인 관리 작업을 수행 하는 단계를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-105">This article provides the steps for doing common management tasks for Groups in Microsoft PowerShell.</span></span> <span data-ttu-id="40ea6-106">또한 그룹에 대 한 PowerShell cmdlet도 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-106">It also lists the PowerShell cmdlets for Groups.</span></span> <span data-ttu-id="40ea6-107">SharePoint 사이트 관리에 대 한 자세한 내용은 [PowerShell을 사용 하 여 Sharepoint Online 사이트 관리](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="40ea6-107">For info about managing SharePoint sites, see [Manage SharePoint Online sites using PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).</span></span>

## <a name="link-to-your-office-365-groups-usage-guidelines"></a><span data-ttu-id="40ea6-108">Office 365 그룹에 연결 사용 지침</span><span class="sxs-lookup"><span data-stu-id="40ea6-108">Link to your Office 365 Groups usage guidelines</span></span>
<span data-ttu-id="40ea6-109"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="40ea6-109"></span></span>

<span data-ttu-id="40ea6-110">사용자가 [Outlook에서 그룹을 만들거나 편집할](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx)때 조직의 사용 지침에 대 한 링크를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-110">When users [create or edit a group in Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), you can show them a link to your organization's usage guidelines.</span></span> <span data-ttu-id="40ea6-111">예를 들어 그룹 이름에 특정 접두사 또는 접미사를 추가 해야 하는 경우</span><span class="sxs-lookup"><span data-stu-id="40ea6-111">For example, if you require a specific prefix or suffix to be added to a group name.</span></span>
  
<span data-ttu-id="40ea6-112">Azure Active Directory PowerShell을 사용 하 여 사용자가 조직의 Office 365 그룹에 대 한 사용 지침을 가리키도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-112">Use the Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups.</span></span> <span data-ttu-id="40ea6-113">[그룹 설정 구성을 위한 Azure Active Directory cmdlet](https://go.microsoft.com/fwlink/?LinkID=827484) 을 확인 하 고 **디렉터리 수준에서 만들기 설정** 의 단계에 따라 사용 지침 하이퍼링크를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-113">Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the usage guideline hyperlink.</span></span> <span data-ttu-id="40ea6-114">AAD cmdlet을 실행 하면 사용자는 Outlook에서 그룹을 만들거나 편집할 때 지침에 대 한 링크를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-114">Once you run the AAD cmdlet, user's will see the link to your guidelines when they create or edit a group in Outlook.</span></span> 
  
![사용 지침 링크를 사용 하 여 새 그룹 만들기](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![그룹 사용 지침을 클릭 하 여 조직 Office 365 그룹 지침을 확인 합니다.](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
## <a name="allow-users-to-send-as-the-office-365-group"></a><span data-ttu-id="40ea6-117">사용자가 Office 365 그룹으로 메일을 보낼 수 있도록 허용</span><span class="sxs-lookup"><span data-stu-id="40ea6-117">Allow users to Send as the Office 365 Group</span></span>
<span data-ttu-id="40ea6-118"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="40ea6-118"></span></span>
  
<span data-ttu-id="40ea6-119">Office 365 그룹을 "다른 사람 이름으로 보내기"로 설정 하려는 경우 [add-recipientpermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission) 및 [add-recipientpermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient) cmdlet을 사용 하 여이를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-119">If you want to enable your Office 365 groups to "Send As", use the [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission) and the [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient) cmdlets to configure this.</span></span> <span data-ttu-id="40ea6-120">이 설정을 사용 하도록 설정 하면 Office 365 그룹 사용자가 Outlook 또는 웹용 Outlook을 사용 하 여 Office 365 그룹으로 전자 메일을 보내고 회신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-120">Once you enable this setting, Office 365 group users can use Outlook or Outlook on the web to send and reply to email as the Office 365 group.</span></span> <span data-ttu-id="40ea6-121">사용자는 그룹으로 이동 하 여 새 전자 메일을 만들고 "다른 사람 이름으로 보내기" 필드를 그룹의 전자 메일 주소로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-121">Users can go to the group, create a new email, and change the "Send As" field to the group's email address.</span></span> 

<span data-ttu-id="40ea6-122">([Exchange 관리 센터 에서도이 작업을 수행할 수](https://docs.microsoft.com/en-us/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group)있습니다.)</span><span class="sxs-lookup"><span data-stu-id="40ea6-122">([You can also do this in the Exchange Admin Center](https://docs.microsoft.com/en-us/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group).)</span></span>
  
<span data-ttu-id="40ea6-123">다음 스크립트를 사용 하 여 \* \<groupalias\> \* 를 업데이트할 그룹의 별칭으로 바꾸고, permssions을 부여 하려는 사용자의 별칭으로 \* \<useralias\> \* 를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-123">Use the following script, replacing *\<GroupAlias\>* with the alias of the group that you want to update, and *\<UserAlias\>* with the alias of the user to whom you want to grant permssions.</span></span> <span data-ttu-id="40ea6-124">[Exchange Online PowerShell에 연결](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) 하 여이 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-124">[Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) to run this script.</span></span>

```PowerShell
$groupAlias = "<GroupAlias>"

$userAlias = "<UserAlias>"


$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

<span data-ttu-id="40ea6-125">일단 cmdlet이 실행 되 면 사용자는 **보낸** 사람 필드에 그룹 전자 메일 주소를 추가 하 여 해당 그룹으로 보낼 outlook 또는 웹용 outlook으로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-125">Once the cmdlet is executed, users can go to Outlook or Outlook on the web to send as the group, by adding the group email address to the **From** field.</span></span> 

## <a name="create-classifications-for-office-groups-in-your-organization"></a><span data-ttu-id="40ea6-126">조직의 Office 그룹에 대 한 분류 만들기</span><span class="sxs-lookup"><span data-stu-id="40ea6-126">Create classifications for Office groups in your organization</span></span>

<span data-ttu-id="40ea6-127">조직의 사용자가 Office 365 그룹을 만들 때 설정할 수 있는 분류를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-127">You can create classifications that the users in your organization can set when they create an Office 365 group.</span></span> <span data-ttu-id="40ea6-128">예를 들어 사용자가 자신이 만드는 그룹에 "Standard", "Secret" 및 "Top Secret"를 설정 하도록 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-128">For example, you can allow users to set "Standard", "Secret", and "Top Secret" on groups they create.</span></span> <span data-ttu-id="40ea6-129">그룹 분류는 기본적으로 설정 되지 않으며 사용자가이를 설정 하기 위해 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-129">Group classifications aren't set by default and you need to create it in order for your users to set it.</span></span> <span data-ttu-id="40ea6-130">Azure Active Directory PowerShell을 사용 하 여 사용자가 Office 365 그룹에 대 한 조직의 사용 지침을 가리키도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-130">Use Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups.</span></span>
  
<span data-ttu-id="40ea6-131">[그룹 설정 구성을 위한 Azure Active Directory cmdlet](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) 을 확인 하 고 **디렉터리 수준에서 만들기 설정** 의 단계에 따라 Office 365 그룹에 대 한 분류를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-131">Check out [Azure Active Directory cmdlets for configuring group settings](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) and follow the steps in the **Create settings at the directory level** to define the classification for Office 365 groups.</span></span> 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

<span data-ttu-id="40ea6-132">각 분류에 설명을 연결 하기 위해 *ClassificationDescriptions* settings 특성을 사용 하 여 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-132">In order to associate a description to each classification you can use the settings attribute  *ClassificationDescriptions* to define.</span></span>
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

<span data-ttu-id="40ea6-133">여기서 분류는 ClassificationList의 문자열과 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-133">where Classification matches the strings in the ClassificationList.</span></span>

<span data-ttu-id="40ea6-134">예제:</span><span class="sxs-lookup"><span data-stu-id="40ea6-134">Example:</span></span>
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

<span data-ttu-id="40ea6-135">위의 Azure Active Directory cmdlet을 실행 하 여 분류를 설정한 후에 특정 그룹에 대 한 분류를 설정 하려면 [remove-unifiedgroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-135">After you run the above Azure Active Directory cmdlet to set your classification, run the [Set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) cmdlet if you want to set the classification for a specific group.</span></span> 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

<span data-ttu-id="40ea6-136">또는 분류가 포함 된 새 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-136">Or create a new group with a classification.</span></span>
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

<span data-ttu-id="40ea6-137">Exchange online PowerShell을 사용 하는 방법에 대 한 자세한 내용은 exchange [online에서 powershell을 사용 하 여](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) 확인 하 고 [exchange Online powershell에 연결](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) 합니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-137">Check out [Using PowerShell with Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) and [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) for more details on using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="40ea6-138">이러한 설정을 사용 하도록 설정 하면 그룹 소유자가 웹 및 Outlook의 Outlook에 있는 드롭다운 메뉴에서 분류를 선택 하 고 그룹 **편집** 페이지에서이를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-138">Once these settings are enabled, the group owner will be able to choose a classification from the drop down menu in Outlook on the Web and Outlook, and save it from the **Edit** group page.</span></span> 
  
![Office 365 그룹 분류 선택](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
## <a name="hide-office-365-groups-from-gal"></a><span data-ttu-id="40ea6-140">GAL에서 Office 365 그룹 숨기기</span><span class="sxs-lookup"><span data-stu-id="40ea6-140">Hide Office 365 Groups from GAL</span></span>
<span data-ttu-id="40ea6-141"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="40ea6-141"></span></span>

<span data-ttu-id="40ea6-142">GAL (전체 주소 목록) 및 조직의 다른 목록에 Office 365 그룹을 표시할지 여부를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-142">You can specify whether a Office 365 group appears in the global address list (GAL) and other lists in your organization.</span></span> <span data-ttu-id="40ea6-143">예를 들어 주소 목록에 표시 하지 않으려는 법무 부서 그룹이 있는 경우 해당 그룹이 GAL에 나타나지 않도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-143">For example, if you have a legal department group that you don't want to show up in the address list, you can stop that group from appearing in GAL.</span></span> <span data-ttu-id="40ea6-144">통합 그룹 cmdlet을 실행 하 여 주소 목록에서 그룹을 다음과 같이 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-144">Run the Set-Unified Group cmdlet to hide the group from address list like this:</span></span>
  
```
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a><span data-ttu-id="40ea6-145">내부 사용자만 Office 365 그룹에 메시지를 보낼 수 있도록 허용</span><span class="sxs-lookup"><span data-stu-id="40ea6-145">Allow only internal users to send message to Office 365 group</span></span>
<span data-ttu-id="40ea6-146"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="40ea6-146"></span></span>

<span data-ttu-id="40ea6-147">다른 조직의 사용자가 Office 365 그룹에 전자 메일을 보낼 수 없도록 하려면 해당 그룹의 설정을 변경 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-147">If you don't want users from other organization to send email to a Office 365 group, you can change the settings for that group.</span></span> <span data-ttu-id="40ea6-148">이를 통해 내부 사용자만 그룹에 전자 메일을 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-148">It will allow only internal users to send an email to your group.</span></span> <span data-ttu-id="40ea6-149">외부 사용자가 해당 그룹에 메시지를 보내려고 하면 해당 그룹이 거부 됩니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-149">If external user try to send message to that group they will be rejected.</span></span>
  
<span data-ttu-id="40ea6-150">다음과 같이 Remove-unifiedgroup cmdlet을 실행 하 여이 설정을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-150">Run the Set-UnifiedGroup cmdlet to update this setting, like this:</span></span>

```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-the-office-365-groups"></a><span data-ttu-id="40ea6-151">Office 365 그룹에 메일 설명 추가</span><span class="sxs-lookup"><span data-stu-id="40ea6-151">Add MailTips to the Office 365 Groups</span></span>
<span data-ttu-id="40ea6-152"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="40ea6-152"></span></span>

<span data-ttu-id="40ea6-153">보낸 사람이 Office 365 그룹에 전자 메일을 보내려고 할 때마다 메일 설명를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-153">Whenever a sender tries to send an email to an Office 365 group, a MailTip can be shown to them.</span></span>
  
<span data-ttu-id="40ea6-154">통합 그룹 cmdlet을 실행 하 여 그룹에 메일 설명를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-154">Run the Set-Unified Group cmdlet to add a mailTip to the group:</span></span>

```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

<span data-ttu-id="40ea6-155">메일 설명와 함께 메일 설명에 대 한 추가 언어를 지정 하는 MailTipTranslations를 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-155">Along with MailTip, you can also set MailTipTranslations, which specifies additional languages for the MailTip.</span></span> <span data-ttu-id="40ea6-156">스페인어 번역을 사용할 수 있다고 가정 하 고 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-156">Suppose you want to have the Spanish translation, then run the following command:</span></span>
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-display-name-of-the-office-365-group"></a><span data-ttu-id="40ea6-157">Office 365 그룹의 표시 이름 변경</span><span class="sxs-lookup"><span data-stu-id="40ea6-157">Change Display name of the Office 365 group</span></span>

<span data-ttu-id="40ea6-158">표시 이름 Office 365 그룹의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-158">Display name specifies the name of the Office 365 group.</span></span> <span data-ttu-id="40ea6-159">Exchange 관리 센터 또는 Office 365 관리자 포털에서이 이름을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-159">You can see this name in your exchange admin center or Office 365 admin portal.</span></span> <span data-ttu-id="40ea6-160">Remove-unifiedgroup 명령을 실행 하 여 그룹의 표시 이름을 편집 하거나 표시 이름을 기존 Office 365 그룹에 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-160">You can edit the display name of the group or assign a display name to an existing Office 365 group by running the Set-UnifiedGroup command:</span></span>

```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a><span data-ttu-id="40ea6-161">Outlook에 대 한 Office 365 그룹의 기본 설정인 공개 또는 비공개로 변경</span><span class="sxs-lookup"><span data-stu-id="40ea6-161">Change the default setting of Office 365 Groups for Outlook to Public or Private</span></span>
<span data-ttu-id="40ea6-162"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="40ea6-162"></span></span>

<span data-ttu-id="40ea6-163">Outlook의 Office 365 그룹은 기본적으로 비공개로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-163">Office 365 Groups in Outlook are created as Private by default.</span></span> <span data-ttu-id="40ea6-164">조직에서 Office 365 그룹을 기본적으로 공용으로 생성 하려는 경우 다음 PowerShell cmdlet 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-164">If your organization wants Office 365 Groups to be created as Public by default (or back to Private), use this PowerShell cmdlet syntax:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
<span data-ttu-id="40ea6-165">비공개로 설정 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-165">To set to Private:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
<span data-ttu-id="40ea6-166">설정을 확인 하려면</span><span class="sxs-lookup"><span data-stu-id="40ea6-166">To verify the setting:</span></span> 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
<span data-ttu-id="40ea6-167">자세한 내용은 [set-organizationconfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig) 및 [Get-set-organizationconfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="40ea6-167">To learn more, see [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig) and [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig).</span></span>
  
## <a name="office-365-groups-cmdlets"></a><span data-ttu-id="40ea6-168">Office 365 그룹 cmdlet</span><span class="sxs-lookup"><span data-stu-id="40ea6-168">Office 365 Groups cmdlets</span></span>

<span data-ttu-id="40ea6-169">Office 365 그룹에서는 다음과 같은 cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-169">The following cmdlets can be used with Office 365 Groups.</span></span>
  
|<span data-ttu-id="40ea6-170">**cmdlet 이름**</span><span class="sxs-lookup"><span data-stu-id="40ea6-170">**Cmdlet name**</span></span>|<span data-ttu-id="40ea6-171">**설명**</span><span class="sxs-lookup"><span data-stu-id="40ea6-171">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="40ea6-172">Remove-unifiedgroup</span><span class="sxs-lookup"><span data-stu-id="40ea6-172">Get-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |<span data-ttu-id="40ea6-173">이 cmdlet을 사용 하 여 기존 Office 365 그룹을 조회 하 고 group 개체의 속성을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-173">Use this cmdlet to look up existing Office 365 Groups, and to view properties of the group object</span></span>  <br/> |
|[<span data-ttu-id="40ea6-174">Remove-unifiedgroup</span><span class="sxs-lookup"><span data-stu-id="40ea6-174">Set-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |<span data-ttu-id="40ea6-175">특정 Office 365 그룹의 속성 업데이트</span><span class="sxs-lookup"><span data-stu-id="40ea6-175">Update the properties of a specific Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="40ea6-176">Remove-unifiedgroup</span><span class="sxs-lookup"><span data-stu-id="40ea6-176">New-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |<span data-ttu-id="40ea6-177">새 Office 365 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-177">Create a new Office 365 group.</span></span> <span data-ttu-id="40ea6-178">이 cmdlet은 최소 매개 변수 집합을 제공 하며, 확장 속성에 대해 값을 설정 하려면 새 그룹을 만든 후 Remove-unifiedgroup을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-178">This cmdlet provides a minimal set of parameters, for setting values for extended properties use Set-UnifiedGroup after creating the new group</span></span>  <br/> |
|[<span data-ttu-id="40ea6-179">Remove-unifiedgroup을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-179">Remove-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |<span data-ttu-id="40ea6-180">기존 Office 365 그룹 삭제</span><span class="sxs-lookup"><span data-stu-id="40ea6-180">Delete an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="40ea6-181">Add-unifiedgrouplinks</span><span class="sxs-lookup"><span data-stu-id="40ea6-181">Get-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |<span data-ttu-id="40ea6-182">Office 365 그룹에 대 한 멤버 자격 및 소유자 정보 검색</span><span class="sxs-lookup"><span data-stu-id="40ea6-182">Retrieve membership and owner information for an Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="40ea6-183">Add-unifiedgrouplinks 추가</span><span class="sxs-lookup"><span data-stu-id="40ea6-183">Add-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |<span data-ttu-id="40ea6-184">기존 Office 365 그룹에 수백 또는 수천 명의 사용자 또는 새 소유자를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-184">Add hundred or thousands of users, or new owners, to an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="40ea6-185">Add-unifiedgrouplinks을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-185">Remove-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |<span data-ttu-id="40ea6-186">기존 Office 365 그룹에서 소유자 및 구성원을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-186">Remove owners and members from an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="40ea6-187">UserPhoto</span><span class="sxs-lookup"><span data-stu-id="40ea6-187">Get-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |<span data-ttu-id="40ea6-188">계정에 연결 된 사용자 사진에 대 한 정보를 확인 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-188">Used to view information about the user photo associated with an account.</span></span> <span data-ttu-id="40ea6-189">Active Directory에 사용자 사진 저장</span><span class="sxs-lookup"><span data-stu-id="40ea6-189">User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="40ea6-190">UserPhoto</span><span class="sxs-lookup"><span data-stu-id="40ea6-190">Set-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |<span data-ttu-id="40ea6-191">사용자 사진을 계정에 연결 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="40ea6-191">Used to associate a user photo with an account.</span></span> <span data-ttu-id="40ea6-192">Active Directory에 사용자 사진 저장</span><span class="sxs-lookup"><span data-stu-id="40ea6-192">User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="40ea6-193">UserPhoto</span><span class="sxs-lookup"><span data-stu-id="40ea6-193">Remove-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |<span data-ttu-id="40ea6-194">Office 365 그룹의 사진 제거</span><span class="sxs-lookup"><span data-stu-id="40ea6-194">Remove the photo for an Office 365 group</span></span>  <br/> |

## <a name="related-topics"></a><span data-ttu-id="40ea6-195">관련 항목</span><span class="sxs-lookup"><span data-stu-id="40ea6-195">Related topics</span></span>

[<span data-ttu-id="40ea6-196">Office 365 그룹으로 메일 그룹 업그레이드</span><span class="sxs-lookup"><span data-stu-id="40ea6-196">Upgrade distribution lists to Office 365 Groups</span></span>](https://docs.microsoft.com/en-us/office365/admin/manage/upgrade-distribution-lists)

[<span data-ttu-id="40ea6-197">Office 365 그룹을 만들 수 있는 사용자 관리</span><span class="sxs-lookup"><span data-stu-id="40ea6-197">Manage who can create Office 365 Groups</span></span>](https://docs.microsoft.com/en-us/office365/admin/create-groups/manage-creation-of-groups)

[<span data-ttu-id="40ea6-198">Office 365 그룹에 대한 게스트 액세스 관리</span><span class="sxs-lookup"><span data-stu-id="40ea6-198">Manage guest access to Office 365 Groups</span></span>](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[<span data-ttu-id="40ea6-199">에서 정적 그룹 구성원을 동적으로 변경</span><span class="sxs-lookup"><span data-stu-id="40ea6-199">Change static group membership to dynamic in</span></span>](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-change-type)
