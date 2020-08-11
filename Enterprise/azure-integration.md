---
title: Microsoft 365과 Azure 통합
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/09/2019
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: a5efce5d-9c9c-4190-b61b-fd273c1d425f
description: 온-프레미스 환경에 암호 동기화 또는 single sign-on을 사용 하려면 Microsoft 365를 Azure AD와 통합 합니다.
ms.openlocfilehash: 64fcf25c75e636bebf78e9367f4cc68b367548f7
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606104"
---
# <a name="azure-integration-with-microsoft-365"></a><span data-ttu-id="d8cbd-103">Microsoft 365과 Azure 통합</span><span class="sxs-lookup"><span data-stu-id="d8cbd-103">Azure integration with Microsoft 365</span></span>

<span data-ttu-id="d8cbd-104">*이 문서는 Microsoft 365 Enterprise와 Office 365 Enterprise에 모두 적용됩니다.*</span><span class="sxs-lookup"><span data-stu-id="d8cbd-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="d8cbd-105">Microsoft 365는 Azure Active Directory (Azure AD)를 사용 하 여 백그라운드에서 사용자 id를 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8cbd-105">Microsoft 365 uses Azure Active Directory (Azure AD) to manage user identities behind the scenes.</span></span> <span data-ttu-id="d8cbd-106">Microsoft 365 구독에는 Azure AD에 대 한 무료 구독이 포함 되어 있어 암호를 동기화 하거나 single sign-on을 온-프레미스 환경에 설정 하려는 경우 Azure AD와 Microsoft 365를 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8cbd-106">Your Microsoft 365 subscription includes a free subscription to Azure AD so that you can integrate Microsoft 365 with Azure AD if you want to sync passwords or set up single sign-on with your on-premises environment.</span></span> <span data-ttu-id="d8cbd-107">계정을 보다 효율적으로 관리 하기 위해 고급 기능을 구입할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8cbd-107">You can also buy advanced features to better manage your accounts.</span></span>
  
<span data-ttu-id="d8cbd-108">Azure는 Microsoft 365 구독을 확장 및 사용자 지정 하는 데 사용할 수 있는 통합 앱 관리 등의 기타 기능도 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8cbd-108">Azure also offers other functionality, like managing integrated apps, that you can use to extend and customize your Microsoft 365 subscriptions.</span></span>
  
<span data-ttu-id="d8cbd-109">안내 설치 및 구성 환경에 대해 Azure AD 배포 관리자를 사용할 수 있습니다 (Microsoft 365에 로그인 해야 함).</span><span class="sxs-lookup"><span data-stu-id="d8cbd-109">You can use the Azure AD deployment advisors for a guided setup and configuration experience (you must be signed in to Microsoft 365):</span></span>

 - [<span data-ttu-id="d8cbd-110">Azure AD Connect advisor</span><span class="sxs-lookup"><span data-stu-id="d8cbd-110">Azure AD Connect advisor</span></span>](https://aka.ms/aadconnectpwsync)
 - [<span data-ttu-id="d8cbd-111">AD FS 배포 관리자</span><span class="sxs-lookup"><span data-stu-id="d8cbd-111">AD FS deployment advisor</span></span>](https://aka.ms/adfsguidance)
 - [<span data-ttu-id="d8cbd-112">Azure AD 설정 가이드</span><span class="sxs-lookup"><span data-stu-id="d8cbd-112">Azure AD setup guide</span></span>](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-microsoft-365-identity-management"></a><span data-ttu-id="d8cbd-113">Azure AD edition 및 Microsoft 365 id 관리</span><span class="sxs-lookup"><span data-stu-id="d8cbd-113">Azure AD editions and Microsoft 365 identity management</span></span>

<span data-ttu-id="d8cbd-114">Microsoft 365에 대 한 유료 구독을 사용 하는 경우 Azure AD에 대 한 무료 구독도 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d8cbd-114">If you have a paid subscription to Microsoft 365, you also have a free subscription to Azure AD.</span></span> <span data-ttu-id="d8cbd-115">Azure AD를 사용 하 여 사용자 및 그룹 계정을 만들고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8cbd-115">You can use Azure AD to create and manage user and group accounts.</span></span> <span data-ttu-id="d8cbd-116">이 구독을 활성화 하려면 일회용 등록을 완료 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8cbd-116">To activate this subscription you have to complete a one-time registration.</span></span> <span data-ttu-id="d8cbd-117">나중에 Microsoft 365 관리 센터에서 Azure AD에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8cbd-117">Afterward, you can access Azure AD from your Microsoft 365 admin center.</span></span> 

<span data-ttu-id="d8cbd-118">자세한 내용은 [무료 AZURE AD 구독 사용](https://go.microsoft.com/fwlink/p/?LinkId=617127)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="d8cbd-118">For instructions, see [use your free Azure AD subscription](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span></span> <span data-ttu-id="d8cbd-119">지침에 따라 Microsoft 365에 가입 하 여 제공 된 무료 Azure AD 구독을 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8cbd-119">Follow the instructions to register the free Azure AD subscription that comes with your subscription to Microsoft 365.</span></span> <span data-ttu-id="d8cbd-120">Azure.microsoft.com로 직접 이동 하 여 등록 하지 않고 microsoft Azure에 대 365 한 평가판 또는 유료 구독을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d8cbd-120">Don't go directly to azure.microsoft.com to sign up or you'll end up with a trial or paid subscription to Microsoft Azure that is separate from your free one for Microsoft 365.</span></span> 
  
<span data-ttu-id="d8cbd-121">무료 구독을 사용 하 여 온-프레미스 디렉터리와 동기화 하 고 single sign-on을 설정 하 고, Salesforce, DropBox 등의 다양 한 소프트웨어와 서비스 응용 프로그램을 동기화 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8cbd-121">With the free subscription you can synchronize with on-premises directories, set up single sign-on, and synchronize with many software as service applications, such as Salesforce, DropBox and many more.</span></span>
  
<span data-ttu-id="d8cbd-122">향상 된 AD DS (Active Directory 도메인 서비스) 기능, 양방향 동기화 및 기타 관리 기능을 사용 하려면 무료 구독을 유료 premium 구독으로 업그레이드 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d8cbd-122">If you want enhanced Active Directory Domain Services (AD DS) functionality, bi-directional synchronization, and other management capabilities, you can upgrade your free subscription to a paid premium subscription.</span></span> <span data-ttu-id="d8cbd-123">자세한 내용은 [Azure Active Directory 버전](https://azure.microsoft.com/pricing/details/active-directory/)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d8cbd-123">For details see [Azure Active Directory editions](https://azure.microsoft.com/pricing/details/active-directory/).</span></span>
  
<span data-ttu-id="d8cbd-124">Microsoft 365 및 Azure AD에 대 한 자세한 내용은 [microsoft 365 Identity 및 Azure Active Directory 이해](about-office-365-identity.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d8cbd-124">For more information about Microsoft 365 and Azure AD, see [Understanding Microsoft 365 Identity and Azure Active Directory](about-office-365-identity.md).</span></span>
  
## <a name="extend-the-capabilities-of-your-microsoft-365-tenant"></a><span data-ttu-id="d8cbd-125">Microsoft 365 테 넌 트의 기능 확장</span><span class="sxs-lookup"><span data-stu-id="d8cbd-125">Extend the capabilities of your Microsoft 365 tenant</span></span>

|<span data-ttu-id="d8cbd-126">**기능**</span><span class="sxs-lookup"><span data-stu-id="d8cbd-126">**Feature**</span></span>|<span data-ttu-id="d8cbd-127">**설명**</span><span class="sxs-lookup"><span data-stu-id="d8cbd-127">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="d8cbd-128">통합 앱</span><span class="sxs-lookup"><span data-stu-id="d8cbd-128">Integrated apps</span></span>  <br/> |<span data-ttu-id="d8cbd-129">개별 앱에 메일, 일정, 연락처, 사용자, 그룹, 파일 및 폴더와 같은 Microsoft 365 데이터에 대 한 액세스 권한을 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8cbd-129">You can grant individual apps access to your Microsoft 365 data, like mail, calendars, contacts, users, groups, files, and folders.</span></span> <span data-ttu-id="d8cbd-130">또한 전역 관리자 수준에서 이러한 앱에 권한을 부여 하 고 Azure AD에 앱을 등록 하 여 전체 회사에서 사용할 수 있도록 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8cbd-130">You can also authorize these apps at global admin level and make them available to your entire company by registering the apps in Azure AD.</span></span> <span data-ttu-id="d8cbd-131">자세한 내용은 [Microsoft 365 관리자를 위한 통합 앱 및 AZURE AD를](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d8cbd-131">For details see [Integrated Apps and Azure AD for Microsoft 365 administrators](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).</span></span>  <br/> <span data-ttu-id="d8cbd-132">또한 [응용 프로그램에 대 한 sso (single sign-on)](https://go.microsoft.com/fwlink/p/?LinkId=698604)도 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="d8cbd-132">Also see [single sign-on to applications](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>  <br/> |
|<span data-ttu-id="d8cbd-133">PowerApps</span><span class="sxs-lookup"><span data-stu-id="d8cbd-133">PowerApps</span></span>  <br/> | <span data-ttu-id="d8cbd-134">Power apps는 SharePoint 목록 및 기타 데이터 앱과 같은 기존 데이터 원본에 연결할 수 있는 모바일 장치용으로 중요 한 앱입니다.</span><span class="sxs-lookup"><span data-stu-id="d8cbd-134">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps.</span></span> <span data-ttu-id="d8cbd-135">자세한 내용은 SharePoint Online 및 [PowerApps 페이지](https://powerapps.microsoft.com/) [에서 목록에 대 한 PowerApp 만들기](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d8cbd-135">See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.</span></span>  <br/> |
   
<span data-ttu-id="d8cbd-136">자세한 내용은 [통합 앱 및 azure ad For Microsoft 365 administrators](integrated-apps-and-azure-ads.md) 및 [azure ad application gallery 및 single sign-on](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on)을 참고 하세요.</span><span class="sxs-lookup"><span data-stu-id="d8cbd-136">Learn more at [Integrated Apps and Azure AD for Microsoft 365 administrators](integrated-apps-and-azure-ads.md) and [Azure AD application gallery and single-sign-on](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).</span></span>

## <a name="see-also"></a><span data-ttu-id="d8cbd-137">기타 참고 항목</span><span class="sxs-lookup"><span data-stu-id="d8cbd-137">See also</span></span>

[<span data-ttu-id="d8cbd-138">Microsoft 365 Enterprise 개요</span><span class="sxs-lookup"><span data-stu-id="d8cbd-138">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
