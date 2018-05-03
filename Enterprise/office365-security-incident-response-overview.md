---
title: Office 365 보안 문제 대응
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 04/27/2018
ms.audience: ITPro
ms.topic: overview
ms.collection:
- o365_security_incident_response
- Strat_O365_IP
ms.service: o365-solutions
localization_priority: Normal
ms.custom: ''
ms.assetid: ''
description: 이 솔루션 수 있는 가장 일반적인 인터넷-보안 공격 아래와 같습니다 Office 365 및 자신에 게 응답 하는 방법에 알려줍니다.
ms.openlocfilehash: b9800070bde662603c731e2b8d64609b4f821cce
ms.sourcegitcommit: a4322cac992ce64b92f0335bf005a7420195d9be
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="office-365-security-incident-response"></a><span data-ttu-id="9bca4-103">Office 365 보안 문제 대응</span><span class="sxs-lookup"><span data-stu-id="9bca4-103">Office 365 Security Incident Response</span></span>

 <span data-ttu-id="9bca4-104">**요약:** 이 솔루션에는 Office 365의 가장 일반적인 보안 인터넷 공격에 대 한 표시기는, 긍정적인 모든 주어진된 공격을 확인 하는 방법 및 그에 응답 하는 방법을 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bca4-104">**Summary:** This solution tells you what the indicators are for the most common cyber-security attacks in Office 365, how to positively confirm any given attack, and how to respond to it.</span></span>
  
## <a name="overview"></a><span data-ttu-id="9bca4-105">개요</span><span class="sxs-lookup"><span data-stu-id="9bca4-105">Overview</span></span>
<span data-ttu-id="9bca4-p101">일부 인터넷 공격을 막을 수 있습니다. 공격자는 지속적으로 방어 전략의 새로운 약점을 찾고 또는 기존 악용 될 때 됩니다. 보안 문제가 생기면의 기간을 단축 공격을 사용 하면 보다 빠르게 응답할 수 있습니다를 인식 하는 방법을 알면는 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bca4-p101">Not all cyber attacks can be thwarted. Attackers are constantly looking for new weaknesses in your defensive strategy or they are exploiting old ones. Knowing how to recognize an attack allows you to respond to it faster, which shortens the duration of the security incident.</span></span>

<span data-ttu-id="9bca4-p102">이 문서 시리즈 Office 365에서 찾을 수 있습니다는 특정 유형의 공격을 이해할 수 있도록 도와줍니다 및 응답 하기 위해 수행할 수 있는 단계를 제공 합니다. 이해를 빠른 진입점 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bca4-p102">This series of article helps you understand what a particular type of attack might look like in Office 365 and gives you steps you can take to respond. They are quick entry points to understanding:</span></span>
 
- <span data-ttu-id="9bca4-111">어떤 공격 이며 작동 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="9bca4-111">What the attack is and how it works.</span></span>
- <span data-ttu-id="9bca4-112">서명 내용 손상 (IOC)에 대 한 확인 하 고 레코드를 찾거나 하는 방법에 대 한 표시기를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bca4-112">What signs, called indicators of compromise (IOC), to look for and how to look for them.</span></span>
- <span data-ttu-id="9bca4-113">긍정적인 공격을 확인 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="9bca4-113">How to positively confirm the attack.</span></span>
- <span data-ttu-id="9bca4-114">나중에 조직을 보호 하는 공격 해제를 잘라내어 향상 하기 위해 수행할 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="9bca4-114">Steps to take to cut off the attack and better protect your organization in the future.</span></span>
- <span data-ttu-id="9bca4-115">각에 대 한 자세한 정보에 대 한 링크 공격 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="9bca4-115">Links to in-depth information on each attack type.</span></span>

<span data-ttu-id="9bca4-116">페이지를 다시 확인 매월 더 많은 문서 시간에 따른 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bca4-116">Check back here monthly as more articles will be added over time.</span></span>

## <a name="detect-and-remediate-articles"></a><span data-ttu-id="9bca4-117">검색 및 문서를 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bca4-117">Detect and Remediate Articles</span></span>
- [<span data-ttu-id="9bca4-118">검색 및 Office 365의에서 불법 사용자의 동의 부여 수정</span><span class="sxs-lookup"><span data-stu-id="9bca4-118">Detect and Remediate Illicit Consent Grants in Office 365</span></span>](detect-and-remediate-illicit-consent-grants.md)
- [<span data-ttu-id="9bca4-119">검색 및 Outlook 규칙 및 Office 365에서에서 사용자 지정 양식 주입 공격 수정</span><span class="sxs-lookup"><span data-stu-id="9bca4-119">Detect and Remediate Outlook Rules and Custom Forms Injections Attacks in Office 365</span></span>](detect-and-remediate-outlook-rules-forms-attack.md)
 
## <a name="secure-office-365-like-a-cybersecurity-pro"></a><span data-ttu-id="9bca4-120">Office 365 전문가 cybersecurity와 같은 보안</span><span class="sxs-lookup"><span data-stu-id="9bca4-120">Secure Office 365 like a cybersecurity pro</span></span>
<span data-ttu-id="9bca4-p103">Office 365 구독 강력한 데이터 및 사용자를 보호 하기 위해 사용할 수 있는 보안 기능 집합을 함께 제공 됩니다.  사용 하는 [Office 365 보안 로드맵: 처음 30 일, 90 일 동안 및 이외 우선순위 가지 주요](https://support.office.com/en-us/article/Office-365-security-roadmap-Top-priorities-for-the-first-30-days-90-days-and-beyond-28c86a1c-e4dd-4aad-a2a6-c768a21cb352) Microsoft Office 365 테 넌 트를 보호 하기 위한 최상의 방법을 구현 하 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bca4-p103">Your Office 365 subscription comes with a powerful set of security capabilities that you can use to protect your data and your users.  Use the [Office 365 security roadmap: Top priorities for the first 30 days, 90 days, and beyond](https://support.office.com/en-us/article/Office-365-security-roadmap-Top-priorities-for-the-first-30-days-90-days-and-beyond-28c86a1c-e4dd-4aad-a2a6-c768a21cb352) to implement Microsoft recommended best practices for securing your Office 365 tenant.</span></span>
- <span data-ttu-id="9bca4-p104">처음 30 일에서 수행 하는 작업입니다.  낮은 영향 및 영향을 주지는 즉시 이러한 사용자에 게 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bca4-p104">Tasks to accomplish in the first 30 days.  These have immediate affect and are low-impact to your users.</span></span>
- <span data-ttu-id="9bca4-p105">90 일에서을 수행 하는 작업입니다. 계획 및 구현 하지만 보안 환경을 크게 개선 하는 약간 더 많은 시간이 걸릴 이러한</span><span class="sxs-lookup"><span data-stu-id="9bca4-p105">Tasks to accomplish in 90 days. These take a bit more time to plan and implement but greatly improve your security posture</span></span>
- <span data-ttu-id="9bca4-p106">90 일 이상. 이러한 향상 된 첫번째 90 일이 작업의에서 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="9bca4-p106">Beyond 90 days. These enhancements build in your first 90 days work.</span></span>






