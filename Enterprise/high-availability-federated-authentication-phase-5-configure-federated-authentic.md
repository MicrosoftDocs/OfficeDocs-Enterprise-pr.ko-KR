---
title: 고가용성 연결 된 인증 Office 365에 대 한 연결 된 인증 단계 5 구성
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 0f1dbf52-5bff-44cc-a264-1b48641af98f
description: '요약: Microsoft Azure의 Office 365에 대 한 고가용성 연결 된 인증 사용자에 대 한 Azure AD 연결을 구성 합니다.'
ms.openlocfilehash: 93e872098b31326de67fb0557354e9f4fc1de9ed
ms.sourcegitcommit: a337ac253054f571a8304e18e426f74bcd385857
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2018
---
# <a name="high-availability-federated-authentication-phase-5-configure-federated-authentication-for-office-365"></a><span data-ttu-id="e6c82-103">고가용성 페더레이션 인증 5 단계: Office 365에 대 한 연결 된 인증 구성</span><span class="sxs-lookup"><span data-stu-id="e6c82-103">High availability federated authentication Phase 5: Configure federated authentication for Office 365</span></span>

 <span data-ttu-id="e6c82-104">**요약:** Microsoft Azure의 Office 365에 대 한 고가용성 연결 된 인증 사용자에 대 한 Azure AD 연결을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-104">**Summary:** Configure Azure AD Connect for your high availability federated authentication for Office 365 in Microsoft Azure.</span></span>
 
<span data-ttu-id="e6c82-p101">Azure 인프라 서비스에서 Office 365에 대 한 고가용성 페더레이션된 인증 배포의이 마지막 단계에서 가져올 하 고 공용 인증 기관에서 발급 한 인증서를 설치, 구성, 확인 하 고 설치 하 고 실행 Azure AD 디렉터리 동기화 서버에 연결 합니다. Azure AD 연결 Office 365 구독 및 Active Directory Federation Services (AD FS) 및 연결 된 인증에 대 한 웹 응용 프로그램 프록시 서버를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-p101">In this final phase of deploying high availability federated authentication for Office 365 in Azure infrastructure services, you get and install a certificate issued by a public certification authority, verify your configuration, and then install and run Azure AD Connect on the directory synchronization server. Azure AD Connect configures your Office 365 subscription and your Active Directory Federation Services (AD FS) and web application proxy servers for federated authentication.</span></span>
  
<span data-ttu-id="e6c82-107">모든 단계에 대 한 [Azure의 Office 365에 대 한 고가용성 연결 된 인증 배포를](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="e6c82-107">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="get-a-public-certificate-and-copy-it-to-the-directory-synchronization-server"></a><span data-ttu-id="e6c82-108">공용 인증서를 얻고 디렉터리 동기화 서버에 복사</span><span class="sxs-lookup"><span data-stu-id="e6c82-108">Get a public certificate and copy it to the directory synchronization server</span></span>

<span data-ttu-id="e6c82-109">다음 속성을 갖는 공용 인증 기관에서 디지털 인증서를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-109">Get a digital certificate from a public certification authority with the following properties:</span></span>
  
- <span data-ttu-id="e6c82-110">SSL 연결을 만들기 위한 적합 한 X.509 인증서입니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-110">An X.509 certificate suitable for creating SSL connections.</span></span>
    
- <span data-ttu-id="e6c82-111">주체 대체 이름 (SAN) 속성을 확장 페더레이션 서비스 FQDN으로 설정 됩니다 (예: fs.contoso.com).</span><span class="sxs-lookup"><span data-stu-id="e6c82-111">The Subject Alternative Name (SAN) extended property is set to your federation service FQDN (example: fs.contoso.com).</span></span>
    
- <span data-ttu-id="e6c82-112">인증서 개인 키가 있어야 하 고 PFX 형식에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-112">The certificate must have the private key and be stored in PFX format.</span></span>
    
<span data-ttu-id="e6c82-p102">또한 조직 컴퓨터와 장치에서 디지털 인증서를 발급 하는 공용 인증 기관을 신뢰 해야 합니다. 이 트러스트를 컴퓨터와 장치에서 신뢰할 수 있는 루트 인증 기관 저장소에 설치 하는 공용 인증 기관에서 루트 인증서를 사용 함으로써 설정 됩니다. 일반적으로 Microsoft Windows를 실행 하는 컴퓨터에는 이러한 유형의 일반적으로 사용 되는 인증 기관에서 설치 된 인증서 집합이 포함 됩니다. 공용 인증 기관에서 루트 인증서가 아직 설치 되지 않은,이 컴퓨터와 조직의 장치에 배포 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-p102">Additionally, your organization computers and devices must trust the public certification authority that is issuing the digital certificate. This trust is established by having a root certificate from the public certification authority installed in the trusted root certification authorities store on your computers and devices. Computers running Microsoft Windows typically have a set of these types of certificates installed from commonly-used certification authorities. If the root certificate from your public certification authority is not already installed, you must deploy this to the computers and devices of your organization.</span></span>
  
<span data-ttu-id="e6c82-117">연결 된 인증에 대 한 인증서 요구 사항에 대 한 자세한 내용은 [페더레이션 설치 및 구성에 대 한 필수 구성 요소](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-prerequisites#prerequisites-for-federation-installation-and-configuration)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="e6c82-117">For more information about certificate requirements for federated authentication, see [Prerequisites for federation installation and configuration](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-prerequisites#prerequisites-for-federation-installation-and-configuration).</span></span>
  
<span data-ttu-id="e6c82-p103">인증서를 받을 때의 폴더 디렉터리 동기화 서버 c: 드라이브에 복사 합니다. 예, SSL.pfx 파일 이름을 지정 하 고 c: 드라이브에 저장\\디렉터리 동기화 서버에서 인증서 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-p103">When you receive the certificate, copy it to a folder on the C: drive of the directory synchronization server. For example, name the file SSL.pfx and store it in the C:\\Certs folder on the directory synchronization server.</span></span>
  
## <a name="verify-your-configuration"></a><span data-ttu-id="e6c82-120">구성 확인</span><span class="sxs-lookup"><span data-stu-id="e6c82-120">Verify your configuration</span></span>

<span data-ttu-id="e6c82-p104">이제 Azure AD 연결 및 Office 365에 대 한 연결 된 인증을 구성 준비가 됩니다. 수 있는지를 확인, 검사 목록을 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-p104">You should now be ready to configure Azure AD Connect and federated authentication for Office 365. To ensure that you are, here is a checklist:</span></span>
  
- <span data-ttu-id="e6c82-123">Office 365 구독 조직의 공용 도메인 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-123">Your organization's public domain is added to your Office 365 subscription.</span></span>
    
- <span data-ttu-id="e6c82-124">조직의 Office 365 사용자 계정 조직의 공용 도메인 이름으로 구성 하 고 성공적으로 로그인 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-124">Your organization's Office 365 user accounts are configured to your organization's public domain name and can successfully sign in.</span></span>
    
- <span data-ttu-id="e6c82-125">페더레이션 서비스 FQDN 기반 공용 도메인 이름을 결정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-125">You have determined a federation service FQDN based your public domain name.</span></span>
    
- <span data-ttu-id="e6c82-126">공용 IP 주소를 인터넷 Azure에 페더레이션 서비스 FQDN 포인트에 대 한 공용 DNS A 레코드를 부하 분산 장치는 웹 응용 프로그램 프록시 서버에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-126">A public DNS A record for your federation service FQDN points to the public IP address of the Internet-facing Azure load balancer for the web application proxy servers.</span></span>
    
- <span data-ttu-id="e6c82-127">개인 IP 주소에 AD FS 서버에 대 한 내부 Azure 부하 분산 장치에 페더레이션 서비스 FQDN 포인트에 대 한 개인 DNS A 레코드입니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-127">A private DNS A record for your federation service FQDN points to the private IP address of the internal Azure load balancer for the AD FS servers.</span></span>
    
- <span data-ttu-id="e6c82-128">공용 인증 기관 isssued 디지털 인증서를 페더레이션 서비스를 설정 하는 SAN와의 SSL 연결에 대 한 적절 한 FQDN은 디렉터리 동기화 서버에 저장 된 PFX 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-128">A public certification authority-isssued digital certificate suitable for SSL connections with the SAN set to your federation service FQDN is a PFX file stored on your directory synchronization server.</span></span>
    
- <span data-ttu-id="e6c82-129">공용 인증 기관에 대 한 루트 인증서가 신뢰할 수 있는 루트 인증 기관에 설치 되어 컴퓨터와 장치에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-129">The root certificate for the public certification authority is installed in the Trusted Root Certification Authorities store on your computers and devices.</span></span>
    
<span data-ttu-id="e6c82-130">Contoso 조직에 대 한 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-130">Here is an example for the Contoso organization:</span></span>
  
<span data-ttu-id="e6c82-131">**높은 가용성을 위해 구성의 예는 페더레이션 Azure에서 인증 인프라**</span><span class="sxs-lookup"><span data-stu-id="e6c82-131">**An example configuration for a high availability federated authentication infrastructure in Azure**</span></span>

![Azure에서 고가용성 Office 365 페더레이션 인증 인프라의 예제 구성](images/ac1a6a0d-0156-4407-9336-6e4cd6db8633.png)
  
## <a name="run-azure-ad-connect-to-configure-federated-authentication"></a><span data-ttu-id="e6c82-133">연결 된 인증을 구성 하려면 Azure AD 연결을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-133">Run Azure AD Connect to configure federated authentication</span></span>

<span data-ttu-id="e6c82-134">Azure AD 연결 도구이 단계와 연결 된 인증에 대 한 AD FS 서버, 웹 응용 프로그램 프록시 서버 및 Office 365를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-134">The Azure AD Connect tool configures the AD FS servers, the web application proxy servers, and Office 365 for federated authentication with these steps:</span></span>
  
1. <span data-ttu-id="e6c82-135">로컬 관리자 권한이 있는 도메인 계정을 사용 하 여 디렉터리 동기화 서버에 원격 데스크톱 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-135">Create a remote desktop connection to your directory synchronization server with a domain account that has local administrator privileges.</span></span>
    
2. <span data-ttu-id="e6c82-136">디렉터리 동기화 서버 바탕 화면에서 Internet Explorer를 열고로 이동 [https://aka.ms/aadconnect](https://aka.ms/aadconnect)합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-136">From the desktop of the directory synchronization server, open Internet Explorer and go to [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span></span>
    
3. <span data-ttu-id="e6c82-137">**Microsoft Azure Active Directory에 연결** 페이지에서 **다운로드**를 클릭 한 다음 **실행**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-137">On the **Microsoft Azure Active Directory Connect** page, click **Download**, and then click **Run**.</span></span>
    
4. <span data-ttu-id="e6c82-138">**Azure AD 연결을 시작** 페이지에서 **동의 함**클릭 하 고 다음을 클릭 **계속.**</span><span class="sxs-lookup"><span data-stu-id="e6c82-138">On the **Welcome to Azure AD Connect** page, click **I agree**, and then click **Continue.**</span></span>
    
5. <span data-ttu-id="e6c82-139">**Express 설정** 페이지에서 **사용자 지정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-139">On the **Express Settings** page, click **Customize**.</span></span>
    
6. <span data-ttu-id="e6c82-140">**필수 구성 요소 설치** 페이지에서 **설치**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-140">On the **Install required components** page, click **Install**.</span></span>
    
7. <span data-ttu-id="e6c82-141">**사용자 로그인** 페이지에서 **AD FS와의 페더레이션을 사용**을 클릭 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-141">On the **User sign-in** page, click **Federation with AD FS**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="e6c82-142">**Azure AD에 연결** 페이지에서 이름 및 Office 365 구독의 전역 관리자 계정의 암호를 입력 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-142">On the **Connect to Azure AD** page, type the name and password of a global administrator account for your Office 365 subscription, and then click **Next**.</span></span>
    
9. <span data-ttu-id="e6c82-143">**디렉터리에 연결** 페이지에서 온-프레미스 Windows Server AD 포리스트에 **포리스트에서**선택 되어있는지 확인, 이름 및 도메인 관리자 계정의 암호를 입력, **디렉터리 추가**클릭 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-143">On the **Connect your directories** page, ensure that your on-premises Windows Server AD forest is selected in **Forest**, type the name and password of a domain administrator account, click **Add Directory**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="e6c82-144">**Azure AD 로그인 구성** 페이지에서 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-144">On the **Azure AD sign-in configuration** page, click **Next**.</span></span>
    
11. <span data-ttu-id="e6c82-145">**도메인 및 OU 필터링** 페이지에서 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-145">On the **Domain and OU filtering** page, click **Next**.</span></span>
    
12. <span data-ttu-id="e6c82-146">**사용자를 고유 하 게 확인** 페이지에서 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-146">On the **Uniquely identifying your users** page, click **Next**.</span></span>
    
13. <span data-ttu-id="e6c82-147">**사용자 및 장치 필터** 페이지에서 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-147">On the **Filter users and devices** page, click **Next**.</span></span>
    
14. <span data-ttu-id="e6c82-148">**선택적 기능** 페이지에서 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-148">On the **Optional features** page, click **Next**.</span></span>
    
15. <span data-ttu-id="e6c82-149">**AD FS 팜** 페이지에서 **새 AD FS 팜 구성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-149">On the **AD FS farm** page, click **Configure a new AD FS farm**.</span></span>
    
16. <span data-ttu-id="e6c82-150">**찾아보기** 를 클릭 하 고 공용 인증 기관에서 얻은 SSL 인증서의 이름과 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-150">Click **Browse** and specify the location and name of the SSL certificate from the public certification authority.</span></span>
    
17. <span data-ttu-id="e6c82-151">대화 상자가 나타나면 인증서 암호를 입력 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-151">When prompted, type the certificate password, and then click **OK**.</span></span>
    
18. <span data-ttu-id="e6c82-152">**주체 이름** 및 **페더레이션 서비스 이름** 으로 페더레이션 서비스 FQDN 설정 하 고 **다음**을 클릭 한 다음 되었는지 확인</span><span class="sxs-lookup"><span data-stu-id="e6c82-152">Verify that the **Subject Name** and **Federation Service Name** are set to your federation service FQDN, and then click **Next**.</span></span>
    
19. <span data-ttu-id="e6c82-153">**AD FS 서버** 페이지에서 첫번째 AD FS 서버 이름 (테이블 M-항목 4-가상 컴퓨터 이름 열)를 입력 한 다음 **추가**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-153">On the **AD FS servers** page, type your first AD FS server's name (Table M - Item 4 - Virtual machine name column), and then click **Add**.</span></span>
    
20. <span data-ttu-id="e6c82-154">두번째 AD FS 서버 이름 (테이블 M-항목 5-가상 컴퓨터 이름 열)를 입력 하 고 **추가**클릭 한 다음 **다음**을 클릭 한 다음 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-154">Type your second AD FS server's name (Table M - Item 5 - Virtual machine name column), click **Add**, and then click **Next**.</span></span>
    
21. <span data-ttu-id="e6c82-155">**웹 응용 프로그램 프록시 서버** 페이지에서 첫번째 웹 응용 프로그램 프록시 서버의 이름 (테이블 M-항목 6-가상 컴퓨터 이름 열)를 입력 한 다음 **추가**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-155">On the **Web Application Proxy servers** page, type your first web application proxy server's name (Table M - Item 6 - Virtual machine name column), and then click **Add**.</span></span>
    
22. <span data-ttu-id="e6c82-156">두번째 웹 응용 프로그램 프록시 서버의 이름 (테이블 M-항목 7-가상 컴퓨터 이름 열)를 입력 하 고 **추가**클릭 한 다음 **다음**을 클릭 한 다음 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-156">Type your second web application proxy server's name (Table M - Item 7 - Virtual machine name column), click **Add**, and then click **Next**.</span></span>
    
23. <span data-ttu-id="e6c82-157">**도메인 관리자 자격 증명** 페이지에서 사용자 이름 및 도메인 관리자 계정의 암호를 입력 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-157">On the **Domain Administrator credentials** page, type the user name and password of a domain administrator account, and then click **Next**.</span></span>
    
24. <span data-ttu-id="e6c82-158">**AD FS 서비스 계정** 페이지에서 사용자 이름 및 엔터프라이즈 관리자 계정의 암호를 입력 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-158">On the **AD FS service account** page, type the user name and password of an enterprise administrator account, and then click **Next**.</span></span>
    
25. <span data-ttu-id="e6c82-159">**도메인** **Azure AD 도메인** 페이지에서 조직의 DNS 도메인 이름을 선택 하 고 ****을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-159">On the **Azure AD Domain** page, in **Domain**, select your organization's DNS domain name, and then click **Next**.</span></span>
    
26. <span data-ttu-id="e6c82-160">**구성 준비 완료** 페이지에서 **설치**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-160">On the **Ready to configure** page, click **Install**.</span></span>
    
27. <span data-ttu-id="e6c82-p105">**설치 완료** 페이지에서 **확인**을 클릭 합니다. 인트라넷 및 인터넷 모두 있는지 여부를 나타내는 두 메시지를 참조 해야 구성을 성공적으로 확인 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-p105">On the **Installation complete** page, click **Verify**. You should see two messages indicating that both the intranet and Internet configuration was successfully verified.</span></span>
    
  - <span data-ttu-id="e6c82-163">인트라넷 메시지 AD FS 서버에 대 한 Azure 내부 부하 분산 장치의 개인 IP 주소를 나열 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-163">The intranet message should list the private IP address of your Azure internal load balancer for your AD FS servers.</span></span>
    
  - <span data-ttu-id="e6c82-164">인터넷 메시지 웹 응용 프로그램 프록시 서버에 대 한 Azure 인터넷 연결 부하 분산 장치의 공용 IP 주소를 나열 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-164">The Internet message should list the public IP address of your Azure Internet-facing load balancer for your web application proxy servers.</span></span>
    
28. <span data-ttu-id="e6c82-165">**설치 완료** 페이지에서 **끝내기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-165">On the **Installation complete** page, click **Exit**.</span></span>
    
<span data-ttu-id="e6c82-166">여기에서는 서버에 대 한 자리 표시자 이름 사용 하 여 최종 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-166">Here is the final configuration, with placeholder names for the servers.</span></span>
  
<span data-ttu-id="e6c82-167">**단계 5: 높은 가용성의 최종 구성을 페더레이션 Azure에서 인증 인프라**</span><span class="sxs-lookup"><span data-stu-id="e6c82-167">**Phase 5: The final configuration of a high availability federated authentication infrastructure in Azure**</span></span>

![Azure에서 고가용성 Office 365 페더레이션 인증 인프라의 최종 구성.](images/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
<span data-ttu-id="e6c82-169">Azure의 Office 365에 대 한 고가용성 연결 된 인증 인프라가 완료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6c82-169">Your high availability federated authentication infrastructure for Office 365 in Azure is complete.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e6c82-170">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e6c82-170">See Also</span></span>

[<span data-ttu-id="e6c82-171">Azure에서 Office 365용 고가용성 페더레이션 인증 배포</span><span class="sxs-lookup"><span data-stu-id="e6c82-171">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="e6c82-172">Office 365 개발/테스트 환경에 대 한 페더레이션된 id</span><span class="sxs-lookup"><span data-stu-id="e6c82-172">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="e6c82-173">클라우드 채택 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="e6c82-173">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="e6c82-174">Office 365용 페더레이션 ID</span><span class="sxs-lookup"><span data-stu-id="e6c82-174">Federated identity for Office 365</span></span>](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


