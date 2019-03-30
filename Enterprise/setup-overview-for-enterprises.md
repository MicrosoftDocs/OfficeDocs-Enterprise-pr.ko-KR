---
title: 조직을 위해 Office 365 Enterprise 배포
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- M365-subscription-management
ms.custom: Adm_O365
ms.assetid: ee73dafb-be54-492e-bcfd-0fbfb5f65e94
description: 다음 개요 단계는 Office 365를 배포하고 Active Directory를 연결하며 데이터를 마이그레이션하고 조직의 사용자가 최신 버전의 Office 2016 사용을 시작할 수 있도록 설계되었습니다.
ms.openlocfilehash: a49d57978faabfac7131db3178cbff02b500667f
ms.sourcegitcommit: 0c775dbd2325f95e3f006424d1446f76caadb588
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/30/2019
ms.locfileid: "31004409"
---
# <a name="deploy-office-365-enterprise-for-your-organization"></a><span data-ttu-id="b3887-103">조직을 위해 Office 365 Enterprise 배포</span><span class="sxs-lookup"><span data-stu-id="b3887-103">Deploy Office 365 Enterprise for your organization</span></span>
<span data-ttu-id="b3887-p101">온 - 프레미스 인프라와 함께 Office 365 Enterprise를 배포하고 통합할 준비가 되셨나요? 다음 개요 단계는 디렉토리를 연결하며 데이터를 마이그레이션하고 조직의 사용자가 최신 버전의 Office 2016 사용을 시작할 수 있도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b3887-p101">Ready to deploy and integrate Office 365 Enterprise with your on-premises infrastructure? These overview steps are designed to help you connect your directory, migrate your data, and help the people in your organization begin using the latest version of Office 2016.</span></span>
  
<span data-ttu-id="b3887-106">이 단계는 Office 365 Enterprise의 사용자 지정 배포를 시작하려는 비즈니스 및 [비영리 기관](https://go.microsoft.com/fwlink/?LinkId=627221)을 위한 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="b3887-106">These steps are for businesses and [nonprofits](https://go.microsoft.com/fwlink/?LinkId=627221) that want to start with a custom deployment of Office 365 Enterprise.</span></span> 
  
<span data-ttu-id="b3887-p102">Office 365 Enterprise가 없습니까? 중소기업을 위한 지침은 [비즈니스 용 Office 365 설정](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b3887-p102">Don't have Office 365 Enterprise? See [Set up Office 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) for instructions for small businesses.</span></span> 
  
## <a name="guided-enterprise-office-365-setup-process-with-fasttrack"></a><span data-ttu-id="b3887-109">FastTrack을 사용한 기업용 Office 365 설치 프로세스</span><span class="sxs-lookup"><span data-stu-id="b3887-109">Guided enterprise Office 365 setup process with FastTrack</span></span>
<span data-ttu-id="b3887-p103">Office 365 **[FastTrack](https://docs.microsoft.com/fasttrack)** 은 Office 365를 배포하는 가장 좋은 방법입니다. FastTrack은 가장 일반적인 배포 구성을 안내하고 단계별로 질문에 답변할 수 있습니다. 파트너로부터 자가 진단 또는 지침을 원하는 경우 [Office 365 설치 가이드](https://support.office.com/article/Set-up-Office-365-for-business-6a3a29a0-e616-4713-99d1-15eda62d04fa), [Office 365 설치 마법사](https://aka.ms/o365fasttrack) 또는 [공식 파트너를 찾으십시오](https://partnercenter.microsoft.com/ko-KR/pcv/search).</span><span class="sxs-lookup"><span data-stu-id="b3887-p103">Office 365 **[FastTrack](https://docs.microsoft.com/fasttrack)** is the best method for deploying Office 365. FastTrack guides you through the most common deployment configurations and can answer questions along the way. If you want to self-help or guidance from a partner, use our [Office 365 setup guide](https://support.office.com/article/Set-up-Office-365-for-business-6a3a29a0-e616-4713-99d1-15eda62d04fa), our [Office 365 setup wizards](https://aka.ms/o365fasttrack), or [find a qualified partner](https://partnercenter.microsoft.com/ko-KR/pcv/search).</span></span>

## <a name="self-deployment-of-office-365"></a><span data-ttu-id="b3887-113">Office 365의 자체 배포</span><span class="sxs-lookup"><span data-stu-id="b3887-113">Self-deployment of Office 365</span></span>
<span data-ttu-id="b3887-114">직접 Office 365를 배포하려는 경우 다음 배포 단계가 도움을 드립니다.</span><span class="sxs-lookup"><span data-stu-id="b3887-114">If you want to deploy Office 365 on your own, the following deployment steps are here to help.</span></span>

1. <span data-ttu-id="b3887-p104">**[Office 365를 준비합니다](get-your-organization-ready-for-office-365.md)**. 이러한 도구와 리소스를 통해 네트워크, 디렉터리 및 최종 사용자가 Office 365를 이용할 준비를 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3887-p104">**[Get ready for Office 365](get-your-organization-ready-for-office-365.md)**. These tools and resources will help you get your network, directory, and end users ready for Office 365.</span></span>

2. <span data-ttu-id="b3887-p105">**[로그인하고 인터넷 도메인을 Office 365에 추가합니다](https://portal.office.com/Domains/AddDomainWizard.aspx?Scenario=AdvancedSetup)**. 포털에 로그인하고 사용자 추가하거나 전자 메일을 마이그레이션하지 않고 Office 365 구독에 하나 이상의 도메인을 추가합니다. 모든 사용자와 서비스를 동시에 구성하려면 [기본 설정 지침](https://support.office.com/article/Set-up-Office-365-for-business-6a3a29a0-e616-4713-99d1-15eda62d04fa)을 따르십시오.</span><span class="sxs-lookup"><span data-stu-id="b3887-p105">**[Sign in and add your internet domain(s) to Office 365](https://portal.office.com/Domains/AddDomainWizard.aspx?Scenario=AdvancedSetup)**. Sign into the portal and add one or more domains to your Office 365 subscription without adding users or migrating email. If you want to configure all your users and services at the same time, follow our [basic set up instructions](https://support.office.com/article/Set-up-Office-365-for-business-6a3a29a0-e616-4713-99d1-15eda62d04fa).</span></span>

>[!IMPORTANT] 
><span data-ttu-id="b3887-120">온-프레미스 디렉토리에서 사용자를 동기화하거나 Single Sign-On을 사용하려는 경우 기본 설치 지침이 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b3887-120">The basic set up instructions won't work if you want to synchronize your users from an on-premises directory or utilize Single Sign-On.</span></span>

3. <span data-ttu-id="b3887-p106">**[디렉터리를 Office 365에 연결합니다](https://support.office.com/article/Understanding-Office-365-Identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9)**. ID 동기화 및/또는 Single Sign-On 구성 옵션을 안내합니다. 사용자 지정된 설정 지침을 확인하려면 [AAD Connect 관리자](https://aka.ms/aadconnectpwsync) 및 [Azure AD Premium 설정 가이드](https://aka.ms/aadpguidance)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b3887-p106">**[Connect your directory to Office 365](https://support.office.com/article/Understanding-Office-365-Identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9)**. Guide to the identity synchronization and/or single sign-on configuration options. Use the [AAD Connect advisor](https://aka.ms/aadconnectpwsync) and the [Azure AD Premium setup guide](https://aka.ms/aadpguidance) to get customized set up guidance.</span></span>
4. <span data-ttu-id="b3887-p107">**[Office 365 서비스 및 응용 프로그램을 구성합니다](configure-services-and-applications.md)**. 전자 메일, 파일 공유, 인스턴트 메시징 또는 다른 Office 365 서비스 및 응용 프로그램 중 하나를 구성하려면 여기에서 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="b3887-p107">**[Configure Office 365 services and applications](configure-services-and-applications.md)**. Start here to configure email, file sharing, instant messaging, or any of the other Office 365 services and applications.</span></span>
5. <span data-ttu-id="b3887-p108">**[데이터를 Office 365로 마이그레이션합니다](migrate-data-to-office-365.md)**. 서비스가 구성되면 데이터 마이그레이션을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3887-p108">**[Migrate data to Office 365](migrate-data-to-office-365.md)**. Once the services are configured, you can start migrating data.</span></span>
6. <span data-ttu-id="b3887-p109">**[사용자가 Office 365를 사용하도록 합니다](https://support.office.com/article/Get-started-with-Office-365-for-business-d6466f0d-5d13-464a-adcb-00906ae87029)**. 조직의 사용자가 Office 365와 리소스를 사용하는 데 자신감을 갖도록 돕습니다.</span><span class="sxs-lookup"><span data-stu-id="b3887-p109">**[Get people using Office 365](https://support.office.com/article/Get-started-with-Office-365-for-business-d6466f0d-5d13-464a-adcb-00906ae87029)**. Help people in your organization build confidence using Office 365 with these resources.</span></span>