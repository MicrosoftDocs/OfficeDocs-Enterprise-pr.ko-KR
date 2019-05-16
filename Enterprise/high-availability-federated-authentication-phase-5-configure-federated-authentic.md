---
title: 고가용성 페더레이션 인증 단계 5 Office 365에 대 한 페더레이션 인증 구성
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 0f1dbf52-5bff-44cc-a264-1b48641af98f
description: '요약: Microsoft Azure에서 Office 365에 대 한 고가용성 페더레이션 인증에 대해 Azure AD Connect를 구성 합니다.'
ms.openlocfilehash: a4c8a76a322824bfdb4df88600881d76cb3e378c
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067324"
---
# <a name="high-availability-federated-authentication-phase-5-configure-federated-authentication-for-office-365"></a><span data-ttu-id="fc23d-103">고가용성 페더레이션 인증 5단계: Office 365에 대해 페더레이션 인증 구성</span><span class="sxs-lookup"><span data-stu-id="fc23d-103">High availability federated authentication Phase 5: Configure federated authentication for Office 365</span></span>

 <span data-ttu-id="fc23d-104">**요약:** Microsoft Azure에서 Office 365에 대 한 고가용성 페더레이션 인증에 대해 Azure AD Connect를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-104">**Summary:** Configure Azure AD Connect for your high availability federated authentication for Office 365 in Microsoft Azure.</span></span>
 
<span data-ttu-id="fc23d-105">Azure 인프라 서비스에서 Office 365에 대 한 고가용성 페더레이션 인증을 배포 하는 마지막 단계에서는 공개 인증 기관에서 발급 한 인증서를 가져오고 설치 하 고, 구성을 확인 한 다음 Azure AD를 설치 및 실행 합니다. 디렉터리 동기화 서버에서 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-105">In this final phase of deploying high availability federated authentication for Office 365 in Azure infrastructure services, you get and install a certificate issued by a public certification authority, verify your configuration, and then install and run Azure AD Connect on the directory synchronization server.</span></span> <span data-ttu-id="fc23d-106">Azure AD Connect는 페더레이션 인증을 위해 Office 365 구독 및 AD FS (Active Directory Federation Services) 및 웹 응용 프로그램 프록시 서버를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-106">Azure AD Connect configures your Office 365 subscription and your Active Directory Federation Services (AD FS) and web application proxy servers for federated authentication.</span></span>
  
<span data-ttu-id="fc23d-107">모든 단계에 대해 [Azure에서 Office 365에 대 한 고가용성 페더레이션 인증 배포](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fc23d-107">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="get-a-public-certificate-and-copy-it-to-the-directory-synchronization-server"></a><span data-ttu-id="fc23d-108">공용 인증서를 가져와 디렉터리 동기화 서버에 복사</span><span class="sxs-lookup"><span data-stu-id="fc23d-108">Get a public certificate and copy it to the directory synchronization server</span></span>

<span data-ttu-id="fc23d-109">다음 속성을 사용 하 여 공용 인증 기관에서 디지털 인증서를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-109">Get a digital certificate from a public certification authority with the following properties:</span></span>
  
- <span data-ttu-id="fc23d-110">SSL 연결을 만드는 데 적합 한 x.509 인증서입니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-110">An X.509 certificate suitable for creating SSL connections.</span></span>
    
- <span data-ttu-id="fc23d-111">SAN (주체 대체 이름) 확장 속성은 페더레이션 서비스 FQDN으로 설정 됩니다 (예: fs.contoso.com).</span><span class="sxs-lookup"><span data-stu-id="fc23d-111">The Subject Alternative Name (SAN) extended property is set to your federation service FQDN (example: fs.contoso.com).</span></span>
    
- <span data-ttu-id="fc23d-112">인증서에는 개인 키가 있고 PFX 형식으로 저장 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-112">The certificate must have the private key and be stored in PFX format.</span></span>
    
<span data-ttu-id="fc23d-113">또한 조직 컴퓨터 및 장치는 디지털 인증서를 발급 하는 공용 인증 기관을 신뢰 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-113">Additionally, your organization computers and devices must trust the public certification authority that is issuing the digital certificate.</span></span> <span data-ttu-id="fc23d-114">이 트러스트는 컴퓨터 및 장치에 있는 신뢰할 수 있는 루트 인증 기관 저장소에 설치 된 공용 인증 기관의 루트 인증서를 보유 하 여 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-114">This trust is established by having a root certificate from the public certification authority installed in the trusted root certification authorities store on your computers and devices.</span></span> <span data-ttu-id="fc23d-115">일반적으로 Microsoft Windows를 실행 하는 컴퓨터에는 일반적으로 사용 되는 인증 기관에서 설치 된 이러한 유형의 인증서가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-115">Computers running Microsoft Windows typically have a set of these types of certificates installed from commonly-used certification authorities.</span></span> <span data-ttu-id="fc23d-116">공용 인증 기관의 루트 인증서가 아직 설치 되어 있지 않은 경우이를 조직의 컴퓨터 및 장치에 배포 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-116">If the root certificate from your public certification authority is not already installed, you must deploy this to the computers and devices of your organization.</span></span>
  
<span data-ttu-id="fc23d-117">페더레이션 인증의 인증서 요구 사항에 대 한 자세한 내용은 [페더레이션 설치 및 구성에 대 한 필수 구성 요소](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-prerequisites#prerequisites-for-federation-installation-and-configuration)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="fc23d-117">For more information about certificate requirements for federated authentication, see [Prerequisites for federation installation and configuration](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-prerequisites#prerequisites-for-federation-installation-and-configuration).</span></span>
  
<span data-ttu-id="fc23d-118">인증서를 받으면 디렉터리 동기화 서버의 C: 드라이브에 있는 폴더로 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-118">When you receive the certificate, copy it to a folder on the C: drive of the directory synchronization server.</span></span> <span data-ttu-id="fc23d-119">예를 들어, 파일 이름을 p C\\e. e l e.</span><span class="sxs-lookup"><span data-stu-id="fc23d-119">For example, name the file SSL.pfx and store it in the C:\\Certs folder on the directory synchronization server.</span></span>
  
## <a name="verify-your-configuration"></a><span data-ttu-id="fc23d-120">구성 확인</span><span class="sxs-lookup"><span data-stu-id="fc23d-120">Verify your configuration</span></span>

<span data-ttu-id="fc23d-121">이제 Office 365에 대해 Azure AD Connect 및 페더레이션 인증을 구성할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-121">You should now be ready to configure Azure AD Connect and federated authentication for Office 365.</span></span> <span data-ttu-id="fc23d-122">다음은 검사 목록을 확인 하는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-122">To ensure that you are, here is a checklist:</span></span>
  
- <span data-ttu-id="fc23d-123">조직의 공용 도메인이 Office 365 구독에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-123">Your organization's public domain is added to your Office 365 subscription.</span></span>
    
- <span data-ttu-id="fc23d-124">조직의 Office 365 사용자 계정이 조직의 공용 도메인 이름으로 구성 되 고 성공적으로 로그인 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-124">Your organization's Office 365 user accounts are configured to your organization's public domain name and can successfully sign in.</span></span>
    
- <span data-ttu-id="fc23d-125">공용 도메인 이름을 기반으로 하는 페더레이션 서비스 FQDN을 결정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-125">You have determined a federation service FQDN based your public domain name.</span></span>
    
- <span data-ttu-id="fc23d-126">페더레이션 서비스 FQDN에 대 한 공용 DNS A 레코드는 웹 응용 프로그램 프록시 서버에 대 한 인터넷 연결에 사용 되는 Azure 부하 분산 장치의 공용 IP 주소를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-126">A public DNS A record for your federation service FQDN points to the public IP address of the Internet-facing Azure load balancer for the web application proxy servers.</span></span>
    
- <span data-ttu-id="fc23d-127">페더레이션 서비스 FQDN에 대 한 개인 DNS A 레코드는 AD FS 서버에 대 한 내부 Azure 부하 분산 장치의 개인 IP 주소를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-127">A private DNS A record for your federation service FQDN points to the private IP address of the internal Azure load balancer for the AD FS servers.</span></span>
    
- <span data-ttu-id="fc23d-128">페더레이션 서비스 FQDN으로 설정 된 SAN과의 SSL 연결에 적합 한 공용 인증 기관-isssued 디지털 인증서는 디렉터리 동기화 서버에 저장 되는 PFX 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-128">A public certification authority-isssued digital certificate suitable for SSL connections with the SAN set to your federation service FQDN is a PFX file stored on your directory synchronization server.</span></span>
    
- <span data-ttu-id="fc23d-129">공용 인증 기관의 루트 인증서는 컴퓨터 및 장치에 있는 신뢰할 수 있는 루트 인증 기관 저장소에 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-129">The root certificate for the public certification authority is installed in the Trusted Root Certification Authorities store on your computers and devices.</span></span>
    
<span data-ttu-id="fc23d-130">다음은 Contoso 조직에 대 한 예입니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-130">Here is an example for the Contoso organization:</span></span>
  
<span data-ttu-id="fc23d-131">**Azure의 고가용성 페더레이션 인증 인프라에 대 한 예제 구성**</span><span class="sxs-lookup"><span data-stu-id="fc23d-131">**An example configuration for a high availability federated authentication infrastructure in Azure**</span></span>

![Azure에서 고가용성 Office 365 페더레이션 인증 인프라의 예제 구성](media/ac1a6a0d-0156-4407-9336-6e4cd6db8633.png)
  
## <a name="run-azure-ad-connect-to-configure-federated-authentication"></a><span data-ttu-id="fc23d-133">Azure AD Connect를 실행 하 여 페더레이션 인증 구성</span><span class="sxs-lookup"><span data-stu-id="fc23d-133">Run Azure AD Connect to configure federated authentication</span></span>

<span data-ttu-id="fc23d-134">Azure AD Connect 도구는 다음 단계를 사용 하 여 페더레이션 인증을 위해 AD FS 서버, 웹 응용 프로그램 프록시 서버 및 Office 365을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-134">The Azure AD Connect tool configures the AD FS servers, the web application proxy servers, and Office 365 for federated authentication with these steps:</span></span>
  
1. <span data-ttu-id="fc23d-135">로컬 관리자 권한이 있는 도메인 계정을 사용 하 여 디렉터리 동기화 서버에 대 한 원격 데스크톱 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-135">Create a remote desktop connection to your directory synchronization server with a domain account that has local administrator privileges.</span></span>
    
2. <span data-ttu-id="fc23d-136">디렉터리 동기화 서버의 데스크톱에서 Internet Explorer를 열고로 [https://aka.ms/aadconnect](https://aka.ms/aadconnect)이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-136">From the desktop of the directory synchronization server, open Internet Explorer and go to [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span></span>
    
3. <span data-ttu-id="fc23d-137">**Microsoft Azure Active Directory 연결** 페이지에서 **다운로드**를 클릭 한 다음 **실행**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-137">On the **Microsoft Azure Active Directory Connect** page, click **Download**, and then click **Run**.</span></span>
    
4. <span data-ttu-id="fc23d-138">**AZURE AD Connect 시작** 페이지에서 **동의 함**을 클릭 하 고 계속을 클릭 **합니다.**</span><span class="sxs-lookup"><span data-stu-id="fc23d-138">On the **Welcome to Azure AD Connect** page, click **I agree**, and then click **Continue.**</span></span>
    
5. <span data-ttu-id="fc23d-139">**기본 설정** 페이지에서 **사용자 지정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-139">On the **Express Settings** page, click **Customize**.</span></span>
    
6. <span data-ttu-id="fc23d-140">**필수 구성 요소 설치** 페이지에서 **설치**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-140">On the **Install required components** page, click **Install**.</span></span>
    
7. <span data-ttu-id="fc23d-141">**사용자 로그인** 페이지에서 **AD FS로 페더레이션**을 클릭하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-141">On the **User sign-in** page, click **Federation with AD FS**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="fc23d-142">**AZURE AD에 연결** 페이지에서 Office 365 구독에 대 한 전역 관리자 계정의 이름과 암호를 입력 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-142">On the **Connect to Azure AD** page, type the name and password of a global administrator account for your Office 365 subscription, and then click **Next**.</span></span>
    
9. <span data-ttu-id="fc23d-143">**디렉터리 연결** 페이지에서 온-프레미스 AD DS (Active Directory 도메인 서비스) 포리스트가 **포리스트에서**선택 되어 있는지 확인 하 고 도메인 관리자 계정의 이름과 암호를 입력 한 다음 **디렉터리 추가**를 클릭 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-143">On the **Connect your directories** page, ensure that your on-premises Active Directory Domain Services (AD DS) forest is selected in **Forest**, type the name and password of a domain administrator account, click **Add Directory**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="fc23d-144">**AZURE AD 로그인 구성** 페이지에서 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-144">On the **Azure AD sign-in configuration** page, click **Next**.</span></span>
    
11. <span data-ttu-id="fc23d-145">**도메인 및 OU 필터링** 페이지에서 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-145">On the **Domain and OU filtering** page, click **Next**.</span></span>
    
12. <span data-ttu-id="fc23d-146">사용자를 **고유 하 게 식별** 페이지에서 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-146">On the **Uniquely identifying your users** page, click **Next**.</span></span>
    
13. <span data-ttu-id="fc23d-147">**사용자 및 장치 필터링** 페이지에서 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-147">On the **Filter users and devices** page, click **Next**.</span></span>
    
14. <span data-ttu-id="fc23d-148">**선택적 기능** 페이지에서 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-148">On the **Optional features** page, click **Next**.</span></span>
    
15. <span data-ttu-id="fc23d-149">**AD fs 팜** 페이지에서 **새 AD FS 팜 구성을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-149">On the **AD FS farm** page, click **Configure a new AD FS farm**.</span></span>
    
16. <span data-ttu-id="fc23d-150">**찾아보기를** 클릭 하 고 공용 인증 기관에서 SSL 인증서의 위치와 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-150">Click **Browse** and specify the location and name of the SSL certificate from the public certification authority.</span></span>
    
17. <span data-ttu-id="fc23d-151">메시지가 나타나면 인증서 암호를 입력 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-151">When prompted, type the certificate password, and then click **OK**.</span></span>
    
18. <span data-ttu-id="fc23d-152">**주체 이름** 및 **페더레이션 서비스 이름이** 페더레이션 서비스 FQDN으로 설정 되어 있는지 확인 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-152">Verify that the **Subject Name** and **Federation Service Name** are set to your federation service FQDN, and then click **Next**.</span></span>
    
19. <span data-ttu-id="fc23d-153">**AD fs 서버** 페이지에서 첫 번째 AD fs 서버의 이름 (테이블 M-항목 4-가상 컴퓨터 이름 열)을 입력 하 고 **추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-153">On the **AD FS servers** page, type your first AD FS server's name (Table M - Item 4 - Virtual machine name column), and then click **Add**.</span></span>
    
20. <span data-ttu-id="fc23d-154">두 번째 AD FS 서버 이름 (테이블 M-항목 5-가상 컴퓨터 이름 열)을 입력 하 고 **추가**를 클릭 한 후 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-154">Type your second AD FS server's name (Table M - Item 5 - Virtual machine name column), click **Add**, and then click **Next**.</span></span>
    
21. <span data-ttu-id="fc23d-155">**웹 응용 프로그램 프록시 서버** 페이지에서 첫 번째 웹 응용 프로그램 프록시 서버의 이름 (테이블 M-항목 6-가상 컴퓨터 이름 열)을 입력 한 다음 **추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-155">On the **Web Application Proxy servers** page, type your first web application proxy server's name (Table M - Item 6 - Virtual machine name column), and then click **Add**.</span></span>
    
22. <span data-ttu-id="fc23d-156">두 번째 웹 응용 프로그램 프록시 서버의 이름 (테이블 M-항목 7-가상 컴퓨터 이름 열)을 입력 하 고 **추가**를 클릭 한 후 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-156">Type your second web application proxy server's name (Table M - Item 7 - Virtual machine name column), click **Add**, and then click **Next**.</span></span>
    
23. <span data-ttu-id="fc23d-157">**도메인 관리자 자격 증명** 페이지에서 도메인 관리자 계정의 사용자 이름과 암호를 입력 한 후 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-157">On the **Domain Administrator credentials** page, type the user name and password of a domain administrator account, and then click **Next**.</span></span>
    
24. <span data-ttu-id="fc23d-158">**AD FS 서비스 계정** 페이지에서 엔터프라이즈 관리자 계정의 사용자 이름과 암호를 입력 한 후 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-158">On the **AD FS service account** page, type the user name and password of an enterprise administrator account, and then click **Next**.</span></span>
    
25. <span data-ttu-id="fc23d-159">**AZURE AD 도메인** 페이지의 **도메인**에서 조직의 DNS 도메인 이름을 선택 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-159">On the **Azure AD Domain** page, in **Domain**, select your organization's DNS domain name, and then click **Next**.</span></span>
    
26. <span data-ttu-id="fc23d-160">**구성 준비 완료** 페이지에서 **설치**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-160">On the **Ready to configure** page, click **Install**.</span></span>
    
27. <span data-ttu-id="fc23d-161">**설치 완료** 페이지에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-161">On the **Installation complete** page, click **Verify**.</span></span> <span data-ttu-id="fc23d-162">인트라넷 구성과 인터넷 구성이 모두 성공적으로 확인 되었음을 나타내는 두 개의 메시지가 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-162">You should see two messages indicating that both the intranet and Internet configuration was successfully verified.</span></span>
    
  - <span data-ttu-id="fc23d-163">인트라넷 메시지는 AD FS 서버에 대 한 Azure 내부 부하 분산 장치의 개인 IP 주소를 나열 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-163">The intranet message should list the private IP address of your Azure internal load balancer for your AD FS servers.</span></span>
    
  - <span data-ttu-id="fc23d-164">인터넷 메시지에는 웹 응용 프로그램 프록시 서버에 대 한 Azure 인터넷 연결 부하 분산 장치의 공용 IP 주소가 나열 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-164">The Internet message should list the public IP address of your Azure Internet-facing load balancer for your web application proxy servers.</span></span>
    
28. <span data-ttu-id="fc23d-165">**설치 완료** 페이지에서 **끝내기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-165">On the **Installation complete** page, click **Exit**.</span></span>
    
<span data-ttu-id="fc23d-166">다음은 서버에 대 한 자리 표시자 이름이 포함 된 최종 구성입니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-166">Here is the final configuration, with placeholder names for the servers.</span></span>
  
<span data-ttu-id="fc23d-167">**5 단계: Azure의 고가용성 페더레이션 인증 인프라에 대 한 최종 구성**</span><span class="sxs-lookup"><span data-stu-id="fc23d-167">**Phase 5: The final configuration of a high availability federated authentication infrastructure in Azure**</span></span>

![Azure에서 고가용성 Office 365 페더레이션 인증 인프라의 최종 구성.](media/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
<span data-ttu-id="fc23d-169">Azure의 Office 365에 대 한 고가용성 페더레이션 인증 인프라가 완료 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fc23d-169">Your high availability federated authentication infrastructure for Office 365 in Azure is complete.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="fc23d-170">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fc23d-170">See Also</span></span>

[<span data-ttu-id="fc23d-171">Azure에서 Office 365용 고가용성 페더레이션 인증 배포</span><span class="sxs-lookup"><span data-stu-id="fc23d-171">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="fc23d-172">Office 365 개발/테스트 환경에 대 한 페더레이션된 id</span><span class="sxs-lookup"><span data-stu-id="fc23d-172">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="fc23d-173">클라우드 채택 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="fc23d-173">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="fc23d-174">Office 365용 페더레이션 ID</span><span class="sxs-lookup"><span data-stu-id="fc23d-174">Federated identity for Office 365</span></span>](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


