---
title: Exchange Online의 다중-지리적으로 분산 기능
ms.author: chrisda
author: chrisda
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Normal
ms.assetid: ''
description: Exchange Online의 다중-지리적으로 분산 기능을 사용 하는 여러 지리적 영역을 Office 365 현재 상태를 확장 합니다.
ms.openlocfilehash: 6acd2ffab1f35b74d06d6ab5f7bfcbf70f88f8b4
ms.sourcegitcommit: 03bb9edd52b1b7cd49791baf90645828b89b32b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/07/2018
ms.locfileid: "27200741"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a><span data-ttu-id="07b2a-103">Exchange Online의 다중-지리적으로 분산 기능</span><span class="sxs-lookup"><span data-stu-id="07b2a-103">Multi-Geo Capabilities in Exchange Online</span></span>

<span data-ttu-id="07b2a-p101">Office 365의 다중-지리적으로 분산 기능 여러 지리적 위치에 걸쳐를 단일 테 넌 트를 사용 하도록 설정 합니다. 다중-지리적으로 분산을 사용 하는 경우 고객 사용자 단위로에서 Exchange Online 사서함 콘텐츠 (보관 된 데이터)의 위치를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-p101">Multi-Geo Capabilities in Office 365 enable a single tenant to span multiple geographic locations. When multi-geo is enabled, customers can select the location of Exchange Online mailbox content (data at rest) on a per-user basis.</span></span>

<span data-ttu-id="07b2a-p102">초기 테 넌 트 위치 (중앙 위치 라고 함)에 대금 청구 주소를 기반으로 결정 됩니다. 다중-지리적으로 분산을 사용 하는 경우에 하 여 추가 위성 위치에 사서함을 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-p102">Your initial tenant location (referred to as the central location) is determined based on your billing address. When multi-geo is enabled, you can place mailboxes in additional satellite locations by:</span></span>

- <span data-ttu-id="07b2a-108">위성 위치를 직접 새 Exchange Online 사서함을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-108">Creating a new Exchange Online mailbox directly in a satellite location.</span></span>

- <span data-ttu-id="07b2a-109">위성 위치에 있는 기존 Exchange Online 사서함을 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-109">Moving an existing Exchange Online mailbox into a satellite location.</span></span>

- <span data-ttu-id="07b2a-110">위성 위치에 직접 온-프레미스 Exchange 조직에서 사서함 온 보 딩 합니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-110">Onboarding a mailbox from an on-premises Exchange organization directly into a satellite location.</span></span>

<span data-ttu-id="07b2a-111">다음 지리적 위치 하는 다중-지리적으로 분산 구성에서 사용 하기 위해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-111">The following geo locations are available for use in a Multi-Geo configuration:</span></span>

- <span data-ttu-id="07b2a-112">아시아 태평양</span><span class="sxs-lookup"><span data-stu-id="07b2a-112">Asia Pacific</span></span>

- <span data-ttu-id="07b2a-113">오스트레일리아</span><span class="sxs-lookup"><span data-stu-id="07b2a-113">Australia</span></span>

- <span data-ttu-id="07b2a-114">캐나다</span><span class="sxs-lookup"><span data-stu-id="07b2a-114">Canada</span></span>

- <span data-ttu-id="07b2a-115">유럽 연합</span><span class="sxs-lookup"><span data-stu-id="07b2a-115">European Union</span></span>

- <span data-ttu-id="07b2a-116">프랑스</span><span class="sxs-lookup"><span data-stu-id="07b2a-116">France</span></span>

- <span data-ttu-id="07b2a-117">인도</span><span class="sxs-lookup"><span data-stu-id="07b2a-117">India</span></span>

- <span data-ttu-id="07b2a-118">일본</span><span class="sxs-lookup"><span data-stu-id="07b2a-118">Japan</span></span>

- <span data-ttu-id="07b2a-119">한국</span><span class="sxs-lookup"><span data-stu-id="07b2a-119">Korea</span></span>

- <span data-ttu-id="07b2a-120">영국</span><span class="sxs-lookup"><span data-stu-id="07b2a-120">United Kingdom</span></span>

- <span data-ttu-id="07b2a-121">미국</span><span class="sxs-lookup"><span data-stu-id="07b2a-121">United States</span></span>

## <a name="prerequisite-configuration"></a><span data-ttu-id="07b2a-122">필수 구성 요소 구성</span><span class="sxs-lookup"><span data-stu-id="07b2a-122">Prerequisite configuration</span></span>
<span data-ttu-id="07b2a-p103">수를 시작 하기 전에 사용 하 여 다중-지리적으로 분산 기능 Exchange Online Microsoft 다중-지리적으로 분산 지원에 대 한 Exchange Online 테 넌 트를 구성 해야 합니다. 이 일회성 구성 프로세스는 Office 365 다중-지리적으로 분산 하 고 라이선스에에서 표시 되려면 테 넌 트 주문 후 트리거됩니다. 이 일회성 구성 프로세스를 완료 하려면 30 일 보다 작은 걸릴 일반적으로 해야 합니다. Office 365 다중-지리적으로 분산을 주문 하려면 Microsoft 담당자에 게 문의 합니다. 자세한 내용은 참조 https://aka.ms/Multi-Geo합니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-p103">Before you can start using Multi-Geo capabilities in Exchange Online, Microsoft needs to configure your Exchange Online tenant for multi-geo support. This one-time configuration process is triggered after you order Office 365 Multi-Geo and the licenses show up in your tenant. This one-time configuration process should typically take less than 30 days to complete. To order Office 365 Multi-Geo, contact your Microsoft representative. For more information, see https://aka.ms/Multi-Geo.</span></span>

<span data-ttu-id="07b2a-p104">구성 완료 되 면 [Office 365 메시지 센터](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) 에서 알림이 표시 됩니다. 다중-지리적으로 분산 라이선스 테 넌 트에 표시 되 면 자동으로 구성이 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-p104">You'll receive notifications in the [Office 365 message center](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) when your configuration has completed. Configuration is automatically triggered once your multi-geo licenses show up in your tenant.</span></span>

## <a name="mailbox-placement-and-moves"></a><span data-ttu-id="07b2a-130">사서함 배치 및 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-130">Mailbox placement and moves</span></span>
<span data-ttu-id="07b2a-131">Microsoft는 필수 구성 요소 다중-지리적으로 분산 구성 단계를 완료 한 후 Exchange Online 됩니다 제한이 사용자 개체의 **PreferredDataLocation** 특성 Azure AD에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-131">After Microsoft completes the prerequisite multi-geo configuration steps, Exchange Online will honor the **PreferredDataLocation** attribute on user objects in Azure AD.</span></span>

<span data-ttu-id="07b2a-p105">Exchange Online은 Exchange Online 디렉터리 서비스에서 **MailboxRegion** 속성으로 Azure AD에서 **PreferredDataLocation** 속성을 동기화합니다. **MailboxRegion** 의 값은 지리적으로 분산 사용자 사서함과 연결 된 보관 사서함 배치할 수를 결정 합니다. 사용자의 기본 사서함 및 보관 사서함을 다른 지리적 위치에 있는 구성 하는 것이 불가능 합니다. 사용자 개체 당 하나만 지리적 위치를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-p105">Exchange Online synchronizes the **PreferredDataLocation** property from Azure AD into the **MailboxRegion** property in the Exchange Online directory service. The value of **MailboxRegion** determines the Geo where user mailboxes and any associated archive mailboxes will be placed. It is not possible to configure a user's primary mailbox and archive mailboxes to reside in different geo locations. Only one geo location may be configured per user object.</span></span>

- <span data-ttu-id="07b2a-136">**PreferredDataLocation** 기존 사서함 사용자에 대해 구성 된 사서함 재배치 큐에 배치 될 하 고 자동으로 지정 된 지리적 위치로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-136">When **PreferredDataLocation** is configured on a user with an existing mailbox, the mailbox will be put into a relocation queue and automatically moved to the specified geo location.</span></span> 

- <span data-ttu-id="07b2a-137">**PreferredDataLocation** 는 기존 사서함이 없는 사용자에 대해 구성 되 면 사서함의 지정 된 지리적 위치에 프로 비전 됩니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-137">When **PreferredDataLocation** is configured on a user without an existing mailbox, the mailbox will be provisioned into the specified geo location.</span></span> 

- <span data-ttu-id="07b2a-138">**PreferredDataLocation** 사용자를 지정 하지 않으면 중앙 위치에서 사서함 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-138">When **PreferredDataLocation** is not specified on a user, the mailbox will be placed in the central location.</span></span>

- <span data-ttu-id="07b2a-139">**PreferredDataLocation** 코드 올바르지 않은 경우 (예: 이름 대신 NAN의 형식), 사서함을 중앙 위치에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-139">If the **PreferredDataLocation** code is incorrect (e.g. a type of NAN instead of NAM), the mailbox will be placed in the central location.</span></span>

<span data-ttu-id="07b2a-p106">**참고**: 다중-지리적으로 분산 기능 및 Skype 모두 지역별로 호스팅되는 비즈니스 온라인 모임에 대 한 속성을 사용 **PreferredDataLocation** 사용자 개체에 서비스를 찾습니다. 지역별로 호스팅된 모임에 대 한 사용자 개체에 **PreferredDataLocation** 값을 구성 하는 경우 해당 사용자에 대 한 사서함 자동으로 이동할 지정한 지리적 위치 다중-지리적으로 분산이 Office 365 테 넌 트에 설정 된 후 합니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-p106">**Note**: multi-geo capabilities and Skype for Business Online regionally hosted meetings both use the **PreferredDataLocation** property on user objects to locate services. If you configure **PreferredDataLocation** values on user objects for regionally hosted meetings, the mailbox for those users will be automatically moved to the specified geo location after multi-geo is enabled on the Office 365 tenant.</span></span>

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a><span data-ttu-id="07b2a-142">다중-지리적으로 분산 Exchange online에 대 한 기능 제한</span><span class="sxs-lookup"><span data-stu-id="07b2a-142">Feature limitations for Multi-Geo in Exchange Online</span></span>
1. <span data-ttu-id="07b2a-p107">사용자 사서함, 리소스 사서함 (회의실 및 기 자재 사서함) 및 공유 사서함 다중-지리적으로 분산 기능을 지원 합니다. 공용 폴더 사서함 및 Office 365 그룹에는 중앙 위치에 남아 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-p107">Only user mailboxes, resource mailboxes (room and equipment mailboxes), and shared mailboxes support multi-geo features. Public Folder Mailboxes and Office 365 Groups remain in the central location.</span></span>
 
2. <span data-ttu-id="07b2a-p108">보안 및 규정 준수 기능 (예: 감사 및 eDiscovery) (EAC)의 Exchange 관리 센터에서 사용할 수 있는 다중-지리적으로 분산 조직에서 사용할 수 없습니다. 대신, 보안 및 규정 준수 기능을 구성 하는 [Office 365 보안 및 규정 준수 센터를](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-p108">Security and compliance features (for example, auditing and eDiscovery) that are available in the Exchange admin center (EAC) aren't available in multi-geo organizations. Instead, you need to use the [Office 365 Security & Compliance Center](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) to configure security and compliance features.</span></span>

3. <span data-ttu-id="07b2a-p109">새로운 지리적 위치에 자신의 사서함을 이동 하는 동안 Mac 사용자를 위한 outlook에서 자신의 온라인 보관 함 폴더에 대 한 액세스의 임시 손실을 경험할 수 있습니다. 이 조건은 크로스-지리적으로 분산 사서함 이동 서로 다른 시간에 완료 될 수 있습니다 때문에 사용자의 기본 및 보관 사서함 다른 지리적 위치에 있는 경우에 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-p109">Outlook for Mac users may experience a temporary loss of access to their Online Archive folder while you move their mailbox to a new geo location. This condition occurs when the user's the primary and archive mailboxes are in different geo locations, because cross-Geo mailbox moves may complete at different times.</span></span>

4. <span data-ttu-id="07b2a-p110">사용자가 여러 (이전의 Outlook Web App 또는 OWA) 웹에서 Outlook의 지리적 위치에 걸친 *사서함 폴더* 를 공유할 수 없습니다. 예, 유럽 연합의 사용자 미국에 있는 사서함에 공유 폴더를 열려면 웹에 있는 Outlook을 사용할 수 없습니다. 그러나 웹 사용자에 게 Outlook [Outlook Web App에서 별도 브라우저 창에서 다른 사용자의 사서함을 열](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362)에서 설명한 대로 별도 브라우저 창을 사용 하 여 서로 다른 Geos의 *다른 사서함* 을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-p110">Users can't share *mailbox folders* across geo locations in Outlook on the web (formerly known as Outlook Web App or OWA). For example, a user in the European Union can't use Outlook on the web to open a shared folder in a mailbox that's located in the United States. However, Outlook on the Web users can open *other mailboxes* in different Geos by using a separate browser window as described in [Open another person’s mailbox in a separate browser window in Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).</span></span>

    <span data-ttu-id="07b2a-152">**참고**: 크로스-지리적으로 분산 사서함 폴더 공유는 Windows에서 Outlook에서 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-152">**Note**: Cross-geo mailbox folder sharing is supported in Outlook on Windows.</span></span>

## <a name="administration"></a><span data-ttu-id="07b2a-153">관리</span><span class="sxs-lookup"><span data-stu-id="07b2a-153">Administration</span></span> 
<span data-ttu-id="07b2a-p111">원격 PowerShell은 보기 및 Office 365 환경에서 다중 지리적으로 분산 속성을 구성 해야 합니다. Office 365를 관리 하는 데 사용 하는 다양 한 PowerShell 모듈에 대 한 자세한 내용은 [Office 365를 관리 하 고 Windows PowerShell을 사용한 Exchange Online](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="07b2a-p111">Remote PowerShell is required to view and configure multi geo properties in your Office 365 environment. For information on various PowerShell modules used to administer Office 365, see [Managing Office 365 and Exchange Online with Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6).</span></span>

- <span data-ttu-id="07b2a-p112">[Microsoft Azure Active Directory PowerShell 모듈](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 또는 사용자 개체에 **PreferredDataLocation** 속성을 표시 하려면 나중에 v1.x 필요 합니다. AAD에 AAD 연결을 통해 동기화 하는 사용자 개체 AAD PowerShell을 통해 직접 수정 하는 **PreferredDataLocation** 값을 가질 수 없습니다. AAD PowerShell을 통해 클라우드 전용 사용자 개체를 수정할 수 있습니다. Azure AD PowerShell 연결할 [Office 365 PowerShell에 연결](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-p112">You need the [Microsoft Azure Active Directory PowerShell Module](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 or later in v1.x to see the **PreferredDataLocation** property on user objects. User objects synchronized via AAD Connect into AAD cannot have their **PreferredDataLocation** value directly modified via AAD PowerShell. Cloud-only user objects can be modified via AAD PowerShell. To connect to Azure AD PowerShell, see [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span> 

- <span data-ttu-id="07b2a-160">Exchange Online PowerShell 연결할 [Connect to Exchange Online PowerShell를](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="07b2a-160">To connect to Exchange Online PowerShell, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span> 

### <a name="connect-directly-to-a-specific-geo-using-exchange-online-powershell"></a><span data-ttu-id="07b2a-161">Exchange Online PowerShell을 사용 하는 특정 지리적으로 분산에 직접 연결</span><span class="sxs-lookup"><span data-stu-id="07b2a-161">Connect directly to a specific Geo using Exchange Online PowerShell</span></span>
<span data-ttu-id="07b2a-p113">일반적으로 Exchange Online PowerShell 기본 지리적 위치에 연결 됩니다. 하지만 기본이 아닌 지리적 위치에 직접 연결할 수도 있습니다. 성능 개선 사항으로 인해만 해당 지리적 위치에 사용자를 관리 하는 경우 기본이 아닌 지리적 위치에 직접 연결 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-p113">Typically, Exchange Online PowerShell will connect to the default geo location. But, you can also connect directly to non-default geo locations. Because of performance improvements, we recommend connecting directly to the non-default geo location when you only manage users in that geo location.</span></span>

<span data-ttu-id="07b2a-p114">특정 지리적 연결할 *ConnectionUri* 매개 변수는은 일반 연결 지침은 다릅니다. 명령 및 값의 나머지 부분 동일 합니다. 단계는.</span><span class="sxs-lookup"><span data-stu-id="07b2a-p114">To connect to a specific Geo, the *ConnectionUri* parameter is different than the regular connection instructions. The rest of the commands and values are the same. The steps are:</span></span>

1. <span data-ttu-id="07b2a-168">로컬 컴퓨터에서 Windows PowerShell을 열고 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-168">On your local computer, open Windows PowerShell and run the following command:</span></span>
    
    ```
    $UserCredential = Get-Credential
    ```
   <span data-ttu-id="07b2a-169">**Windows PowerShell 자격 증명 요청** 대화 상자에 작업 또는 학교 계정 및 암호를 입력 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-169">In the **Windows PowerShell Credential Request** dialog box, type your work or school account and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="07b2a-p115">바꾸기 `<emailaddress>` 다음 명령 실행 하 고 대상 지리적 위치에서 **모든** 사서함의 전자 메일 주소를 가진 합니다. 사서함과 1 단계에서에서 자격 증명에 대 한 관계에 대 한 사용자 권한을 요인; 되지 않습니다. 전자 메일 주소 단순히 위치에 알려 Exchange Online에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-p115">Replace `<emailaddress>` with the email address of **any** mailbox in the target geo location and run the following command. Your permissions on the mailbox and the relationship to your credentials in Step 1 are not a factor; the email address simply tells Exchange Online where to connect.</span></span>
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   <span data-ttu-id="07b2a-172">예 연결 하려는 지리적으로 유효한 사서함의 전자 메일 주소 olga@contoso.onmicrosoft.com을 사용 하는 경우에 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-172">For example, if olga@contoso.onmicrosoft.com is the email address of a valid mailbox in the Geo you want to connect, run the following command:</span></span>

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. <span data-ttu-id="07b2a-173">다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-173">Run the following command:</span></span>
    
    ```
    Import-PSSession $Session
    ```

### <a name="azure-ad-connect-version-requirements"></a><span data-ttu-id="07b2a-174">Azure AD 연결 버전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="07b2a-174">Azure AD Connect version requirements</span></span>
<span data-ttu-id="07b2a-p116">AAD 연결 버전 1.1.524.0 또는 이상 온-프레미스 Active Directory에서 동기화 되는 사용자 개체에서 **PreferredDataLocation** 속성을 설정 하기 위한 방법만 지원된 됩니다. AAD에 AAD 연결을 통해 동기화 하는 사용자 개체 AAD PowerShell을 통해 직접 수정 하는 **PreferredDataLocation** 값을 가질 수 없습니다. AAD PowerShell을 통해 클라우드 전용 사용자 개체를 수정할 수 있습니다. 자세한 내용은 참조 하십시오. [Azure Active Directory 연결 동기화: Office 365 리소스에 대 한 기본 설정된 데이터 위치 구성](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)합니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-p116">AAD Connect version 1.1.524.0 or later is the only supported method for setting the **PreferredDataLocation** property on user objects that are synchronized from on-premises Active Directory. User objects synchronized via AAD Connect into AAD cannot have their **PreferredDataLocation** value directly modified via AAD PowerShell. Cloud-only user objects can be modified via AAD PowerShell. For detailed instructions, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

### <a name="geo-codes"></a><span data-ttu-id="07b2a-179">지리적으로 분산 코드</span><span class="sxs-lookup"><span data-stu-id="07b2a-179">Geo Codes</span></span>
<span data-ttu-id="07b2a-p117">세 글자로 된 코드를 사용 하 여 **PreferredDataLocation** 속성에는 지리적으로 분산을 지정 합니다. 다음 표에서 사용 가능한 Geos에 대 한 코드가 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-p117">You use three-letter codes to specify the Geo in the **PreferredDataLocation** property. The following table lists the codes for the available Geos:</span></span>

|<span data-ttu-id="07b2a-182">지역</span><span class="sxs-lookup"><span data-stu-id="07b2a-182">Geo</span></span> |<span data-ttu-id="07b2a-183">코드</span><span class="sxs-lookup"><span data-stu-id="07b2a-183">Code</span></span> |
|---------|---------|
|<span data-ttu-id="07b2a-184">아시아/태평양</span><span class="sxs-lookup"><span data-stu-id="07b2a-184">Asia/Pacific</span></span> |<span data-ttu-id="07b2a-185">APC</span><span class="sxs-lookup"><span data-stu-id="07b2a-185">APC</span></span> |
|<span data-ttu-id="07b2a-186">오스트레일리아</span><span class="sxs-lookup"><span data-stu-id="07b2a-186">Australia</span></span> |<span data-ttu-id="07b2a-187">AUS</span><span class="sxs-lookup"><span data-stu-id="07b2a-187">AUS</span></span> |
|<span data-ttu-id="07b2a-188">캐나다</span><span class="sxs-lookup"><span data-stu-id="07b2a-188">Canada</span></span> |<span data-ttu-id="07b2a-189">CAN</span><span class="sxs-lookup"><span data-stu-id="07b2a-189">CAN</span></span> |
|<span data-ttu-id="07b2a-190">유럽 연합</span><span class="sxs-lookup"><span data-stu-id="07b2a-190">European Union</span></span> |<span data-ttu-id="07b2a-191">EUR</span><span class="sxs-lookup"><span data-stu-id="07b2a-191">EUR</span></span> |
|<span data-ttu-id="07b2a-192">프랑스</span><span class="sxs-lookup"><span data-stu-id="07b2a-192">France</span></span> |<span data-ttu-id="07b2a-193">FRA</span><span class="sxs-lookup"><span data-stu-id="07b2a-193">FRA</span></span>|
|<span data-ttu-id="07b2a-194">인도</span><span class="sxs-lookup"><span data-stu-id="07b2a-194">India</span></span> |<span data-ttu-id="07b2a-195">찾기</span><span class="sxs-lookup"><span data-stu-id="07b2a-195">IND</span></span> |
|<span data-ttu-id="07b2a-196">일본</span><span class="sxs-lookup"><span data-stu-id="07b2a-196">Japan</span></span> |<span data-ttu-id="07b2a-197">JPN</span><span class="sxs-lookup"><span data-stu-id="07b2a-197">JPN</span></span> |
|<span data-ttu-id="07b2a-198">한국</span><span class="sxs-lookup"><span data-stu-id="07b2a-198">Korea</span></span> |<span data-ttu-id="07b2a-199">KOR</span><span class="sxs-lookup"><span data-stu-id="07b2a-199">KOR</span></span> |
|<span data-ttu-id="07b2a-200">영국</span><span class="sxs-lookup"><span data-stu-id="07b2a-200">United Kingdom</span></span> |<span data-ttu-id="07b2a-201">GBR</span><span class="sxs-lookup"><span data-stu-id="07b2a-201">GBR</span></span> |
|<span data-ttu-id="07b2a-202">미국</span><span class="sxs-lookup"><span data-stu-id="07b2a-202">United States</span></span> |<span data-ttu-id="07b2a-203">NAM</span><span class="sxs-lookup"><span data-stu-id="07b2a-203">NAM</span></span> |

<span data-ttu-id="07b2a-p118">**참고**: **PreferredDataLocation** 및 **MailboxRegion** 속성은 문자열 없음 오류 검사 합니다. 잘못 된 값 (예: NAN)를 입력 하는 경우 사서함 기본 지리적으로 분산에에서 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-p118">**Note**: The **PreferredDataLocation** and **MailboxRegion** properties are strings with no error checking. If you enter an invalid value (for example, NAN) the mailbox will be placed in the default Geo.</span></span>

### <a name="view-the-available-geos-that-are-configured-in-your-exchange-online-organization"></a><span data-ttu-id="07b2a-206">Exchange Online 조직에 구성 된 사용 가능한 Geos 보기</span><span class="sxs-lookup"><span data-stu-id="07b2a-206">View the available Geos that are configured in your Exchange Online organization</span></span>
<span data-ttu-id="07b2a-207">Exchange Online 조직에 구성 된 Geos의 목록을 보려면 다음 명령을 실행 Exchange Online PowerShell:</span><span class="sxs-lookup"><span data-stu-id="07b2a-207">To see the list of configured Geos in your Exchange Online organization, run the following command in Exchange Online PowerShell:</span></span>

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

<span data-ttu-id="07b2a-208">이 명령의 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-208">The output of the command looks like this:</span></span>

```
APC
AUS
CAN
EUR
FRA
GBR
JPN
KOR
NAM
```

### <a name="view-the-default-geo-for-your-exchange-online-organization"></a><span data-ttu-id="07b2a-209">Exchange Online 조직에 대 한 기본 지리적으로 분산 보기</span><span class="sxs-lookup"><span data-stu-id="07b2a-209">View the default Geo for your Exchange Online organization</span></span>
<span data-ttu-id="07b2a-210">Exchange Online 조직의 기본 geo를 보려면 다음 명령을 실행 Exchange Online PowerShell:</span><span class="sxs-lookup"><span data-stu-id="07b2a-210">To view the default geo of your Exchange Online organization, run the following command in Exchange Online PowerShell:</span></span>

```
Get-OrganizationConfig | Select DefaultMailboxRegion
```

<span data-ttu-id="07b2a-211">이 명령의 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-211">The output of the command looks like this:</span></span>

```
DefaultMailboxRegion
--------------------
NAM
```


### <a name="find-the-geo-location-of-a-mailbox"></a><span data-ttu-id="07b2a-212">사서함의 지리적 위치를 찾기</span><span class="sxs-lookup"><span data-stu-id="07b2a-212">Find the Geo location of a mailbox</span></span>
<span data-ttu-id="07b2a-213">Exchange Online PowerShell 표시 다음 다중 geo에서에서 **Get-mailbox** cmdlet 관련 사서함에서 속성:</span><span class="sxs-lookup"><span data-stu-id="07b2a-213">The **Get-Mailbox** cmdlet in Exchange Online PowerShell displays the following multi-geo related properties on mailboxes:</span></span>

- <span data-ttu-id="07b2a-p119">**데이터베이스**: 사서함이 현재 위치한 지시 지리적으로 분산 코드에 해당 하는 처음 3 글자 데이터베이스 이름입니다. 온라인 보관 사서함 **archivedatabase 사서함의 경우** 에 대 한 속성을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-p119">**Database**: The first 3 letters of the database name correspond to the Geo code, which tells you where the mailbox is currently located. For Online Archive Mailboxes the **ArchiveDatabase** property should be used.</span></span>

- <span data-ttu-id="07b2a-216">**MailboxRegion**: (Azure AD에 **PreferredDataLocation** 에서 동기화) 관리자에 의해 설정 된 지리적 위치 코드를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-216">**MailboxRegion**: Specifies the geo location code that was set by the admin (synchronized from **PreferredDataLocation** in Azure AD).</span></span>

- <span data-ttu-id="07b2a-217">**MailboxRegionLastUpdateTime**: MailboxRegion 마지막으로 업데이트 된 시간 (자동 또는 수동)를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-217">**MailboxRegionLastUpdateTime**: Indicates when MailboxRegion was last updated (either automatically or manually).</span></span>

<span data-ttu-id="07b2a-218">사서함에 대 한 이러한 속성을 보려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-218">To see these properties for a mailbox, use the following syntax:</span></span>

```
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

<span data-ttu-id="07b2a-219">예, 사서함 chris@contoso.onmicrosoft.com에 대 한 지리적으로 분산 정보를 보려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-219">For example, to see the Geo information for the mailbox chris@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

<span data-ttu-id="07b2a-220">이 명령의 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-220">The output of the command looks like this:</span></span>

```
Database                    : EURPR03DG077-db007 
MailboxRegion               : EUR 
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM 
```

> <span data-ttu-id="07b2a-221">**참고:** 데이터베이스 이름에서 지리적으로 분산 위치 코드 **MailboxRegion** 값을 일치 하지 않으면, 사서함 자동으로 재배치 큐에 배치 될 수 있습니다 및이 **MailboxRegion** 값으로 지정 된 지리적 위치로 이동 하는 (Exchange Online을 찾고 프로그램 일치 하지 않습니다 이러한 속성 값 사이)입니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-221">**Note:** If the geo location code in the database name doesn't match **MailboxRegion** value, the mailbox will be automatically be put into a relocation queue and moved to the geo location specified by the **MailboxRegion** value (Exchange Online looks for a mismatch between these property values).</span></span>

### <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo"></a><span data-ttu-id="07b2a-222">특정 지리적으로 기존 클라우드 전용 사서함 이동</span><span class="sxs-lookup"><span data-stu-id="07b2a-222">Move an existing cloud-only mailbox to a specific Geo</span></span>
<span data-ttu-id="07b2a-p120">클라우드 전용 사용자가 사용자를 AAD 연결을 통해 테 넌 트 syncrhonized 하지 않습니다. 이 사용자는 Azure AD에서 직접 작성 되었습니다. Windows PowerShell 용 Azure AD 모듈 **Get-msoluser** 및 **이와** cmdlet을 사용 하 여를 보거나 클라우드 전용 사용자의 사서함을 저장할 하 여 지리적으로 분산을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-p120">A cloud-only user is a user not syncrhonized to the tenant via AAD Connect. This user was created directly in Azure AD. Use the **Get-MsolUser** and **Set-MsolUser** cmdlets in the Azure AD Module for Windows PowerShell to view or specify the Geo where a cloud-only user's mailbox will be stored.</span></span>

<span data-ttu-id="07b2a-226">사용자에 대 한 **PreferredDataLocation** 값을 보려면 Azure AD PowerShell에서이 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-226">To view the **PreferredDataLocation** value for a user, use this syntax in Azure AD PowerShell:</span></span>

```
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

<span data-ttu-id="07b2a-227">예, 사용자 michelle@contoso.onmicrosoft.com에 대 한 **PreferredDataLocation** 값을 보려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-227">For example, to see the **PreferredDataLocation** value for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

<span data-ttu-id="07b2a-228">이 명령의 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-228">The output of the command looks like this:</span></span>

```
UserPrincipalName     : michelle@contoso.onmicrosoft.com
PreferredDataLocation : EUR
```

<span data-ttu-id="07b2a-229">클라우드 전용 사용자 개체에 대 한 **PreferredDataLocation** 값을 수정 하려면 다음 구문을 사용 하 여 Azure AD PowerShell에서:</span><span class="sxs-lookup"><span data-stu-id="07b2a-229">To modify the **PreferredDataLocation** value for a cloud-only user object, use the following syntax in Azure AD PowerShell:</span></span>

``` 
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoCode>
```

<span data-ttu-id="07b2a-230">예, 사용자 michelle@contoso.onmicrosoft.com에 대 한 유럽 연합 (EUR) geo로 **PreferredDataLocation** 값을 설정 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-230">For example, to set the **PreferredDataLocation** value to the European Union (EUR) geo for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

<span data-ttu-id="07b2a-231">**참고:**</span><span class="sxs-lookup"><span data-stu-id="07b2a-231">**Notes**:</span></span>

- <span data-ttu-id="07b2a-p121">설명한 것 처럼 이전에 사용할 수 없습니다이 절차에서 온-프레미스 Active Directory 동기화 된 사용자 개체에 대 한 합니다. AAD 연결을 사용 하 여 **PreferredDataLocation** 값을 변경 해야 합니다. 자세한 내용은 참조 [Azure Active Directory 연결 동기화: Office 365 리소스에 대 한 기본 설정된 데이터 위치 구성](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)합니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-p121">As mentioned previously you cannot use this procedure for synchronized user objects from on-premises Active Directory. You need to change the **PreferredDataLocation** value using AAD Connect. For more information, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span> 

- <span data-ttu-id="07b2a-235">얼마나 오래 걸리는 여러 요인에 따라 새 원하는 지리적 위치에 해당 현재 지리적으로 분산 mailboxfrom 위치를 변경 하려면:</span><span class="sxs-lookup"><span data-stu-id="07b2a-235">How long it takes to relocate a mailboxfrom its current geo to the new desired geo location depends on several factors:</span></span>
 
  - <span data-ttu-id="07b2a-236">사서함의 종류와 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-236">The size and type of mailbox.</span></span>
 
  - <span data-ttu-id="07b2a-237">이동 중인 사서함의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-237">The number of mailboxes being moved.</span></span>
 
  - <span data-ttu-id="07b2a-238">이동 리소스의 가용성입니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-238">The availability of move resources.</span></span>

#### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a><span data-ttu-id="07b2a-239">소송 보존으로 설정에 있는 사서함을 사용 하지 않도록 설정 하는 이동</span><span class="sxs-lookup"><span data-stu-id="07b2a-239">Move disabled mailboxes that are on Litigation Hold</span></span>
<span data-ttu-id="07b2a-p122">EDiscovery 목적으로 사용할 수 없는 상태로 자신의 **PreferredDataLocation** 값을 변경 하 여 이동할 수에 대 한 보존 되 소송 보존으로 설정에 있는 사서함을 사용할 수 없습니다. 소송 보존에 사용할 수 없는 사서함을 이동할:</span><span class="sxs-lookup"><span data-stu-id="07b2a-p122">Disabled mailboxes on Litigation Hold that are preserved for eDiscovery purposes cannot be moved by changing their **PreferredDataLocation** value in their disabled state. To move a disabled mailbox on litigation hold:</span></span>

1. <span data-ttu-id="07b2a-242">일시적으로 사서함 라이선스를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-242">Temporarily assign a license to the mailbox.</span></span>

2. <span data-ttu-id="07b2a-243">**PreferredDataLocation**를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-243">Change the **PreferredDataLocation**.</span></span>

3. <span data-ttu-id="07b2a-244">해당 비활성화 된 상태로 다시 설정 하려면 선택한 지리적 위치로 이동 된 후 사서함에서 라이선스를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-244">Remove the license from the mailbox after it has been moved to the selected geo location to put it back into the disabled state.</span></span>

### <a name="create-new-cloud-mailboxes-in-a-specific-geo"></a><span data-ttu-id="07b2a-245">특정 지리적에서 새 클라우드 사서함 만들기</span><span class="sxs-lookup"><span data-stu-id="07b2a-245">Create new cloud mailboxes in a specific Geo</span></span> 
<span data-ttu-id="07b2a-246">특정 지리적 위치에 새 사서함을 만들려면 다음이 단계 중 하나를 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-246">To create a new mailbox in a specific geo location, you need to do either of these steps:</span></span>

- <span data-ttu-id="07b2a-p123">이전 섹션 *하기 전에* 사서함이 Exchange에서 만든 온라인에서 설명한 대로 **PreferredDataLocation** 값을 구성 합니다. 라이선스를 할당 하기 전에 사용자에 **PreferredDataLocation** 값을 구성 예입니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-p123">Configure the **PreferredDataLocation** value as described in the previous section *before* the mailbox is created in Exchange Online. For example, configure the **PreferredDataLocation** value on a user before assigning a license.</span></span> 

- <span data-ttu-id="07b2a-249">**PreferredDataLocation** 값을 설정 하는 동시에 게 라이선스를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-249">Assign a license at the same time you set the **PreferredDataLocation** value.</span></span>

<span data-ttu-id="07b2a-250">새 클라우드 전용 사용이 허가 된 사용자 (AAD 연결 하지 동기화)에 특정 지리적으로 분산을 만들려면 Azure AD PowerShell에서 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-250">To create a new cloud-only licensed user (not AAD Connect synchronized) in a specific Geo, use the following syntax in Azure AD PowerShell:</span></span>

```
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoCode> 
```
<span data-ttu-id="07b2a-251">이 예제에서는 다음 값을 갖는 동 Brunner에 대 한 새 사용자 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-251">This example create a new user account for Elizabeth Brunner with the following values:</span></span>

- <span data-ttu-id="07b2a-252">사용자 계정 이름: ebrunner@contoso.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="07b2a-252">User principal name: ebrunner@contoso.onmicrosoft.com</span></span>

- <span data-ttu-id="07b2a-253">이름: 동</span><span class="sxs-lookup"><span data-stu-id="07b2a-253">First name: Elizabeth</span></span>

- <span data-ttu-id="07b2a-254">성: Brunner</span><span class="sxs-lookup"><span data-stu-id="07b2a-254">Last name: Brunner</span></span>

- <span data-ttu-id="07b2a-255">표시 이름 동 Brunner</span><span class="sxs-lookup"><span data-stu-id="07b2a-255">Display name Elizabeth Brunner</span></span>

- <span data-ttu-id="07b2a-256">암호: 임의로 생성 하 고 (하기 때문에 *Password* 매개 변수를 사용 하지) 명령의 결과에 표시 된</span><span class="sxs-lookup"><span data-stu-id="07b2a-256">Password: randomly-generated and shown in the results of the command (because we're not using the *Password* parameter)</span></span>

- <span data-ttu-id="07b2a-257">라이선스: contoso:ENTERPRISEPREMIUM (e 5)</span><span class="sxs-lookup"><span data-stu-id="07b2a-257">License: contoso:ENTERPRISEPREMIUM (E5)</span></span>

- <span data-ttu-id="07b2a-258">위치: 오스트레일리아 (오스트레일리아)</span><span class="sxs-lookup"><span data-stu-id="07b2a-258">Location: Australia (AUS)</span></span>

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

<span data-ttu-id="07b2a-259">새 사용자 계정 만들기 및 Azure AD PowerShell에서 LicenseAssignment 값 찾기 (영문) 하는 방법에 대 한 자세한 내용은 [Office 365 PowerShell을 사용한 사용자 계정 만들기](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) 및 [보기 라이선스 및 Office 365 PowerShell을 사용 하 여 서비스를](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="07b2a-259">For more information about creating new user accounts and finding LicenseAssignment values in Azure AD PowerShell, see [Create user accounts with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) and [View licenses and services with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span></span>

> <span data-ttu-id="07b2a-p124">**참고:** 예: **Enable-mailbox** 또는 \*\*New-mailbox Exchange Online cmdlet을 사용 하 여 해야 사서함을 사용 하도록 설정 하 고 필요한 **PreferredDataLocation**에 지정 된 지리적으로 분산에서 직접 만들어야 하는 사서함을 Exchange Online PowerShell를 사용 하는 경우 \*\*클라우드 서비스에 대해 직접 합니다. **Enable-remotemailbox** 온-프레미스 Exchange cmdlet을 사용 하면 사서함의 기본 지리적으로 분산에서에서 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-p124">**Note:** If you are using Exchange Online PowerShell to enable a mailbox and need the mailbox to be created directly in the Geo that's specified in **PreferredDataLocation**, you need to use an Exchange Online cmdlet such as **Enable-Mailbox** or **New-Mailbox** directly against the cloud service. If you use the **Enable-RemoteMailbox** on-premises Exchange cmdlet, the mailbox will be created in the default Geo.</span></span>

### <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo"></a><span data-ttu-id="07b2a-262">온보드 기존 온-프레미스 사서함에는 특정 지리적으로 분산</span><span class="sxs-lookup"><span data-stu-id="07b2a-262">Onboard existing on-premises mailboxes in a specific Geo</span></span>
<span data-ttu-id="07b2a-263">온-프레미스 Exchange 조직에서 사서함을 Exchange Online에 포함 하 여 [EAC의 마이그레이션 대시보드](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)및 [New-migrationbatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) cmdlet은 Exchange 온라인 마이그레이션할 표준 온 보 딩 도구와 프로세스를 사용할 수 있습니다. PowerShell 합니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-263">You can use the standard onboarding tools and processes to migrate a mailbox from an on-premises Exchange organization to Exchange Online, including the [Migration dashboard in the EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331), and the [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) cmdlet in Exchange Online PowerShell.</span></span>

<span data-ttu-id="07b2a-p125">첫번째 단계에서는 onboarded, 되어야 하 고 Azure AD에 올바른 **PreferredDataLocation** 값을 구성 하는 확인 하는 각 사서함에 대해 존재 하는 사용자 개체를 확인 하는 것입니다. 온 보 딩 도구 **PreferredDataLocation** 값 존중 하 고는 지정 된 지리적으로 분산을 직접는 사서함을 마이그레이션합니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-p125">The first step is to verify a user object exists for each mailbox to be onboarded, and verify the correct **PreferredDataLocation** value is configured in Azure AD. The onboarding tools will respect the **PreferredDataLocation** value and will migrate the mailboxes directly to the specified Geo.</span></span>

<span data-ttu-id="07b2a-266">또는 [New-moverequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) cmdlet을 사용 하 여 Exchange Online PowerShell에서 특정 지리적 위치에 직접 온보드 사서함에는 다음 단계를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-266">Or, you can use the following steps to onboard mailboxes directly in a specific geo location using the [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) cmdlet in Exchange Online PowerShell.</span></span>

1. <span data-ttu-id="07b2a-p126">Onboarded 및 **PreferredDataLocation** Azure AD에 원하는 값으로 설정 되어 되도록 각 사서함에 대 한 사용자 개체가 있는지 확인 합니다. **PreferredDataLocation** 값 동기화 됩니다 해당 메일 사용자 개체의 **MailboxRegion** 특성에 Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="07b2a-p126">Verify the user object exists for each mailbox to be onboarded and that **PreferredDataLocation** is set to the desired value in Azure AD. The value of **PreferredDataLocation** will be synchronized to the **MailboxRegion** attribute of the corresponding mail user object in Exchange Online.</span></span>

2. <span data-ttu-id="07b2a-269">이 항목의 앞부분에서 연결 지침을 사용 하 여 지리적으로 분산 된 특정 위성에 직접 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-269">Connect directly to the specific satellite Geo using the connection instructions from earlier in this topic.</span></span>

3. <span data-ttu-id="07b2a-270">Exchange Online PowerShell에서 다음 명령을 실행 하 여 변수에 사서함 마이그레이션을 수행 하기 위해 사용 되는 온-프레미스 관리자 자격 증명을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-270">In Exchange Online PowerShell, store the on-premises administrator credentials that's used to perform a mailbox migration in a variable by running the following command:</span></span>

    ```
    $RC = Get-Credential
    ```

4. <span data-ttu-id="07b2a-271">Exchange Online PowerShell에서 새 **New-moverequest** 를 다음 예제와 비슷한 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-271">In Exchange Online PowerShell, create a new **New-MoveRequest** similar to the following example:</span></span> 

    ```
    New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
    ```

5. <span data-ttu-id="07b2a-272">현재에 연결 되어 위성 위치에서 온-프레미스 Exchange로 마이그레이션하기 위해 필요한 모든 사서함에 대 한 #4 단계를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-272">Repeat step #4 for every mailbox you need to migrate from on-premises Exchange to the satellite location you are currently connected to.</span></span>

6. <span data-ttu-id="07b2a-273">서로 다른 위성 위치에 추가 사서함 마이그레이션 해야하는 경우 각 특정 위성 위치에 대해 2 ~ 4 단계를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-273">If you need to migrate additional mailboxes to a different satellite location, repeat steps 2 through 4 for each specific satellite location.</span></span>

### <a name="multi-geo-reporting"></a><span data-ttu-id="07b2a-274">다중-지리적으로 분산 보고</span><span class="sxs-lookup"><span data-stu-id="07b2a-274">Multi-Geo Reporting</span></span>
<span data-ttu-id="07b2a-p127">지리적 위치에 따라 사용자 수를 표시 하는 Office 365 관리 센터에서 **다중-지리적으로 분산 사용 현황 보고서** 입니다. 보고서 현재 달에 대 한 사용자 분포를 표시 하 고 지난 6 개월에 대 한 기록 데이터를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="07b2a-p127">**Multi-Geo Usage Reports** in the Office 365 admin center displays the user count by geo location. The report displays user distribution for the current month and provides historical data for the past 6 months.</span></span>
