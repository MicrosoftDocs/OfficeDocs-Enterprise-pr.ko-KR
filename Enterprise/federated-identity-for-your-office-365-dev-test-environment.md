---
title: Office 365 개발/테스트 환경용 페더레이션 ID
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/09/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 65a6d687-a16a-4415-9fd5-011ba9c5fd80
description: '요약: Office 365 개발/테스트 환경에 대한 페더레이션 인증을 구성합니다.'
ms.openlocfilehash: b016e168ac1bfcf180c1c4ba04846416dbd098f4
ms.sourcegitcommit: dffbcfb1cbc9776a29229a787c1eab4192e55cff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/28/2019
ms.locfileid: "30948639"
---
# <a name="federated-identity-for-your-office-365-devtest-environment"></a><span data-ttu-id="3225e-103">Office 365 개발/테스트 환경용 페더레이션 ID</span><span class="sxs-lookup"><span data-stu-id="3225e-103">Federated identity for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="3225e-104">**요약:** Office 365 개발/테스트 환경에 대한 페더레이션 인증을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-104">**Summary:** Configure federated authentication for your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="3225e-p101">Office 365은 페더레이션 ID를 지원합니다. 즉, 자격 증명 자체의 유효성 검사를 수행하는 대신, Office 365는 Office 365가 신뢰하는 페더레이션 인증 서버에 사용자를 연결하는 것을 의미합니다. 사용자의 자격 증명이 올바른 경우 페더레이션 인증 서버는 보안 토큰을 발급하며, 그런 후에 클라이언트는 인증의 증거로 해당 보안 토큰을 Office 365로 전송합니다. 페더레이션 ID를 사용하면 Office 365 구독과 고급 인증 및 보안 시나리오의 부하 부담을 줄이고 강화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-p101">Office 365 supports federated identity. This means that instead of performing the validation of credentials itself, Office 365 refers the connecting user to a federated authentication server that Office 365 trusts. If the user's credentials are correct, the federated authentication server issues a security token that the client then sends to Office 365 as proof of authentication. Federated identity allows for the offloading and scaling up of authentication for an Office 365 subscription and advanced authentication and security scenarios.</span></span>
  
<span data-ttu-id="3225e-109">이 문서에서는 Office 365 개발/테스트 환경에 대한 페더레이션 인증을 구성하여 다음과 같은 결과를 얻는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-109">This article describes how you can configure federated authentication for the Office 365 dev/test environment, resulting in the following:</span></span>
  
<span data-ttu-id="3225e-110">**그림 1: Office 365 개발/테스트 환경에 대한 페더레이션 인증**</span><span class="sxs-lookup"><span data-stu-id="3225e-110">**Figure 1: The federated authentication for Office 365 dev/test environment**</span></span>

![Office 365 개발/테스트 환경에 대한 페더레이션 인증](media/f50039e4-796a-42c0-bfdc-87c2026b1579.png)
  
<span data-ttu-id="3225e-112">그림 1에 나오는 구성은 다음으로 이루어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-112">The configuration shown in Figure 1 consists of:</span></span> 
  
- <span data-ttu-id="3225e-113">Office 365 E5 평가판 구독: 만든 날로부터 30일 이후에 만료됩니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-113">An Office 365 E5 Trial Subscription, which expires 30 days from when you create it.</span></span>
    
- <span data-ttu-id="3225e-p102">인터넷에 연결된 간소화된 조직 인트라넷: Azure Virtual Network의 하위 집합에 있는 5개의 가상 머신(DC1, APP1, CLIENT1, ADFS1 및 PROXY1)으로 구성되어 있습니다. Azure AD Connect가 APP1에서 실행되며 Windows Server AD 도메인의 계정 목록을 Office 365와 동기화합니다. PROXY1은 들어오는 인증 요청을 수신합니다. ADFS1은 DC1을 사용하여 자격 증명이 유효한지 검사하고 보안 토큰을 발급합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-p102">A simplified organization intranet connected to the Internet, consisting of five virtual machines on a subnet of an Azure virtual network (DC1, APP1, CLIENT1, ADFS1, and PROXY1). Azure AD Connect runs on APP1 to synchronize the list of accounts in the Windows Server AD domain to Office 365. PROXY1 receives the incoming authentication requests. ADFS1 validates credentials with DC1 and issues security tokens.</span></span>
    
<span data-ttu-id="3225e-118">이 개발/테스트 환경의 5가지 주요 설정 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-118">There are five phases to setting up this dev/test environment:</span></span>
  
1. <span data-ttu-id="3225e-119">DirSync를 사용하여 시뮬레이트된 엔터프라이즈 Office 365 개발/테스트 환경 만들기</span><span class="sxs-lookup"><span data-stu-id="3225e-119">Create the simulated enterprise Office 365 dev/test environment with DirSync.</span></span>
    
2. <span data-ttu-id="3225e-120">AD FS 서버(ADFS1)를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-120">Create the AD FS server (ADFS1).</span></span>
    
3. <span data-ttu-id="3225e-121">웹 프록시 서버(PROXY1)를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-121">Create the web proxy server (PROXY1).</span></span>
    
4. <span data-ttu-id="3225e-122">자체 서명된 인증서를 만들고 ADFS1과 PROXY1을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-122">Create a self-signed certificate and configure ADFS1 and PROXY1.</span></span>
    
5. <span data-ttu-id="3225e-123">페더레이션 ID에 대해 Office 365를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-123">Configure Office 365 for federated identity.</span></span>
    
<span data-ttu-id="3225e-124">프로덕션 환경의 Azure에서 Office 365용 페더레이션 인증을 배포하는 과정을 단계별로 진행하려면 [Azure에서 Office 365용 고가용성 페더레이션 인증 배포](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3225e-124">To step through a production deployment of federated authentication for Office 365 in Azure, see [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="3225e-125">Azure 평가판 구독으로는 이 개발/테스트 환경을 구성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-125">You cannot configure this dev/test environment with an Azure Trial subscription.</span></span> 
  
> [!TIP]
> <span data-ttu-id="3225e-126">[여기](http://aka.ms/catlgstack)를 클릭하여 One Microsoft 클라우드 테스트 랩 가이드 스택의 모든 문서에 대한 가상 맵을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-126">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-the-simulated-enterprise-office-365-devtest-environment-with-dirsync"></a><span data-ttu-id="3225e-127">1단계: DirSync를 사용하여 시뮬레이트된 엔터프라이즈 Office 365 개발/테스트 환경 만들기</span><span class="sxs-lookup"><span data-stu-id="3225e-127">Phase 1: Create the simulated enterprise Office 365 dev/test environment with DirSync</span></span>

<span data-ttu-id="3225e-128">[Office 365 개발/테스트 환경에 대한 디렉터리 동기화](dirsync-for-your-office-365-dev-test-environment.md)의 지침에 따라 APP1을 DirSync 서버로 사용하여 시뮬레이트된 엔터프라이즈 Office 365 개발/테스트 환경을 만들고, DC1에서 Office 365와 Windows Server AD 계정 간에 ID를 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-128">Follow the instructions in [Directory synchronization for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md) to create the simulated enterprise Office 365 dev/test environment with APP1 as the DirSync server and synchronized identity between Office 365 and the Windows Server AD accounts on DC1.</span></span>
  
<span data-ttu-id="3225e-p103">다음으로, 현재 도메인 이름에 따라 새 공용 DNS 도메인 이름을 만든 후 Office 365 구독에 추가합니다. 이름 **testlab.**\<공용 도메인>을 사용하는 것이 좋습니다. 예를 들어, 공용 도메인 이름이 contoso.com이면 공용 도메인 이름 testlab.contoso.com을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-p103">Next, create a new public DNS domain name based on your current domain name and add it to your Office 365 subscription. We recommend using the name **testlab.**\<your public domain>. For example, if your public domain name is contoso.com, add the public domain name testlab.contoso.com.</span></span>
  
<span data-ttu-id="3225e-132">DNS 공급자에 올바른 DNS 레코드를 만들고 Office 365 평가판 구독에 도메인을 추가하는 방법에 대한 지침은 [Office 365에 사용자 및 도메인 추가](https://support.office.com/article/Add-users-and-domain-to-Office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3225e-132">For instructions on how to create the correct DNS records in your DNS provider and add the domain to your Office 365 trial subscription, see [Add users and domain to Office 365](https://support.office.com/article/Add-users-and-domain-to-Office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611).</span></span> 
  
<span data-ttu-id="3225e-133">구성 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-133">Here is your resulting configuration.</span></span>
  
<span data-ttu-id="3225e-134">**그림 2: Office 365 개발/테스트 환경에 대한 디렉터리 동기화**</span><span class="sxs-lookup"><span data-stu-id="3225e-134">**Figure 2: Directory synchronization for the Office 365 dev/test environment**</span></span>

![디렉터리 동기화를 사용하는 Office 365 개발/테스트 환경](media/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="3225e-136">그림 2에서는 Azure Virtual Network에 Office 365와 CLIENT1, APP1 및 DC1 가상 머신이 포함된 Office 365 개발/테스트 환경에 대한 디렉터리 동기화를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-136">Figure 2 shows the directory synchronizationc for Office 365 dev/test environment, which includes Office 365 and CLIENT1, APP1, and DC1 virtual machines in an Azure virtual network.</span></span>
  
## <a name="phase-2-create-the-ad-fs-server"></a><span data-ttu-id="3225e-137">2단계: AD FS 서버 만들기</span><span class="sxs-lookup"><span data-stu-id="3225e-137">Phase 2: Create the AD FS server</span></span>

<span data-ttu-id="3225e-138">AD FS 서버는 Office 365와 DC1에 호스트된 corp.contoso.com 도메인의 계정 간에 페더레이션 인증을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-138">An AD FS server provides federated authentication between Office 365 and the accounts in the corp.contoso.com domain hosted on DC1.</span></span>
  
<span data-ttu-id="3225e-139">ADFS1에 대한 Azure Virtual Machine을 만들려면 구독 및 리소스 그룹의 이름, 기본 구성에 대한 Azure 위치를 입력한 후 로컬 컴퓨터의 Azure PowerShell 명령 프롬프트에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-139">To create an Azure virtual machine for ADFS1, fill in the name of your subscription and the resource group and Azure location for your Base Configuration, and then run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$subscrName="<your Azure subscription name>"
$rgName="<the resource group name of your Base Configuration>"
Connect-AzAccount
Select-AzSubscription -SubscriptionName $subscrName
$staticIP="10.0.0.100"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip = New-AzPublicIpAddress -Name ADFS1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic = New-AzNetworkInterface -Name ADFS1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName ADFS1 -VMSize Standard_D2_v2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for ADFS1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName ADFS1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "ADFS-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```
<!--
> [!TIP]
> Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-f79bc2c2?redir=0) for a text file that has all the PowerShell commands in this article.
-->
  
<span data-ttu-id="3225e-140">다음으로, [Azure Portal](http://portal.azure.com)에서 ADFS1 로컬 관리자 계정 이름과 암호를 사용하여 ADFS1 가상 머신에 연결하고 Windows PowerShell 명령 프롬프트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-140">Next, use the [Azure portal](http://portal.azure.com) to connect to the ADFS1 virtual machine using the ADFS1 local administrator account name and password, and then open a Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="3225e-141">ADFS1과 DC1 사이의 이름 확인 및 네트워크 통신을 확인하려면 **ping dc1.corp.contoso.com** 명령을 실행하고 4개의 응답이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-141">To check name resolution and network communication between ADFS1 and DC1, run the **ping dc1.corp.contoso.com** command and check that there are four replies.</span></span>
  
<span data-ttu-id="3225e-142">다음으로, ADFS1의 Windows PowerShell 프롬프트에 다음 명령을 사용하여 ADFS1 가상 머신을 CORP 도메인에 가입합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-142">Next, join the ADFS1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt on ADFS1.</span></span>
  
```
$cred=Get-Credential -UserName "CORP\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

<span data-ttu-id="3225e-143">구성 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-143">Here is your resulting configuration.</span></span>
  
<span data-ttu-id="3225e-144">**그림 3: AD FS 서버 추가**</span><span class="sxs-lookup"><span data-stu-id="3225e-144">**Figure 3: Adding the AD FS server**</span></span>

![AD FS 서버가 Office 365에 대한 DirSync 개발/테스트 환경에 추가됨](media/da82f39e-426d-41e2-842a-c13b382d63d5.png)
  
<span data-ttu-id="3225e-146">그림 3은 Office 365 개발/테스트 환경에 대한 DirSync에 ADFS1 서버를 추가하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-146">Figure 3 shows the addition of the ADFS1 server to the DirSync for Office 365 dev/test environment.</span></span>
  
## <a name="phase-3-create-the-web-proxy-server"></a><span data-ttu-id="3225e-147">3단계: 웹 프록시 서버 만들기</span><span class="sxs-lookup"><span data-stu-id="3225e-147">Phase 3: Create the web proxy server</span></span>

<span data-ttu-id="3225e-148">PROXY1은 인증을 시도하는 사용자와 ADFS1 간의 인증 메시지 프록시를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-148">PROXY1 provides proxying of authentication messages between users trying to authenticate and ADFS1.</span></span>
  
<span data-ttu-id="3225e-149">PROXY1에 대한 Azure Virtual Machine을 만들려면 리소스 그룹의 이름과 Azure 위치를 입력하고, 로컬 컴퓨터의 Azure PowerShell 명령 프롬프트에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-149">To create an Azure virtual machine for PROXY1, fill in the name of your resource group and Azure location, and then run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<the resource group name of your Base Configuration>"
$staticIP="10.0.0.101"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip = New-AzPublicIpAddress -Name PROXY1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Static
$nic = New-AzNetworkInterface -Name PROXY1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName PROXY1 -VMSize Standard_D2_v2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for PROXY1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName PROXY1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "PROXY1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> <span data-ttu-id="3225e-150">PROXY1은 이 머신을 가리키는 공용 DNS 레코드를 만들게 되고, PROXY1 가상 머신을 다시 시작할 때 변경되지 않아야 하므로 고정 공용 IP 주소가 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-150">PROXY1 is assigned a static public IP address because you will create a public DNS record that points to it and it must not change when you restart the PROXY1 virtual machine.</span></span> 
  
<span data-ttu-id="3225e-p104">다음으로, CorpNet 서브넷에 대한 네트워크 보안 그룹에 인터넷에서 PROXY1의 개인 IP 주소 및 TCP 포트 443으로의 요청되지 않은 인바운드 트래픽을 허용하는 규칙을 추가합니다. 로컬 컴퓨터의 Azure PowerShell 명령 프롬프트에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-p104">Next, add a rule to the network security group for the CorpNet subnet to allow unsolicited inbound traffic from the Internet to PROXY1's private IP address and TCP port 443. Run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<the resource group name of your Base Configuration>"
Get-AzNetworkSecurityGroup -Name CorpNet -ResourceGroupName $rgName | Add-AzNetworkSecurityRuleConfig -Name "HTTPS-to-PROXY1" -Description "Allow TCP 443 to PROXY1" -Access "Allow" -Protocol "Tcp" -Direction "Inbound" -Priority 101 -SourceAddressPrefix "Internet" -SourcePortRange "*" -DestinationAddressPrefix "10.0.0.101" -DestinationPortRange "443" | Set-AzNetworkSecurityGroup
```

<span data-ttu-id="3225e-153">다음으로, [Azure Portal](http://portal.azure.com)에서 PROXY1 로컬 관리자 계정 이름과 암호를 사용하여 PROXY1 가상 머신에 연결하고 PROXY1에서 Windows PowerShell 명령 프롬프트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-153">Next, use the [Azure portal](http://portal.azure.com) to connect to the PROXY1 virtual machine using the PROXY1 local administrator account name and password, and then open a Windows PowerShell command prompt on PROXY1.</span></span>
  
<span data-ttu-id="3225e-154">RPOXY1과 DC1 사이의 이름 확인 및 네트워크 통신을 확인하려면 **ping dc1.corp.contoso.com** 명령을 실행하고 4개의 응답이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-154">To check name resolution and network communication between PROXY1 and DC1, run the **ping dc1.corp.contoso.com** command and check that there are four replies.</span></span>
  
<span data-ttu-id="3225e-155">다음으로, PROXY1의 Windows PowerShell 프롬프트에 다음 명령을 사용하여 PROXY1 가상 머신을 CORP 도메인에 가입합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-155">Next, join the PROXY1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt on PROXY1.</span></span>
  
```
$cred=Get-Credential -UserName "CORP\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

<span data-ttu-id="3225e-156">로컬 컴퓨터에서 다음 Azure PowerShell 명령을 사용하여 PROXY1의 공용 IP 주소를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-156">Display the public IP address of PROXY1 with these Azure PowerShell commands on your local computer:</span></span>
  
```
Write-Host (Get-AzPublicIpaddress -Name "PROXY1-PIP" -ResourceGroup $rgName).IPAddress
```

<span data-ttu-id="3225e-p105">다음으로, 공용 DNS 공급자를 사용하고, **Write-Host** 명령에 의해 표시되는 IP 주소로 확인되는 **fs.testlab.**\<DNS 호스트 이름>에 대한 새 공용 DNS A 레코드를 만듭니다. **fs.testlab.**\<DNS 도메인 이름>을 이제부터 *페더레이션 서비스 FQDN*이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-p105">Next, work with your public DNS provider and create a new public DNS A record for **fs.testlab.**\<your DNS domain name> that resolves to the IP address displayed by the **Write-Host** command. The **fs.testlab.**\<your DNS domain name> is hereafter referred to as the  *federation service FQDN*  .</span></span>
  
<span data-ttu-id="3225e-159">다음으로, [Azure Portal](http://portal.azure.com)에서 CORP\\User1 자격 증명을 사용하여 DC1 가상 머신에 연결하고 관리자 수준 Windows PowerShell 명령 프롬프트에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-159">Next, use the [Azure portal](http://portal.azure.com) to connect to the DC1 virtual machine using the CORP\\User1 credentials, and then run the following commands at an administrator-level Windows PowerShell command prompt:</span></span>
  
```
$testZone="<the FQDN of your testlab domain from phase 1, example: testlab.contoso.com>"
$testZoneFile= $testZone + ".dns"
Add-DnsServerPrimaryZone -Name $testZone -ZoneFile $testZoneFile
Add-DnsServerResourceRecordA -Name "fs" -ZoneName $testZone -AllowUpdateAny -IPv4Address "10.0.0.100" -TimeToLive 01:00:00
```

<span data-ttu-id="3225e-160">이러한 명령은 Azure Virtual Network의 가상 머신이 ADFS1의 개인 IP 주소로 확인될 수 있는 페더레이션 서비스에 대한 DNS A 레코드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-160">These commands create a DNS A record for your federation service FQDN that virtual machines on the Azure virtual network can resolve to ADFS1's private IP address.</span></span>
  
<span data-ttu-id="3225e-161">구성 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-161">Here is your resulting configuration.</span></span>
  
<span data-ttu-id="3225e-162">**그림 4: 웹 응용 프로그램 프록시 서버 추가**</span><span class="sxs-lookup"><span data-stu-id="3225e-162">**Figure 4: Adding the web application proxy server**</span></span>

![Office 365 개발/테스트 환경에 대한 DirSync에 추가된 웹 응용 프로그램 프록시 서버](media/f50039e4-796a-42c0-bfdc-87c2026b1579.png)
  
<span data-ttu-id="3225e-164">그림 4에서는 PROXY1 서버를 추가하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-164">Figure 4 shows the addition of the PROXY1 server.</span></span>
  
## <a name="phase-4-create-a-self-signed-certificate-and-configure-adfs1-and-proxy1"></a><span data-ttu-id="3225e-165">4단계: 자체 서명된 인증서를 만들고 ADFS1 및 PROXY1을 구성</span><span class="sxs-lookup"><span data-stu-id="3225e-165">Phase 4: Create a self-signed certificate and configure ADFS1 and PROXY1</span></span>

<span data-ttu-id="3225e-166">이 단계에서는 페더레이션 서비스 FQDN의 자체 서명된 디지털 인증서를 만들고 ADFS1 및 PROXY1을 AD FS 팜으로 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-166">In this phase, you create a self-signed digital certificate for your federation service FQDN and configure ADFS1 and PROXY1 as an AD FS farm.</span></span>
  
<span data-ttu-id="3225e-167">먼저, [Azure Portal](http://portal.azure.com)에서 CORP\\User1 자격 증명을 사용하여 DC1 가상 머신에 연결하고 관리자 수준 Windows PowerShell 명령 프롬프트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-167">First, use the [Azure portal](http://portal.azure.com) to connect to the DC1 virtual machine using the CORP\\User1 credentials, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="3225e-168">다음으로, DC1의 Windows PowerShell 명령 프롬프트에서 다음 명령을 사용하여 AD FS 서비스 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-168">Next, create AD FS service account with this command at the Windows PowerShell command prompt on DC1:</span></span>
  
```
New-ADUser -SamAccountName ADFS-Service -AccountPassword (read-host "Set user password" -assecurestring) -name "ADFS-Service" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

<span data-ttu-id="3225e-p106">이 명령은 계정 암호를 묻는 메시지를 표시합니다. 강력한 암호를 선택하고 안전한 위치에 기록해둡니다. 이 단계와 5단계에서 해당 암호가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-p106">Note that this command prompts you to supply the account password. Choose a strong password and record it in a secured location. You will need it for this phase and Phase 5.</span></span>
  
<span data-ttu-id="3225e-p107">[Azure Portal](http://portal.azure.com)에서 CORP\\User1 자격 증명을 사용하여 ADFS1 가상 머신에 연결합니다. ADFS1에서 관리자 수준 Windows PowerShell 명령 프롬프트를 열고 페더레이션 서비스 FQDN을 입력한 후 다음 명령을 실행하여 자체 서명된 인증서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-p107">Use the [Azure portal](http://portal.azure.com) to connect to the ADFS1 virtual machine using the CORP\\User1 credentials. Open an administrator-level Windows PowerShell command prompt on ADFS1, fill in your federation service FQDN, and then run these commands to create a self-signed certificate:</span></span>
  
```
$fedServiceFQDN="<federation service FQDN>"
New-SelfSignedCertificate -DnsName $fedServiceFQDN -CertStoreLocation "cert:\LocalMachine\My"
New-Item -path c:\Certs -type directory
New-SmbShare -name Certs -path c:\Certs -changeaccess CORP\User1
```

<span data-ttu-id="3225e-174">다음 단계를 사용하여 새 자체 서명된 인증서를 파일로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-174">Next, use these steps to save the new self-signed certificate as a file.</span></span>
  
1. <span data-ttu-id="3225e-175">**시작**을 클릭하고 **mmc.exe**를 입력한 후 **Enter** 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-175">Click **Start**, type **mmc.exe**, and then press **Enter**.</span></span>
    
2. <span data-ttu-id="3225e-176">**파일 > 스냅인 추가/제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-176">Click **File > Add/Remove Snap-in**.</span></span>
    
3. <span data-ttu-id="3225e-177">**스냅인 추가 또는 제거**의 사용 가능한 스냅인 목록에서 **인증서**를 두 번 클릭하고 **컴퓨터 계정**을 클릭한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-177">In **Add or Remove Snap-ins**, double-click **Certificates** in the list of available snap-ins, click **Computer account**, and then click **Next**.</span></span>
    
4. <span data-ttu-id="3225e-178">**컴퓨터 선택**에서 **마침**을 클릭한 후 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-178">In **Select Computer**, click **Finish**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="3225e-179">트리 창에서 **인증서(로컬 컴퓨터) > 개인 > 인증서**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-179">In the tree pane, open **Certificates (Local Computer) > Personal > Certificates**.</span></span>
    
6. <span data-ttu-id="3225e-180">페더레이션 서비스 FQDN을 갖는 인증서를 마우스 오른쪽 단추로 클릭하고 **모든 작업**을 클릭한 후 **내보내기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-180">Right-click the certificate with your federation service FQDN, click **All tasks**, and then click **Export**.</span></span>
    
7. <span data-ttu-id="3225e-181">**시작** 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-181">On the **Welcome** page, click **Next**.</span></span>
    
8. <span data-ttu-id="3225e-182">**개인 키 내보내기** 페이지에서 **예**를 클릭하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-182">On the **Export Private Key** page, click **Yes**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="3225e-183">**파일 내보내기 형식** 페이지에서 **확장된 모든 속성 내보내기**를 클릭한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-183">On the **Export File Format** page, click **Export all extended properties**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="3225e-184">**보안** 페이지에서 **암호**를 클릭하고 **암호** 및 **암호 확인**에 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-184">On the **Security** page, click **Password** and type a password in **Password** and **Confirm password.**</span></span>
    
11. <span data-ttu-id="3225e-185">**내보낼 파일** 페이지에서 **찾아보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-185">On the **File to Export** page, click **Browse**.</span></span>
    
12. <span data-ttu-id="3225e-186">**C:\\Certs** 폴더로 이동한 후 **파일 이름**에 **SSL**을 입력하고 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-186">Browse to the **C:\\Certs** folder, type **SSL** in **File name**, and then click **Save.**</span></span>
    
13. <span data-ttu-id="3225e-187">**내보낼 파일** 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-187">On the **File to Export** page, click **Next**.</span></span>
    
14. <span data-ttu-id="3225e-p108">**인증서 내보내기 마법사 완료** 페이지에서 **마침**을 클릭합니다. 메시지가 표시되면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-p108">On the **Completing the Certificate Export Wizard** page, click **Finish**. When prompted, click **OK**.</span></span>
    
<span data-ttu-id="3225e-190">다음으로, ADFS1의 Windows PowerShell 명령 프롬프트에서 다음 명령을 사용하여 AD FS 서비스를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-190">Next, install the AD FS service with this command at the Windows PowerShell command prompt on ADFS1:</span></span>
  
```
Install-WindowsFeature ADFS-Federation -IncludeManagementTools
```

<span data-ttu-id="3225e-191">설치가 완료될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-191">Wait for the installation to complete.</span></span>
  
<span data-ttu-id="3225e-192">다음으로, 다음 단계에 따라 AD FS 서비스를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-192">Next, configure the AD FS service with these steps:</span></span>
  
1. <span data-ttu-id="3225e-193">**시작**을 클릭하고 **서버 관리자** 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-193">Click **Start**, and then click the **Server Manager** icon.</span></span>
    
2. <span data-ttu-id="3225e-194">서버 관리자의 트리 창에서 **AD FS**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-194">In the tree pane of Server Manager, click **AD FS**.</span></span>
    
3. <span data-ttu-id="3225e-195">맨 위에 있는 도구 모음에서 주황색 주의 기호를 클릭한 후 **이 서버에 페더레이션 서비스 구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-195">In the tool bar at the top, click the orange caution symbol, and then click **Configure the federation service on this server**.</span></span>
    
4. <span data-ttu-id="3225e-196">ADFS(Active Directory Federation Services) 구성 마법사의 **시작** 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-196">On the **Welcome** page of the Active Directory Federation Services Configuration Wizard, click **Next**.</span></span>
    
5. <span data-ttu-id="3225e-197">**AD DS에 연결** 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-197">On the **Connect to AD DS** page, click **Next**.</span></span>
    
6. <span data-ttu-id="3225e-198">**서비스 속성 지정** 페이지에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-198">On the **Specify Service Properties** page:</span></span>
    
  - <span data-ttu-id="3225e-199">**SSL 인증서**에 대해 아래쪽 화살표를 클릭하고 페더레이션 서비스 FQDN의 이름을 갖는 인증서를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-199">For **SSL Certificate**, click the down arrow, and then click the certificate with the name of your federation service FQDN.</span></span>
    
  - <span data-ttu-id="3225e-200">**페더레이션 서비스 표시 이름**에 가상의 조직 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-200">In **Federation Service Display Name**, type the name of your fictional organization.</span></span>
    
  - <span data-ttu-id="3225e-201">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-201">Click **Next**.</span></span>
    
7. <span data-ttu-id="3225e-202">**서비스 계정 지정** 페이지에서 **계정 이름**에 대해 **선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-202">On the **Specify Service Account** page, click **Select** for **Account name**.</span></span>
    
8. <span data-ttu-id="3225e-203">**사용자 또는 서비스 계정 선택**에서 **ADFS-Service**를 입력하고 **이름 확인**을 클릭한 후 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-203">In **Select User or Service Account**, type **ADFS-Service**, click **Check Names**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="3225e-204">**계정 암호**에서 ADFS-Service 계정의 암호를 입력한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-204">In **Account Password**, type the password for the ADFS-Service account, and then click **Next**.</span></span>
    
10. <span data-ttu-id="3225e-205">**구성 데이터베이스 지정** 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-205">On the **Specify Configuration Database** page, click **Next**.</span></span>
    
11. <span data-ttu-id="3225e-206">**옵션 검토** 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-206">On the **Review Options** page, click **Next**.</span></span>
    
12. <span data-ttu-id="3225e-207">**필수 조건 확인** 페이지에서 **구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-207">On the **Pre-requisite Checks** page, click **Configure**.</span></span>
    
13. <span data-ttu-id="3225e-208">**결과** 페이지에서 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-208">On the **Results** page, click **Close**.</span></span>
    
14. <span data-ttu-id="3225e-209">**시작**을 클릭하고 전원 아이콘을 클릭한 후 **다시 시작**을 클릭하고 **계속**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-209">Click **Start**, click the power icon, click **Restart**, and then click **Continue**.</span></span>
    
<span data-ttu-id="3225e-210">[Azure Portal](http://portal.azure.com)에서 CORP\\User1 계정 자격 증명을 사용하여 PROXY1에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-210">From the [Azure portal](http://portal.azure.com), connect to PROXY1 with the CORP\\User1 account credentials.</span></span>
  
<span data-ttu-id="3225e-211">그런 후 다음 단계를 사용하여 자체 서명된 인증서를 설치하고 PROXY1을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-211">Next, use these steps to install the self-signed certificate and configure PROXY1.</span></span>
  
1. <span data-ttu-id="3225e-212">**시작**을 클릭하고 **mmc.exe**를 입력한 후 **Enter** 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-212">Click **Start**, type **mmc.exe**, and then press **Enter**.</span></span>
    
2. <span data-ttu-id="3225e-213">**파일 > 스냅인 추가/제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-213">Click **File > Add/Remove Snap-in**.</span></span>
    
3. <span data-ttu-id="3225e-214">**스냅인 추가 또는 제거**의 사용 가능한 스냅인 목록에서 **인증서**를 두 번 클릭하고 **컴퓨터 계정**을 클릭한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-214">In **Add or Remove Snap-ins**, double-click **Certificates** in the list of available snap-ins, click **Computer account**, and then click **Next**.</span></span>
    
4. <span data-ttu-id="3225e-215">**컴퓨터 선택**에서 **마침**을 클릭한 후 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-215">In **Select Computer**, click **Finish**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="3225e-216">트리 창에서 **인증서(로컬 컴퓨터) > 개인 > 인증서**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-216">In the tree pane, open **Certificates (Local Computer) > Personal > Certificates**.</span></span>
    
6. <span data-ttu-id="3225e-217">**개인**을 마우스 오른쪽 단추로 클릭하고 **모든 작업**을 클릭한 후 **가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-217">Right-click **Personal**, click **All tasks**, and then click **Import**.</span></span>
    
7. <span data-ttu-id="3225e-218">**시작** 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-218">On the **Welcome** page, click **Next**.</span></span>
    
8. <span data-ttu-id="3225e-219">**가져올 파일** 페이지에서 **\\\\adfs1\\certs\\ssl.pfx**를 클릭한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-219">On the **File to Import** page, type **\\\\adfs1\\certs\\ssl.pfx**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="3225e-220">**개인 키 보호** 페이지의 **암호**에서 인증서 암호를 입력하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-220">On the **Private key protection** page, type the certificate password in **Password**, and then click **Next.**</span></span>
    
10. <span data-ttu-id="3225e-221">**인증서 저장소** 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-221">On the **Certificate store** page, click **Next.**</span></span>
    
11. <span data-ttu-id="3225e-222">**완료** 페이지에서 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-222">On the **Completing** page, click **Finish**.</span></span>
    
12. <span data-ttu-id="3225e-223">**인증서 저장소** 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-223">On the **Certificate Store** page, click **Next**.</span></span>
    
13. <span data-ttu-id="3225e-224">메시지가 표시되면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-224">When prompted, click **OK**.</span></span>
    
14. <span data-ttu-id="3225e-225">트리 창에서 **인증서**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-225">Click **Certificates** in the tree pane.</span></span>
    
15. <span data-ttu-id="3225e-226">인증서를 마우스 오른쪽 단추로 클릭하고 **복사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-226">Right-click the certificate, and then click **Copy**.</span></span>
    
16. <span data-ttu-id="3225e-227">트리 창에서 **신뢰할 수 있는 루트 인증 기관 > 인증서**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-227">In the tree pane, open **Trusted Root Certification Authorities > Certificates**.</span></span>
    
17. <span data-ttu-id="3225e-228">설치된 인증서 목록 아래로 마우스 포인터를 가져간 후 마우스 오른쪽 단추를 클릭하고 **붙여넣기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-228">Move your mouse pointer below the list of installed certificates, right-click, and then click **Paste**.</span></span>
    
<span data-ttu-id="3225e-229">관리자 수준 PowerShell 명령 프롬프트를 열고 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-229">Open an administrator-level PowerShell command prompt and run the following command:</span></span>
  
```
Install-WindowsFeature Web-Application-Proxy -IncludeManagementTools
```

<span data-ttu-id="3225e-230">설치가 완료될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-230">Wait for the installation to complete.</span></span>
  
<span data-ttu-id="3225e-231">다음 단계를 사용하여 ADFS1을 해당 페더레이션 서버로 사용하도록 웹 응용 프로그램 프록시 서비스를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-231">Use these steps to configure the web application proxy service to use ADFS1 as its federation server:</span></span>
  
1. <span data-ttu-id="3225e-232">**시작**을 클릭하고 **서버 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-232">Click **Start**, and then click **Server Manager**.</span></span>
    
2. <span data-ttu-id="3225e-233">트리 창에서 **원격 액세스**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-233">In the tree pane, click **Remote Access**.</span></span>
    
3. <span data-ttu-id="3225e-234">맨 위에 있는 도구 모음에서 주황색 주의 기호를 클릭한 후 **웹 응용 프로그램 프록시 마법사 열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-234">In the tool bar at the top, click the orange caution symbol, and then click **Open the Web Application Proxy Wizard**.</span></span>
    
4. <span data-ttu-id="3225e-235">웹 응용 프로그램 프록시 구성 마법사의 **시작** 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-235">On the **Welcome** page of the Web Application Proxy Configuration Wizard, click **Next**.</span></span>
    
5. <span data-ttu-id="3225e-236">**페더레이션 서버** 페이지에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-236">On the **Federation Server** page:</span></span>
    
  - <span data-ttu-id="3225e-237">**페더레이션 서비스 이름**에 페더레이션 서비스 FQDN을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-237">Type your federation service FQDN in **Federation service name**.</span></span>
    
  - <span data-ttu-id="3225e-238">**사용자 이름**에 **CORP\\User1**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-238">Type **CORP\\User1** in **User name**.</span></span>
    
  - <span data-ttu-id="3225e-239">**암호**에 User1 계정의 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-239">Type the password for the User1 account in **Password**.</span></span>
    
  - <span data-ttu-id="3225e-240">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-240">Click **Next**.</span></span>
    
6. <span data-ttu-id="3225e-241">**AD FS 프록시 인증서** 페이지에서 아래쪽 화살표를 클릭하고, 사용자의 페더레이션 서비스 FQDN을 갖는 인증서를 클릭한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-241">On the **AD FS Proxy Certificate** page, click the down arrow, click the certificate with your federation service FQDN, and then click **Next**.</span></span>
    
7. <span data-ttu-id="3225e-242">**확인**페이지에서 **구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-242">On the **Confirmation** page, click **Configure**.</span></span>
    
8. <span data-ttu-id="3225e-243">**결과** 페이지에서 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-243">On the **Results** page, click **Close**.</span></span>
    
## <a name="phase-5-configure-office-365-for-federated-identity"></a><span data-ttu-id="3225e-244">5단계: 페더레이션 ID에 대해 Office 365 구성</span><span class="sxs-lookup"><span data-stu-id="3225e-244">Phase 5: Configure Office 365 for federated identity</span></span>

<span data-ttu-id="3225e-245">[Azure Portal](http://portal.azure.com)에서 CORP\\User1 계정 자격 증명을 사용하여 APP1 가상 머신에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-245">Use the [Azure portal](http://portal.azure.com) to connect to the APP1 virtual machine with the CORP\\User1 account credentials.</span></span>
  
<span data-ttu-id="3225e-246">다음 단계를 사용하여 페더레이션 인증을 위해 Azure AD Connect 및 Office 365 구독을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-246">Use these steps to configure Azure AD Connect and your Office 365 subscription for federated authentication:</span></span>
  
1. <span data-ttu-id="3225e-247">데스크톱에서 **Azure AD Connect**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-247">From the desktop, double-click **Azure AD Connect**.</span></span>
    
2. <span data-ttu-id="3225e-248">**Azure AD Connect 시작** 페이지에서 **구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-248">On the **Welcome to Azure AD Connect** page, click **Configure**.</span></span>
    
3. <span data-ttu-id="3225e-249">**추가 작업** 페이지에서 **사용자 로그인 변경**을 클릭한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-249">On the **Additional tasks** page, click **Change user sign-in**, and then click **Next**.</span></span>
    
4. <span data-ttu-id="3225e-250">**Azure AD에 연결** 페이지에서 Office 365 전역 관리자 계정 이름과 암호를 입력한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-250">On the **Connect to Azure AD** page, type your Office 365 global administrator account name and password, and then click **Next**.</span></span>
    
5. <span data-ttu-id="3225e-251">**사용자 로그인** 페이지에서 **AD FS로 페더레이션**을 클릭하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-251">On the **User sign-in** page, click **Federation with AD FS**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="3225e-252">**AD FS 팜** 페이지에서 **기존 AD FS 팜 사용**을 클릭하고 **서버 이름**에 **ADFS1**을 입력한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-252">On the **AD FS farm** page, click **Use an existing AD FS farm**, type **ADFS1** in **Server Name**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="3225e-253">서버 자격 증명을 묻는 메시지가 표시되면 CORP\\User1 계정의 자격 증명을 입력하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-253">When prompted for server credentials, enter the credentials of the CORP\\User1 account, and then click **OK**.</span></span>
    
8. <span data-ttu-id="3225e-254">**도메인 관리자** 자격 증명 페이지의 **사용자 이름**에 **CORP\\User1**을 입력하고 **암호**에 계정 암호를 입력한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-254">On the **Domain Administrator** credentials page, type **CORP\\User1** in **Username** and the account password in **Password**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="3225e-255">**AD FS 서비스 계정** 페이지에서 **도메인 사용자 이름**에 **CORP\\ADFS-Service**를 입력하고 **도메인 사용자 암호**에 계정 암호를 입력한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-255">On the **AD FS service account** page, type **CORP\\ADFS-Service** in **Domain Username** and the account password in **Domain User Password**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="3225e-256">**Azure AD 도메인** 페이지의 **도메인**에서 이전에 1단계에서 만든 후 Office 365 구독에 추가했던 도메인의 이름을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-256">On the **Azure AD Domain** page, in **Domain**, select the name of the domain you previously created and added to your Office 365 subscription in Phase 1, and then click **Next**.</span></span>
    
11. <span data-ttu-id="3225e-257">**구성 준비 완료** 페이지에서 **구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-257">On the **Ready to configure** page, click **Configure**.</span></span>
    
12. <span data-ttu-id="3225e-258">**설치 완료** 페이지에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-258">On the **Installation complete** page, click **Verify**.</span></span>
    
    <span data-ttu-id="3225e-259">인트라넷 및 인터넷 구성을 모두 확인했음을 나타내는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-259">You should see messages indicating that both the intranet and Internet configuration was verified.</span></span>
    
13. <span data-ttu-id="3225e-260">**설치 완료** 페이지에서 **끝내기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-260">On the **Installation complete** page, click **Exit**.</span></span>
    
<span data-ttu-id="3225e-261">페더레이션 인증이 작동하는지 확인하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-261">To demonstrate that federated authentication is working:</span></span>
  
1. <span data-ttu-id="3225e-262">로컬 컴퓨터에서 브라우저의 새 개인 인스턴스를 열고 [https://admin.microsoft.com](https://admin.microsoft.com)으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-262">Open a new private instance of your browser on your local computer and go to [https://admin.microsoft.com](https://admin.microsoft.com).</span></span>
    
2. <span data-ttu-id="3225e-263">로그인 자격 증명으로 **user1@**\<1단계에서 만든 도메인>을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-263">For the sign-in credentials, type **user1@**\<the domain created in Phase 1>.</span></span> 
    
    <span data-ttu-id="3225e-p109">예를 들어, 테스트 도메인이 **testlab.contoso.com**이면 **user1@testlab.contoso.com**을 입력합니다. Tab 키를 누르거나 Office 365에서 사용자를 자동으로 리디렉션하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-p109">For example, if your test domain is **testlab.contoso.com**, you would type **user1@testlab.contoso.com**. Press TAB or allow Office 365 to automatically redirect you.</span></span>
    
    <span data-ttu-id="3225e-p110">이제 **연결이 비공개가 아닙니다.** 페이지가 표시됩니다. 데스크톱 컴퓨터에서 유효한지 확인할 수 없는 자체 서명된 인증서를 ADFS1에 설치했으므로 이 메시지가 표시되는 것입니다. 페더레이션 인증의 프로덕션 배포에서 신뢰할 수 있는 인증 기관에서 발급한 인증서를 사용하면 사용자에게 이 페이지가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-p110">You should now see a **Your connection is not private** page. You are seeing this because you installed a self-signed certificate on ADFS1 that your desktop computer cannot validate. In a production deployment of federated authentication, you would use a certificate from a trusted certification authority and your users would not see this page.</span></span>
    
3. <span data-ttu-id="3225e-269">**연결이 비공개가 아닙니다.** 페이지에서 **고급**을 클릭하고 **\<페더레이션 서비스 FQDN>으로 이동**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-269">On the **Your connection is not private** page, click **Advanced**, and then click **Proceed to \<your federation service FQDN>**.</span></span> 
    
4. <span data-ttu-id="3225e-270">가상의 조직 이름이 표시된 페이지에서 다음을 사용하여 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-270">On the page with the name of your fictional organization, sign in with the following:</span></span>
    
  - <span data-ttu-id="3225e-271">이름: **CORP\\User1**</span><span class="sxs-lookup"><span data-stu-id="3225e-271">**CORP\\User1** for the name</span></span>
    
  - <span data-ttu-id="3225e-272">User1 계정에 대한 암호</span><span class="sxs-lookup"><span data-stu-id="3225e-272">The password for the User1 account</span></span>
    
    <span data-ttu-id="3225e-273">**Microsoft Office 홈** 페이지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-273">You should see the **Microsoft Office Home** page.</span></span>
    
<span data-ttu-id="3225e-p111">이 절차에서는 Office 365 평가판 구독이 DC1에 호스트된 Windows Server AD corp.contoso.com 도메인과 페더레이션되는 방법을 보여줍니다. 다음은 인증 프로세스의 기본 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-p111">This procedure demonstrates that your Office 365 trial subscription is federated with the Windows Server AD corp.contoso.com domain hosted on DC1. Here are the basics of the authentication process:</span></span>
  
1. <span data-ttu-id="3225e-276">1단계에서 만든 페더레이션 도메인을 로그인 계정 이름 내에서 사용할 경우 Office 365는 페더레이션 서비스 FQDN 및 PROXY1으로 브라우저를 리디렉션합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-276">When you use the federated domain that you created in Phase 1 within the sign-in account name, Office 365 redirects your browser to your federation service FQDN and PROXY1.</span></span>
    
2. <span data-ttu-id="3225e-277">PROXY1은 가상의 회사 로그인 페이지를 로컬 컴퓨터로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-277">PROXY1 sends your local computer the fictional company sign-in page.</span></span>
    
3. <span data-ttu-id="3225e-278">CORP\\User1 및 암호를 PROXY1으로 보내면 ADFS1로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-278">When you send CORP\\User1 and the password to PROXY1, it forwards them to ADFS1.</span></span>
    
4. <span data-ttu-id="3225e-279">ADFS1은 DC1을 사용하여 CORP\\User1의 유효성을 검사하고 로컬 컴퓨터로 보안 토큰을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-279">ADFS1 validates CORP\\User1 and the password with DC1 and sends your local computer a security token.</span></span>
    
5. <span data-ttu-id="3225e-280">로컬 컴퓨터가 Office 365로 보안 토큰을 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-280">Your local computer sends the security token to Office 365.</span></span>
    
6. <span data-ttu-id="3225e-281">Office 365는 보안 토큰이 ADFS1에서 생성되었는지 확인하고 액세스를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-281">Office 365 validates that the security token was created by ADFS1 and allows access.</span></span>
    
<span data-ttu-id="3225e-p112">이제 Office 365 평가판 구독이 페더레이션 인증으로 구성됩니다. 고급 인증 시나리오에 대해 이 개발/테스트 환경을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3225e-p112">Your Office 365 trial subscription is now configured with federated authentication. You can use this dev/test environment for advanced authentication scenarios.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="3225e-284">다음 단계</span><span class="sxs-lookup"><span data-stu-id="3225e-284">Next Step</span></span>

<span data-ttu-id="3225e-285">Azure의 Office 365에 대해 프로덕션에서 사용할 수 있는 고가용성 페더레이션 인증을 배포할 준비가 되면 [Azure에서 Office 365용 고가용성 페더레이션 인증 배포](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3225e-285">When you are ready to deploy production-ready, high availability federated authentication for Office 365 in Azure, see [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="3225e-286">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3225e-286">See Also</span></span>

[<span data-ttu-id="3225e-287">클라우드 도입 TLG(테스트 랩 가이드)</span><span class="sxs-lookup"><span data-stu-id="3225e-287">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="3225e-288">기본 구성 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="3225e-288">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="3225e-289">Office 365 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="3225e-289">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="3225e-290">클라우드 도입 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="3225e-290">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="3225e-291">Azure에서 Office 365용 고가용성 페더레이션 인증 배포</span><span class="sxs-lookup"><span data-stu-id="3225e-291">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)


