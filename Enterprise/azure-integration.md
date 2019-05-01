---
title: Office 365와 Azure 통합
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: a5efce5d-9c9c-4190-b61b-fd273c1d425f
description: Office 365 구독에는 Azure AD에 대 한 구독이 포함 되어 있습니다. 온-프레미스 환경에 대 한 암호 동기화 또는 single sign-on을 사용 하려면 Office 365와 Azure AD를 통합 합니다.
ms.openlocfilehash: 0ad1c064d2ffe29f0f06e1368cd728d8b3bd630b
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490144"
---
# <a name="azure-integration-with-office-365"></a><span data-ttu-id="b4b14-104">Office 365와 Azure 통합</span><span class="sxs-lookup"><span data-stu-id="b4b14-104">Azure integration with Office 365</span></span>

<span data-ttu-id="b4b14-105">Office 365에서는 azure Active Directory (azure AD)를 사용 하 여 백그라운드에서 사용자 id를 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4b14-105">Office 365 uses Azure Active Directory (Azure AD) to manage user identities behind the scenes.</span></span> <span data-ttu-id="b4b14-106">office 365 구독에는 azure ad에 대 한 무료 구독이 포함 되어 있어 암호를 동기화 하거나 single sign-on을 온-프레미스 환경에 설정 하려는 경우 azure ad와 office 365를 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4b14-106">Your Office 365 subscription includes a free subscription to Azure AD so that you can integrate Office 365 with Azure AD if you want to sync passwords or set up single sign-on with your on-premises environment.</span></span> <span data-ttu-id="b4b14-107">계정을 보다 효율적으로 관리 하기 위해 고급 기능을 구입할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4b14-107">You can also buy advanced features to better manage your accounts.</span></span>
  
<span data-ttu-id="b4b14-108">Azure는 또한 Office 365 구독을 확장 및 사용자 지정 하는 데 사용할 수 있는 통합 앱 관리 등의 기타 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4b14-108">Azure also offers other functionality, like managing integrated apps, that you can use to extend and customize your Office 365 subscriptions.</span></span>
  
<span data-ttu-id="b4b14-109">Azure AD 배포 관리자는 다음과 같은 안내 설치 및 구성 환경에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4b14-109">You can use the Azure AD deployment advisors for a guided setup and configuration experience:</span></span>
 - [<span data-ttu-id="b4b14-110">Azure AD Connect advisor</span><span class="sxs-lookup"><span data-stu-id="b4b14-110">Azure AD Connect advisor</span></span>](https://aka.ms/aadconnectpwsync)
 - [<span data-ttu-id="b4b14-111">AD FS 배포 관리자</span><span class="sxs-lookup"><span data-stu-id="b4b14-111">AD FS deployment advisor</span></span>](https://aka.ms/adfsguidance)
 - [<span data-ttu-id="b4b14-112">Azure RMS 배포 마법사</span><span class="sxs-lookup"><span data-stu-id="b4b14-112">Azure RMS Deployment Wizard</span></span>](https://aka.ms/azuremsguidance)
 - [<span data-ttu-id="b4b14-113">Azure AD Premium 설정 가이드</span><span class="sxs-lookup"><span data-stu-id="b4b14-113">Azure AD Premium setup guide</span></span>](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-office-365-identity-management"></a><span data-ttu-id="b4b14-114">Azure AD edition 및 Office 365 id 관리</span><span class="sxs-lookup"><span data-stu-id="b4b14-114">Azure AD editions and Office 365 identity management</span></span>

<span data-ttu-id="b4b14-115">Office 365에 대 한 유료 구독을 사용 하는 경우 Azure AD에 대 한 무료 구독도 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4b14-115">If you have a paid subscription to Office 365, you also have a free subscription to Azure AD.</span></span> <span data-ttu-id="b4b14-116">Azure AD를 사용 하 여 사용자 및 그룹 계정을 만들고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4b14-116">You can use Azure AD to create and manage user and group accounts.</span></span> <span data-ttu-id="b4b14-117">이 구독을 활성화 하려면 일회용 등록을 완료 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4b14-117">To activate this subscription you have to complete a one-time registration.</span></span> <span data-ttu-id="b4b14-118">나중에 Office 365 관리 포털에서 Azure AD에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4b14-118">Afterward, you can access Azure AD from your Office 365 admin portal.</span></span> <span data-ttu-id="b4b14-119">자세한 내용은 [무료 Azure AD 구독 등록](https://go.microsoft.com/fwlink/p/?LinkId=617127)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="b4b14-119">For instructions, see [register your free Azure AD subscription](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span></span> 
  
> [!TIP]
> <span data-ttu-id="b4b14-120">위의 지침에 따라 Office 365 구독에 제공 된 무료 Azure AD 구독을 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4b14-120">Follow the instructions above to register the free Azure AD subscription that comes with your subscription to Office 365.</span></span> <span data-ttu-id="b4b14-121">등록을 위해 azure.microsoft.com로 직접 이동 하지 마세요. 또는 Office 365 용 무료 프로그램과는 별도의 microsoft azure 평가판 또는 유료 구독을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4b14-121">Don't go directly to azure.microsoft.com to sign up or you'll end up with a trial or paid subscription to Microsoft Azure that is separate from your free one for Office 365.</span></span> 
  
<span data-ttu-id="b4b14-122">무료 구독을 사용 하 여 온-프레미스 디렉터리와 동기화 하 고 single sign-on을 설정 하 고, Salesforce, DropBox 등의 다양 한 소프트웨어와 서비스 응용 프로그램을 동기화 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4b14-122">With the free subscription you can synchronize with on-premises directories, set up single sign-on, and synchronize with many software as service applications, such as Salesforce, DropBox and many more.</span></span>
  
<span data-ttu-id="b4b14-123">향상 된 AD DS 기능, 양방향 동기화 및 기타 관리 기능을 사용 하려면 무료 구독을 유료 프리미엄 구독으로 업그레이드 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4b14-123">If you want enhanced AD DS functionality, bi-directional synchronization, and other management capabilities, you can upgrade your free subscription to a paid premium subscription.</span></span> <span data-ttu-id="b4b14-124">자세한 내용은 [Azure Active Directory 버전](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b4b14-124">For details see [Azure Active Directory editions](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis).</span></span>
  
<span data-ttu-id="b4b14-125">office 365 및 azure AD에 대 한 자세한 내용은 [office 365 id 및 azure Active Directory 이해](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b4b14-125">For more information about Office 365 and Azure AD, see [Understanding Office 365 Identity and Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9).</span></span>
  
## <a name="extend-the-capabilities-of-your-office-365-tenant"></a><span data-ttu-id="b4b14-126">Office 365 테 넌 트의 기능 확장</span><span class="sxs-lookup"><span data-stu-id="b4b14-126">Extend the capabilities of your Office 365 tenant</span></span>

|<span data-ttu-id="b4b14-127">**기능**</span><span class="sxs-lookup"><span data-stu-id="b4b14-127">**Feature**</span></span>|<span data-ttu-id="b4b14-128">**설명**</span><span class="sxs-lookup"><span data-stu-id="b4b14-128">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="b4b14-129">통합 앱</span><span class="sxs-lookup"><span data-stu-id="b4b14-129">Integrated apps</span></span>  <br/> |<span data-ttu-id="b4b14-130">개별 앱에 메일, 일정, 연락처, 사용자, 그룹, 파일 및 폴더와 같은 Office 365 데이터에 대 한 액세스 권한을 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4b14-130">You can grant individual apps access to your Office 365 data, like mail, calendars, contacts, users, groups, files, and folders.</span></span> <span data-ttu-id="b4b14-131">또한 전역 관리자 수준에서 이러한 앱에 권한을 부여 하 고 Azure AD에 앱을 등록 하 여 전체 회사에서 사용할 수 있도록 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4b14-131">You can also authorize these apps at global admin level and make them available to your entire company by registering the apps in Azure AD.</span></span> <span data-ttu-id="b4b14-132">자세한 내용은 [Office 365 관리자를 위한 통합 앱 및 Azure AD를](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b4b14-132">For details see [Integrated Apps and Azure AD for Office 365 administrators](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).</span></span>  <br/> <span data-ttu-id="b4b14-133">[Azure AD 응용 프로그램 갤러리 및 single sign-on](https://go.microsoft.com/fwlink/p/?LinkId=698604)도 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b4b14-133">See also [Azure AD application gallery and single-sign-on](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>  <br/> |
|<span data-ttu-id="b4b14-134">PowerApps</span><span class="sxs-lookup"><span data-stu-id="b4b14-134">PowerApps</span></span>  <br/> | <span data-ttu-id="b4b14-135">Power apps는 SharePoint 목록 및 기타 데이터 앱과 같은 기존 데이터 원본에 연결할 수 있는 모바일 장치용으로 중요 한 앱입니다.</span><span class="sxs-lookup"><span data-stu-id="b4b14-135">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps.</span></span> <span data-ttu-id="b4b14-136">자세한 내용은 SharePoint Online 및 [PowerApps 페이지](https://powerapps.microsoft.com/) [에서 목록에 대 한 PowerApp 만들기](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b4b14-136">See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.</span></span>  <br/> |
   
<span data-ttu-id="b4b14-137">Microsoft Cloud 및 Office 365에 대 한 기타 리소스는 다음 리소스를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b4b14-137">For other resources about the Microsoft Cloud and Office 365, see these resources:</span></span>
  
- [<span data-ttu-id="b4b14-138">엔터프라이즈 설계자 용 Microsoft 클라우드 id</span><span class="sxs-lookup"><span data-stu-id="b4b14-138">Microsoft Cloud Identity for Enterprise Architects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524586)
    
- [<span data-ttu-id="b4b14-139">Microsoft Azure에서 Office 365 DirSync(디렉터리 동기화)를 배포</span><span class="sxs-lookup"><span data-stu-id="b4b14-139">Deploy Office 365 Directory Synchronization (DirSync) in Microsoft Azure</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=517887)
    

<span data-ttu-id="b4b14-140">자세한 내용은 [통합 앱 및 azure ad for Office 365 관리자](integrated-apps-and-azure-ads.md) 및 [azure ad application gallery 및 single sign-on](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on)을 참고 하세요.</span><span class="sxs-lookup"><span data-stu-id="b4b14-140">Learn more at [Integrated Apps and Azure AD for Office 365 administrators](integrated-apps-and-azure-ads.md) and [Azure AD application gallery and single-sign-on](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).</span></span>

### <a name="power-apps"></a><span data-ttu-id="b4b14-141">파워 앱</span><span class="sxs-lookup"><span data-stu-id="b4b14-141">Power Apps</span></span>
<span data-ttu-id="b4b14-142">Power apps는 SharePoint 목록 및 기타 데이터 앱과 같은 기존 데이터 원본에 연결할 수 있는 모바일 장치용으로 중요 한 앱입니다.</span><span class="sxs-lookup"><span data-stu-id="b4b14-142">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps.</span></span> <span data-ttu-id="b4b14-143">자세한 내용은 SharePoint Online 및 [PowerApps 페이지](https://powerapps.microsoft.com/) [에서 목록에 대 한 PowerApp 만들기](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b4b14-143">See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.</span></span>