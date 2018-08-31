---
title: Office 365 관리 센터에서 Azure 권한 관리 활성화
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 5/11/2016
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 5b6d3ac7-b1ac-428e-b03e-50e882f85a6e
description: 정품 인증 및 권한 관리 서비스를 사용 하 여 Office 365를 사용 하는 방법을 설명 하는 항목을 가리킵니다.
ms.openlocfilehash: b3df1f7ff39214d5ab7ab8f5c730299c1c22f30b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541931"
---
# <a name="activate-rights-management-in-the-office-365-admin-center"></a><span data-ttu-id="7a652-103">Office 365 관리 센터에서 Azure 권한 관리 활성화</span><span class="sxs-lookup"><span data-stu-id="7a652-103">Activate Rights Management in the Office 365 admin center</span></span>

<span data-ttu-id="7a652-104">이 항목을 설정 하 고 RMS를 사용 하 여 Office 365를 사용 하는 방법을 설명 하는 항목을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="7a652-104">This topic points to topics that describe how to enable and use RMS with Office 365.</span></span>
  
<span data-ttu-id="7a652-p101">Office 365 응용 프로그램의 정보 권한 관리 (IRM) 기능을 사용할 수 있습니다 (RMS) 권한 관리 서비스 및 서비스를 활성화 해야 합니다. RMS를 활성화 하면 조직 Azure RMS를 사용 하 여 중요 한 문서 및 전자 메일을 보호 하기 위해 시작할 수 있습니다. 이 정보 보호 솔루션 모든 파일의 형식의 보호할 수 및 Excel, Microsoft Word 및 다른 사용자를 Exchange Online 및 SharePoint Online과 같은 클라이언트 응용 프로그램을 통합 하 고 Microsoft Exchange 및 Microsoft SharePoint와 같은 서버입니다.</span><span class="sxs-lookup"><span data-stu-id="7a652-p101">You must activate the Rights Management service (RMS) before you can use the Information Rights Management (IRM) features of Office 365 applications and services. After you activate RMS, your organization can start to protect important documents and emails by using Azure RMS. This information protection solution can protect all file types and integrates with client applications like Excel, Microsoft Word, and others, Exchange Online and SharePoint Online, and servers such as Microsoft Exchange and Microsoft SharePoint.</span></span>
  
> [!TIP]
> <span data-ttu-id="7a652-108">권한 관리 해야 하는지 여부 확실 하지 않은 경우 [이러한 비즈니스 문제 또는 요구 사항](https://docs.microsoft.com/rights-management/understand-explore/azure-rms-problems-it-solves), 하나 이상의 조직에 있는지 여부를 확인 하 고 일부 [작업의 권한 관리의 예](https://docs.microsoft.com/rights-management/understand-explore/what-admins-users-see)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="7a652-108">If you're not sure whether you need Rights Management, check whether your organization has one or more of [these business problems or requirements](https://docs.microsoft.com/rights-management/understand-explore/azure-rms-problems-it-solves), and see some [examples of Rights Management in action](https://docs.microsoft.com/rights-management/understand-explore/what-admins-users-see).</span></span> 
  
<span data-ttu-id="7a652-109">다음이 링크를 사용 하 여 RMS에 대 한 자세한 내용은:</span><span class="sxs-lookup"><span data-stu-id="7a652-109">Use these links for more information on RMS:</span></span>
  
- <span data-ttu-id="7a652-110">RMS에 대 한 자세한 내용은, [Azure 권한 관리](https://docs.microsoft.com/rights-management/understand-explore/what-is-azure-rms)를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a652-110">To learn more about RMS, see [What is Azure Rights Management](https://docs.microsoft.com/rights-management/understand-explore/what-is-azure-rms).</span></span>
    
- <span data-ttu-id="7a652-111">RMS의 새로운 기능 인 경우 [Azure 권한 관리 개요를](https://docs.microsoft.com/rights-management/understand-explore/azure-rights-management)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="7a652-111">If you're new to RMS, see [Overview of Azure Rights Management](https://docs.microsoft.com/rights-management/understand-explore/azure-rights-management).</span></span>
    
- <span data-ttu-id="7a652-112">배포 단계에 대 한 개요 [Azure 권한 관리 배포 안내서](https://docs.microsoft.com/rights-management/plan-design/deployment-roadmap)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="7a652-112">For an overview of the deployment steps see the [Azure Rights Management deployment roadmap](https://docs.microsoft.com/rights-management/plan-design/deployment-roadmap).</span></span>
    
- <span data-ttu-id="7a652-113">Office 365에 대 한 RMS를 활성화 하는 방법에 대 한 자세한 내용은 [Azure 권한 관리 활성화](https://technet.microsoft.com/library/jj658941.aspx)합니다.</span><span class="sxs-lookup"><span data-stu-id="7a652-113">For instructions about activating RMS for Office 365, see [Activating Azure Rights Management](https://technet.microsoft.com/library/jj658941.aspx).</span></span>
    
- <span data-ttu-id="7a652-p102">Office에서 Azure RMS와 IRM의 차이점에 대 한 자세한 내용은? 다른 권한 관리 용어에 대 한 지원 여부 [권한 관리에 대 한 용어](https://technet.microsoft.com/library/dn595132.aspx)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="7a652-p102">Confused about the difference between Azure RMS and IRM in Office? Want help with other Rights Management terms? See [Terminology for Rights Management](https://technet.microsoft.com/library/dn595132.aspx).</span></span>
    

