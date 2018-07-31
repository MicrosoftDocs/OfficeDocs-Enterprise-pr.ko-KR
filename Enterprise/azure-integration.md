---
title: Office 365와 azure 통합
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 12/29/2016
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MOE150
- MED150
- BCS160
ms.assetid: a5efce5d-9c9c-4190-b61b-fd273c1d425f
description: Office 365 구독 Azure AD에 대 한 구독을 포함합니다. 온-프레미스 환경 암호 동기화 또는 single sign-on을 사용할 경우 Azure AD와 Office 365를 통합 합니다.
ms.openlocfilehash: abeda5eb915ac4ff9e395ab3b28f1e0cb7a68163
ms.sourcegitcommit: 92d16c0926e4be3fd493fe9b4eb317fb54996bca
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2018
ms.locfileid: "21550082"
---
# <a name="azure-integration-with-office-365"></a><span data-ttu-id="f792b-104">Office 365와 azure 통합</span><span class="sxs-lookup"><span data-stu-id="f792b-104">Azure integration with Office 365</span></span>

<span data-ttu-id="f792b-p102">Office 365 Azure Active Directory (Azure AD)를 사용 하 여 백그라운드에서 사용자 id를 관리 합니다. Office 365 구독 암호 동기화 또는 온-프레미스 환경에서 single sign-on을 설정 하려면 Azure AD를 사용한 Office 365를 통합할 수 있도록 Azure AD에 대 한 무료 구독을 포함 합니다. 또한 사용자 계정 관리 효율을 높이 고급 기능을 구입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f792b-p102">Office 365 uses Azure Active Directory (Azure AD)to manage user identities behind the scenes. Your Office 365 subscription includes a free subscription to Azure AD so that you can integrate Office 365 with Azure AD if you want to sync passwords or set up single sign-on with your on-premises environment. You can also buy advanced features to better manage your accounts.</span></span>
  
<span data-ttu-id="f792b-108">Azure 확장 하 고 Office 365 구독을 사용자 지정 하는데 사용할 수 있는 통합 된 응용 프로그램, 관리와 같은 다른 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f792b-108">Azure also offers other functionality, like managing integrated apps, that you can use to extend and customize your Office 365 subscriptions.</span></span>
  
<span data-ttu-id="f792b-109">Azure AD 문에 사용할 수도 있습니다: [Azure AD 연결 관리자](https://aka.ms/aadconnectpwsync), [AD FS 배포 관리자](https://aka.ms/adfsguidance), [Azure RMS Deploymnet 마법사](https://aka.ms/azuremsguidance)및 [Azure AD 프리미엄 설치 가이드](https://aka.ms/aadpguidance)입니다.</span><span class="sxs-lookup"><span data-stu-id="f792b-109">You can also use the Azure AD advisors: the [Azure AD Connect advisor](https://aka.ms/aadconnectpwsync), the [AD FS deployment advisor](https://aka.ms/adfsguidance), the [Azure RMS Deploymnet Wizard](https://aka.ms/azuremsguidance), and the [Azure AD Premium setup guide](https://aka.ms/aadpguidance).</span></span>
  
## <a name="azure-ad-editions-and-office-365-identity-management"></a><span data-ttu-id="f792b-110">Azure AD 버전 및 Office 365 id 관리</span><span class="sxs-lookup"><span data-stu-id="f792b-110">Azure AD editions and Office 365 identity management</span></span>

<span data-ttu-id="f792b-p103">Office 365에 대 한 유료 구독을 설치한 경우 Azure AD에 대 한 무료 구독을 해야 합니다. Azure AD 사용자 및 그룹 계정 만들기 및 관리를 사용할 수 있습니다. 이 구독을 활성화 하려면 일회성 등록을 완료 해야 합니다. 나중에 대 한 Office 365 관리 포털에서 Azure AD를 액세스할 수 있습니다. 자세한 내용은 [무료 사용자 등록 Azure AD 구독](https://go.microsoft.com/fwlink/p/?LinkId=617127)합니다.</span><span class="sxs-lookup"><span data-stu-id="f792b-p103">If you have a paid subscription to Office 365, you also have a free subscription to Azure AD. You can use Azure AD to create and manage user and group accounts. To activate this subscription you have to complete a one-time registration. Afterward, you can access Azure AD from your Office 365 admin portal. For instructions, see [register your free Azure AD subscription](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span></span> 
  
> [!TIP]
> <span data-ttu-id="f792b-p104">Office 365를 통해 구독와 함께 제공 되는 등록 무료 Azure AD 구독에 위의 지침을 따릅니다. 등록 (영문)를 Azure.Microsoft.com로 직접 이동 하지 또는 Office 365에 대 한 무료 컴퓨터로 별도로 Microsoft Azure에 대 한 평가판 또는 유료 구독으로 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="f792b-p104">Follow the instructions above to register the free Azure AD subscription that comes with your subscription to Office 365. Don't go directly to Azure.Microsoft.com to sign up or you'll end up with a trial or paid subscription to Microsoft Azure that is separate from your free one for Office 365.</span></span> 
  
<span data-ttu-id="f792b-118">무료 구독을 온-프레미스 디렉터리와 동기화, single sign-on을 설정 및 가지 Salesforce, 드롭 상자 등의 많은 등의 서비스 응용 프로그램으로 다양 한 소프트웨어와 동기화 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f792b-118">With the free subscription you can synchronize with on-premises directories, set up single sign-on, and synchronize with many software as service applications, such as Salesforce, DropBox and many more.</span></span>
  
<span data-ttu-id="f792b-p105">향상 된 AD DS 기능, 양방향 동기화 및 기타 관리 기능을 하려는 경우에 프리미엄 유료 구독으로 무료 구독을 업그레이드할 수 있습니다. 자세한 내용은 [Azure Active Directory editions](https://go.microsoft.com/fwlink/p/?LinkId=524280)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="f792b-p105">If you want enhanced AD DS functionality, bi-directional synchronization, and other management capabilities, you can upgrade your free subscription to a paid premium subscription. For details see [Azure Active Directory editions](https://go.microsoft.com/fwlink/p/?LinkId=524280).</span></span>
  
<span data-ttu-id="f792b-121">Office 365와 Azure AD 하는 방법에 대 한 자세한 내용은 [Office 365 Id 이해 하 고 Azure Active Directory를](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="f792b-121">For more information about Office 365 and Azure AD, see [Understanding Office 365 Identity and Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9).</span></span>
  
## <a name="extend-the-capabilities-of-your-office-365-tenant"></a><span data-ttu-id="f792b-122">Office 365 테 넌 트의 기능을 확장</span><span class="sxs-lookup"><span data-stu-id="f792b-122">Extend the capabilities of your Office 365 tenant</span></span>

|<span data-ttu-id="f792b-123">**기능**</span><span class="sxs-lookup"><span data-stu-id="f792b-123">**Feature**</span></span>|<span data-ttu-id="f792b-124">**설명**</span><span class="sxs-lookup"><span data-stu-id="f792b-124">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="f792b-125">통합 된 앱</span><span class="sxs-lookup"><span data-stu-id="f792b-125">Integrated apps</span></span>  <br/> |<span data-ttu-id="f792b-p106">메일, 일정, 연락처, 사용자, 그룹, 파일 및 폴더와 같은 Office 365 데이터, 개별 응용 프로그램 액세스를 허용할 수 있습니다. 전역 관리자 수준에서 이러한 앱 권한을 부여 하 고 사용할 수 있도록 전체 회사 Azure AD에 앱을 등록 하 여 수도 있습니다. 자세한 내용은 [통합 Apps 및 Office 365 관리자를 위한 Azure AD를](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="f792b-p106">You can grant individual apps access to your Office 365 data, like mail, calendars, contacts, users, groups, files, and folders. You can also authorize these apps at global admin level and make them available to your entire company by registering the apps in Azure AD. For details see [Integrated Apps and Azure AD for Office 365 administrators](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).  </span></span><br/> <span data-ttu-id="f792b-129">참고 [Azure AD 응용 프로그램 갤러리 및 single sign-on](https://go.microsoft.com/fwlink/p/?LinkId=698604)합니다.</span><span class="sxs-lookup"><span data-stu-id="f792b-129">See also [Azure AD application gallery and single-sign-on](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>  <br/> |
|<span data-ttu-id="f792b-130">PowerApps</span><span class="sxs-lookup"><span data-stu-id="f792b-130">PowerApps</span></span>  <br/> | <span data-ttu-id="f792b-p107">전원 앱은 SharePoint 목록 같은 원본 기존 데이터에 연결할 수 있는 모바일 장치에 대 한 초점된 앱 및 다른 데이터 응용 프로그램입니다. 자세한 내용은 [SharePoint Online에서 목록에 대 한 들어오지 않습니다 만들기](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) 및 [PowerApps 페이지](https://powerapps.microsoft.com/) 를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="f792b-p107">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps. See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.  </span></span><br/> |
   
<span data-ttu-id="f792b-133">Microsoft 클라우드 및 Office 365에 대 한 기타 리소스에 대 한 다음이 리소스를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="f792b-133">For other resources about the Microsoft Cloud and Office 365, see these resources:</span></span>
  
- [<span data-ttu-id="f792b-134">Microsoft Cloud ID for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="f792b-134">Microsoft Cloud Identity for Enterprise Architects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=828642)
    
- [<span data-ttu-id="f792b-135">Microsoft Azure에서 Office 365 DirSync(디렉터리 동기화)를 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="f792b-135">Deploy Office 365 Directory Synchronization (DirSync) in Microsoft Azure</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=517887)
    

