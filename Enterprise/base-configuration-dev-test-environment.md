---
title: 기본 구성 개발/테스트 환경
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 6fcbb50c-ac68-4be7-9fc5-dd0f275c1e3d
description: '요약: Microsoft Azure에서 개발/테스트 환경으로 간소화된 인트라넷을 만듭니다.'
ms.openlocfilehash: 6d53bb61ea7d325b15590c8aabe0740df3b92750
ms.sourcegitcommit: 8fcf6fd9f0c45a5445654ef811410fca3f4f5512
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2018
ms.locfileid: "19193758"
---
# <a name="base-configuration-devtest-environment"></a><span data-ttu-id="cb200-103">기본 구성 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="cb200-103">Base Configuration dev/test environment</span></span>

 <span data-ttu-id="cb200-104">**요약:** Microsoft Azure에서 개발/테스트 환경으로 간소화된 인트라넷을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-104">**Summary:** Create a simplified intranet as a dev/test environment in Microsoft Azure.</span></span>
  
<span data-ttu-id="cb200-105">이 문서에서는 Azure에서 다음과 같은 기본 구성 개발/테스트 환경을 만들기 위한 단계별 지침을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-105">This article provides you with step-by-step instructions to create the following Base Configuration dev/test environment in Azure:</span></span>
  
<span data-ttu-id="cb200-106">**그림 1: 기본 구성 개발/테스트 환경**</span><span class="sxs-lookup"><span data-stu-id="cb200-106">**Figure 1: The Base Configuration dev/test environment**</span></span>

![CLIENT1 가상 머신을 사용한 Azure의 기본 구성 4단계](images/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
<span data-ttu-id="cb200-p101">그림 1의 기본 구성 개발/테스트 환경은 인터넷에 연결된 단순화된 전용 인트라넷을 시뮬레이트하는 TestLab이라는 클라우드 전용 Azure Virtual Network의 Corpnet 서브넷으로 구성됩니다. 여기에는 WIndows Server 2016에서 실행되는 다음과 같은 3개의 Azure Virtual Machine이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-p101">The Base Configuration dev/test environment in Figure 1 consists of the Corpnet subnet in a cloud-only Azure virtual network named TestLab that simulates a simplified, private intranet connected to the Internet. It contains three Azure virtual machines running WIndows Server 2016:</span></span>
  
- <span data-ttu-id="cb200-110">DC1은 인트라넷 도메인 컨트롤러 및 DNS(Domain Name System) 서버로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-110">DC1 is configured as an intranet domain controller and Domain Name System (DNS) server</span></span>
    
- <span data-ttu-id="cb200-111">APP1은 일반 응용 프로그램 및 웹 서버로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-111">APP1 is configured as a general application and web server</span></span>
    
- <span data-ttu-id="cb200-112">CLIENT1은 인트라넷 클라이언트의 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-112">CLIENT1 acts as an intranet client</span></span>
    
<span data-ttu-id="cb200-113">이 구성에서 DC1, APP1, CLIENT1 및 추가 Corpnet 서브넷 컴퓨터에 다음이 수행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-113">This configuration allows DC1, APP1, CLIENT1, and additional Corpnet subnet computers to be:</span></span> 
  
- <span data-ttu-id="cb200-114">업데이트를 설치하고, 실시간으로 인터넷 리소스에 액세스하고, Microsoft Office 365 및 기타 Azure 서비스와 같은 공용 클라우드 기술에 참여하기 위해 인터넷에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-114">Connected to the Internet to install updates, access Internet resources in real time, and participate in public cloud technologies such as Microsoft Office 365 and other Azure services.</span></span>
    
- <span data-ttu-id="cb200-115">인터넷 또는 조직 네트워크에 연결된 컴퓨터에서 원격 데스크톱 연결을 사용하여 원격으로 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-115">Remotely managed using Remote Desktop connections from your computer that is connected to the Internet or your organization network.</span></span>
    
<span data-ttu-id="cb200-116">다음과 같은 결과 테스트 환경을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-116">You can use the resulting test environment:</span></span>
  
- <span data-ttu-id="cb200-117">응용 프로그램 개발 및 테스트용으로</span><span class="sxs-lookup"><span data-stu-id="cb200-117">For application development and testing.</span></span>
    
- <span data-ttu-id="cb200-118">추가 가상 머신, Azure 서비스 또는 기타 Microsoft 클라우드 서비스(예: Office 365 및 EMS(Enterprise Security + Mobility))가 포함된 직접 디자인한 확장된 테스트 환경의 초기 구성으로</span><span class="sxs-lookup"><span data-stu-id="cb200-118">As the initial configuration of an extended test environment of your own design that includes additional virtual machines, Azure services, or other Microsoft cloud offerings such as Office 365 and Enterprise Security + Mobility (EMS).</span></span>
    
<span data-ttu-id="cb200-119">Azure에서 기본 구성 테스트 환경을 설정하는 과정은 다음 4단계로 진행됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-119">There are four phases to setting up the Base Configuration test environment in Azure:</span></span>
  
1. <span data-ttu-id="cb200-120">가상 네트워크를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-120">Phase 2: Create the cross-premises virtual network in Azure</span></span>
    
2. <span data-ttu-id="cb200-121">DC1을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-121">Configure DC1.</span></span>
    
3. <span data-ttu-id="cb200-122">APP1을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-122">Configure APP1.</span></span>
    
4. <span data-ttu-id="cb200-123">CLIENT1을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-123">Configure CLIENT1.</span></span>
    
<span data-ttu-id="cb200-p102">Azure 구독이 아직 없으면 [Azure 평가](https://azure.microsoft.com/pricing/free-trial/)에서 평가판에 등록할 수 있습니다. MSDN 또는 Visual Studio 구독이 있는 경우 [Visual Studio 구독자를 위한 월별 Azure 크레딧](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cb200-p102">If you do not already have an Azure subscription, you can sign up for a free trial at [Try Azure](https://azure.microsoft.com/pricing/free-trial/). If you have an MSDN or Visual Studio subscription, see [Monthly Azure credit for Visual Studio subscribers](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span></span>
  
> [!NOTE]
> <span data-ttu-id="cb200-p103">Azure의 가상 머신은 실행될 때 비용이 계속 발생합니다. 이 비용은 평가판, MSDN 구독 또는 유료 구독과 별도로 청구됩니다. Azure Virtual Machine을 실행하는 비용에 대한 자세한 내용은 [가상 머신 가격 책정 정보](https://azure.microsoft.com/pricing/details/virtual-machines/) 및 [Azure 가격 계산기](https://azure.microsoft.com/pricing/calculator/)를 참조하세요. 비용을 줄이려면 [Azure에서 테스트 환경 가상 머신 비용 최소화](base-configuration-dev-test-environment.md#mincost)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cb200-p103">Virtual machines in Azure incur an ongoing monetary cost when they are running. This cost is billed against your free trial, MSDN subscription, or paid subscription. For more information about the costs of running Azure virtual machines, see [Virtual Machines Pricing Details](https://azure.microsoft.com/pricing/details/virtual-machines/) and [Azure Pricing Calculator](https://azure.microsoft.com/pricing/calculator/). To keep costs down, see [Minimizing the costs of test environment virtual machines in Azure](base-configuration-dev-test-environment.md#mincost).</span></span> 
  
![Microsoft 클라우드의 테스트 랩 가이드](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="cb200-131">[여기](http://aka.ms/catlgstack)를 클릭하여 One Microsoft 클라우드 테스트 랩 가이드 스택의 모든 문서에 대한 가상 맵을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-131">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-the-virtual-network"></a><span data-ttu-id="cb200-132">1단계: 가상 네트워크 만들기</span><span class="sxs-lookup"><span data-stu-id="cb200-132">Phase 2: Create the cross-premises virtual network in Azure</span></span>

<span data-ttu-id="cb200-133">먼저 Azure PowerShell 프롬프트를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-133">First, start an Azure PowerShell prompt and login to your account.</span></span>
  
> [!NOTE]
> <span data-ttu-id="cb200-p104">다음 명령 집합은 최신 버전의 Azure PowerShell을 사용합니다. [Azure PowerShell cmdlet으로 시작](https://docs.microsoft.com/ko-KR/powershell/azureps-cmdlets-docs/)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cb200-p104">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/ko-KR/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="cb200-136">다음 명령을 사용하여 Azure 계정에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-136">Sign in to your Azure account with the following command.</span></span>
  
```
Login-AzureRMAccount
```

> [!TIP]
> <span data-ttu-id="cb200-137">이 문서의 PowerShell 명령을 모두 포함하는 텍스트 파일을 가져오려면 [여기](https://gallery.technet.microsoft.com/PowerShell-commands-for-ba957d3d)를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-137">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-ba957d3d) to get a text file that contains all of the PowerShell commands in this article.</span></span>
  
<span data-ttu-id="cb200-138">다음 명령을 사용하여 구독 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-138">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

<span data-ttu-id="cb200-p105">Azure 구독을 설정합니다. < 및 > 문자를 포함하여 따옴표 안에 있는 모든 것을 올바른 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-p105">Set your Azure subscription. Replace everything within the quotes, including the < and > characters, with the correct name.</span></span>
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

<span data-ttu-id="cb200-p106">다음으로 기본 구성 테스트 랩에 대한 새 리소스 그룹을 만듭니다. 고유한 리소스 그룹 이름을 확인하려면 이 명령을 사용하여 기존 리소스 그룹을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-p106">Next, create a new resource group for your virtual network. To determine a unique resource group name, use this command to list your existing resource groups.</span></span>
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="cb200-p107">이러한 명령을 사용하여 새 리소스 그룹을 만듭니다. < 및 > 문자를 포함하여 따옴표 안에 있는 모든 내용을 올바른 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-p107">Create your new resource group with these commands. Set the variables by replacing everything within the quotes, including the < and > characters, with the correct names.</span></span>
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="cb200-145">다음으로, 기본 구성의 Corpnet 서브넷을 호스트할 TestLab 가상 네트워크를 만들고 네트워크 보안 그룹으로 보호합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-145">Next, you create the TestLab virtual network that will host the Corpnet subnet of the base configuration and protect it with a network security group.</span></span>
  
```
$rgName="<name of your new resource group>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$corpnetSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet -DNSServer 10.0.0.4
$rule1=New-AzureRMNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$nsg=Get-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
```

<span data-ttu-id="cb200-146">다음은 현재 구성입니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-146">This is your current configuration.</span></span>
  
![가상 네트워크 및 서브넷을 사용한 Azure의 기본 구성 1단계](images/0b5634fc-4e1c-469d-873d-97ed7e587411.png)
  
## <a name="phase-2-configure-dc1"></a><span data-ttu-id="cb200-148">2단계: DC1 구성</span><span class="sxs-lookup"><span data-stu-id="cb200-148">Phase 2: Configure DC1</span></span>

<span data-ttu-id="cb200-149">이 단계에서는 DC1 가상 머신을 만들고 Windows Server AD(Active Directory) 도메인 corp.contoso.com 및 TestLab 가상 네트워크의 가상 머신에 대한 DNS 서버의 도메인 컨트롤러로 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-149">Next, we create the adVM virtual machine in Azure. adVM is a domain controller for the corp.contoso.com Windows Server Active Directory (AD) domain and a DNS server for the virtual machines of the SP2016Vnet virtual network.</span></span>
  
<span data-ttu-id="cb200-150">DC1에 대한 Azure Virtual Machine을 만들려면 리소스 그룹의 이름을 입력하고 로컬 컴퓨터의 Azure PowerShell 명령 프롬프트에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-150">First, fill in the name of your resource group and run these commands at the Azure PowerShell command prompt on your local computer to create an Azure virtual machine for adVM.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name DC1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name DC1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress 10.0.0.4
$vm=New-AzureRMVMConfig -VMName DC1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for DC1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName DC1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "DC1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType StandardLRS
$diskConfig=New-AzureRmDiskConfig -AccountType StandardLRS -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzureRmDisk -DiskName "DC1-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name "DC1-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="cb200-p108">DC1의 로컬 관리자 계정에 대한 사용자 이름과 암호를 입력하라는 메시지가 표시됩니다. 강력한 암호를 사용하고 이름 및 암호를 안전한 위치에 보관합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-p108">You will be prompted for a user name and password for the local administrator account on DC1. Use a strong password and record both the name and password in a secure location.</span></span>
  
<span data-ttu-id="cb200-153">다음으로, DC1 가상 머신에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-153">Next, connect to the DC1 virtual machine.</span></span>
  
### <a name="connect-to-dc1-using-local-administrator-account-credentials"></a><span data-ttu-id="cb200-154">로컬 관리자 계정 자격 증명을 사용하여 DC1에 연결</span><span class="sxs-lookup"><span data-stu-id="cb200-154">Connect to DC1 using local administrator account credentials</span></span>

1. <span data-ttu-id="cb200-155">[Azure Portal](https://portal.azure.com)에서 **리소스 그룹 >** [새 리소스 그룹의 이름] **> DC1 > 연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-155">In the [Azure portalhttps://portal.azure.com](https://portal.azure.com), click **Resource Groups >** <the name of your new resource group> **> adVM > Connect**.</span></span>
    
2. <span data-ttu-id="cb200-p109">열려 있는 창에서 **RDP 파일 다운로드**를 클릭합니다. 다운로드된 DC1.rdp 파일을 열고 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-p109">In the open pane, click **Download RDP file**. Open the DC1.rdp file that is downloaded, and then click **Connect**.</span></span>
    
3. <span data-ttu-id="cb200-158">DC1 로컬 관리자 계정 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-158">Specify the DC1 local administrator account name:</span></span>
    
  - <span data-ttu-id="cb200-159">Windows 7:</span><span class="sxs-lookup"><span data-stu-id="cb200-159">For Windows 7:</span></span>
    
    <span data-ttu-id="cb200-p110">**Windows 보안** 대화 상자에서 **다른 계정 사용**을 클릭합니다. **사용자 이름**에서 **DC1\\**[로컬 관리자 계정 이름]을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-p110">In the **Windows Security** dialog box, click **Use another account**. In **User name**, type **DC1\\**[Local administrator account name].</span></span>
    
  - <span data-ttu-id="cb200-162">Windows 8.1 또는 Windows 10:</span><span class="sxs-lookup"><span data-stu-id="cb200-162">For Windows 8 or Windows 10:</span></span>
    
    <span data-ttu-id="cb200-p111">**Windows 보안** 대화 상자에서 **기타 선택 사항**을 클릭하고 **다른 계정 사용**을 클릭합니다. **사용자 이름**에서 **DC1\\**[로컬 관리자 계정 이름]을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-p111">In the **Windows Security** dialog box, click **More choices**, and then click **Use a different account**. In **User name**, type **DC1\\**[Local administrator account name].</span></span>
    
4. <span data-ttu-id="cb200-165">**암호**에서 로컬 관리자 계정의 암호를 입력하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-165">In **Password**, type the password of the ADMIN_NAME account, and then click **OK**.</span></span>
    
5. <span data-ttu-id="cb200-166">메시지가 표시되면 **예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-166">When prompted, click **Yes**.</span></span>
    
<span data-ttu-id="cb200-167">다음으로 DC1의 관리자 수준 Windows PowerShell 명령 프롬프트에서 다음 명령을 사용하여 추가 데이터 디스크를 드라이브 문자 F:의 새로운 볼륨으로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-167">Next, add an extra data disk as a new volume with the drive letter F: with these commands at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="cb200-p112">그런 다음 DC1을 corp.contoso.com 도메인에 대한 도메인 컨트롤러 및 DNS 서버로 구성합니다. 관리자 수준 Windows PowerShell 명령 프롬프트에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-p112">Next, configure adVM as a domain controller and DNS server for the corp.contoso.com domain. Run these commands at an administrator-level Windows PowerShell command prompt on adVM.</span></span>
  
```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSForest -DomainName corp.contoso.com -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs"
```
<span data-ttu-id="cb200-p113">안전 모드 관리자 암호를 지정해야 합니다. 이 암호를 안전한 장소에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-p113">You will need to specify a safe mode administrator password. Store this password in a secure location.</span></span>
  
<span data-ttu-id="cb200-172">이러한 명령은 완료하는 데 몇 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-172">Note that these commands can take a few minutes to complete.</span></span>
  
<span data-ttu-id="cb200-173">DC1이 다시 시작되면 DC1 가상 컴퓨터에 다시 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-173">After adVM restarts, reconnect to the adVM virtual machine.</span></span>
  
### <a name="connect-to-dc1-using-domain-credentials"></a><span data-ttu-id="cb200-174">도메인 자격 증명을 사용하여 DC1에 연결</span><span class="sxs-lookup"><span data-stu-id="cb200-174">Connect to DC1 using domain credentials</span></span>

1. <span data-ttu-id="cb200-175">[Azure Portal](https://portal.azure.com)에서 **리소스 그룹 >** [리소스 그룹 이름] **> DC1 > 연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-175">In the [Azure portal](https://portal.azure.com), click **Resource Groups >** [your resource group name] **> DC1 > Connect**.</span></span>
    
2. <span data-ttu-id="cb200-176">다운로드된 DC1.rdp 파일을 실행하고 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-176">Run the adVM.rdp file that is downloaded, and then click **Connect**.</span></span>
    
3. <span data-ttu-id="cb200-p114">**Windows 보안**에서 **다른 계정 사용**을 클릭합니다. **사용자 이름**에서 **CORP\\**[로컬 관리자 계정 이름]을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-p114">In **Windows Security**, click **Use another account**. In **User name**, type \***CORP\\**<ADMIN_NAME>.</span></span>
    
4. <span data-ttu-id="cb200-179">**암호**에서 로컬 관리자 계정의 암호를 입력하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-179">In **Password**, type the password of the ADMIN_NAME account, and then click **OK**.</span></span>
    
5. <span data-ttu-id="cb200-180">메시지가 표시되면 **예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-180">When prompted, click **Yes**.</span></span>
    
<span data-ttu-id="cb200-p115">다음으로, CORP 도메인 구성원 컴퓨터에 로그인할 때 사용할 사용자 계정을 Active Directory에서 만듭니다. 관리자 수준 Windows PowerShell 명령 프롬프트에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-p115">Next, create a user account in Active Directory that will be used when logging in to CORP domain member computers. Run this command at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
New-ADUser -SamAccountName User1 -AccountPassword (read-host "Set user password" -assecurestring) -name "User1" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

<span data-ttu-id="cb200-p116">이 명령은 User1 계정 암호를 묻는 메시지를 표시합니다. 이 계정은 모든 CORP 도메인 구성원 컴퓨터에 대한 원격 데스크톱 연결에 사용되므로 강력한 암호를 선택합니다. User1 계정 암호를 기록한 후 안전한 위치에 보관합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-p116">Note that this command prompts you to supply the User1 account password. Because this account will be used for remote desktop connections for all CORP domain member computers, choose a strong password. Record the User1 account password and store it in a secured location.</span></span>
  
<span data-ttu-id="cb200-p117">다음으로, 새 User1 계정을 엔터프라이즈 관리자로 구성합니다. 관리자 수준 Windows PowerShell 명령 프롬프트에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-p117">Next, configure the new User1 account as an Enterprise Administrator. Run this command at the administrator-level Windows PowerShell command prompt.</span></span>
  
```
Add-ADPrincipalGroupMembership -Identity "CN=User1,CN=Users,DC=corp,DC=contoso,DC=com" -MemberOf "CN=Enterprise Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Domain Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Schema Admins,CN=Users,DC=corp,DC=contoso,DC=com"
```

<span data-ttu-id="cb200-188">DC1과의 원격 데스크톱 세션을 닫은 후 CORP\\User1 계정을 사용하여 다시 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-188">Close the Remote Desktop session with DC1 and then reconnect using the CORP\\User1 account.</span></span>
  
<span data-ttu-id="cb200-189">다음으로, Ping 도구에 대한 트래픽을 허용하려면 관리자 수준의 Windows PowerShell 명령 프롬프트에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-189">Next, to allow traffic for the Ping tool, run this command at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
```

<span data-ttu-id="cb200-190">다음은 현재 구성입니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-190">This is your current configuration.</span></span>
  
![DC1 가상 머신을 사용한 Azure의 기본 구성 2단계](images/49069908-29c3-4d73-87f7-debbea067261.png)
  
## <a name="phase-3-configure-app1"></a><span data-ttu-id="cb200-192">3단계: APP1 구성</span><span class="sxs-lookup"><span data-stu-id="cb200-192">Phase 3: Configure APP1</span></span>

<span data-ttu-id="cb200-193">APP1은 웹 및 파일 공유 서비스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-193">APP1 provides web and file sharing services.</span></span>

-> [!NOTE]  
<span data-ttu-id="cb200-p118">-> 다음 명령 집합은 Windows Server 2016 Datacenter를 실행하는 CLIENT1을 만듭니다. 이 작업은 모든 유형의 Azure 구독에서 수행할 수 있습니다. Visual Studio 기반 Azure 구독이 있는 경우 [Azure Portal](https://portal.azure.com)을 사용하여 Windows 10이 실행되는 CLIENT1을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-p118">-> The following command set creates CLIENT1 running Windows Server 2016 Datacenter, which can be done for all types of Azure subscriptions. If you have an Visual Studio-based Azure subscription, you can create CLIENT1 running Windows 10 with the [Azure portal](https://portal.azure.com).</span></span> 

<span data-ttu-id="cb200-196">APP1에 대한 Azure Virtual Machine을 만들려면 리소스 그룹의 이름을 입력하고 로컬 컴퓨터의 Azure PowerShell 명령 프롬프트에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-196">First, fill in the name of your resource group and run these commands at the Azure PowerShell command prompt on your local computer to create an Azure virtual machine for adVM.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name APP1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name APP1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzureRMVMConfig -VMName APP1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for APP1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName APP1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "APP1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType StandardLRS
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="cb200-197">다음으로, APP1 로컬 관리자 계정 이름과 암호를 사용하여 APP1 가상 머신에 연결하고 Windows PowerShell 명령 프롬프트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-197">Next, connect to the APP1 virtual machine using the APP1 local administrator account name and password, and then open a Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="cb200-198">APP1과 DC1 사이의 이름 확인 및 네트워크 통신을 확인하려면 **ping dc1.corp.contoso.com** 명령을 실행하고 4개의 응답이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-198">To check name resolution and network communication between APP1 and DC1, run the **ping dc1.corp.contoso.com** command and verify that there are four replies.</span></span>
  
<span data-ttu-id="cb200-199">다음으로, Windows PowerShell 프롬프트에 다음 명령을 사용하여 APP1 가상 머신을 CORP 도메인에 가입합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-199">Join the SharePoint virtual machine to the Windows Server AD domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

<span data-ttu-id="cb200-200">**Add-Computer** 명령을 실행한 후 CORP\\User1 도메인 계정 자격 증명을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-200">Note that you must supply domain account credentials after running the **Add-Computer** command.</span></span>
  
<span data-ttu-id="cb200-201">APP1을 다시 시작한 후에 CORP\\User1 계정을 사용하여 연결한 후 관리자 수준 Windows PowerShell 명령 프롬프트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-201">After APP1 restarts, connect to it using the CORP\\User1 account, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="cb200-202">다음으로, APP1의 Windows PowerShell 명령 프롬프트에서 다음 명령을 사용하여 APP1을 웹 서버로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-202">Next, make APP1 a web server with this command at the Windows PowerShell command prompt on APP1.</span></span>
  
```
Install-WindowsFeature Web-WebServer -IncludeManagementTools
```

<span data-ttu-id="cb200-203">그런 후 다음 PowerShell 명령을 사용하여 APP1의 폴더 내에 공유 폴더 및 텍스트 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-203">Next, create a shared folder and a text file within the folder on APP1 with these PowerShell commands.</span></span>
  
```
New-Item -path c:\files -type directory
Write-Output "This is a shared file." | out-file c:\files\example.txt
New-SmbShare -name files -path c:\files -changeaccess CORP\User1
```

<span data-ttu-id="cb200-204">다음은 현재 구성입니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-204">This is your current configuration.</span></span>
  
![APP1 가상 머신을 사용한 Azure의 기본 구성 3단계](images/92cfabb0-7f9d-4291-964d-ac32d52748d7.png)
  
## <a name="phase-4-configure-client1"></a><span data-ttu-id="cb200-206">4단계: CLIENT1 구성</span><span class="sxs-lookup"><span data-stu-id="cb200-206">Phase 4: Configure CLIENT1</span></span>

<span data-ttu-id="cb200-207">CLIENT1은 Contoso 인트라넷에서 일반적인 랩톱, 태블릿 또는 데스크톱 컴퓨터의 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-207">CLIENT1 acts as a typical laptop, tablet, or desktop computer on the Contoso intranet.</span></span>
  
<span data-ttu-id="cb200-208">먼저 리소스 그룹의 이름을 입력하고 로컬 컴퓨터의 Azure PowerShell 명령 프롬프트에 다음 명령을 실행하여 CLIENT1에 대한 Azure Virtual Machine을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-208">First, fill in the name of your resource group and run these commands at the Azure PowerShell command prompt on your local computer to create an Azure virtual machine for adVM.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name CLIENT1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name CLIENT1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzureRMVMConfig -VMName CLIENT1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for CLIENT1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName CLIENT1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "CLIENT1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType StandardLRS
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="cb200-209">다음으로, CLIENT1 로컬 관리자 계정 이름과 암호를 사용하여 CLIENT1 가상 머신에 연결하고 관리자 수준 Windows PowerShell 명령 프롬프트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-209">Next, connect to the CLIENT1 virtual machine using the CLIENT1 local administrator account name and password, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="cb200-210">CLIENT1과 DC1 사이의 이름 확인 및 네트워크 통신을 확인하려면 Windows PowerShell 명령 프롬프트에서 **ping dc1.corp.contoso.com** 명령을 실행하고 4개의 응답이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-210">To check name resolution and network communication between CLIENT1 and DC1, run the **ping dc1.corp.contoso.com** command at a Windows PowerShell command prompt and verify that there are four replies.</span></span>
  
<span data-ttu-id="cb200-211">다음으로, Windows PowerShell 프롬프트에 다음 명령을 사용하여 CLIENT1 가상 머신을 CORP 도메인에 가입합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-211">Join the SharePoint virtual machine to the Windows Server AD domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

<span data-ttu-id="cb200-212">**Add-Computer** 명령을 실행한 후 CORP\\User1 도메인 계정 자격 증명을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-212">Note that you must supply domain account credentials after running the **Add-Computer** command.</span></span>
  
<span data-ttu-id="cb200-213">CLIENT1을 다시 시작한 후에 CORP\\User1 계정 이름 및 암호를 사용하여 연결한 후 관리자 수준 Windows PowerShell 명령 프롬프트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-213">After CLIENT1 restarts, connect to it using the CORP\\User1 account name and password, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="cb200-214">그런 후 CLIENT1에서 APP1의 웹 및 파일 공유 리소스에 액세스할 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-214">Next, verify that you can access web and file share resources on APP1 from CLIENT1.</span></span>
  
### <a name="verify-client-access-to-app1"></a><span data-ttu-id="cb200-215">APP1에 대한 CLIENT 액세스 확인</span><span class="sxs-lookup"><span data-stu-id="cb200-215">Verify CLIENT access to APP1</span></span>

1. <span data-ttu-id="cb200-216">서버 관리자의 트리 창에서 **로컬 서버**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-216">In Server Manager, in the tree pane, click **Local Server**.</span></span>
    
2. <span data-ttu-id="cb200-217">**CLIENT1에 대한 속성**에서 **IE 보안 강화 구성** 옆의 **켜기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-217">In **Properties for CLIENT1**, click **On** next to **IE Enhanced Security Configuration**.</span></span>
    
3. <span data-ttu-id="cb200-218">**Internet Explorer 보안 강화 구성**에서 **관리자** 및 **사용자**에 대해 **끄기**를 클릭한 후 ** 확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-218">In **Internet Explorer Enhanced Security Configuration**, click **Off** for **Administrators** and **Users**, and then click **OK**.</span></span>
    
4. <span data-ttu-id="cb200-219">시작 화면에서 **Internet Explorer**를 클릭하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-219">From the Start screen, click **Internet Explorer**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="cb200-p119">주소 표시줄에 **http:\//app1.corp.contoso.com/** 을 입력하고 Enter 키를 누릅니다. APP1에 대한 기본 인터넷 정보 서비스 웹 페이지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-p119">In the Address bar, type **http:\//app1.corp.contoso.com/**, and then press ENTER. You should see the default Internet Information Services web page for APP1.</span></span>
    
6. <span data-ttu-id="cb200-222">바탕 화면 작업 표시줄에서 파일 탐색기 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-222">From the desktop taskbar, click the File Explorer icon.</span></span>
    
7. <span data-ttu-id="cb200-p120">주소 표시줄에 **\\\\app1\\Files일**를 입력하고 Enter 키를 누릅니다. Files 공유 폴더의 내용이 포함된 폴더 창이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-p120">In the address bar, type **\\\\app1\\Files**, and then press ENTER. You should see a folder window with the contents of the Files shared folder.</span></span>
    
8. <span data-ttu-id="cb200-p121">**Files** 공유 폴더 창에서 **Example.txt** 파일을 두 번 클릭합니다. Example.txt 파일의 내용을 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-p121">In the **Files** shared folder window, double-click the **Example.txt** file. You should see the contents of the Example.txt file.</span></span>
    
9. <span data-ttu-id="cb200-227">**example.txt - 메모장**과 **Files** 공유 폴더 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-227">Close the **example.txt - Notepad** and the **Files** shared folder windows.</span></span>
    
<span data-ttu-id="cb200-228">다음은 최종 구성입니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-228">This is your final configuration.</span></span>
  
![CLIENT1 가상 머신을 사용한 Azure의 기본 구성 4단계](images/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
<span data-ttu-id="cb200-230">Azure의 기본 구성은 이제 응용 프로그램 개발 및 테스트나 추가 테스트 환경 구축에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-230">Your Base Configuration in Azure is now ready for application development and testing or for building additional test environments.</span></span> 
  
> [!TIP]
> <span data-ttu-id="cb200-231">[여기](http://aka.ms/catlgstack)를 클릭하여 One Microsoft 클라우드 테스트 랩 가이드 스택의 모든 기사에 대한 가상 맵을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-231">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
<span data-ttu-id="cb200-232"><a name="mincost"> </a></span><span class="sxs-lookup"><span data-stu-id="cb200-232"></span></span>
## <a name="minimizing-the-costs-of-test-environment-virtual-machines-in-azure"></a><span data-ttu-id="cb200-233">Azure의 테스트 환경 가상 머신 비용 최소화</span><span class="sxs-lookup"><span data-stu-id="cb200-233">Minimizing the costs of test environment virtual machines in Azure</span></span>

<span data-ttu-id="cb200-234">테스트 환경 가상 머신의 실행 비용을 최소화하려면 다음 중 하나를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-234">To minimize the cost of running the test environment virtual machines, you can do one of the following:</span></span>
  
- <span data-ttu-id="cb200-p122">테스트 환경을 만들고 가능한 한 빠르게 필요한 테스트 및 데모를 수행합니다. 완료되면 테스트 환경에 대한 리소스 그룹을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-p122">Create the test environment and perform your needed testing and demonstration as quickly as possible. When complete, delete the resource group for the test environment.</span></span>
    
- <span data-ttu-id="cb200-237">테스트 환경 가상 머신을 할당 취소 상태로 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-237">Shut down your test environment virtual machines into a deallocated state.</span></span>
    
<span data-ttu-id="cb200-238">Azure PowerShell을 사용하여 가상 머신을 종료하려면 리소스 그룹 이름을 채우고 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-238">To shut down the virtual machines with Azure PowerShell, fill in the resource group name and run these commands.</span></span>
  
```
$rgName="<your resource group name>"
Stop-AzureRMVM -ResourceGroupName $rgName -Name "CLIENT1" -Force
Stop-AzureRMVM -ResourceGroupName $rgName -Name "APP1" -Force
Stop-AzureRMVM -ResourceGroupName $rgName -Name "DC1" -Force
```

<span data-ttu-id="cb200-239">중지됨(할당 해제됨) 상태에서 모든 가상 머신을 시작할 때 가상 머신이 적절히 작동되도록 하려면 다음 순서로 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-239">To ensure that your virtual machines work properly when starting all of them from the Stopped (Deallocated) state, you should start them in the following order:</span></span>
  
1. <span data-ttu-id="cb200-240">DC1</span><span class="sxs-lookup"><span data-stu-id="cb200-240">DC1</span></span>
2. <span data-ttu-id="cb200-241">APP1</span><span class="sxs-lookup"><span data-stu-id="cb200-241">Click APP1.</span></span>
3. <span data-ttu-id="cb200-242">CLIENT1</span><span class="sxs-lookup"><span data-stu-id="cb200-242">CLIENT1</span></span>
    
<span data-ttu-id="cb200-243">Azure PowerShell을 사용하여 가상 머신을 순서대로 시작하려면 리소스 그룹 이름을 채우고 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cb200-243">To start the virtual machines in order with Azure PowerShell, fill in the resource group name and run these commands.</span></span>
  
```
$rgName="<your resource group name>"
Start-AzureRMVM -ResourceGroupName $rgName -Name "DC1"
Start-AzureRMVM -ResourceGroupName $rgName -Name "APP1"
Start-AzureRMVM -ResourceGroupName $rgName -Name "CLIENT1"
```

## <a name="see-also"></a><span data-ttu-id="cb200-244">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cb200-244">See Also</span></span>

- [<span data-ttu-id="cb200-245">Office 365 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="cb200-245">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
- [<span data-ttu-id="cb200-246">Office 365 개발/테스트 환경용 DirSync</span><span class="sxs-lookup"><span data-stu-id="cb200-246">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
- [<span data-ttu-id="cb200-247">Office 365 개발/테스트 환경용 Cloud App Security</span><span class="sxs-lookup"><span data-stu-id="cb200-247">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
- [<span data-ttu-id="cb200-248">Office 365 개발/테스트 환경용 Advanced Threat Protection</span><span class="sxs-lookup"><span data-stu-id="cb200-248">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
- [<span data-ttu-id="cb200-249">클라우드 도입 및 하이브리드 솔루션</span><span class="sxs-lookup"><span data-stu-id="cb200-249">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
