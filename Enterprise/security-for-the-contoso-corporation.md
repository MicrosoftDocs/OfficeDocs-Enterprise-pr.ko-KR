---
title: "Contoso Corporation에 대 한 보안"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 8f6f9894-5394-4110-8b0a-b8765028c10b
description: "요약: Contoso이 Microsoft의 클라우드 서비스의 기능을 위해 보안 요구 사항이 매핑되어야 하 고 클라우드 보안 준비에 대 한 경로 결정 하는 방법을 이해 합니다."
ms.openlocfilehash: f7c6667ce96a01771ce4f18339daf4c62173e4d9
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2017
---
# <a name="security-for-the-contoso-corporation"></a><span data-ttu-id="f3cb4-103">Contoso Corporation에 대 한 보안</span><span class="sxs-lookup"><span data-stu-id="f3cb4-103">Security for the Contoso Corporation</span></span>

 <span data-ttu-id="f3cb4-104">**요약:** Contoso이 Microsoft의 클라우드 서비스의 기능을 위해 보안 요구 사항이 매핑되어야 하 고 클라우드 보안 준비에 대 한 경로 결정 하는 방법을 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-104">**Summary:** Understand how Contoso mapped their security requirements to features in Microsoft's cloud offerings and determined a path to cloud security readiness.</span></span>
  
<span data-ttu-id="f3cb4-p101">Contoso는 자신의 정보 보안 및 보호 하는 방법에 대 한 심각한 합니다. 클라우드 포함 한 IT 인프라, 전환할 때가 온-프레미스 보안 요구 사항을 지원 하 고 Microsoft의 클라우드 서비스에서 구현 하는 된 있는지 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-p101">Contoso is serious about their information security and protection. When transitioning their IT infrastructure to a cloud-inclusive one, they made sure that their on-premises security requirements were supported and implemented in Microsoft's cloud offerings.</span></span>
  
## <a name="contosos-security-requirements-in-the-cloud"></a><span data-ttu-id="f3cb4-107">클라우드에서 Contoso의 보안 요구 사항</span><span class="sxs-lookup"><span data-stu-id="f3cb4-107">Contoso's security requirements in the cloud</span></span>

<span data-ttu-id="f3cb4-108">클라우드를 위한 Contoso의 보안 요구 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-108">Here are Contoso's security requirements for the cloud:</span></span>
  
- <span data-ttu-id="f3cb4-109">클라우드 리소스에 대 한 강력한 인증</span><span class="sxs-lookup"><span data-stu-id="f3cb4-109">Strong authentication to cloud resources</span></span>
    
    <span data-ttu-id="f3cb4-110">클라우드 리소스 액세스를 인증 해야 하 고, 활용 하 여 가능한 경우에 다단계 인증 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-110">Cloud resource access must be authenticated and, where possible, leverage multi-factor authentication.</span></span>
    
- <span data-ttu-id="f3cb4-111">인터넷을 통해 트래픽에 대 한 암호화</span><span class="sxs-lookup"><span data-stu-id="f3cb4-111">Encryption for traffic across the Internet</span></span>
    
    <span data-ttu-id="f3cb4-p102">인터넷을 통해 전송 되는 없음 데이터는 일반 텍스트 형식입니다. 항상 HTTPS 연결, IPsec 또는 다른 끝-데이터 암호화 방법을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-p102">No data sent across the Internet is in plain text form. Always use HTTPS connections, IPsec, or other end-to-end data encryption methods.</span></span>
    
- <span data-ttu-id="f3cb4-114">클라우드에서 보관 된 데이터에 대 한 암호화</span><span class="sxs-lookup"><span data-stu-id="f3cb4-114">Encryption for data at rest in the cloud</span></span>
    
    <span data-ttu-id="f3cb4-115">또는 다른 곳에서 클라우드 디스크에 저장 된 모든 데이터를 암호화 된 형식에서 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-115">All data stored on disks or elsewhere in the cloud must be in an encrypted form.</span></span>
    
- <span data-ttu-id="f3cb4-116">최소 권한 액세스에 대 한 Acl</span><span class="sxs-lookup"><span data-stu-id="f3cb4-116">ACLs for least privilege access</span></span>
    
    <span data-ttu-id="f3cb4-117">계정 권한 클라우드에서 리소스 및 작업을 수행 하기 수 있는 항목에 액세스 하려면 최소 권한 지침을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-117">Account permissions to access resources in the cloud and what they are allowed to do must follow least-privilege guidelines.</span></span>
    
## <a name="contosos-data-sensitivity-classification"></a><span data-ttu-id="f3cb4-118">Contoso의 데이터 민감도 분류</span><span class="sxs-lookup"><span data-stu-id="f3cb4-118">Contoso's data sensitivity classification</span></span>

<span data-ttu-id="f3cb4-119">정보를 사용 하 여 Microsoft의 [데이터 분류 도구 키트](https://msdn.microsoft.com/library/hh204743.aspx)에, Contoso 자신의 데이터에 대 한 분석을 수행 하 고 다음 수준을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-119">Using the information in Microsoft's [Data Classification Toolkit](https://msdn.microsoft.com/library/hh204743.aspx), Contoso performed an analysis of their data and determined the following levels.</span></span>
  
|<span data-ttu-id="f3cb4-120">**수준 1: 낮은 비즈니스 가치**</span><span class="sxs-lookup"><span data-stu-id="f3cb4-120">**Level 1: Low business value**</span></span>|<span data-ttu-id="f3cb4-121">**수준 2: 중간 규모 비즈니스 가치**</span><span class="sxs-lookup"><span data-stu-id="f3cb4-121">**Level 2: Medium business value**</span></span>|<span data-ttu-id="f3cb4-122">**수준 3: 높은 비즈니스 가치**</span><span class="sxs-lookup"><span data-stu-id="f3cb4-122">**Level 3: High business value**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="f3cb4-123">데이터를 암호화와 인증 된 사용자만 사용할 수 있는</span><span class="sxs-lookup"><span data-stu-id="f3cb4-123">Data is encrypted and available only to authenticated users</span></span>  <br/> <span data-ttu-id="f3cb4-p103">온-프레미스 및 클라우드 기반 저장소 및 Office 365와 같은 작업에 저장 된 모든 데이터를 제공 합니다. 서비스 및 클라이언트 장치 사이 전송 및 서비스에 상주 하는 동안 데이터가 암호화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-p103">Provided for all data stored on premises and in cloud-based storage and workloads, such as Office 365. Data is encrypted while it resides in the service and in transit between the service and client devices.</span></span>  <br/> <span data-ttu-id="f3cb4-126">수준 1 데이터의 예는 일반적인 비즈니스 통신 (전자 메일) 및 관리, 판매에 대 한 파일 및 작업자를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-126">Examples of Level 1 data are normal business communications (email) and files for administrative, sales, and support workers.</span></span>  <br/> |<span data-ttu-id="f3cb4-127">수준 1을 더한 값 강력한 인증 및 데이터 손실 방지</span><span class="sxs-lookup"><span data-stu-id="f3cb4-127">Level 1 plus strong authentication and data loss protection</span></span>  <br/> <span data-ttu-id="f3cb4-p104">강력한 인증 SMS 유효성 검사 규칙이 다단계 인증을 포함합니다. 데이터 손실 방지를 사용 하면 중요 또는 중요 한 정보는 온-프레미스 네트워크 외부 이동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-p104">Strong authentication includes multi-factor authentication with SMS validation. Data loss prevention ensures that sensitive or critical information does not travel outside the on-premises network.</span></span>  <br/> <span data-ttu-id="f3cb4-130">수준 2 데이터의 예로 재무 및 법적 정보 및 새 제품에 대 한 데이터를 연구 및 개발 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-130">Examples of Level 2 data are financial and legal information and research and development data for new products.</span></span>  <br/> |<span data-ttu-id="f3cb4-131">수준 2와 가장 높은 수준의 암호화, 인증 및 감사</span><span class="sxs-lookup"><span data-stu-id="f3cb4-131">Level 2 plus the highest levels of encryption, authentication, and auditing</span></span>  <br/> <span data-ttu-id="f3cb4-132">가장 높은 수준의 보관 하 고 클라우드, 국가별 규정 준수 데이터에 대 한 암호화 다단계 인증 스마트 카드 및 세분화 된 감사 및 경고와 함께 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-132">The highest levels of encryption for data at rest and in the cloud, compliant with regional regulations, combined with multi-factor authentication with smart cards and granular auditing and alerting.</span></span>  <br/> <span data-ttu-id="f3cb4-133">수준 3 데이터의 예로 고객 및 파트너 개인 식별 정보 및 제품 엔지니어링 사양 독점 제조 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-133">Examples of Level 3 data are customer and partner personally identifiable information and product engineering specifications and proprietary manufacturing techniques.</span></span>  <br/> |
   
## <a name="mapping-microsoft-cloud-offerings-and-features-to-contosos-data-levels"></a><span data-ttu-id="f3cb4-134">Contoso의 데이터 수준을 Microsoft 클라우드 서비스 및 기능에 매핑</span><span class="sxs-lookup"><span data-stu-id="f3cb4-134">Mapping Microsoft cloud offerings and features to Contoso's data levels</span></span>

<span data-ttu-id="f3cb4-135">다음 표에서 Microsoft의 클라우드 서비스에서 Contoso의 데이터 수준 기능에 대 한 매핑이 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-135">The following table shows the mapping of Contoso's data levels to features in Microsoft's cloud offerings:</span></span>
  
||<span data-ttu-id="f3cb4-136">**SaaS**</span><span class="sxs-lookup"><span data-stu-id="f3cb4-136">**SaaS**</span></span>|<span data-ttu-id="f3cb4-137">**Azure PaaS**</span><span class="sxs-lookup"><span data-stu-id="f3cb4-137">**Azure PaaS**</span></span>|<span data-ttu-id="f3cb4-138">**Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="f3cb4-138">**Azure IaaS**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="f3cb4-139">수준 1: 낮은 비즈니스 가치</span><span class="sxs-lookup"><span data-stu-id="f3cb4-139">Level 1: Low business value</span></span>  <br/> | <span data-ttu-id="f3cb4-140">모든 연결에 대 한 HTTPS</span><span class="sxs-lookup"><span data-stu-id="f3cb4-140">HTTPS for all connections</span></span> <br/>  <span data-ttu-id="f3cb4-141">작동 중단 시 암호화</span><span class="sxs-lookup"><span data-stu-id="f3cb4-141">Encryption at rest</span></span> <br/> | <span data-ttu-id="f3cb4-142">HTTPS 연결에만 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-142">Support only HTTPS connections</span></span> <br/>  <span data-ttu-id="f3cb4-143">Azure에 저장 된 파일을 암호화 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-143">Encrypt files stored in Azure</span></span> <br/> | <span data-ttu-id="f3cb4-144">서버 액세스에 대 한 HTTPS 또는 IPsec 필요</span><span class="sxs-lookup"><span data-stu-id="f3cb4-144">Require HTTPS or IPsec for server access</span></span> <br/>  <span data-ttu-id="f3cb4-145">Azure 디스크 암호화</span><span class="sxs-lookup"><span data-stu-id="f3cb4-145">Azure disk encryption</span></span> <br/> |
|<span data-ttu-id="f3cb4-146">수준 2: 중간 규모 비즈니스 가치</span><span class="sxs-lookup"><span data-stu-id="f3cb4-146">Level 2: Medium business value</span></span>  <br/> | <span data-ttu-id="f3cb4-147">Azure AD 다단계 인증 (MFA) SMS 사용</span><span class="sxs-lookup"><span data-stu-id="f3cb4-147">Azure AD multi-factor authentication (MFA) with SMS</span></span> <br/> | <span data-ttu-id="f3cb4-148">Azure 키 볼트를 사용 하 여 암호화 키에 대 한</span><span class="sxs-lookup"><span data-stu-id="f3cb4-148">Use Azure Key Vault for encryption keys</span></span> <br/>  <span data-ttu-id="f3cb4-149">SMS 사용 하는 azure AD MFA</span><span class="sxs-lookup"><span data-stu-id="f3cb4-149">Azure AD MFA with SMS</span></span> <br/> | <span data-ttu-id="f3cb4-150">SMS 사용 하는 MFA</span><span class="sxs-lookup"><span data-stu-id="f3cb4-150">MFA with SMS</span></span> <br/> |
|<span data-ttu-id="f3cb4-151">수준 3: 높은 비즈니스 가치</span><span class="sxs-lookup"><span data-stu-id="f3cb4-151">Level 3: High business value</span></span>  <br/> | <span data-ttu-id="f3cb4-152">Azure 권한 관리 시스템 (RMS)</span><span class="sxs-lookup"><span data-stu-id="f3cb4-152">Azure Rights Management System (RMS)</span></span> <br/>  <span data-ttu-id="f3cb4-153">스마트 카드와 함께 azure AD MFA</span><span class="sxs-lookup"><span data-stu-id="f3cb4-153">Azure AD MFA with smart cards</span></span> <br/>  <span data-ttu-id="f3cb4-154">Intune 조건부 액세스</span><span class="sxs-lookup"><span data-stu-id="f3cb4-154">Intune conditional access</span></span> <br/> | <span data-ttu-id="f3cb4-155">Azure RMS</span><span class="sxs-lookup"><span data-stu-id="f3cb4-155">Azure RMS</span></span> <br/>  <span data-ttu-id="f3cb4-156">스마트 카드와 함께 azure AD MFA</span><span class="sxs-lookup"><span data-stu-id="f3cb4-156">Azure AD MFA with smart cards</span></span> <br/> | <span data-ttu-id="f3cb4-157">스마트 카드와 함께 MFA</span><span class="sxs-lookup"><span data-stu-id="f3cb4-157">MFA with smart cards</span></span> <br/> |
   
## <a name="contosos-information-policies"></a><span data-ttu-id="f3cb4-158">Contoso의 정보 정책</span><span class="sxs-lookup"><span data-stu-id="f3cb4-158">Contoso's information policies</span></span>

<span data-ttu-id="f3cb4-159">다음 표에 Contoso의 정보 정책입니다.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-159">The following table lists Contoso's information policies.</span></span>
  
||<span data-ttu-id="f3cb4-160">**액세스**</span><span class="sxs-lookup"><span data-stu-id="f3cb4-160">**Access**</span></span>|<span data-ttu-id="f3cb4-161">**데이터 보존 기간**</span><span class="sxs-lookup"><span data-stu-id="f3cb4-161">**Data retention**</span></span>|<span data-ttu-id="f3cb4-162">**정보 보호**</span><span class="sxs-lookup"><span data-stu-id="f3cb4-162">**Information protection**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="f3cb4-163">수준 1: 낮은 비즈니스 가치</span><span class="sxs-lookup"><span data-stu-id="f3cb4-163">Level 1: Low business value</span></span>  <br/> | <span data-ttu-id="f3cb4-164">모두에 대 한 액세스를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-164">Allow access to all</span></span> <br/> |<span data-ttu-id="f3cb4-165">6개월</span><span class="sxs-lookup"><span data-stu-id="f3cb4-165">6 months</span></span>  <br/> |<span data-ttu-id="f3cb4-166">암호화를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="f3cb4-166">Use encryption</span></span>  <br/> |
|<span data-ttu-id="f3cb4-167">수준 2: 중간 규모 비즈니스 가치</span><span class="sxs-lookup"><span data-stu-id="f3cb4-167">Level 2: Medium business value</span></span>  <br/> | <span data-ttu-id="f3cb4-168">Contoso 직원, 하청 및 파트너에 대 한 액세스를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-168">Allow access to Contoso employees, subcontractors, and partners</span></span> <br/>  <span data-ttu-id="f3cb4-169">MFA, TLS 및 MAM를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="f3cb4-169">Use MFA, TLS, and MAM</span></span> <br/> |<span data-ttu-id="f3cb4-170">2년</span><span class="sxs-lookup"><span data-stu-id="f3cb4-170">2 years</span></span>  <br/> |<span data-ttu-id="f3cb4-171">데이터 무결성을 위해 해시 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-171">Use hash values for data integrity</span></span>  <br/> |
|<span data-ttu-id="f3cb4-172">수준 3: 높은 비즈니스 가치</span><span class="sxs-lookup"><span data-stu-id="f3cb4-172">Level 3: High business value</span></span>  <br/> | <span data-ttu-id="f3cb4-173">임원 및 엔지니어링, 제조에 잠재 고객에 대 한 액세스를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-173">Allow access to executives and leads in engineering and manufacturing</span></span> <br/>  <span data-ttu-id="f3cb4-174">관리 되는 네트워크 장치와 RMS</span><span class="sxs-lookup"><span data-stu-id="f3cb4-174">RMS with managed network devices only</span></span> <br/> |<span data-ttu-id="f3cb4-175">7 년</span><span class="sxs-lookup"><span data-stu-id="f3cb4-175">7 years</span></span>  <br/> |<span data-ttu-id="f3cb4-176">부인 방지에 대 한 디지털 서명 사용</span><span class="sxs-lookup"><span data-stu-id="f3cb4-176">Use digital signatures for non-repudiation</span></span>  <br/> |
   
## <a name="contosos-path-to-cloud-security-readiness"></a><span data-ttu-id="f3cb4-177">클라우드 보안 준비에 대 한 Contoso의 경로</span><span class="sxs-lookup"><span data-stu-id="f3cb4-177">Contoso's path to cloud security readiness</span></span>

<span data-ttu-id="f3cb4-178">Microsoft 클라우드를 위한 보안을 준비 하려면 다음 단계를 사용 하는 Contoso 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-178">Contoso used the following steps to ready their security for the Microsoft cloud:</span></span>
  
1. <span data-ttu-id="f3cb4-179">관리자 계정을 클라우드를 위한 최적화</span><span class="sxs-lookup"><span data-stu-id="f3cb4-179">Optimize administrator accounts for the cloud</span></span>
    
    <span data-ttu-id="f3cb4-180">Contoso 않은 기존 Windows Server AD 관리자 계정의 전자 광범위 한 검토 하 고 일련의 클라우드 관리자 계정 및 그룹을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-180">Contoso did an extensive review of the existing Windows Server AD administrator accounts and set up a series of cloud administrator accounts and groups.</span></span>
    
2. <span data-ttu-id="f3cb4-181">세 수준으로 데이터 분류 분석을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-181">Perform data classification analysis into three levels</span></span>
    
    <span data-ttu-id="f3cb4-182">Contoso 신중 하 게 검토를 수행 하 고 Contoso의 가장 중요 한 데이터를 보호 하는 기능을 제공 하는 Microsoft 클라우드를 결정 하는데 사용 된 세 수준을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-182">Contoso performed a careful review and determined the three levels, which was used to determine the Microsoft cloud offering features to protect Contoso's most valuable data.</span></span>
    
3. <span data-ttu-id="f3cb4-183">데이터 수준에 대 한 액세스, 보존 및 정보 보호 정책 결정</span><span class="sxs-lookup"><span data-stu-id="f3cb4-183">Determine access, retention, and information protection policies for data levels</span></span>
    
    <span data-ttu-id="f3cb4-184">데이터 수준에 따라, Contoso는 클라우드로 이동 하는 향후 IT 작업을 사용 하는데 사용 되는 자세한 요구 사항을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-184">Based on the data levels, Contoso determined detailed requirements, which will be used to qualify future IT workloads being moved to the cloud.</span></span>
    
## <a name="contosos-use-of-office-365-security-best-practices"></a><span data-ttu-id="f3cb4-185">Contoso의 사용 하 여 Office 365 보안에 대 한 유용한 정보</span><span class="sxs-lookup"><span data-stu-id="f3cb4-185">Contoso's use of Office 365 security best practices</span></span>

<span data-ttu-id="f3cb4-186">Office 365 보안 모범 사례에 따라 Contoso의 보안 관리자 및 IT 부서 배포한 다음 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-186">In accordance with Office 365 security best practices, Contoso's security administrators and IT department have deployed the following:</span></span>
  
- <span data-ttu-id="f3cb4-187">**매우 강력한 암호를 가진 전역 관리자 계정 전용**</span><span class="sxs-lookup"><span data-stu-id="f3cb4-187">**Dedicated global administrator accounts with very strong passwords**</span></span>
    
    <span data-ttu-id="f3cb4-p105">대신 일상적인 사용자 계정에 전역 관리자 역할을 할당을 보다 Contoso는 만들기, 3 매우 강력한 암호를 가진 전역 관리자 계정 전용입니다. 특정 관리 작업에 대 한만 수행 되는 전역 관리자 계정을 사용 하 여 서명 하 고 암호는 지정 된 직원에 게만 알려져 있습니다. Contoso의 보안 관리자가 해당 IT 사용자의 작업 함수 및 책임에 적절 한 계정에 관리자 역할을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-p105">Rather than assign the global admin role to everyday user accounts, Contoso has create three, dedicated global administrator accounts with very strong passwords. Signing in with a global administrator account is only done for specific administrative tasks and the passwords are only known to designated staff. Contoso's security administrators have assigned admin roles to accounts that are appropriate to that IT person's job function and responsibility.</span></span>
    
    <span data-ttu-id="f3cb4-191">자세한 내용은 [Office 365에 대 한 관리자 역할](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-191">For more information, see [About Office 365 admin roles](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d).</span></span>
    
- <span data-ttu-id="f3cb4-192">**중요 한 사용자 계정에 대 한다 단계 인증 (MFA)**</span><span class="sxs-lookup"><span data-stu-id="f3cb4-192">**Multi-factor authentication (MFA) for important user accounts**</span></span>
    
    <span data-ttu-id="f3cb4-p106">MFA는 사용자를 전화 통화, 텍스트 메시지 또는 올바르게 자신의 암호를 입력 한 후 스마트 전화기에서 전자 app 알림을 확인을 요구 하 여 로그인 프로세스에 추가 계층의 보호를 추가 합니다. MFA와 계정 암호가 손상 된 경우에 Office 365 사용자 계정 허가 되지 않은 로그인에 대해 보호 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-p106">MFA adds an additional layer of protection to the sign-in process by requiring users to acknowledge a phone call, text message, or an app notification on their smart phone after correctly entering their password. With MFA, Office 365 user accounts are protected against unauthorized sign-in even if an account password is compromised.</span></span>
    
  - <span data-ttu-id="f3cb4-195">Office 365 구독의 손상을 보호 하기 위해 Contoso MFA 모든 세 전역 관리자 계정에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-195">To protect against a compromise of the Office 365 subscription, Contoso enabled MFA on all three global administrator accounts.</span></span>
    
  - <span data-ttu-id="f3cb4-196">공격자는 조직에서 신뢰할 수 있는 사용자의 자격 증명을 침해 및 악의적인 전자 메일을 보내는 피싱 공격 으로부터 보호 하기 위해 Contoso 임원 직원을 포함 하 여 관리자에 대 한 모든 사용자 계정에서 MFA을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-196">To protect against phishing attacks, in which an attacker compromises the credentials of a trusted person in the organization and sends malicious emails, Contoso enabled MFA on all user accounts for managers, including the executive staff.</span></span>
    
    <span data-ttu-id="f3cb4-197">자세한 내용은 [Office 365 배포에 대 한 다중 요소 인증에 대 한 계획](https://support.office.com/article/Plan-for-multifactor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba) 을 참조합니다</span><span class="sxs-lookup"><span data-stu-id="f3cb4-197">For more information, see [Plan for multi-factor authentication for Office 365 Deployments](https://support.office.com/article/Plan-for-multifactor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)</span></span>
    
- <span data-ttu-id="f3cb4-198">**고급 보안 관리 (ASM)**</span><span class="sxs-lookup"><span data-stu-id="f3cb4-198">**Advanced Security Management (ASM)**</span></span>
    
    <span data-ttu-id="f3cb4-p107">ASM 사용 하 여 비정상적인 활동을 모니터링 하는 정책을 구성 합니다. IT 관리자는 많은 양의 데이터를 다운로드 하는 등의 비정상적인 또는 위험한 사용자 동작의 알림을 받을 수 있도록 ASM와 경고를 설정 하는 Contoso 보안 관리자가 다중이 로그인 시도 또는 알 수 없거나 위험한 IP 주소에서 로그인을 실패 했습니다.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-p107">ASM uses configured policies to monitor for anomalous activity. Contoso security administrators set up alerts with ASM so that IT administrators are notified of unusual or risky user activity, such as downloading large amounts of data, multiple failed sign-in attempts, or sign-ins from unknown or dangerous IP addresses</span></span>
    
    <span data-ttu-id="f3cb4-201">자세한 내용은 [개요 (영문)의 고급 보안 Office 365의에서 관리 ](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-201">For more information, see [Overview of Advanced Security Management in Office 365 ](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).</span></span>
    
- <span data-ttu-id="f3cb4-202">**안전한 전자 메일 흐름 및 사서함 감사 로깅**</span><span class="sxs-lookup"><span data-stu-id="f3cb4-202">**Secure email flow and mailbox audit logging**</span></span>
    
    <span data-ttu-id="f3cb4-p108">Contoso 보안 전문가 Exchange Online Protection 및 고급 위협 보호 ATP ()를 사용 하 여 알 수 없는 맬웨어, 바이러스 및 전자 메일을 통해 전송 되는 악성 Url 보호 하기 위해 됩니다. Contoso에 활성화 된 사서함 감사 메시지를 전송 하는 사용자 사서함 및 사서함 소유자, 위임된 된 사용자 또는 관리자에 의해 수행 되는 다른 작업에 로그인 사용자를 확인 하려면 로깅을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-p108">Contoso security specialists are using Exchange Online Protection and Advanced Threat Protection (ATP) to protect against unknown malware, viruses, and malicious URLs transmitted through emails. Contoso has also enabled mailbox audit logging to determine who has logged into user mailboxes, sent messages, and other activities performed by the mailbox owner, a delegated user, or an administrator.</span></span>
    
    <span data-ttu-id="f3cb4-205">자세한 내용은 다음을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-205">For more information, see:</span></span> 
    
  - [<span data-ttu-id="f3cb4-206">Office 365 전자 메일 스팸 방지 보호 기능</span><span class="sxs-lookup"><span data-stu-id="f3cb4-206">Office 365 Email Anti-Spam Protection</span></span>](https://support.office.com/article/Office-365-Email-AntiSpam-Protection-6a601501-a6a8-4559-b2e7-56b59c96a586)
    
  - [<span data-ttu-id="f3cb4-207">안전한 첨부 파일 및 안전 링크에 대 한 고급 위협 보호</span><span class="sxs-lookup"><span data-stu-id="f3cb4-207">Advanced threat protection for safe attachments and safe links</span></span>](https://technet.microsoft.com/library/mt148491.aspx)
    
  - [<span data-ttu-id="f3cb4-208">Office 365에서 사서함 감사를 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="f3cb4-208">Enable mailbox auditing in Office 365</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=626109)
    
- <span data-ttu-id="f3cb4-209">**데이터 손실 방지 (DLP)**</span><span class="sxs-lookup"><span data-stu-id="f3cb4-209">**Data Loss Prevention (DLP)**</span></span>
    
    <span data-ttu-id="f3cb4-210">Contoso가의 중요 한 데이터를 식별 하 고 Exchange Online, SharePoint Online 및 OneDrive 사용자가 실수로 또는 의도적으로 데이터를 공유 하는 것을 방지 하기에 대 한 DLP 정책을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-210">Contoso has identified its sensitive data and configured DLP policies for Exchange Online, SharePoint Online, and OneDrive to help prevent users from accidentally or intentionally sharing the data.</span></span> 
    
    <span data-ttu-id="f3cb4-211">자세한 내용은 [데이터 손실 방지 정책 개요](https://support.office.com/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="f3cb4-211">For more information, see [Overview of data loss prevention policies](https://support.office.com/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e).</span></span>
    
## <a name="see-also"></a><span data-ttu-id="f3cb4-212">See Also</span><span class="sxs-lookup"><span data-stu-id="f3cb4-212">See Also</span></span>

[<span data-ttu-id="f3cb4-213">Microsoft 클라우드 Contoso</span><span class="sxs-lookup"><span data-stu-id="f3cb4-213">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="f3cb4-214">Microsoft 클라우드 IT 아키텍처 리소스</span><span class="sxs-lookup"><span data-stu-id="f3cb4-214">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="f3cb4-215">Microsoft의 엔터프라이즈 클라우드 로드맵: IT 의사 결정권자를 위한 리소스</span><span class="sxs-lookup"><span data-stu-id="f3cb4-215">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)
  
[<span data-ttu-id="f3cb4-216">Office 365에 대 한 보안 모범 사례</span><span class="sxs-lookup"><span data-stu-id="f3cb4-216">Security best practices for Office 365</span></span>](https://support.office.com/article/Security-best-practices-for-Office-365-9295e396-e53d-49b9-ae9b-0b5828cdedc3)




