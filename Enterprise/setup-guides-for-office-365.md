---
title: Microsoft 365 및 Office 365 서비스용 설정 가이드
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/15/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365_Setup
search.appverid:
- MET150
- MET150
- BCS160
ms.assetid: 165f46e8-3533-4d76-be57-97f81ebd40f2
description: 설치 가이드를 사용 하 여 Microsoft 365 또는 Office 365의 계획 및 구성을 가속화 합니다.
ms.openlocfilehash: 92c792b3d82a6a0f1405059ae50db581823704dc
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2020
ms.locfileid: "44735976"
---
# <a name="setup-guides-for-microsoft-365-and-office-365-services"></a><span data-ttu-id="baef2-103">Microsoft 365 및 Office 365 서비스용 설정 가이드</span><span class="sxs-lookup"><span data-stu-id="baef2-103">Setup guides for Microsoft 365 and Office 365 services</span></span>

<span data-ttu-id="baef2-104">Microsoft 365 및 Office 365 설치 가이드에서는 앱 및 서비스를 배포 하기 위한 관리자가 조정할 때 사용할 지침 및 리소스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-104">Microsoft 365 and Office 365 setup guides give admins tailored guidance and resources for deploying apps and services.</span></span> <span data-ttu-id="baef2-105">이러한 가이드는 FastTrack 온 보 딩 전문가가 개별 상호 작용에서 공유 하는 것과 동일한 모범 사례를 사용 하 여 작성 되었으며, Microsoft 365 관리 센터 내의 모든 관리자가 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-105">These guides are created using the same best practices that FastTrack onboarding specialists share in individual interactions, and they're available to all admins within the Microsoft 365 admin center.</span></span> <span data-ttu-id="baef2-106">제품 설정에 대 한 정보를 제공 하 고, 보안 기능을 사용 하며, 공동 작업 도구를 배포 하 고, 고급 배포 속도를 향상 하기 위한 스크립트를 제공</span><span class="sxs-lookup"><span data-stu-id="baef2-106">They give information on product setup, enabling security features, deploying collaboration tools, and provide scripts to speed up advanced deployments.</span></span>

## <a name="how-to-access-setup-guides-in-the-microsoft-365-admin-center"></a><span data-ttu-id="baef2-107">Microsoft 365 관리 센터에서 설치 가이드에 액세스 하는 방법</span><span class="sxs-lookup"><span data-stu-id="baef2-107">How to access setup guides in the Microsoft 365 admin center</span></span>

<span data-ttu-id="baef2-108">설치 가이드는 Microsoft 365 관리 센터의 [설치 지침](https://aka.ms/setupguidance) 페이지에서 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-108">The setup guides are accessible from the [Setup guidance](https://aka.ms/setupguidance) page in the Microsoft 365 admin center.</span></span> <span data-ttu-id="baef2-109">진행 상황을 추적 하 고 언제 든 지 안내선을 완성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-109">You can keep track of the status of your progress and you have the option to return at any time to complete a guide.</span></span> <span data-ttu-id="baef2-110">**설치 지침** 페이지에 연결 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-110">To reach the **Setup guidance** page:</span></span>

1. <span data-ttu-id="baef2-111">[관리 센터](https://admin.microsoft.com/)에서 **홈** 페이지로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-111">In the [admin center](https://admin.microsoft.com/), go to the **Home** page.</span></span>
2. <span data-ttu-id="baef2-112">**교육 & 가이드** 카드를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-112">Find the **Training & guides** card.</span></span> 

  ![Microsoft 365 관리 센터의 가이드 카드 & 교육](./media/setup-guides-for-office-365/adminportal-trainingandguides.png)

3. <span data-ttu-id="baef2-114">**사용자 지정 설치 지침**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-114">Select **Customized setup guidance**.</span></span>

  ![Microsoft 365 관리 센터의 설치 지침 페이지 스크린샷](./media/setup-guides-for-office-365/adminportal-setupguidance.png)

>[!NOTE]
><span data-ttu-id="baef2-116">Microsoft 365 관리 센터에 액세스 하려면 테 넌 트 관리자 권한이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-116">Tenant administrator permissions are required to access the Microsoft 365 admin center.</span></span>

## <a name="how-do-setup-guides-work-in-the-microsoft-365-admin-center"></a><span data-ttu-id="baef2-117">Microsoft 365 관리 센터에서 설정 가이드는 어떻게 작동 하나요?</span><span class="sxs-lookup"><span data-stu-id="baef2-117">How do setup guides work in the Microsoft 365 admin center?</span></span>

<span data-ttu-id="baef2-118">각 가이드에서는 구성을 변경 하는 데 사용할 수 있는 스크립트, 리소스, 문서 및 필요에 따라 단계별 지침을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-118">Each guide provides you with step-by-step instructions, resources, articles, and when needed, scripts you can use to make configuration changes.</span></span> <span data-ttu-id="baef2-119">이러한 가이드에서는 소규모 및 대규모 orgs에 대 한 특정 요구 사항을 반영 하는 선택 항목을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-119">These guides provide you with choices that reflect the specific needs of both small and large orgs.</span></span> <span data-ttu-id="baef2-120">또한 제공 되는 지침에는 신규 및 숙련 된 관리자 모두에 대 한 지원이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-120">Additionally, the guidance provided includes assistance for both new and more experienced admins.</span></span>

![설정 가이드의 예](./media/setup-guides-for-office-365/m365-setupguide-example.png)

<span data-ttu-id="baef2-122">가이드를 사용 하 여 계획 단계에서 특정 Microsoft 365 및 Office 365 기능에 대해 자세히 알아보고, 설정을 수정 하기 위한 배포를 완료 한 후에 다시 방문 합니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-122">You can use the guides to learn more about specific Microsoft 365 and Office 365 features during the planning phase or revisit them after you've completed a deployment to modify a setting.</span></span>

## <a name="guides-for-initial-setup"></a><span data-ttu-id="baef2-123">초기 설정 가이드</span><span class="sxs-lookup"><span data-stu-id="baef2-123">Guides for initial setup</span></span>

### <a name="prepare-your-environment"></a><span data-ttu-id="baef2-124">작업 환경 준비</span><span class="sxs-lookup"><span data-stu-id="baef2-124">Prepare your environment</span></span>

<span data-ttu-id="baef2-125">**환경 준비** 가이드에서는 Microsoft 365 및 Office 365 서비스에 대 한 조직의 환경을 준비 하는 데 도움이 되는 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-125">The **Prepare your environment** guide helps you prepare your org's environment for Microsoft 365 and Office 365 services.</span></span> <span data-ttu-id="baef2-126">목표에 관계 없이 성공적인 배포를 위해 완료 해야 하는 작업이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-126">Regardless of your goals, there are tasks you'll need to complete to ensure a successful deployment.</span></span> <span data-ttu-id="baef2-127">환경을 준비 하는 동안 오류가 발생 하지 않도록 하려면 도메인을 연결 하 고, 사용자를 추가 하 고, 라이선스를 할당 하 고, Exchange Online을 사용 하 여 전자 메일을 설정 하 고, Office 앱을 설치 또는 배포 하는 단계별 지침을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-127">To avoid any errors while preparing your environment, you're provided with step-by-step instructions to connect your domain, add users, assign licenses, set up email with Exchange Online, and install or deploy Office apps.</span></span> 

|||
|:-------|:-----|
| <span data-ttu-id="baef2-128">**실행**</span><span class="sxs-lookup"><span data-stu-id="baef2-128">**Run:**</span></span> | [<span data-ttu-id="baef2-129">작업 환경 준비</span><span class="sxs-lookup"><span data-stu-id="baef2-129">Prepare your environment</span></span>](https://aka.ms/prepareyourenvironment) |
||||

### <a name="email-setup-advisor"></a><span data-ttu-id="baef2-130">전자 메일 설정 도우미</span><span class="sxs-lookup"><span data-stu-id="baef2-130">Email setup advisor</span></span>

<span data-ttu-id="baef2-131">**전자 메일 설정 관리자** 는 조직에 대해 Exchange Online을 구성 하는 데 필요한 단계별 지침을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-131">The **Email setup advisor** provides you with the step-by-step guidance needed for configuring Exchange Online for your organization.</span></span> <span data-ttu-id="baef2-132">여기에는 새 전자 메일 계정 설정, 전자 메일 마이그레이션, 전자 메일 보호 구성 등이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-132">This includes setting up new email accounts, migrating email, and configuring email protection.</span></span> <span data-ttu-id="baef2-133">전자 메일을 설정 하려면이 관리자를 사용 하 여 조직의 현재 메일 시스템, 마이그레이션되는 사서함 수, 사용자 및 해당 액세스를 관리 하는 방법에 따라 권장 되는 마이그레이션 방법을 수신 합니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-133">For a successful email set up, use this advisor and you'll receive the recommended migration method based on your org's current mail system, the number of mailboxes being migrated, and how you want to manage users and their access.</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="baef2-134">**실행**</span><span class="sxs-lookup"><span data-stu-id="baef2-134">**Run:**</span></span> | [<span data-ttu-id="baef2-135">전자 메일 설정 도우미</span><span class="sxs-lookup"><span data-stu-id="baef2-135">Email setup advisor</span></span>](https://aka.ms/office365setup) |
||||

### <a name="gmail-contacts-and-calendar-advisor"></a><span data-ttu-id="baef2-136">Gmail 연락처 및 일정 도우미</span><span class="sxs-lookup"><span data-stu-id="baef2-136">Gmail contacts and calendar advisor</span></span>

<span data-ttu-id="baef2-137">Gmail 사용자의 사서함을 Microsoft 365로 마이그레이션하는 경우 전자 메일 메시지가 마이그레이션되고 연락처 및 일정 항목은 마이그레이션되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-137">When you migrate a Gmail user's mailbox to Microsoft 365, email messages are migrated, but contacts and calendar items are not.</span></span> <span data-ttu-id="baef2-138">이 관리자는 Outlook.com, Outlook 클라이언트 또는 PowerShell과 함께 import 및 export 메서드를 사용 하 여 Google 연락처 및 Google 일정 항목을 Microsoft 365로 가져오는 단계를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-138">This advisor provides steps for importing Google contacts and Google calendar items to Microsoft 365 using import and export methods with Outlook.com, the Outlook client, or PowerShell.</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="baef2-139">**실행**</span><span class="sxs-lookup"><span data-stu-id="baef2-139">**Run:**</span></span> |  [<span data-ttu-id="baef2-140">Gmail 연락처 및 일정 도우미</span><span class="sxs-lookup"><span data-stu-id="baef2-140">Gmail contacts and calendar advisor</span></span>](https://aka.ms/gmailcontactscalendar) |
|||

### <a name="microsoft-365-deployment-advisor"></a><span data-ttu-id="baef2-141">Microsoft 365 배포 관리자</span><span class="sxs-lookup"><span data-stu-id="baef2-141">Microsoft 365 deployment advisor</span></span>

<span data-ttu-id="baef2-142">**Microsoft 365 배포 관리자** 는 생산성 도구, 보안 정책 및 장치 관리 기능을 설정할 때 상업적 고객에 게 지침을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-142">The **Microsoft 365 deployment advisor** provides commercial customers with guidance when setting up productivity tools, security policies, and device management capabilities.</span></span> <span data-ttu-id="baef2-143">Microsoft 365 Business Premium 또는 Microsoft 365 Enterprise 구독을 사용할 경우이 관리자를 사용 하 여 조직의 장치를 설정 및 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-143">With a Microsoft 365 Business Premium or Microsoft 365 Enterprise subscription, you can use this advisor to set up and configure your organization's devices.</span></span> <span data-ttu-id="baef2-144">사용자는 클라우드 서비스를 사용 하도록 설정 하 고, 장치를 지원 되는 최신 버전의 Windows 10으로 업데이트 하 고, 장치를 Azure Active Directory (Azure AD)에 단일 중앙 위치에 가입 하기 위한 지침 및 리소스에 대 한 액세스 권한을 수신 합니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-144">You'll receive guidance and access to resources to enable your cloud services, update devices to the latest supported version of Windows 10, and join devices to Azure Active Directory (Azure AD), all in one central location.</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="baef2-145">**실행**</span><span class="sxs-lookup"><span data-stu-id="baef2-145">**Run:**</span></span> | [<span data-ttu-id="baef2-146">Microsoft 365 배포 관리자</span><span class="sxs-lookup"><span data-stu-id="baef2-146">Microsoft 365 deployment advisor</span></span>](https://aka.ms/microsoft365setupguide) |
|||

### <a name="remote-work-setup-guide"></a><span data-ttu-id="baef2-147">원격 작업 설정 가이드</span><span class="sxs-lookup"><span data-stu-id="baef2-147">Remote work setup guide</span></span>

<span data-ttu-id="baef2-148">**원격 작업 설정 가이드** 에서는 사용자가 원격으로 작업을 수행 하 고, 데이터가 안전 하며, 사용자의 자격 증명을 safeguarded 수 있도록 하는 데 필요한 팁과 리소스가 조직에 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-148">The **Remote work setup guide** provides organizations with the tips and resources needed to ensure your users can successfully work remotely, your data is secure, and users' credentials are safeguarded.</span></span> <span data-ttu-id="baef2-149">조직의 네트워크에 대 한 원격 작업자의 장치 연결을 최적화 하기 위한 지침을 받을 수 있으며,이를 통해 VPN 인프라에 대 한 부담을 절감할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-149">You'll receive guidance to optimize remote workers' device connection to your organization's network, which will reduce the strain on your VPN infrastructure.</span></span> 

|||
|:-------|:-----|
| <span data-ttu-id="baef2-150">**실행**</span><span class="sxs-lookup"><span data-stu-id="baef2-150">**Run:**</span></span> | [<span data-ttu-id="baef2-151">원격 작업 설정 가이드</span><span class="sxs-lookup"><span data-stu-id="baef2-151">Remote work setup guide</span></span>](https://aka.ms/remoteworksetup) |
|||

## <a name="guides-for-security"></a><span data-ttu-id="baef2-152">보안 가이드</span><span class="sxs-lookup"><span data-stu-id="baef2-152">Guides for security</span></span>

### <a name="azure-ad-setup-guide"></a><span data-ttu-id="baef2-153">Azure AD 설정 가이드</span><span class="sxs-lookup"><span data-stu-id="baef2-153">Azure AD setup guide</span></span>

<span data-ttu-id="baef2-154">**AZURE AD 설정 가이드** 에서는 조직에 강력한 보안 파운데이션이 있는지 확인 하는 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-154">The **Azure AD setup guide** provides information to ensure your org has a strong security foundation.</span></span> <span data-ttu-id="baef2-155">이 가이드에서는 관리자를 위한 azure AD (역할 기반 액세스 제어), Azure FS (온-프레미스 디렉터리에 연결) 및 Azure AD Connect Health와 같은 초기 기능을 설정 하 여 자동화 된 동기화 중에 하이브리드 id의 상태를 모니터링할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-155">In this guide you’ll set up initial features, like Azure role-based access control (Azure RBAC) for admins, Azure AD Connect for your on-premises directory, and Azure AD Connect Health, so you can monitor your hybrid identity's health during automated syncs.</span></span> <span data-ttu-id="baef2-156">또한 셀프 서비스 암호 재설정, 조건부 액세스 및 통합 된 타사 로그인 (선택적 고급 ID 보호, 사용자 프로비저닝 자동화 포함)에 대 한 필수 정보도 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-156">It also includes essential information on enabling self-service password resets, conditional access and integrated third-party sign-on including optional advanced ID protection, and user provisioning automation.</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="baef2-157">**실행**</span><span class="sxs-lookup"><span data-stu-id="baef2-157">**Run:**</span></span> | [<span data-ttu-id="baef2-158">Azure AD 설정 가이드</span><span class="sxs-lookup"><span data-stu-id="baef2-158">Azure AD setup guide</span></span>](https://aka.ms/aadpguidance) |
|||

### <a name="microsoft-defender-advanced-threat-protection-atp-advisor"></a><span data-ttu-id="baef2-159">Microsoft Defender ATP (Advanced Threat Protection) advisor</span><span class="sxs-lookup"><span data-stu-id="baef2-159">Microsoft Defender Advanced Threat Protection (ATP) advisor</span></span>

<span data-ttu-id="baef2-160">Microsoft Defender ATP 관리자는 엔터프라이즈 네트워크가 고급 위협에 대해 예방, 감지, 조사 및 대응 하는 데 도움이 되는 지침을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-160">The Microsoft Defender ATP advisor provides instructions that will help your enterprise network prevent, detect, investigate, and respond to advanced threats.</span></span> <span data-ttu-id="baef2-161">조직의 취약성에 대 한 정보를 확인 하 고 가장 적합 한 배포 패키지 및 구성 방법을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-161">Make an informed assessment of your org's vulnerability and decide which deployment package and configuration methods are best.</span></span> 

>[!NOTE]
><span data-ttu-id="baef2-162">Microsoft Volume License가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-162">A Microsoft Volume License is required for Microsoft Defender ATP.</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="baef2-163">**실행**</span><span class="sxs-lookup"><span data-stu-id="baef2-163">**Run:**</span></span> | [<span data-ttu-id="baef2-164">Microsoft Defender Advanced Threat Protection advisor</span><span class="sxs-lookup"><span data-stu-id="baef2-164">Microsoft Defender Advanced Threat Protection advisor</span></span>](https://aka.ms/mdatpsetup) |
|||

### <a name="exchange-online-protection-setup-guide"></a><span data-ttu-id="baef2-165">Exchange Online Protection 설정 가이드</span><span class="sxs-lookup"><span data-stu-id="baef2-165">Exchange Online Protection setup guide</span></span>

<span data-ttu-id="baef2-166">Microsoft EOP (Exchange Online Protection)는 메시징 정책 위반 으로부터 조직을 보호 하는 기능을 사용 하 여 스팸 및 맬웨어에 대 한 보호를 위한 클라우드 기반 전자 메일 필터링 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-166">Microsoft Exchange Online Protection (EOP) is a cloud-based email filtering service for protection against spam and malware, with features to safeguard your organization from messaging policy violations.</span></span> <span data-ttu-id="baef2-167">이 가이드에서는 세 가지 배포 시나리오에서 온- &mdash; 프레미스 사서함, 하이브리드 (온-프레미스 및 클라우드) 사서함 또는 모든 클라우드 사서함이 &mdash; 조직에 적합 한지 여부를 선택 하 여 EOP를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-167">With this guide you'll set up EOP by selecting which of the three deployment scenarios&mdash;on-premises mailboxes, hybrid (mix of on-premises and cloud) mailboxes, or all cloud mailboxes&mdash;fits your organization.</span></span> <span data-ttu-id="baef2-168">이 가이드에서는 사용자의 라이선스를 설정 및 검토 하 고, Microsoft 365 관리 센터에서 사용 권한을 할당 하 고, 보안 & 준수 센터에서 조직의 맬웨어 방지 및 스팸 정책을 구성할 수 있는 정보와 리소스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-168">The guide provides information and resources to set up and review your user's licensing, assign permissions in the Microsoft 365 admin center, and configure your organization's anti-malware and spam policies in the Security & Compliance Center.</span></span> 

|||
|:-------|:-----|
| <span data-ttu-id="baef2-169">**실행**</span><span class="sxs-lookup"><span data-stu-id="baef2-169">**Run:**</span></span> | [<span data-ttu-id="baef2-170">Exchange Online Protection 설정 가이드</span><span class="sxs-lookup"><span data-stu-id="baef2-170">Exchange Online Protection setup guide</span></span>](https://aka.ms/EOPguidance) |
|||

### <a name="office-365-advanced-threat-protection-advisor"></a><span data-ttu-id="baef2-171">Office 365 Advanced Threat Protection advisor</span><span class="sxs-lookup"><span data-stu-id="baef2-171">Office 365 Advanced Threat Protection advisor</span></span>

<span data-ttu-id="baef2-172">Office 365 Advanced Threat Protection advisor는 환경에서 전자 메일 메시지, 링크 및 타사 공동 작업 도구를 통해 발생할 수 있는 악의적인 위협 으로부터 조직을 보호 합니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-172">The Office 365 Advanced Threat Protection advisor safeguards your organization against malicious threats that your environment might encounter through email messages, links, and third-party collaboration tools.</span></span> <span data-ttu-id="baef2-173">이 가이드에서는 조직의 요구에 맞게 advanced threat protection 계획을 준비 하 고 식별 하는 데 도움이 되는 리소스와 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-173">This guide provides you with the resources and information to help you prepare and identify the advanced threat protection plan to fit your organization's needs.</span></span> 

|||
|:-------|:-----|
| <span data-ttu-id="baef2-174">**실행**</span><span class="sxs-lookup"><span data-stu-id="baef2-174">**Run:**</span></span> | [<span data-ttu-id="baef2-175">Office 365 Advanced Threat Protection advisor</span><span class="sxs-lookup"><span data-stu-id="baef2-175">Office 365 Advanced Threat Protection advisor</span></span>](https://aka.ms/oatpsetup) |
|||

### <a name="active-directory-federation-services-ad-fs-deployment-advisor"></a><span data-ttu-id="baef2-176">AD FS (Active Directory Federation Services) 배포 관리자</span><span class="sxs-lookup"><span data-stu-id="baef2-176">Active Directory Federation Services (AD FS) deployment advisor</span></span>

<span data-ttu-id="baef2-177">**AD FS 배포 관리자** 는 Microsoft 365 및 Office 365 서비스용 사용자를 인증 하는 온-프레미스 AD FS 인프라를 배포 하는 방법에 대 한 단계별 지침을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-177">The **AD FS deployment advisor** provides you with step-by-step guidance on deploying an on-premises AD FS infrastructure that authenticates users for Microsoft 365 and Office 365 services.</span></span> <span data-ttu-id="baef2-178">이 가이드를 사용 하 여 조직에서 AD FS 구성 요소와 요구 사항을 검토 하 고, 배포에 필요한 SSL 인증서를 취득 및 설치 하 고, 필요한 웹 응용 프로그램 프록시 서버를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-178">With this guide your org can review AD FS components and requirements, acquire and install SSL certificates that are necessary for deployment, and install a required web application proxy server.</span></span> 

|||
|:-------|:-----|
| <span data-ttu-id="baef2-179">**실행**</span><span class="sxs-lookup"><span data-stu-id="baef2-179">**Run:**</span></span> | [<span data-ttu-id="baef2-180">AD FS 배포 관리자</span><span class="sxs-lookup"><span data-stu-id="baef2-180">AD FS deployment advisor</span></span>](https://aka.ms/adfsguidance) |
|||

## <a name="guides-for-collaboration"></a><span data-ttu-id="baef2-181">공동 작업용 가이드</span><span class="sxs-lookup"><span data-stu-id="baef2-181">Guides for collaboration</span></span>

### <a name="microsoft-365-apps-for-enterprise-deployment-advisor"></a><span data-ttu-id="baef2-182">엔터프라이즈 배포 관리자를 위한 Microsoft 365 앱</span><span class="sxs-lookup"><span data-stu-id="baef2-182">Microsoft 365 Apps for enterprise deployment advisor</span></span>

<span data-ttu-id="baef2-183">**Microsoft 365 Apps for enterprise 배포 관리자** 는 Word, Excel, PowerPoint 및 OneNote와 같은 최신 버전의 Office 제품을 실행 하는 사용자의 장치를 제공 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-183">The **Microsoft 365 Apps for enterprise deployment advisor** helps you get your users' devices running the latest version of Office products like Word, Excel, PowerPoint, and OneNote.</span></span> <span data-ttu-id="baef2-184">관리 도구를 사용 하 여 엔터프라이즈 배포에 간편 하 게 설치할 수 있는 옵션이 포함 된 다양 한 배포 방법에 대 한 지침을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-184">You'll get guidance on the various deployment methods that include easy self-install options to enterprise deployments with management tools.</span></span> <span data-ttu-id="baef2-185">지침은 환경을 평가 하 고, 특정 배포 요구 사항을 파악 하 고, 필요한 지원 도구를 구현 하 여 성공적인 설치를 보장 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-185">The instructions will help you assess your environment, figure out your specific deployment requirements, and implement the necessary support tools to ensure a successful install.</span></span> 

|||
|:-------|:-----|
| <span data-ttu-id="baef2-186">**실행**</span><span class="sxs-lookup"><span data-stu-id="baef2-186">**Run:**</span></span> | [<span data-ttu-id="baef2-187">Microsoft 365 Apps 배포 관리자</span><span class="sxs-lookup"><span data-stu-id="baef2-187">Microsoft 365 Apps deployment advisor</span></span>](https://aka.ms/OPPquickstartguide) |
|||

### <a name="mobile-apps-setup-assistant"></a><span data-ttu-id="baef2-188">모바일 앱 설정 도우미</span><span class="sxs-lookup"><span data-stu-id="baef2-188">Mobile apps setup assistant</span></span>

<span data-ttu-id="baef2-189">이 설정 도우미는 Windows, iOS 및 Android 모바일 장치에 Office 앱을 다운로드 하 고 설치 하기 위한 지침을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-189">This setup assistant provides instructions for the download and installation of Office apps on your Windows, iOS, and Android mobile devices.</span></span> <span data-ttu-id="baef2-190">이 가이드에서는 휴대폰 및 태블릿 장치에 Microsoft 365 및 Office 365 앱을 다운로드 하 고 설치 하는 단계별 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-190">This guide provides you with step-by-step information to download and install Microsoft 365 and Office 365 apps on your phone and tablet devices.</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="baef2-191">**실행**</span><span class="sxs-lookup"><span data-stu-id="baef2-191">**Run:**</span></span> | [<span data-ttu-id="baef2-192">모바일 앱 설정 도우미</span><span class="sxs-lookup"><span data-stu-id="baef2-192">Mobile apps setup assistant</span></span>](https://aka.ms/officeappguidance) |
|||

### <a name="microsoft-teams-setup-guide"></a><span data-ttu-id="baef2-193">Microsoft 팀 설정 가이드</span><span class="sxs-lookup"><span data-stu-id="baef2-193">Microsoft Teams setup guide</span></span>

<span data-ttu-id="baef2-194">**Microsoft 팀 설정 가이드** 에서는 조직에서 팀과 개인 통신에 대 한 메시징, 통화, 오디오 또는 비디오 회의를 통해 실시간 대화를 호스트 하는 팀 작업 영역을 설정할 수 있는 지침을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-194">The **Microsoft Teams setup guide** provides your organization with guidance to set up team workspaces that host real-time conversations through messaging, calls, and audio or video meetings for both team and private communication.</span></span> <span data-ttu-id="baef2-195">팀 관리 센터 내에서 Network Planner 도구 및 팀 관리자를 사용 하 여 조직의 네트워크 요구 사항을 확인 하기 위한 지침을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-195">You'll receive the instructions for determining your organization's network requirements by using the Network Planner tool and the Teams advisor within the Teams admin center.</span></span> <span data-ttu-id="baef2-196">배포가 완료 되 면 팀을 사용 하 여 시작 하기 위한 유용한 리소스가 가이드에 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-196">Once your deployment is complete, the guide includes helpful resources to get started using Teams.</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="baef2-197">**실행**</span><span class="sxs-lookup"><span data-stu-id="baef2-197">**Run:**</span></span> | [<span data-ttu-id="baef2-198">Microsoft 팀 설정 가이드</span><span class="sxs-lookup"><span data-stu-id="baef2-198">Microsoft Teams setup guide</span></span>](https://aka.ms/teamsguidance) |
|||

### <a name="sharepoint-deployment-advisor"></a><span data-ttu-id="baef2-199">SharePoint 배포 관리자</span><span class="sxs-lookup"><span data-stu-id="baef2-199">SharePoint deployment advisor</span></span>

<span data-ttu-id="baef2-200">**Sharepoint 배포 관리자** 는 sharepoint 문서 저장 및 콘텐츠 관리를 설정 하 고, 사이트를 만들고, 외부 공유를 구성 하 고, 데이터를 마이그레이션하고, 고급 설정을 구성 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-200">The **SharePoint deployment advisor** helps you set up your SharePoint document storage and content management, create sites, configure external sharing, migrate data and configure advanced settings, all to drive user engagement and communication within your organization.</span></span> <span data-ttu-id="baef2-201">콘텐츠 공유 권한 정책을 구성 하는 단계를 따르고, 마이그레이션 동기화 도구를 선택 하 고, SharePoint 환경에 대 한 보안 설정을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-201">You'll follow steps for configuring your content-sharing permission policies, choose your migration sync tools, as well as enable the security settings for your SharePoint environment.</span></span> 

|||
|:-------|:-----|
| <span data-ttu-id="baef2-202">**실행**</span><span class="sxs-lookup"><span data-stu-id="baef2-202">**Run:**</span></span> | [<span data-ttu-id="baef2-203">SharePoint 배포 관리자</span><span class="sxs-lookup"><span data-stu-id="baef2-203">SharePoint deployment advisor</span></span>](https://aka.ms/spoguidance) |
|||

### <a name="onedrive-quick-start-guide"></a><span data-ttu-id="baef2-204">OneDrive 빠른 시작 가이드</span><span class="sxs-lookup"><span data-stu-id="baef2-204">OneDrive quick start guide</span></span>

<span data-ttu-id="baef2-205">이 가이드를 사용 하 여 OneDrive 파일 저장, 공유, 공동 작업 및 동기화 기능을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-205">Use this guide to get started with OneDrive file storage, sharing, collaboration, and syncing capabilities.</span></span> <span data-ttu-id="baef2-206">OneDrive에서는 사용자가 Microsoft 365 앱 파일을 동기화 하 고, 외부 공유를 구성 하 고, 사용자 데이터를 마이그레이션하고, 고급 보안 및 장치 액세스 설정을 구성할 수 있는 중앙 위치를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-206">OneDrive provides a central location where users can sync their Microsoft 365 Apps files, configure external sharing, migrate user data, and configure advanced security and device access settings.</span></span> <span data-ttu-id="baef2-207">Onedrive 설정 가이드는 OneDrive 구독 또는 독립 실행형 OneDrive 계획을 사용 하 여 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-207">The OneDrive setup guide can be deployed using a OneDrive subscription or a standalone OneDrive plan.</span></span> 

|||
|:-------|:-----|
| <span data-ttu-id="baef2-208">**실행**</span><span class="sxs-lookup"><span data-stu-id="baef2-208">**Run:**</span></span> | [<span data-ttu-id="baef2-209">OneDrive 설정 가이드</span><span class="sxs-lookup"><span data-stu-id="baef2-209">OneDrive setup guide</span></span>](https://aka.ms/ODfBquickstartguide) |
|||

## <a name="advanced-wizards"></a><span data-ttu-id="baef2-210">고급 마법사</span><span class="sxs-lookup"><span data-stu-id="baef2-210">Advanced wizards</span></span>

### <a name="in-place-upgrade-with-configuration-manager"></a><span data-ttu-id="baef2-211">구성 관리자를 사용한 전체 업그레이드</span><span class="sxs-lookup"><span data-stu-id="baef2-211">In-place upgrade with Configuration Manager</span></span>

<span data-ttu-id="baef2-212">Windows 7 및 Windows 8.1 장치를 최신 버전의 Windows 10으로 업그레이드 하는 경우 **Configuration Manager를** 사용 하 여 전체 업그레이드 가이드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-212">Use the **In-place upgrade with Configuration Manager** guide when upgrading Windows 7 and Windows 8.1 devices to the latest version of Windows 10.</span></span> <span data-ttu-id="baef2-213">제공 된 스크립트를 사용 하 여 필수 구성 요소를 확인 하 고 전체 업그레이드를 자동으로 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-213">You'll use the script provided to check the prerequisites and automatically configure an in-place upgrade.</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="baef2-214">**실행**</span><span class="sxs-lookup"><span data-stu-id="baef2-214">**Run:**</span></span> | [<span data-ttu-id="baef2-215">구성 관리자를 사용한 전체 업그레이드</span><span class="sxs-lookup"><span data-stu-id="baef2-215">In-place upgrade with Configuration Manager</span></span>](https://aka.ms/win10upgradedemo) |
|||

### <a name="deploy-office-to-your-users"></a><span data-ttu-id="baef2-216">사용자에 게 Office 배포</span><span class="sxs-lookup"><span data-stu-id="baef2-216">Deploy Office to your users</span></span>

<span data-ttu-id="baef2-217">Office 배포 도구를 사용 하 여 설치를 사용자 지정 하는 기능을 사용 하 여 클라우드에서 Office 앱을 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-217">Deploy Office apps from the cloud with the ability to customize your installation by using the Office Deployment Tool.</span></span> <span data-ttu-id="baef2-218">이 가이드는 고급 설정을 사용 하 여 사용자 지정 된 Office 구성을 만들거나 미리 작성 된 권장 구성을 사용할 수 있도록 도와줍니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-218">This guide helps you create a customized Office configuration with advanced settings, or you can use a pre-built recommended configuration.</span></span> <span data-ttu-id="baef2-219">사용자가 자동 설치를 수행 하 고 있거나 사용자에 게 개별적으로 또는 대량으로 배포 하 고 있는지 여부에 관계 없이이 고급 마법사는 사용자에 게 조직에 맞게 구성 된 Office 설치를 제공 하는 단계별 지침을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-219">Whether your users are conducting a self-install or you're deploying to your users individually or in bulk, this advanced wizard provides you with step-by-step instructions to give users an Office installation tailored to your organization.</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="baef2-220">**실행**</span><span class="sxs-lookup"><span data-stu-id="baef2-220">**Run:**</span></span> | [<span data-ttu-id="baef2-221">사용자에 게 Office 배포</span><span class="sxs-lookup"><span data-stu-id="baef2-221">Deploy Office to your users</span></span>](https://aka.ms/proplusodt) |
|||

### <a name="deploy-and-update-microsoft-365-apps-with-configuration-manager"></a><span data-ttu-id="baef2-222">Configuration Manager를 사용 하 여 Microsoft 365 앱 배포 및 업데이트</span><span class="sxs-lookup"><span data-stu-id="baef2-222">Deploy and update Microsoft 365 Apps with Configuration Manager</span></span>

<span data-ttu-id="baef2-223">Configuration Manager를 사용 하는 조직의 경우이 가이드를 사용 하 여 FastTrack 엔지니어가 권장 하는 모범 사례를 사용 하 여 Microsoft 365 앱 배포를 자동으로 구성 하는 스크립트를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-223">For organizations using Configuration Manager, you can use this guide to generate a script that will automatically configure your Microsoft 365 Apps deployment using best practices recommended by FastTrack engineers.</span></span> <span data-ttu-id="baef2-224">이 가이드를 사용 하 여 배포 그룹을 작성 하 고, Office 앱 및 기능을 사용자 지정 하 고, 동적 또는 간결한 설치를 구성한 다음 스크립트를 실행 하 여 배포를 대상으로 하는 데 필요한 응용 프로그램, 자동 배포 규칙 및 장치 모음을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="baef2-224">Use this guide to build your deployment groups, customize your Office apps and features, configure dynamic or lean installations, and then run the script to create the applications, automatic deployment rules, and device collections you need to target your deployment.</span></span> 

|||
|:-------|:-----|
| <span data-ttu-id="baef2-225">**실행**</span><span class="sxs-lookup"><span data-stu-id="baef2-225">**Run:**</span></span> | [<span data-ttu-id="baef2-226">Configuration Manager를 사용 하 여 Microsoft 365 앱 배포 및 업데이트</span><span class="sxs-lookup"><span data-stu-id="baef2-226">Deploy and update Microsoft 365 Apps with Configuration Manager</span></span>](https://aka.ms/oppinstall) |
|||

