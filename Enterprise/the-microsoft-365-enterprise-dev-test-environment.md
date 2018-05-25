---
title: Microsoft 365 Enterprise 개발/테스트 환경
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 6f916a77-301c-4be2-b407-6cec4d80df76
description: '요약: 이 테스트 랩 가이드를 사용하여 Office 365 E5, EMS(Enterprise Mobility + Security) E5 및 Windows 10 Enterprise를 실행하는 컴퓨터가 포함되는 개발/테스트 환경을 만듭니다.'
ms.openlocfilehash: 5a4c23b3bde309a75a61e574e91823ecdd4629fe
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/27/2018
---
# <a name="the-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="984be-103">Microsoft 365 Enterprise 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="984be-103">The Microsoft 365 Enterprise dev/test environment</span></span>

 <span data-ttu-id="984be-104">**요약:** 이 테스트 랩 가이드를 사용하여 Office 365 E5, EMS(Enterprise Mobility + Security) E5 및 Windows 10 Enterprise를 실행하는 컴퓨터가 포함되는 개발/테스트 환경을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="984be-104">**Summary:** Use this Test Lab Guide to create a dev/test environment that includes Office 365 E5, Enterprise Mobility + Security (EMS) E5, and a computer running Windows 10 Enterprise.</span></span>
  
<span data-ttu-id="984be-105">이 문서에서는 [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise)의 특성 및 기능을 테스트하는 간소화된 환경을 만들기 위한 단계별 지침을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="984be-105">This article provides you with step-by-step instructions to create a simplified environment to test the features and functionality of [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise).</span></span>
  
## <a name="phase-1-create-your-office-365-e5-subscription"></a><span data-ttu-id="984be-106">1단계: Office 365 E5 구독 만들기</span><span class="sxs-lookup"><span data-stu-id="984be-106">Phase 1: Create your Office 365 dev/test environment</span></span>

<span data-ttu-id="984be-107">그림 1과 같이 [Office 365 개발/테스트 환경](office-365-dev-test-environment.md)의 2, 3단계의 세부 단계를 수행하여 경량의 Office 365 개발/테스트 환경을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="984be-107">Follow the steps in Phase 2 and Phase 3 of the [Office 365 dev/test environment](office-365-dev-test-environment.md) to create a lightweight Office 365 dev/test environment, as shown in Figure 1.</span></span>
  
<span data-ttu-id="984be-108">**그림 1: 해당 Azure AD(Active Directory) 테넌트 및 사용자 계정을 사용하는 Office 365 E5 구독**</span><span class="sxs-lookup"><span data-stu-id="984be-108">**Figure 1: Your Office 365 E5 subscription with its Azure Active Directory (AD) tenant and user accounts**</span></span>

![Microsoft 3656 Enterprise 개발/테스트 환경 1단계](images/65bb027b-fb59-46eb-aec2-38c0af425168.png)

> [!NOTE]
> <span data-ttu-id="984be-p101">Office 365 E5 평가판 구독 기간은 30일이며, 60일까지 쉽게 연장할 수 있습니다. 영구 개발/테스트 환경의 경우 소수의 라이선스를 사용해서 유료 구독을 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="984be-p101">The Office 365 E5 trial subscription is 30 days, which can be easily extended to 60 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
## <a name="phase-2-add-ems"></a><span data-ttu-id="984be-112">2단계: EMS 추가</span><span class="sxs-lookup"><span data-stu-id="984be-112">Phase 2: Add EMS</span></span>

<span data-ttu-id="984be-113">이 단계에서는 EMS E5 평가판 구독을 등록하고 Office 365 E5 평가판 구독과 동일한 조직에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="984be-113">In this phase, you sign up for the EMS trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
<span data-ttu-id="984be-114">먼저, EMS E5 평가판 구독을 추가하고 전역 관리자 계정에 EMS 라이선스를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="984be-114">First, add the EMS E5 trial subscription and assign an EMS license to your global administrator account.</span></span>
  
1. <span data-ttu-id="984be-p102">인터넷 브라우저의 개인 인스턴스를 사용하고 전역 관리자 계정 자격 증명으로 Office 365 포털에 로그인합니다. 도움을 받으려면 [Office 365에 로그인하는 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="984be-p102">If needed, use a private instance of your Internet browser and sign in to the Office 365 portal with the global administrator account of your Office 365 E5 trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="984be-117">**관리** 타일을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="984be-117">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="984be-118">브라우저의 **Office 관리 센터** 탭에 있는 왼쪽 탐색 영역에서 **대금 청구 > 서비스 구매**를 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="984be-118">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="984be-p103">
            **구매 서비스** 페이지에서 **Enterprise Mobility + Security E5** 항목을 찾습니다. 마우스 포인터를 가져간 후 **평가판 시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="984be-p103">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="984be-121">**주문 확인** 페이지에서 **지금 평가판 사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="984be-121">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="984be-122">**주문 접수** 페이지에서 **계속**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="984be-122">On the **Order receipt** page, click **Continue**.</span></span>
    
7. <span data-ttu-id="984be-123">브라우저의 **Office 365 관리 센터** 탭에 있는 왼쪽 탐색 영역에서 **사용자 > 활성 사용자**를 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="984be-123">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
8. <span data-ttu-id="984be-124">전역 관리자 계정을 클릭한 다음, **제품 라이선스**에 대해 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="984be-124">Click your global administrator account, and then click Edit for Product licenses.</span></span>
    
9. <span data-ttu-id="984be-125">**제품 라이선스** 창에서 **Enterprise Mobility + Security E5**에 대한 제품 라이선스를 **설정**으로 바꾸고 **저장**을 클릭한 후 **닫기**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="984be-125">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
> [!NOTE]
> <span data-ttu-id="984be-p104">Enterprise Mobility + Security E5 평가판 구독 기간은 90일입니다. 영구 개발/테스트 환경의 경우 소수의 라이선스를 사용해서 유료 구독을 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="984be-p104">The Enterprise Mobility + Security E5 trial subscription is 90 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
 <span data-ttu-id="984be-128">[Office 365 개발/테스트 환경](office-365-dev-test-environment.md)의 ***3단계를 완료한 경우,*** 다른 모든 계정(사용자 2, 사용자 3, 사용자 4 및 사용자 5)에 대해 이전 절차의 8 및 9단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="984be-128">***If you completed Phase 3 of the*** [Office 365 dev/test environment](office-365-dev-test-environment.md), repeat steps 8 and 9 of the previous procedure for all of your other accounts (User 2, User 3, User 4, and User 5).</span></span>
  
<span data-ttu-id="984be-129">이제 개발/테스트 환경에는 다음이 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="984be-129">Your Office 365 and EMS dev/test environment now has:</span></span>
  
- <span data-ttu-id="984be-130">사용자 계정 목록과 동일한 Azure AD 테넌트를 공유하는 Office 365 E5 Enterprise 및 EMS E5 평가판 구독</span><span class="sxs-lookup"><span data-stu-id="984be-130">Office 365 E5 Enterprise and EMS trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
- <span data-ttu-id="984be-131">모든 해당 사용자 계정(전역 관리자만 또는 5개의 사용자 계정 모두)이 Office 365 E5 및 EMS E5를 사용하도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="984be-131">All your appropriate user accounts (either just the global administrator or all five user accounts) are enabled to use Office 365 E5 and EMS E5.</span></span>
    
<span data-ttu-id="984be-132">그림 2는 EMS를 추가하는 구성 결과를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="984be-132">Figure 2 shows your resulting configuration, which adds EMS.</span></span>
  
<span data-ttu-id="984be-133">**그림 2: EMS 평가판 구독 추가**</span><span class="sxs-lookup"><span data-stu-id="984be-133">**Figure 2: Adding the EMS trial subscription**</span></span>

![Microsoft 3656 Enterprise 개발/테스트 환경 2단계](images/8a01a483-3de2-41f3-a845-141c7edd0cb0.png)
  
## <a name="phase-3-create-a-windows-10-enterprise-computer"></a><span data-ttu-id="984be-135">3단계: Windows 10 Enterprise 컴퓨터 만들기</span><span class="sxs-lookup"><span data-stu-id="984be-135">Phase 3: Create a Windows 10 Enterprise computer</span></span>

<span data-ttu-id="984be-136">이 단계에서는 Windows 10 Enterprise를 실행하는 독립 실행형 컴퓨터를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="984be-136">In this phase, you create a standalone computer running Windows 10 Enterprise.</span></span>
  
### <a name="physical-computer"></a><span data-ttu-id="984be-137">실제 컴퓨터</span><span class="sxs-lookup"><span data-stu-id="984be-137">Physical computer</span></span>

<span data-ttu-id="984be-p105">개인용 컴퓨터를 구한 후 Windows 10 Enterprise를 설치합니다. Windows 10 Enterprise 평가판을 [여기](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise)에서 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="984be-p105">Obtain a personal computer and install Windows 10 Enterprise on it. You can download the Windows 10 Enterprise trial [here](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).</span></span>
  
### <a name="virtual-machine"></a><span data-ttu-id="984be-140">가상 컴퓨터</span><span class="sxs-lookup"><span data-stu-id="984be-140">Virtual machine</span></span>

<span data-ttu-id="984be-p106">사용자가 선택한 하이퍼바이저를 사용하여 가상 머신을 만들고 Windows 10 Enterprise를 설치합니다. Windows 10 Enterprise 평가판을 [여기](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise)에서 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="984be-p106">Create a virtual machine using the hypervisor of your choice and install Windows 10 Enterprise on it. You can download the Windows 10 Enterprise trial [here](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).</span></span>
  
### <a name="virtual-machine-in-azure"></a><span data-ttu-id="984be-143">Azure의 가상 머신</span><span class="sxs-lookup"><span data-stu-id="984be-143">Virtual machine in Azure</span></span>

<span data-ttu-id="984be-p107">Microsoft Azure에서 Windows 10 가상 머신을 만들려면 Windows 10 Enterprise에 대한 이미지에 액세스할 수 있는 ***Visual Studio 기반 구독이 있어야 합니다***. 다른 유형의 Azure 구독(예: 평가판 및 유료 구독)으로는 이 이미지에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="984be-p107">To create a Windows 10 virtual machine in Microsoft Azure, ***you must have a Visual Studio-based subscription***, which has access to the image for Windows 10 Enterprise. Other types of Azure subscriptions, such as trial and paid subscriptions, do not have access to this image.</span></span>
  
> [!NOTE]
> <span data-ttu-id="984be-p108">다음 명령에서는 최신 버전의 Azure PowerShell을 사용합니다. [Azure PowerShell cmdlet 시작](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/)을 참조하세요. 이러한 명령 집합은 WIN10이라는 Windows 10 Enterprise 가상 머신과 리소스 그룹, 저장소 계정 및 가상 네트워크를 포함하는 모든 필수 인프라를 빌드합니다. Azure 인프라 서비스에 이미 익숙한 경우 혅 배포된 인프라에 맞게 이러한 지침을 조정하세요.</span><span class="sxs-lookup"><span data-stu-id="984be-p108">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/). These command sets build a Windows 10 Enterprise virtual machine named WIN10 and all of its required infrastructure, including a resource group, a storage account, and a virtual network. If you are already familiar with Azure infrastructure services, please adapt these instructions to suit your currently deployed infrastructure.</span></span> 
  
<span data-ttu-id="984be-150">먼저 Microsoft PowerShell 프롬프트를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="984be-150">First, start a Microsoft PowerShell prompt.</span></span>
  
<span data-ttu-id="984be-151">다음 명령을 사용하여 Azure 계정에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="984be-151">Sign in to your Azure account with the following command.</span></span>
  
```
Login-AzureRMAccount
```

<span data-ttu-id="984be-152">다음 명령을 사용하여 구독 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="984be-152">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

<span data-ttu-id="984be-p109">Azure 구독을 설정합니다. \< 및 > 문자를 포함하여 따옴표 안에 있는 모든 것을 올바른 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="984be-p109">Set your Azure subscription. Replace everything within the quotes, including the < and > characters, with the correct name.</span></span>
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

<span data-ttu-id="984be-p110">다음으로 새 리소스 그룹을 만듭니다. 고유한 리소스 그룹 이름을 확인하려면 이 명령을 사용하여 기존 리소스 그룹을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="984be-p110">Next, create a new resource group. To determine a unique resource group name, use this command to list your existing resource groups.</span></span>
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="984be-p111">이러한 명령을 사용하여 새 리소스 그룹을 만듭니다. \< 및 > 문자를 포함하여 따옴표 안에 있는 모든 내용을 올바른 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="984be-p111">Create your new resource group with these commands. Set the variables by replacing everything within the quotes, including the < and > characters, with the correct names.</span></span>
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="984be-p112">그런 후 다음 명령을 사용하여 새 가상 네트워크와 WIN10 가상 머신을 만듭니다. 메시지가 표시되면 WIN10의 로컬 관리자 계정에 대한 이름 및 암호를 제공하고 이러한 항목을 안전한 장소에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="984be-p112">Next, you create a new virtual network and the WIN10 virtual machine with these commands. When prompted, provide the name and password of the local administrator account for WIN10 and store these in a secure location.</span></span>
  
```
$corpnetSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzureRMVirtualNetwork -Name "M365Ent-TestLab" -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet
$rule1=New-AzureRMNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name "M365Ent-TestLab"
$nsg=Get-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
$pip=New-AzureRMPublicIpAddress -Name WIN10-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name WIN10-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzureRMVMConfig -VMName WIN10 -VMSize Standard_D1_V2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for WIN10."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName WIN10 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsDesktop -Offer Windows-10 -Skus RS3-Pro -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name WIN10-TestLab-OSDisk -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

## <a name="phase-4-join-your-windows-10-computer-to-azure-ad"></a><span data-ttu-id="984be-161">4단계: Azure AD에 Windows 10 컴퓨터 가입</span><span class="sxs-lookup"><span data-stu-id="984be-161">Phase 4: Join your Windows 10 computer to Azure AD</span></span>

<span data-ttu-id="984be-162">Windows 10 Enterprise가 있는 실제 또는 가상 머신을 만든 후에 로컬 관리자 계정으로 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="984be-162">After the physical or virtual machine with Windows 10 Enterprise is created, sign in with a local administrator account.</span></span>
  
> [!NOTE]
> <span data-ttu-id="984be-p113">Azure의 가상 머신은 [다음 지침](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon)을 사용하여 연결합니다. 로컬 관리자 계정의 자격 증명을 사용하여 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="984be-p113">For a virtual machine in Azure, connect to it using [these instructions](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon). Sign in with the credentials of the local administrator account.</span></span> 
  
<span data-ttu-id="984be-165">다음으로, WIN10 컴퓨터를 Office 365 및 EMS 구독의 Azure 테넌트에 가입합니다.</span><span class="sxs-lookup"><span data-stu-id="984be-165">Next, join the WIN10 computer to the Azure AD tenant of your Office 365 and EMS subscriptions.</span></span>
  
1. <span data-ttu-id="984be-166">WIN10 컴퓨터의 데스크톱에서 **시작 > 설정 > 계정 > 회사 또는 학교 액세스 > 연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="984be-166">At the desktop of the WIN10 computer, click **Start > Settings > Accounts > Access work or school > Connect**.</span></span>
    
2. <span data-ttu-id="984be-167">**회사 또는 학교 계정 설정** 대화 상자에서 **Azure Active Directory에 이 장치 가입**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="984be-167">In the **Set up a work or school account** dialog box, click **Join this device to Azure Active Directory**.</span></span>
    
3. <span data-ttu-id="984be-168">**회사 또는 학교 계정**에서 Office 365 구독의 전역 관리자 계정 이름을 입력하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="984be-168">In **Work or school account**, type the global administrator account name of your Office 365 subscription, and then click **Next**.</span></span>
    
4. <span data-ttu-id="984be-169">**암호 입력**에 전역 관리자 계정의 암호를 입력하고 **로그인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="984be-169">In **Enter password**, type the password for your global administrator account, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="984be-170">사용자의 조직이 맞는지 묻는 메시지가 표시되면 **가입**을 클릭하고 **완료**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="984be-170">When prompted to make sure this is your organization, click **Join**, and then click **Done**.</span></span>
    
6. <span data-ttu-id="984be-171">설정 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="984be-171">Close the Help window.</span></span>
    
<span data-ttu-id="984be-172">다음으로, WIN10 컴퓨터에 Office 2016을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="984be-172">Next, install Office 2016 on the WIN10 computer.</span></span>
  
1. <span data-ttu-id="984be-p114">Microsoft Edge 브라우저를 열고 전역 관리자 계정 자격 증명으로 Office 365 포털에 로그인합니다. 도움을 받으려면 [Office 365에 로그인하는 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="984be-p114">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="984be-175">**Microsoft Office 홈** 탭에서 **Office 2016 설치**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="984be-175">On the **Microsoft Office Home** tab, click **Install Office 2016**.</span></span>
    
3. <span data-ttu-id="984be-176">수행할 작업을 묻는 메시지가 표시되면 **실행**을 클릭하고 **사용자 계정 컨트롤**에 대해 **예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="984be-176">When prompted with what to do, click **Run**, and then click **Yes** for **User Account Control**.</span></span>
    
4. <span data-ttu-id="984be-p115">Office 설치가 완료될 때까지 기다립니다. **모두 완료되었습니다.** 가 표시되면 **닫기**를 두 번 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="984be-p115">Wait for Office to complete its installation. When you see **You're all set!**, click **Close** twice.</span></span>
    
<span data-ttu-id="984be-179">그림 3에는 Office 365 및 EMS 구독의 Azure 테넌트에 가입된 WIN10 컴퓨터를 포함하는 사용자 환경 결과가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="984be-179">Figure 3 shows your resulting environment, which includes the WIN10 computer that has joined the Azure AD tenant of your Office 365 and EMS subscriptions.</span></span>
  
<span data-ttu-id="984be-180">**그림 3: Azure AD 테넌트에 WIN10 컴퓨터 계정 추가**</span><span class="sxs-lookup"><span data-stu-id="984be-180">**Figure 3: Adding the WIN10 computer account to the Azure AD tenant**</span></span>

![Microsoft 3656 Enterprise 개발/테스트 환경 4단계](images/20680f6a-f77e-4333-aaa9-f7cf5e4b0d03.png)
  
<span data-ttu-id="984be-182">이제 [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise)의 추가 기능을 사용해볼 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="984be-182">You are now ready to experiment with additional features of [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise).</span></span>
  
## <a name="next-steps"></a><span data-ttu-id="984be-183">다음 단계</span><span class="sxs-lookup"><span data-stu-id="984be-183">Next steps</span></span>

<span data-ttu-id="984be-184">다음 추가 문서를 사용하여 Microsoft 365 Enterprise의 기능을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="984be-184">Use these additional articles to explore features of Microsoft 365 Enterprise:</span></span>
  
- [<span data-ttu-id="984be-185">MAM(모바일 응용 프로그램 관리) 정책 추가</span><span class="sxs-lookup"><span data-stu-id="984be-185">Add mobile application management (MAM) policies</span></span>](https://technet.microsoft.com/library/mt764059.aspx)
    
- [<span data-ttu-id="984be-186">iOS 및 Android 장치 등록</span><span class="sxs-lookup"><span data-stu-id="984be-186">Enroll iOS and Android devices in your Microsoft Enterprise 365 dev/test environment</span></span>](https://technet.microsoft.com/library/mt743077.aspx)
    
- [<span data-ttu-id="984be-187">Advanced Security Management 구성 및 테스트</span><span class="sxs-lookup"><span data-stu-id="984be-187">Configure and test Advanced Security Management</span></span>](https://technet.microsoft.com/library/mt757250.aspx)
    
- [<span data-ttu-id="984be-188">Advanced Threat Protection 구성 및 테스트</span><span class="sxs-lookup"><span data-stu-id="984be-188">Configure and test Advanced Threat Protection</span></span>](https://technet.microsoft.com/library/mt490479.aspx)
    
## <a name="see-also"></a><span data-ttu-id="984be-189">참고 항목</span><span class="sxs-lookup"><span data-stu-id="984be-189">See Also</span></span>

- [<span data-ttu-id="984be-190">Microsoft 365 Enterprise 설명서</span><span class="sxs-lookup"><span data-stu-id="984be-190">Microsoft 365 Enterprise documentation and resources</span></span>](https://docs.microsoft.com/microsoft-365-enterprise/)
- <span data-ttu-id="984be-191">[Microsoft 365 Enterprise 배포](https://docs.microsoft.com/microsoft-365/enterprise/deploy-microsoft-365-enterprise)</span><span class="sxs-lookup"><span data-stu-id="984be-191">Microsoft 365 Enterprise[](https://docs.microsoft.com/microsoft-365/enterprise/deploy-microsoft-365-enterprise)</span></span>
- [<span data-ttu-id="984be-192">One Microsoft Cloud 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="984be-192">The One Microsoft Cloud dev/test environment</span></span>](the-one-microsoft-cloud-dev-test-environment.md)
- [<span data-ttu-id="984be-193">클라우드 도입 TLG(테스트 랩 가이드)</span><span class="sxs-lookup"><span data-stu-id="984be-193">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
