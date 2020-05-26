---
title: Multi-Geo 환경에서 Exchange Online 사서함 관리
ms.reviewer: adwood
ms.author: chrisda
author: chrisda
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
localization_priority: Priority
description: Microsoft PowerShell을 사용하여 Exchange Online Multi-Geo 설정을 관리하는 방법을 알아보세요.
ms.openlocfilehash: d2498178193f71c1ffaea6141a09cc76e826e99e
ms.sourcegitcommit: ee6fcb8c78de748fa203deacf799f66ad99f18e1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2020
ms.locfileid: "44352948"
---
# <a name="administering-exchange-online-mailboxes-in-a-multi-geo-environment"></a><span data-ttu-id="fe7b7-103">Multi-Geo 환경에서 Exchange Online 사서함 관리</span><span class="sxs-lookup"><span data-stu-id="fe7b7-103">Administering Exchange Online mailboxes in a multi-geo environment</span></span>

<span data-ttu-id="fe7b7-104">Microsoft 365 환경에서 Multi-Geo 속성을 보고 구성하려면 원격 PowerShell이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-104">Remote PowerShell is required to view and configure multi geo properties in your Microsoft 365 environment.</span></span> <span data-ttu-id="fe7b7-105">Exchange Online PowerShell에 연결하려면 [Exchange Online PowerShell에 연결](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-105">To connect to Exchange Online PowerShell, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span>

<span data-ttu-id="fe7b7-106">사용자 개체의 **PreferredDataLocation** 속성을 보려면 v1.x에서 [Microsoft Azure Active Directory PowerShell 모듈](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 이상이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-106">You need the [Microsoft Azure Active Directory PowerShell Module](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 or later in v1.x to see the **PreferredDataLocation** property on user objects.</span></span> <span data-ttu-id="fe7b7-107">AAD Connect를 통해 AAD에 동기화된 사용자 개체의 **PreferredDataLocation** 값은 AAD PowerShell을 통해 직접 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-107">User objects synchronized via AAD Connect into AAD cannot have their **PreferredDataLocation** value directly modified via AAD PowerShell.</span></span> <span data-ttu-id="fe7b7-108">클라우드 전용 사용자 개체는 AAD PowerShell을 통해 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-108">Cloud-only user objects can be modified via AAD PowerShell.</span></span> <span data-ttu-id="fe7b7-109">Azure AD PowerShell에 연결하려면 [PowerShell에 연결](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-109">To connect to Azure AD PowerShell, see [Connect to PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span>

## <a name="connect-directly-to-a-geo-location-using-exchange-online-powershell"></a><span data-ttu-id="fe7b7-110">Exchange Online PowerShell을 사용하여 지리적 위치에 직접 연결</span><span class="sxs-lookup"><span data-stu-id="fe7b7-110">Connect directly to a geo location using Exchange Online PowerShell</span></span>

<span data-ttu-id="fe7b7-111">일반적으로 Exchange Online PowerShell은 중앙 지리적 위치에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-111">Typically, Exchange Online PowerShell will connect to the central geo location.</span></span> <span data-ttu-id="fe7b7-112">그러나 위성 지리적 위치에 직접 연결할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-112">But, you can also connect directly to satellite geo locations.</span></span> <span data-ttu-id="fe7b7-113">특정 위치의 사용자만 관리하는 경우 성능 개선을 위해 해당 위성 위치에 직접 연결할 것을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-113">Because of performance improvements, we recommend connecting directly to the satellite geo location when you only manage users in that location.</span></span>

<span data-ttu-id="fe7b7-114">특정 지리적 위치에 연결하려는 경우 *ConnectionUri* 매개 변수가 일반 연결 지침과는 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-114">To connect to a specific geo location, the *ConnectionUri* parameter is different than the regular connection instructions.</span></span> <span data-ttu-id="fe7b7-115">나머지 명령과 값은 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-115">The rest of the commands and values are the same.</span></span> <span data-ttu-id="fe7b7-116">그 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-116">The steps are:</span></span>

1. <span data-ttu-id="fe7b7-117">로컬 컴퓨터에서 Windows PowerShell을 열고 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-117">On your local computer, open Windows PowerShell and run the following command:</span></span>

   ```powershell
   $UserCredential = Get-Credential
   ```

   <span data-ttu-id="fe7b7-118">**Windows PowerShell 자격 증명 요청** 대화 상자에서 회사 또는 학교 계정 사용자 이름과 비밀번호를 입력한 다음, **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-118">In the **Windows PowerShell Credential Request** dialog box, type your work or school account and password, and then click **OK**.</span></span>

2. <span data-ttu-id="fe7b7-119">대상 지리적 위치에서 `<emailaddress>`를 **원하는** 사서함의 이메일 주소로 바꾸고 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-119">Replace `<emailaddress>` with the email address of **any** mailbox in the target geo location and run the following command.</span></span> <span data-ttu-id="fe7b7-120">1단계에서 사서함에 대한 권한과 자격 증명과의 관계는 요인이 아닙니다. 이메일 주소는 단지 연결할 위치를 Exchange Online에 알려줄 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-120">Your permissions on the mailbox and the relationship to your credentials in Step 1 are not a factor; the email address simply tells Exchange Online where to connect.</span></span>
  
   ```powershell
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   <span data-ttu-id="fe7b7-121">예를 들어 olga@contoso.onmicrosoft.com이 연결할 지리적 위치의 유효한 사서함 전자 메일 주소인 경우 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-121">For example, if olga@contoso.onmicrosoft.com is the email address of a valid mailbox in the geo location where you want to connect, run the following command:</span></span>

   ```powershell
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

3. <span data-ttu-id="fe7b7-122">다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-122">Run the following command:</span></span>

    ```powershell
    Import-PSSession $Session
    ```

## <a name="view-the-available-geo-locations-that-are-configured-in-your-exchange-online-organization"></a><span data-ttu-id="fe7b7-123">Exchange Online 조직에서 구성된 사용 가능한 지리적 위치 보기</span><span class="sxs-lookup"><span data-stu-id="fe7b7-123">View the available geo locations that are configured in your Exchange Online organization</span></span>

<span data-ttu-id="fe7b7-124">Microsoft 365 Multi-Geo에서 구성된 지리적 위치 목록을 보려면 Exchange Online PowerShell에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-124">To see the list of configured geo locations in Microsoft 365 Multi-Geo, run the following command in Exchange Online PowerShell:</span></span>

```powershell
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

## <a name="view-the-central-geo-location-for-your-exchange-online-organization"></a><span data-ttu-id="fe7b7-125">Exchange Online 조직의 중앙 지리적 위치 보기</span><span class="sxs-lookup"><span data-stu-id="fe7b7-125">View the central geo location for your Exchange Online organization</span></span>

<span data-ttu-id="fe7b7-126">테넌트의 중앙 지리적 위치를 보려면 Exchange Online PowerShell에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-126">To view your tenant's central geo location, run the following command in Exchange Online PowerShell:</span></span>

```powershell
Get-OrganizationConfig | Select DefaultMailboxRegion
```

## <a name="find-the-geo-location-of-a-mailbox"></a><span data-ttu-id="fe7b7-127">사서함의 지리적 위치 찾기</span><span class="sxs-lookup"><span data-stu-id="fe7b7-127">Find the geo location of a mailbox</span></span>

<span data-ttu-id="fe7b7-128">Exchange Online PowerShell의 **Get-Mailbox** cmdlet은 사서함에 다음과 같은 Multi-Geo 관련 속성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-128">The **Get-Mailbox** cmdlet in Exchange Online PowerShell displays the following multi-geo related properties on mailboxes:</span></span>

- <span data-ttu-id="fe7b7-129">**Database**: 데이터베이스 이름의 첫 세 글자는 지역 코드에 해당하며, 사서함의 현재 위치를 알려줍니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-129">**Database**: The first 3 letters of the database name correspond to the geo code, which tells you where the mailbox is currently located.</span></span> <span data-ttu-id="fe7b7-130">온라인 보관 사서함의 경우 **ArchiveDatabase** 속성을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-130">For Online Archive Mailboxes the **ArchiveDatabase** property should be used.</span></span>

- <span data-ttu-id="fe7b7-131">**MailboxRegion**: 관리자가 설정한 지리적 위치 코드를 지정합니다(Azure AD의 **PreferredDataLocation**에서 동기화됨).</span><span class="sxs-lookup"><span data-stu-id="fe7b7-131">**MailboxRegion**: Specifies the geo location code that was set by the admin (synchronized from **PreferredDataLocation** in Azure AD).</span></span>

- <span data-ttu-id="fe7b7-132">**MailboxRegionLastUpdateTime**: MailboxRegion이 마지막으로 업데이트(자동 또는 수동으로)된 시간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-132">**MailboxRegionLastUpdateTime**: Indicates when MailboxRegion was last updated (either automatically or manually).</span></span>

<span data-ttu-id="fe7b7-133">사서함의 속성을 보려면 다음 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-133">To see these properties for a mailbox, use the following syntax:</span></span>

```powershell
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

<span data-ttu-id="fe7b7-134">예를 들어 chris@contoso.onmicrosoft.com의 사서함 위치 정보를 보려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-134">For example, to see the geo location information for the mailbox chris@contoso.onmicrosoft.com, run the following command:</span></span>

```powershell
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

<span data-ttu-id="fe7b7-135">이 명령의 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-135">The output of the command looks like this:</span></span>

```powershell
Database                    : EURPR03DG077-db007
MailboxRegion               : EUR
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM
```

> <span data-ttu-id="fe7b7-136">**참고:** 데이터베이스 이름의 지리적 위치 코드가 **MailboxRegion** 값과 일치하지 않는 경우 사서함은 자동으로 재배치 큐에 넣어지며 **MailboxRegion** 값에서 지정한 지리적 위치로 이동합니다(Exchange Online이 이러한 속성 값 사이의 불일치를 찾음).</span><span class="sxs-lookup"><span data-stu-id="fe7b7-136">**Note:** If the geo location code in the database name doesn't match **MailboxRegion** value, the mailbox will be automatically be put into a relocation queue and moved to the geo location specified by the **MailboxRegion** value (Exchange Online looks for a mismatch between these property values).</span></span>

## <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo-location"></a><span data-ttu-id="fe7b7-137">기존 클라우드 전용 사서함을 특정 지리적 위치로 이동</span><span class="sxs-lookup"><span data-stu-id="fe7b7-137">Move an existing cloud-only mailbox to a specific geo location</span></span>

<span data-ttu-id="fe7b7-138">클라우드 전용 사용자는 AAD Connect로 테넌트에 동기화되지 않은 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-138">A cloud-only user is a user not synchronized to the tenant via AAD Connect.</span></span> <span data-ttu-id="fe7b7-139">이 사용자는 Azure AD에서 직접 만들어졌습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-139">This user was created directly in Azure AD.</span></span> <span data-ttu-id="fe7b7-140">Windows PowerShell용 Azure AD 모듈에서 **Get-MsolUser** 및 **Set-MsolUser** cmdlet을 사용하여 클라우드 전용 사용자의 사서함을 저장할 지리적 위치를 보거나 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-140">Use the **Get-MsolUser** and **Set-MsolUser** cmdlets in the Azure AD Module for Windows PowerShell to view or specify the geo location where a cloud-only user's mailbox will be stored.</span></span>

<span data-ttu-id="fe7b7-141">사용자의 **PreferredDataLocation** 값을 보려면 Azure AD PowerShell에서 이 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-141">To view the **PreferredDataLocation** value for a user, use this syntax in Azure AD PowerShell:</span></span>

```powershell
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

<span data-ttu-id="fe7b7-142">예를 들어 사용자 michelle@contoso.onmicrosoft.com의 **PreferredDataLocation** 값을 보려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-142">For example, to see the **PreferredDataLocation** value for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

```powershell
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

<span data-ttu-id="fe7b7-143">클라우드 전용 사용자 개체의 **PreferredDataLocation** 값을 수정하려면 Azure AD PowerShell에서 다음 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-143">To modify the **PreferredDataLocation** value for a cloud-only user object, use the following syntax in Azure AD PowerShell:</span></span>

```powershell
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoLocationCode>
```

<span data-ttu-id="fe7b7-144">예를 들어 사용자 michelle@contoso.onmicrosoft.com의 유럽 연합(EUR) 지역에 **PreferredDataLocation** 값을 설정하려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-144">For example, to set the **PreferredDataLocation** value to the European Union (EUR) geo for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

```powershell
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

<span data-ttu-id="fe7b7-145">**참고**:</span><span class="sxs-lookup"><span data-stu-id="fe7b7-145">**Notes**:</span></span>

- <span data-ttu-id="fe7b7-146">앞서 설명한 대로 온-프레미스 Active Directory의 동기화된 사용자 개체에는 이 절차를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-146">As mentioned previously you cannot use this procedure for synchronized user objects from on-premises Active Directory.</span></span> <span data-ttu-id="fe7b7-147">Active Directory에서 **PreferredDataLocation** 값을 변경하고 AAD Connect를 사용하여 동기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-147">You need to change the **PreferredDataLocation** value in Active Directory and synchronize it using AAD Connect.</span></span> <span data-ttu-id="fe7b7-148">자세한 내용은 [Azure Active Directory Connect 동기화: Microsoft 365 리소스의 기본 데이터 위치 구성](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-148">For more information, see [Azure Active Directory Connect sync: Configure preferred data location for Microsoft 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

- <span data-ttu-id="fe7b7-149">새로운 지리적 위치로 사서함 위치를 변경하는 데 걸리는 시간은 몇 가지 요인에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-149">How long it takes to relocate a mailbox to a new geo location depends on several factors:</span></span>

  - <span data-ttu-id="fe7b7-150">사서함 크기 및 유형</span><span class="sxs-lookup"><span data-stu-id="fe7b7-150">The size and type of mailbox.</span></span>

  - <span data-ttu-id="fe7b7-151">이동 중인 사서함 수</span><span class="sxs-lookup"><span data-stu-id="fe7b7-151">The number of mailboxes being moved.</span></span>

  - <span data-ttu-id="fe7b7-152">이동 리소스의 가용성</span><span class="sxs-lookup"><span data-stu-id="fe7b7-152">The availability of move resources.</span></span>

### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a><span data-ttu-id="fe7b7-153">사용하지 않도록 설정한 소송 보존 중인 사서함 이동</span><span class="sxs-lookup"><span data-stu-id="fe7b7-153">Move disabled mailboxes that are on Litigation Hold</span></span>

<span data-ttu-id="fe7b7-154">eDiscovery 목적으로 보존된 소송 보존 중인 사서함을 사용하지 않도록 설정하면, 사용하지 않도록 설정한 상태에서 **PreferredDataLocation** 값을 변경해도 이동할 수가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-154">Disabled mailboxes on Litigation Hold that are preserved for eDiscovery purposes cannot be moved by changing their **PreferredDataLocation** value in their disabled state.</span></span> <span data-ttu-id="fe7b7-155">사용하지 않도록 설정한 소송 보존 중인 사서함을 이동하려면:</span><span class="sxs-lookup"><span data-stu-id="fe7b7-155">To move a disabled mailbox on litigation hold:</span></span>

1. <span data-ttu-id="fe7b7-156">사서함에 일시적으로 라이선스를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-156">Temporarily assign a license to the mailbox.</span></span>

2. <span data-ttu-id="fe7b7-157">**PreferredDataLocation**을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-157">Change the **PreferredDataLocation**.</span></span>

3. <span data-ttu-id="fe7b7-158">선택한 지리적 위치로 라이선스를 이동한 후 사서함에서 라이선스를 제거함으로써 사용 안 함 상태로 되돌립니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-158">Remove the license from the mailbox after it has been moved to the selected geo location to put it back into the disabled state.</span></span>

## <a name="create-new-cloud-mailboxes-in-a-specific-geo-location"></a><span data-ttu-id="fe7b7-159">특정 지리적 위치에 새 클라우드 사서함 만들기</span><span class="sxs-lookup"><span data-stu-id="fe7b7-159">Create new cloud mailboxes in a specific geo location</span></span>

<span data-ttu-id="fe7b7-160">특정 지리적 위치에 새 사서함을 만들려면 다음 단계 중 하나를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-160">To create a new mailbox in a specific geo location, you need to do either of these steps:</span></span>

- <span data-ttu-id="fe7b7-161">Exchange Online에 사서함을 만들기 *전에* 이전 섹션에 설명된 대로 **PreferredDataLocation** 값부터 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-161">Configure the **PreferredDataLocation** value as described in the previous section *before* the mailbox is created in Exchange Online.</span></span> <span data-ttu-id="fe7b7-162">예를 들어 라이선스를 할당하기 전에 먼저 사용자의 **PreferredDataLocation** 값을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-162">For example, configure the **PreferredDataLocation** value on a user before assigning a license.</span></span>

- <span data-ttu-id="fe7b7-163">**PreferredDataLocation** 값을 설정함과 동시에 라이선스를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-163">Assign a license at the same time you set the **PreferredDataLocation** value.</span></span>

<span data-ttu-id="fe7b7-164">특정 지리적 위치에 새로운 클라우드 전용 라이선스 사용자 (AAD Connect 동기화가 아닌)를 만들려면 Azure AD PowerShell에서 다음 구문을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-164">To create a new cloud-only licensed user (not AAD Connect synchronized) in a specific geo location, use the following syntax in Azure AD PowerShell:</span></span>

```powershell
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoLocationCode>
```

<span data-ttu-id="fe7b7-165">이 예제에서는 다음 값을 사용하여 Elizabeth Brunner를 위한 새 사용자 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-165">This example create a new user account for Elizabeth Brunner with the following values:</span></span>

- <span data-ttu-id="fe7b7-166">사용자 계정 이름: ebrunner@contoso.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="fe7b7-166">User principal name: ebrunner@contoso.onmicrosoft.com</span></span>

- <span data-ttu-id="fe7b7-167">이름: Elizabeth</span><span class="sxs-lookup"><span data-stu-id="fe7b7-167">First name: Elizabeth</span></span>

- <span data-ttu-id="fe7b7-168">성: Brunner</span><span class="sxs-lookup"><span data-stu-id="fe7b7-168">Last name: Brunner</span></span>

- <span data-ttu-id="fe7b7-169">표시할 이름: Elizabeth Brunner</span><span class="sxs-lookup"><span data-stu-id="fe7b7-169">Display name: Elizabeth Brunner</span></span>

- <span data-ttu-id="fe7b7-170">비밀번호: 임의로 생성되고 명령의 결과에 표시됨(*비밀번호* 매개 변수를 사용하지 않고 있기 때문)</span><span class="sxs-lookup"><span data-stu-id="fe7b7-170">Password: randomly-generated and shown in the results of the command (because we're not using the *Password* parameter)</span></span>

- <span data-ttu-id="fe7b7-171">라이선스: `contoso:ENTERPRISEPREMIUM` (E5)</span><span class="sxs-lookup"><span data-stu-id="fe7b7-171">License: `contoso:ENTERPRISEPREMIUM` (E5)</span></span>

- <span data-ttu-id="fe7b7-172">위치: 오스트레일리아(AUS)</span><span class="sxs-lookup"><span data-stu-id="fe7b7-172">Location: Australia (AUS)</span></span>

```powershell
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

<span data-ttu-id="fe7b7-173">새 사용자 계정을 만들고 Azure AD PowerShell에서 LicenseAssignment 값을 찾는 방법에 대한 자세한 내용은 [PowerShell을 사용하여 사용자 계정 만들기](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) 및 [PowerShell을 사용하여 라이선스 및 서비스 보기](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-173">For more information about creating new user accounts and finding LicenseAssignment values in Azure AD PowerShell, see [Create user accounts with PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) and [View licenses and services with PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span></span>

> [!NOTE]
> <span data-ttu-id="fe7b7-174">Exchange Online PowerShell로 사서함을 사용하도록 설정하고 해당 사서함을 **PreferredDataLocation**에 지정된 지리적 위치에 직접 만들려면 **Enable-Mailbox** 또는 **New-Mailbox** 등의 Exchange Online cmdlet을 클라우드 서비스에 직접 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-174">If you are using Exchange Online PowerShell to enable a mailbox and need the mailbox to be created directly in the geo location that's specified in **PreferredDataLocation**, you need to use an Exchange Online cmdlet such as **Enable-Mailbox** or **New-Mailbox** directly against the cloud service.</span></span> <span data-ttu-id="fe7b7-175">온 - 프레미스 Exchange PowerShell에서 **Enable-RemoteMailbox** cmdlet를 사용하면 사서함이 중앙 지리적 위치에 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-175">If you use the **Enable-RemoteMailbox** cmdlet in on-premises Exchange PowerShell, the mailbox will be created in the central geo location.</span></span>

## <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo-location"></a><span data-ttu-id="fe7b7-176">특정 지리적 위치에 기존 온-프레미스 사서함 등록</span><span class="sxs-lookup"><span data-stu-id="fe7b7-176">Onboard existing on-premises mailboxes in a specific geo location</span></span>

<span data-ttu-id="fe7b7-177">표준 등록 도구와 프로세스를 사용하여 사서함을 온-프레미스 Exchange 조직에서 Exchange Online으로 마이그레이션할 수 있습니다([EAC의 마이그레이션 대시보드](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331), Exchange Online PowerShell의 [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/new-migrationbatch) cmdlet 포함).</span><span class="sxs-lookup"><span data-stu-id="fe7b7-177">You can use the standard onboarding tools and processes to migrate a mailbox from an on-premises Exchange organization to Exchange Online, including the [Migration dashboard in the EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331), and the [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/new-migrationbatch) cmdlet in Exchange Online PowerShell.</span></span>

<span data-ttu-id="fe7b7-178">첫 번째 단계는 등록될 사서함마다 사용자 개체가 있는지 확인하고 Azure AD에 올바른 **PreferredDataLocation** 값이 구성되었는지 확인하는 일입니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-178">The first step is to verify a user object exists for each mailbox to be onboarded, and verify the correct **PreferredDataLocation** value is configured in Azure AD.</span></span> <span data-ttu-id="fe7b7-179">등록 도구는 **PreferredDataLocation** 값을 고려하고 사서함을 지정된 지리적 위치에 직접 마이그레이션합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-179">The onboarding tools will respect the **PreferredDataLocation** value and will migrate the mailboxes directly to the specified geo location.</span></span>

<span data-ttu-id="fe7b7-180">또는 Exchange Online PowerShell의 [새로 만들기 MoveRequest](https://docs.microsoft.com/powershell/module/exchange/new-moverequest) cmdlet을 사용하는 다음 단계를 통해 사서함을 특정 지리적 위치에 직접 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-180">Or, you can use the following steps to onboard mailboxes directly in a specific geo location using the [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/new-moverequest) cmdlet in Exchange Online PowerShell.</span></span>

1. <span data-ttu-id="fe7b7-181">등록될 사서함마다 사용자 개체가 있고 **PreferredDataLocation**이 Azure AD에서 원하는 값으로 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-181">Verify the user object exists for each mailbox to be onboarded and that **PreferredDataLocation** is set to the desired value in Azure AD.</span></span> <span data-ttu-id="fe7b7-182">**PreferredDataLocation** 값은 Exchange Online에서 해당 메일 사용자 개체의 **MailboxRegion** 특성에 동기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-182">The value of **PreferredDataLocation** will be synchronized to the **MailboxRegion** attribute of the corresponding mail user object in Exchange Online.</span></span>

2. <span data-ttu-id="fe7b7-183">이 항목 앞부분의 연결 지침을 사용하여 특정 위성 지리적 위치에 직접 연결하십시오.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-183">Connect directly to the specific satellite geo location using the connection instructions from earlier in this topic.</span></span>

3. <span data-ttu-id="fe7b7-184">Exchange Online PowerShell에서 다음 명령을 실행하여, 변수에서 사서함 마이그레이션을 수행하는 데 사용되는 온-프레미스 관리자 자격 증명을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-184">In Exchange Online PowerShell, store the on-premises administrator credentials that's used to perform a mailbox migration in a variable by running the following command:</span></span>

   ```powershell
   $RC = Get-Credential
   ```

4. <span data-ttu-id="fe7b7-185">Exchange Online PowerShell에서 다음 예제와 비슷한 새로운 **New-MoveRequest**를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-185">In Exchange Online PowerShell, create a new **New-MoveRequest** similar to the following example:</span></span>

   ```powershell
   New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
   ```

5. <span data-ttu-id="fe7b7-186">온-프레미스 Exchange에서 현재 연결된 위성 지리적 위치로 마이그레이션해야 할 모든 사서함에 4단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-186">Repeat step #4 for every mailbox you need to migrate from on-premises Exchange to the satellite geo location you are currently connected to.</span></span>

6. <span data-ttu-id="fe7b7-187">다른 위성 지리적 위치에 추가 사서함을 마이그레이션해야 할 경우 각각의 특정 위치에 2단계에서 4단계까지를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-187">If you need to migrate additional mailboxes to different satellite geo locations, repeat steps 2 through 4 for each specific location.</span></span>

## <a name="multi-geo-reporting"></a><span data-ttu-id="fe7b7-188">Multi-Geo 보고</span><span class="sxs-lookup"><span data-stu-id="fe7b7-188">Multi-geo reporting</span></span>

<span data-ttu-id="fe7b7-189">Microsoft 365 관리자 센터의 **Multi-Geo 사용 보고서**는 지리적 위치별 사용자 수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-189">**Multi-Geo Usage Reports** in the Microsoft 365 admin center displays the user count by geo location.</span></span> <span data-ttu-id="fe7b7-190">보고서는 이번 달의 사용자 분포를 표시하고 지난 6개월 동안의 기록 데이터를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b7-190">The report displays user distribution for the current month and provides historical data for the past 6 months.</span></span>

## <a name="see-also"></a><span data-ttu-id="fe7b7-191">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fe7b7-191">See also</span></span>

[<span data-ttu-id="fe7b7-192">Windows PowerShell로 Microsoft 365 및 Exchange Online 관리</span><span class="sxs-lookup"><span data-stu-id="fe7b7-192">Managing Microsoft 365 and Exchange Online with Windows PowerShell</span></span>](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6)
