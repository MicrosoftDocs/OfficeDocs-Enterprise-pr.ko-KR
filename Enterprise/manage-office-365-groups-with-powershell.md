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
- MET150
- MOE150
- MED150
- MBS150
- BSA160
- BCS160
ms.assetid: aeb669aa-1770-4537-9de2-a82ac11b0540
description: 이 문서는 Microsoft PowerShell에서 그룹에 대 한 일반적인 관리 작업을 수행 하는 단계를 제공 합니다.
ms.openlocfilehash: 83b7340cea1fd8d38bba073353b61f0b17fad8a0
ms.sourcegitcommit: e56f830ccff8d74d9edbff4a46a9ee1d613291ed
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/05/2019
ms.locfileid: "29741231"
---
# <a name="manage-office-365-groups-with-powershell"></a><span data-ttu-id="472f4-103">PowerShell을 사용하여 Office 365 그룹 관리</span><span class="sxs-lookup"><span data-stu-id="472f4-103">Manage Office 365 Groups with PowerShell</span></span>

 <span data-ttu-id="472f4-104">*마지막 업데이트 된-18 년 4 월, 2018*</span><span class="sxs-lookup"><span data-stu-id="472f4-104">*Last updated 18 April, 2018*</span></span> 
  
<span data-ttu-id="472f4-p101">이 문서는 Microsoft PowerShell에서 그룹에 대 한 일반적인 관리 작업을 수행 하는 단계를 제공 합니다. 또한 그룹에 대 한 PowerShell cmdlet 목록을 제공 합니다. SharePoint 사이트를 관리 하는 방법에 대 한 정보를 [PowerShell을 사용 하 여 SharePoint Online 관리 사이트](https://support.office.com/article/52ecc2ab-88c3-486e-b8ff-ef6a968ccd87.aspx)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="472f4-p101">This article provides the steps for doing common management tasks for Groups in Microsoft PowerShell. It also lists the PowerShell cmdlets for Groups. For info about managing SharePoint sites, see [Manage SharePoint Online sites using PowerShell](https://support.office.com/article/52ecc2ab-88c3-486e-b8ff-ef6a968ccd87.aspx).</span></span>
  
## <a name="common-tasks-for-managing-office-365-groups"></a><span data-ttu-id="472f4-108">Office 365 그룹을 관리 하기 위한 일반 작업</span><span class="sxs-lookup"><span data-stu-id="472f4-108">Common tasks for managing Office 365 Groups</span></span>

- [<span data-ttu-id="472f4-109">Office 365 그룹에 업그레이드 메일 그룹</span><span class="sxs-lookup"><span data-stu-id="472f4-109">Upgrade distribution lists to Office 365 Groups</span></span>](https://support.office.com/article/787d7a75-e201-46f3-a242-f698162ff09f.aspx)
    
- [<span data-ttu-id="472f4-110">Office 365 그룹을 만들 수 있는 사용자 관리</span><span class="sxs-lookup"><span data-stu-id="472f4-110">Manage who can create Office 365 Groups</span></span>](https://support.office.com/article/4c46c8cb-17d0-44b5-9776-005fced8e618.aspx)
    
- [<span data-ttu-id="472f4-111">Office 365 그룹에 대한 게스트 액세스 관리</span><span class="sxs-lookup"><span data-stu-id="472f4-111">Manage guest access to Office 365 Groups</span></span>](https://support.office.com/article/7c713d74-a144-4eab-92e7-d50df526ff96.aspx)
    
- [<span data-ttu-id="472f4-112">Azure Active Directory에서 동적으로 그룹 관리</span><span class="sxs-lookup"><span data-stu-id="472f4-112">Manage groups dynamically in Azure Active Directory</span></span>](https://go.microsoft.com/fwlink/?linkid=847632)
    
- <span data-ttu-id="472f4-113">Office 365 그룹에 수백 또는 수천 사용자를 추가 [추가 UnifiedGroupLinks cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=616191)을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="472f4-113">Add hundreds or thousands of users to Office 365 groups, use the [Add-UnifiedGroupLinks cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=616191).</span></span>
    
### <a name="link-to-your-office-365-groups-usage-guidelines"></a><span data-ttu-id="472f4-114">Office 365 그룹 사용 지침에 연결</span><span class="sxs-lookup"><span data-stu-id="472f4-114">Link to your Office 365 Groups usage guidelines</span></span>
<span data-ttu-id="472f4-115"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="472f4-115"></span></span>

<span data-ttu-id="472f4-p102">때 사용자가 [Outlook에서 그룹 만들기 또는 편집](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx)을 표시할 수 있습니다 조직의 사용 지침에 대 한 링크입니다. 예: 경우 필요한 특정 접두사 또는 그룹 이름에 추가할 접미사입니다.</span><span class="sxs-lookup"><span data-stu-id="472f4-p102">When users [create or edit a group in Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), you can show them a link to your organization's usage guidelines. For example, if you require a specific prefix or suffix to be added to a group name.</span></span>
  
<span data-ttu-id="472f4-p103">Azure Active Directory PowerShell을 사용 하 여 사용자에 게 Office 365 그룹에 대 한 조직의 사용 지침을 가리키도록 합니다. [그룹 설정을 구성 하기 위한 Azure Active Directory cmdlet](https://go.microsoft.com/fwlink/?LinkID=827484) 아웃 확인 하 고 사용 현황 지침은 하이퍼링크를 정의 하는 **디렉터리 수준에서 설정 만들기의** 에서 단계를 수행 합니다. 한번 AAD cmdlet을 실행, 사용자의 표시 됩니다 지침에 대 한 링크를 만들거나 Outlook에서 그룹을 편집 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="472f4-p103">Use the Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups. Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the usage guideline hyperlink. Once you run the AAD cmdlet, user's will see the link to your guidelines when they create or edit a group in Outlook.</span></span> 
  
![사용 현황 지침 링크를 사용 하 여 새 그룹 만들기](media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![조직의 Office 365 그룹 지침을 보려면 그룹 사용 지침을 클릭 합니다.](media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
### <a name="allow-users-to-send-as-the-office-365-group"></a><span data-ttu-id="472f4-123">Office 365 그룹으로 사용자가 보내기 하도록 허용</span><span class="sxs-lookup"><span data-stu-id="472f4-123">Allow users to Send as the Office 365 Group</span></span>
<span data-ttu-id="472f4-124"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="472f4-124"></span></span>

<span data-ttu-id="472f4-p104">Exchange 관리 센터에도 수행할 수 있습니다. [허용 구성원 "으로 보내기" 또는 "대신 보내기의"는 Office 365 그룹을](https://support.office.com/article/0ad41414-0cc6-4b97-90fb-06bec7bcf590.aspx)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="472f4-p104">You can also do this in the Exchange Admin Center. See [Allow members to "Send as" or "Send on behalf of" an Office 365 Group](https://support.office.com/article/0ad41414-0cc6-4b97-90fb-06bec7bcf590.aspx).</span></span>
  
<span data-ttu-id="472f4-p105">Office 365 그룹 "다른 사람 이름으로 보내기"를 사용 하도록 설정 하려면이 설정을 구성 하려면 [Add-recipientpermission](https://go.microsoft.com/fwlink/p/?LinkId=723960) 및 [Get RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=733239) cmdlet을 사용 합니다. 이 설정을 사용 하면 한 후 Office 365 그룹 사용자를 보내고 Office 365 그룹으로 전자 메일에 회신 Outlook 또는 Outlook 웹에서 사용할 수 있습니다. 사용자는 새 전자 메일을 만들고 "다른 이름으로 보내기" 필드 그룹의 전자 메일 주소를 변경 하려면 그룹에 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="472f4-p105">If you want to enable your Office 365 groups to "Send As", use the [Add-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=723960) and the [Get-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=733239) cmdlets to configure this. Once you enable this setting, Office 365 group users can use Outlook or Outlook on the web to send and reply to email as the Office 365 group. Users can go to the group, create a new email, and change the "Send As" field to the group's email address.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="472f4-130">메시지 그룹에 전송 되 고 그룹 대화에 표시 되도록 "사람 이름으로 보내기" 전자 메일을 작성 하는 경우 **참조** 필드에 그룹 전자 메일 주소를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="472f4-130">You'll need to add the group email address to the **Cc** field when you compose the "send as" email, so that the message is sent to the Group and appears in group conversations.</span></span> 
  
<span data-ttu-id="472f4-131">이 시간에 사서함 정책을 업데이트 하는 유일한 방법은 [PowerShell](https://technet.microsoft.com/en-us/library/cc482986.aspx)을 통해 됩니다.</span><span class="sxs-lookup"><span data-stu-id="472f4-131">At this time, the only way to update the mailbox policy is through [PowerShell](https://technet.microsoft.com/en-us/library/cc482986.aspx).</span></span>
  
- <span data-ttu-id="472f4-132">이 명령을 사용 하 여 그룹 별칭을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="472f4-132">Use this command to set the group alias.</span></span>
    
  ```
  $groupAlias = "TestSendAs"
  ```

- <span data-ttu-id="472f4-133">사용자 별칭을 설정 하려면이 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="472f4-133">Use this command to set the user alias.</span></span>
    
  ```
  $userAlias = "User"
  ```

- <span data-ttu-id="472f4-134">이 명령을 사용 하 여 받는 사람 세부 정보를 가져오는데 Get-recipient cmdlet에는 groupalias를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="472f4-134">Use this command to pass the groupalias to the Get-Recipient cmdlet to get the recipient details.</span></span>
    
  ```
  $groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias
  ```

- <span data-ttu-id="472f4-p106">다음 대상 받는 사람 이름 (그룹 이름) Add-recipientpermission cmdlet에 전달 해야 합니다. 사용자에 대 한 sendas 사용 권한을 부여지 것입니다 useralias-트러스트를 받 매개 변수에 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="472f4-p106">Then the target recipient name (Group name) needs to be passed to the Add-RecipientPermission cmdlet. The useralias for whom the sendas permission will be given will be assigned to the -Trustee parameter.</span></span>
    
  ```
  Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
  ```

- <span data-ttu-id="472f4-137">Cmdlet가 실행 되 면 사용자가 Outlook 또는 Outlook 웹에 있는 그룹 전자 메일 주소에서 \*\*\*\* 필드를 추가 하 여 그룹으로 보낼으로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="472f4-137">Once the cmdlet is executed, users can go to Outlook or Outlook on the web to send as the group, by adding the group email address to the **From** field.</span></span> 
    
### <a name="create-classifications-for-office-groups-in-your-organization"></a><span data-ttu-id="472f4-138">조직에서 Office 그룹에 대 한 분류 만들기</span><span class="sxs-lookup"><span data-stu-id="472f4-138">Create classifications for Office groups in your organization</span></span>

<span data-ttu-id="472f4-p107">조직에서 사용자가 Office 365 그룹을 만들 때 설정할 수 있는 분류를 만들 수 있습니다. 예, 자신이 만든 그룹에 "표준", "Secret" 및 "위쪽 비밀"를 설정 하는 사용자를 허용할 수 있습니다. 기본적으로 설정 되지 않은 그룹 분류 하 고를 설정 하 여 사용자에 대 한 순서 대로 만들어야 합니다. PowerShell Azure Active Directory를 사용 하 여 사용자에 게 Office 365 그룹에 대 한 조직의 사용 지침을 가리키도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="472f4-p107">You can create classifications that the users in your organization can set when they create an Office 365 group. For example, you can allow users to set "Standard", "Secret", and "Top Secret" on groups they create. Group classifications aren't set by default and you need to create it in order for your users to set it. Use Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups.</span></span>
  
<span data-ttu-id="472f4-143">[그룹 설정을 구성 하기 위한 Azure Active Directory cmdlet](https://go.microsoft.com/fwlink/?LinkID=827484) 아웃 확인 하 고 Office 365 그룹에 대 한 분류를 정의 하는 **디렉터리 수준에서 설정 만들기의** 에서 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="472f4-143">Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the classification for Office 365 groups.</span></span> 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

<span data-ttu-id="472f4-144">사용할 수 있는 각 분류에 대 한 설명을 연결 하기 위해 설정을 정의 하려면 *ClassificationDescriptions* 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="472f4-144">In order to associate a description to each classification you can use the settings attribute  *ClassificationDescriptions*  to define.</span></span> 
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description", where Classification matches the strings in the ClassificationList.
```

<span data-ttu-id="472f4-145">예제:</span><span class="sxs-lookup"><span data-stu-id="472f4-145">Example:</span></span>
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

<span data-ttu-id="472f4-146">프로그램 분류를 설정 하려면 위의 Azure Active Directory cmdlet을 실행 한 후 특정 그룹에 대 한 분류를 설정 하려는 경우 [집합 UnifiedGroup](https://go.microsoft.com/fwlink/?LinkID=616189) cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="472f4-146">After you run the above Azure Active Directory cmdlet to set your classification, run the [Set-UnifiedGroup](https://go.microsoft.com/fwlink/?LinkID=616189) cmdlet if you want to set the classification for a specific group.</span></span> 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

<span data-ttu-id="472f4-147">또는 분류를 사용 하 여 새 그룹 만들기.</span><span class="sxs-lookup"><span data-stu-id="472f4-147">Or create a new group with a classification.</span></span>
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

<span data-ttu-id="472f4-148">에 대 한 자세한 내용은 Exchange Online PowerShell을 사용 하 여 [Exchange online PowerShell을 사용 하](https://go.microsoft.com/fwlink/?LinkID=402831) 고 [Connect to Exchange Online PowerShell](https://go.microsoft.com/fwlink/?LinkID=722415) 체크아웃 합니다.</span><span class="sxs-lookup"><span data-stu-id="472f4-148">Check out [Using PowerShell with Exchange Online](https://go.microsoft.com/fwlink/?LinkID=402831) and [Connect to Exchange Online PowerShell](https://go.microsoft.com/fwlink/?LinkID=722415) for more details on using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="472f4-149">이러한 설정을 사용 하도록 설정 된 후 그룹 소유자가 수는 분류 드롭다운 메뉴의 웹 서버 및 Outlook에는 Outlook에서 선택 하 고 그룹 **편집** 페이지에서 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="472f4-149">Once these settings are enabled, the group owner will be able to choose a classification from the drop down menu in Outlook on the Web and Outlook, and save it from the **Edit** group page.</span></span> 
  
![Office 365 그룹 분류를 선택 합니다.](media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
### <a name="hide-office-365-groups-from-gal"></a><span data-ttu-id="472f4-151">GAL에서 Office 365 그룹 숨기기</span><span class="sxs-lookup"><span data-stu-id="472f4-151">Hide Office 365 Groups from GAL</span></span>
<span data-ttu-id="472f4-152"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="472f4-152"></span></span>

<span data-ttu-id="472f4-p108">Office 365 그룹 전체 주소 목록 (gal 전체) 및 조직의 다른 목록에 표시할지 여부를 지정할 수 있습니다. 예, 주소 목록에 표시 되려면 원하지 않는 법률 부서 그룹을 설치한 경우 GAL에 나타나지 않게 해당 그룹을 중지할 수 있습니다. 다음과 같은 주소 목록에서 그룹을 숨기려면 Set-Unified 그룹 commandlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="472f4-p108">You can specify whether a Office 365 group appears in the global address list (GAL) and other lists in your organization. For example, if you have a legal department group that you don't want to show up in the address list, you can stop that group from appearing in GAL. Run the Set-Unified Group commandlet to hide the group from address list like this:</span></span>
  
```
  Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

### <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a><span data-ttu-id="472f4-156">Office 365 그룹에 메시지를 보내려고 내부 사용자만 허용</span><span class="sxs-lookup"><span data-stu-id="472f4-156">Allow only internal users to send message to Office 365 group</span></span>
<span data-ttu-id="472f4-157"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="472f4-157"></span></span>

<span data-ttu-id="472f4-p109">다른 조직에서 사용자가 Office 365 그룹에 전자 메일을 보낼 수 하지 않을 경우에 해당 그룹에 대 한 설정을 변경할 수 있습니다. 내부 사용자만 그룹에 전자 메일을 보낼 수 있습니다. 외부 사용자가 해당 그룹에 메시지를 전송 하려고 하는 경우 거부 됩니다.</span><span class="sxs-lookup"><span data-stu-id="472f4-p109">If you don't want users from other organization to send email to a Office 365 group, you can change the settings for that group. It will allow only internal users to send an email to your group. If external user try to send message to that group they will be rejected.</span></span>
  
<span data-ttu-id="472f4-161">다음과 같이이 설정을 업데이트 하려면 집합 UnifiedGroup commandlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="472f4-161">Run the Set-UnifiedGroup commandlet to update this setting, like this:</span></span>
  
```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

### <a name="add-mailtips-to-the-office-365-groups"></a><span data-ttu-id="472f4-162">Office 365 그룹에 메일 설명을 추가합니다</span><span class="sxs-lookup"><span data-stu-id="472f4-162">Add MailTips to the Office 365 Groups</span></span>
<span data-ttu-id="472f4-163"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="472f4-163"></span></span>

<span data-ttu-id="472f4-164">보낸사람을 Office 365 그룹에 전자 메일을 보낼 하려고 때마다 메일 설명은 자신을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="472f4-164">Whenever a sender tries to send an email to an Office 365 group, a MailTip can be shown to him.</span></span>
  
<span data-ttu-id="472f4-165">그룹에 메일 설명을 추가 하려면 Set-Unified 그룹 commandlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="472f4-165">Run the Set-Unified Group commandlet to add a mailTip to the group:</span></span>
  
```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

<span data-ttu-id="472f4-p110">메일 설명, 함께 설정할 수도 있습니다 MailTipTranslations 보려면 추가 언어를 지정 하는 메일 설명은 합니다. 스페인어 번역을 한 후 다음 명령을 실행 하려는 경우를 가정해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="472f4-p110">Along with MailTip, you can also set MailTipTranslations, which specifies additional languages fro the MailTip. Suppose you want to have the Spanish translation, then run the following command:</span></span>
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

### <a name="change-display-name-of-the-office-365-group"></a><span data-ttu-id="472f4-168">Office 365 그룹의 표시 이름 변경</span><span class="sxs-lookup"><span data-stu-id="472f4-168">Change Display name of the Office 365 group</span></span>

<span data-ttu-id="472f4-p111">표시 이름에는 Office 365 그룹의 이름을 지정합니다. Exchange 관리 센터 또는 o365 관리 포털에이 이름을 확인할 수 있습니다. 그룹의 표시 이름을 편집 하거나 집합 UnifiedGroup 명령을 실행 하 여 기존 Office 365 그룹에 표시 이름을 할당 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="472f4-p111">Display name specifies the name of the Office 365 group. You can see this name in your exchange admin center or o365 admin portal. You can edit the display name of the group or assign a display name to an exisiting Office 365 group by running Set-UnifiedGroup command:</span></span>
  
```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

### <a name="manage-user-photos-in-office-365-groups"></a><span data-ttu-id="472f4-172">Office 365 그룹에서 사용자 사진 관리</span><span class="sxs-lookup"><span data-stu-id="472f4-172">Manage user photos in Office 365 Groups</span></span>

|<span data-ttu-id="472f4-173">**cmdlet 이름**</span><span class="sxs-lookup"><span data-stu-id="472f4-173">**Cmdlet name**</span></span>|<span data-ttu-id="472f4-174">**설명**</span><span class="sxs-lookup"><span data-stu-id="472f4-174">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="472f4-175">Get-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="472f4-175">Get-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |<span data-ttu-id="472f4-p112">사용 하는 계정에 연결 된 사용자 사진에 대 한 정보를 볼 수 있습니다. Active Directory에 저장 된 사용자 사진</span><span class="sxs-lookup"><span data-stu-id="472f4-p112">Used to view information about the user photo associated with an account. User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="472f4-178">집합 UserPhoto</span><span class="sxs-lookup"><span data-stu-id="472f4-178">Set-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |<span data-ttu-id="472f4-p113">계정을 사용 하 여 사용자 사진에 연결 하는 데 사용 됩니다. Active Directory에 저장 된 사용자 사진</span><span class="sxs-lookup"><span data-stu-id="472f4-p113">Used to associate a user photo with an account. User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="472f4-181">UserPhoto 제거</span><span class="sxs-lookup"><span data-stu-id="472f4-181">Remove-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |<span data-ttu-id="472f4-182">Office 365 그룹에 대 한 사진 제거</span><span class="sxs-lookup"><span data-stu-id="472f4-182">Remove the photo for an Office 365 group</span></span>  <br/> |
   
### <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a><span data-ttu-id="472f4-183">Outlook에 대 한 Office 365 그룹의 기본 설정을 공용 또는 개인으로 변경</span><span class="sxs-lookup"><span data-stu-id="472f4-183">Change the default setting of Office 365 Groups for Outlook to Public or Private</span></span>
<span data-ttu-id="472f4-184"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="472f4-184"></span></span>

<span data-ttu-id="472f4-p114">Office 365 Outlook에서 그룹으로 개인 기본적으로 만들어집니다. 조직이 기본적으로 (또는를 Private) 공용으로 만들어야 하는 Outlook에 대 한 Office 365 그룹을 하려는 경우에이 PowerShell cmdlet 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="472f4-p114">Office 365 Groups in Outlook are created as Private by default. If your organization wants Office 365 Groups for Outlook to be created as Public by default (or back to Private), use this PowerShell cmdlet syntax:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
<span data-ttu-id="472f4-187">Private로 설정:</span><span class="sxs-lookup"><span data-stu-id="472f4-187">To set to Private:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
<span data-ttu-id="472f4-188">설정을 확인</span><span class="sxs-lookup"><span data-stu-id="472f4-188">To verify the setting:</span></span> 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
<span data-ttu-id="472f4-189">자세한 내용은 [Set-organizationconfig](https://go.microsoft.com/fwlink/?linkid=871816) 및 [Get-organizationconfig](https://go.microsoft.com/fwlink/?linkid=871817)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="472f4-189">To learn more, see [Set-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871816) and [Get-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871817).</span></span>
  
## <a name="office-365-groups-cmdlets"></a><span data-ttu-id="472f4-190">Office 365 그룹 cmdlet</span><span class="sxs-lookup"><span data-stu-id="472f4-190">Office 365 Groups cmdlets</span></span>

<span data-ttu-id="472f4-p115">Office 365 그룹에는 다음 cmdlet은 사용할 수 최근에 했습니다. 이 사용할 수 없는 경우 Office 365 구독 업데이트 되지 않은이 기능을 가진 아직 합니다. 메시지 센터 및 [Microsoft 365 로드맵](https://www.microsoft.com/microsoft-365/roadmap)확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="472f4-p115">The following cmdlets were recently made available to Office 365 Groups. If you aren't able to use these, your Office 365 subscription has not been updated with this functionality yet. Check your Message Center and the [Microsoft 365 Roadmap](https://www.microsoft.com/microsoft-365/roadmap).</span></span>
  
|<span data-ttu-id="472f4-194">**cmdlet 이름**</span><span class="sxs-lookup"><span data-stu-id="472f4-194">**Cmdlet name**</span></span>|<span data-ttu-id="472f4-195">**설명**</span><span class="sxs-lookup"><span data-stu-id="472f4-195">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="472f4-196">Get-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="472f4-196">Get-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |<span data-ttu-id="472f4-197">이 cmdlet을 사용 하면 기존 Office 365 그룹을 조회 하 고 그룹 개체의 속성을 보려면</span><span class="sxs-lookup"><span data-stu-id="472f4-197">Use this cmdlet to look up existing Office 365 Groups, and to view properties of the group object</span></span>  <br/> |
|[<span data-ttu-id="472f4-198">Set-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="472f4-198">Set-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |<span data-ttu-id="472f4-199">특정 Office 365 그룹의 속성을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="472f4-199">Update the properties of a specific Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="472f4-200">New-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="472f4-200">New-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |<span data-ttu-id="472f4-p116">새 Office 365 그룹을 만듭니다. 이 cmdlet은 최소한의 매개 변수 집합을 제공, 설정에 대 한 확장 된 속성 값을 사용 하 여 집합 UnifiedGroup 새 그룹을 만든 후</span><span class="sxs-lookup"><span data-stu-id="472f4-p116">Create a new Office 365 group. This cmdlet provides a minimal set of parameters, for setting values for extended properties use Set-UnifiedGroup after creating the new group</span></span>  <br/> |
|[<span data-ttu-id="472f4-203">Remove-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="472f4-203">Remove-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |<span data-ttu-id="472f4-204">기존 Office 365 그룹 삭제</span><span class="sxs-lookup"><span data-stu-id="472f4-204">Delete an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="472f4-205">Get-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="472f4-205">Get-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |<span data-ttu-id="472f4-206">Office 365 그룹 멤버 자격 및 소유자 정보를 검색</span><span class="sxs-lookup"><span data-stu-id="472f4-206">Retrieve membership and owner information for an Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="472f4-207">Add-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="472f4-207">Add-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |<span data-ttu-id="472f4-208">추가 백 또는 다양 한 사용자 또는 기존 Office 365 그룹에 새 소유자</span><span class="sxs-lookup"><span data-stu-id="472f4-208">Add hundred or thousands of users, or new owners, to an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="472f4-209">Remove-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="472f4-209">Remove-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |<span data-ttu-id="472f4-210">기존 Office 365 그룹에서 소유자 및 구성원을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="472f4-210">Remove owners and members from an existing Office 365 Group</span></span>  <br/> |
   
## <a name="for-more-information"></a><span data-ttu-id="472f4-211">자세한 내용</span><span class="sxs-lookup"><span data-stu-id="472f4-211">For more information</span></span>

[<span data-ttu-id="472f4-212">Office 365 PowerShell을 사용하여 Office 365 관리</span><span class="sxs-lookup"><span data-stu-id="472f4-212">Manage Office 365 with Office 365 PowerShell</span></span>](powershell/manage-office-365-with-office-365-powershell.md)
