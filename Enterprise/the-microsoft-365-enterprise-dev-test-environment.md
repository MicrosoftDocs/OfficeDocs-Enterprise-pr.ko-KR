---
title: "Microsoft 365 엔터프라이즈 개발/테스트 환경"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_TLGs
- Strat_O365_Enterprise
ms.assetid: 6f916a77-301c-4be2-b407-6cec4d80df76
description: "요약:이 테스트 랩 가이드를 사용 하 여 Office 365 e 5, Enterprise 이동성 + 보안 (EMS) e 5 및 Windows 10 Enterprise를 실행 하는 컴퓨터를 포함 하는 개발/테스트 환경을 만들 수 있습니다."
ms.openlocfilehash: 3996035bf954b9e6e8ee1f6157c875a041fc3f90
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/09/2018
---
# <a name="the-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="4b15a-103">Microsoft 365 엔터프라이즈 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="4b15a-103">The Microsoft 365 Enterprise dev/test environment</span></span>

 <span data-ttu-id="4b15a-104">**요약:** 이 테스트 랩 가이드를 사용 하 여 Office 365 e 5, Enterprise 이동성 + 보안 (EMS) e 5 및 Windows 10 Enterprise를 실행 하는 컴퓨터를 포함 하는 개발/테스트 환경을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-104">**Summary:** Use this Test Lab Guide to create a dev/test environment that includes Office 365 E5, Enterprise Mobility + Security (EMS) E5, and a computer running Windows 10 Enterprise.</span></span>
  
<span data-ttu-id="4b15a-105">이 문서를 [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise)의 특징과 기능을 테스트 하려면 단순화 된 환경을 만드는 단계별 지침을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-105">This article provides you with step-by-step instructions to create a simplified environment to test the features and functionality of [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise).</span></span>
  
## <a name="phase-1-create-your-office-365-e5-subscription"></a><span data-ttu-id="4b15a-106">1 단계: Office 365 E5 구독 만들기</span><span class="sxs-lookup"><span data-stu-id="4b15a-106">Phase 1: Create your Office 365 E5 subscription</span></span>

<span data-ttu-id="4b15a-107">2 단계 및 [Office 365 개발/테스트 환경](office-365-dev-test-environment.md) 의 3 단계를 그림 1에 표시 된 것과 같이 lightweight Office 365 개발/테스트 환경 만들기의 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-107">Follow the steps in Phase 2 and Phase 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md) to create a lightweight Office 365 dev/test environment, as shown in Figure 1.</span></span>
  
<span data-ttu-id="4b15a-108">**그림 1: 해당 Azure Active Directory (AD) 테 넌 트 및 사용자 계정으로 Office 365 E5 구독**</span><span class="sxs-lookup"><span data-stu-id="4b15a-108">**Figure 1: Your Office 365 E5 subscription with its Azure Active Directory (AD) tenant and user accounts**</span></span>

![Microsoft 3656 Enterprise 개발/테스트 환경 1단계](images/65bb027b-fb59-46eb-aec2-38c0af425168.png)
  
## <a name="phase-2-add-ems"></a><span data-ttu-id="4b15a-110">2 단계: EMS 추가</span><span class="sxs-lookup"><span data-stu-id="4b15a-110">Phase 2: Add EMS</span></span>

<span data-ttu-id="4b15a-111">이 단계에서 EMS E5 평가판 구독에 대 한 등록 하 여 Office 365 E5 평가판 구독와 같은 조직에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-111">In this phase, you sign up for the EMS E5 trial subscription and add it to the same organization as your Office 365 E5 trial subscription.</span></span>
  
<span data-ttu-id="4b15a-112">먼저, EMS E5 평가판 구독을 추가 하 고 전역 관리자 계정에는 EMS 라이선스를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-112">First, add the EMS E5 trial subscription and assign an EMS license to your global administrator account.</span></span>
  
1. <span data-ttu-id="4b15a-p101">인터넷 브라우저의 개인 인스턴스와 전역 관리자 계정 자격 증명을 사용 하 여 Office 365 포털에 로그인 합니다. 도움말을 보려면 [Office 365에 로그인 할 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="4b15a-p101">With a private instance of an Internet browser, sign in to the Office 365 portal with your global administrator account credentials. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="4b15a-115">**Admin** 타일을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-115">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="4b15a-116">왼쪽 탐색 영역에서 브라우저에서 **Office 관리 센터** 탭을 클릭 **대금 청구 > 구매 서비스**합니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-116">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="4b15a-p102">**서비스 구매** 페이지 **Enterprise 이동성 + 보안 e 5** 항목을 찾습니다. 마우스 포인터를 올려 하 고 **무료 평가판을 시작**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-p102">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="4b15a-119">**주문 확인** 페이지에서 **지금 시도**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-119">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="4b15a-120">**순서 확인** 페이지에서 **계속**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-120">On the **Order receipt** page, click **Continue**.</span></span>
    
7. <span data-ttu-id="4b15a-121">왼쪽 탐색 영역에서 브라우저에서 **Office 365 관리 센터** 탭을 클릭 **사용자 > 활성 사용자**합니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-121">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
8. <span data-ttu-id="4b15a-122">전역 관리자 계정을 클릭 하 고 **제품 라이선스**에 대 한 **편집** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-122">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
9. <span data-ttu-id="4b15a-123">**제품 라이선스** 창에서 **엔터프라이즈 이동성 + 보안 e 5** **전환**에 대 한 제품 라이선스 설정, **저장** 을 클릭 하 고 두번 **닫기** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-123">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
> [!NOTE]
> <span data-ttu-id="4b15a-p103">Enterprise Mobility + Security E5 평가판 구독 기간은 90일입니다. 영구 개발/테스트 환경의 경우 소수의 라이선스를 사용해서 유료 구독을 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-p103">The Enterprise Mobility + Security E5 trial subscription is 90 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
 <span data-ttu-id="4b15a-126">***3 단계를 완료 한 경우*** [Office 365 개발/테스트 환경](office-365-dev-test-environment.md) 에서는 모든 (사용자 2, 사용자 3, 4 사용자 및 사용자 5) 사용자 계정에 대해 8과 이전 절차의 9 단계를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-126">***If you completed Phase 3 of*** [Office 365 dev/test environment](office-365-dev-test-environment.md) , repeat steps 8 and 9 of the previous procedure for all of your other accounts (User 2, User 3, User 4, and User 5).</span></span>
  
<span data-ttu-id="4b15a-127">개발/테스트 환경을 현재가지고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-127">Your dev/test environment now has:</span></span>
  
- <span data-ttu-id="4b15a-128">사용자 계정 목록과 동일한 조직 및 동일한 Azure AD 테넌트를 공유하는 Office 365 E5 Enterprise 및 EMS 평가판 구독</span><span class="sxs-lookup"><span data-stu-id="4b15a-128">Office 365 E5 Enterprise and EMS trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="4b15a-129">Office 365 e 5 및 EMS e 5를 사용 하 여 모든 적절 한 사용자 계정 (전역 관리자만 또는 모든 5 개의 사용자 계정) 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-129">All your appropriate user accounts (either just the global administrator or all five user accounts) are enabled to use Office 365 E5 and EMS E5.</span></span>
    
<span data-ttu-id="4b15a-130">그림 2 EMS를 추가 하는 구성에 결과 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-130">Figure 2 shows your resulting configuration, which adds EMS.</span></span>
  
<span data-ttu-id="4b15a-131">**그림 2: EMS 평가판 구독 추가 (영문)**</span><span class="sxs-lookup"><span data-stu-id="4b15a-131">**Figure 2: Adding the EMS trial subscription**</span></span>

![Microsoft 3656 Enterprise 개발/테스트 환경 2단계](images/8a01a483-3de2-41f3-a845-141c7edd0cb0.png)
  
## <a name="phase-3-create-a-windows-10-enterprise-computer"></a><span data-ttu-id="4b15a-133">3 단계: Windows 10 엔터프라이즈 컴퓨터 만들기</span><span class="sxs-lookup"><span data-stu-id="4b15a-133">Phase 3: Create a Windows 10 Enterprise computer</span></span>

<span data-ttu-id="4b15a-134">이 단계에서는 Windows 10 Enterprise를 실행 하는 독립 실행형 컴퓨터를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-134">In this phase, you create a standalone computer running Windows 10 Enterprise.</span></span>
  
### <a name="physical-computer"></a><span data-ttu-id="4b15a-135">실제 컴퓨터</span><span class="sxs-lookup"><span data-stu-id="4b15a-135">Physical computer</span></span>

<span data-ttu-id="4b15a-p104">개인 컴퓨터를 받아에 Windows 10 Enterprise를 설치 합니다. Windows 10 Enterprise 평가판 [여기](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise)다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-p104">Obtain a personal computer and install Windows 10 Enterprise on it. You can download the Windows 10 Enterprise trial [here](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).</span></span>
  
### <a name="virtual-machine"></a><span data-ttu-id="4b15a-138">가상 컴퓨터</span><span class="sxs-lookup"><span data-stu-id="4b15a-138">Virtual machine</span></span>

<span data-ttu-id="4b15a-p105">사용자가 선택한 하이퍼바이저를 사용 하 여 가상 컴퓨터를 만들고에 Windows 10 Enterprise를 설치 합니다. Windows 10 Enterprise 평가판 [여기](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise)다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-p105">Create a virtual machine using the hypervisor of your choice and install Windows 10 Enterprise on it. You can download the Windows 10 Enterprise trial [here](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).</span></span>
  
### <a name="virtual-machine-in-azure"></a><span data-ttu-id="4b15a-141">Azure에 가상 컴퓨터</span><span class="sxs-lookup"><span data-stu-id="4b15a-141">Virtual machine in Azure</span></span>

<span data-ttu-id="4b15a-p106">***Visual Studio 기반 구독 있어야***Windows 10 Enterprise에 대 한 이미지에 액세스할 수 있는 Microsoft Azure에서 Windows 10 가상 컴퓨터를 생성 합니다. 다른 유형의 평가판 및 유료 구독 등 Azure 구독에이 이미지에 대 한 액세스를 사용할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-p106">To create a Windows 10 virtual machine in Microsoft Azure, ***you must have a Visual Studio-based subscription***, which has access to the image for Windows 10 Enterprise. Other types of Azure subscriptions, such as trial and paid subscriptions, do not have access to this image.</span></span>
  
> [!NOTE]
> <span data-ttu-id="4b15a-p107">다음 명령 집합 텍스트 Azure PowerShell의 최신 버전을 사용 합니다. [Azure PowerShell cmdlet 시작](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/)을 참조 하십시오. 이 명령 집합 빌드 Windows 10 엔터프라이즈 가상 컴퓨터에는 WIN10 및 리소스 그룹, 사용자는 저장소 계정이 및 가상 네트워크를 포함 하 여 필요한 인프라의 모든 라는 합니다. Azure 인프라 서비스에 익숙한 사용자의 현재 배포 된 인프라에 맞게 이러한 지침에 맞게 조정 하십시오.</span><span class="sxs-lookup"><span data-stu-id="4b15a-p107">The following command sets use te latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/). These command sets build a Windows 10 Enterprise virtual machine named WIN10 and all of its required infrastructure, including a resource group, a storage account, and a virtual network. If you are already familiar with Azure infrastructure services, please adapt these instructions to suit your currently deployed infrastructure.</span></span> 
  
<span data-ttu-id="4b15a-148">먼저, Microsoft PowerShell 프롬프트를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-148">First, start a Microsoft PowerShell prompt.</span></span>
  
<span data-ttu-id="4b15a-149">다음 명령 사용 하 여 Azure 계정에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-149">Sign in to your Azure account with the following command.</span></span>
  
```
Login-AzureRMAccount
```

<span data-ttu-id="4b15a-150">다음 명령을 사용하여 구독 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-150">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

<span data-ttu-id="4b15a-p108">Azure 구독을 설정 합니다. 따옴표를 포함 하 여 입력을 내에 있는 모든 항목을 교체는 \< 및 > 올바른 이름의 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-p108">Set your Azure subscription. Replace everything within the quotes, including the \< and > characters, with the correct name.</span></span>
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

<span data-ttu-id="4b15a-p109">다음으로 새 리소스 그룹을 만듭니다. 고유한 리소스 그룹 이름을 확인하려면 이 명령을 사용하여 기존 리소스 그룹을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-p109">Next, create a new resource group. To determine a unique resource group name, use this command to list your existing resource groups.</span></span>
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="4b15a-p110">이러한 명령을 사용 하면 새 자원 그룹을 만듭니다. 교체 따옴표를 포함 하 여 입력을 내에 있는 모든 항목은 \< 및 > 올바른 이름 사용 하 여 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-p110">Create your new resource group with these commands. Replace everything within the quotes, including the \< and > characters, with the correct names.</span></span>
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="4b15a-p111">리소스 관리자 기반 가상 컴퓨터 저장소 리소스 관리자 기반 계정이 필요합니다. *소문자 및 숫자를 포함 하* 여 저장소 계정에 대해 전역적으로 고유 이름을 선택 해야 합니다. 기존 저장소 계정을 나열 하려면이 명령을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-p111">Resource Manager-based virtual machines require a Resource Manager-based storage account. You must pick a globally unique name for your storage account  *that contains only lowercase letters and numbers*  . You can use this command to list the existing storage accounts.</span></span>
  
```
Get-AzureRMStorageAccount | Sort StorageAccountName | Select StorageAccountName
```

<span data-ttu-id="4b15a-160">이 명령을 사용하여 제안된 저장소 계정 이름이 고유한지 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-160">Use this command to test whether a proposed storage account name is unique.</span></span>
  
```
Get-AzureRmStorageAccountNameAvailability "<proposed name>"
```

<span data-ttu-id="4b15a-161">이러한 명령을 사용하여 새 테스트 환경에 대한 새 저장소 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-161">Create a new storage account for your new test environment with these commands.</span></span>
  
```
$rgName="<your new resource group name>"
$saName="<storage account name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
New-AzureRMStorageAccount -Name $saName -ResourceGroupName $rgName -Type Standard_LRS -Location $locName
```

<span data-ttu-id="4b15a-p112">다음으로 만들면 새 가상 네트워크에 연결 하 고 WIN10 가상 컴퓨터 이러한 명령을 사용 합니다. 대화 상자가 나타나면 WIN10에 대 한 이름 및 로컬 관리자 계정의 암호를 제공 하 고 이러한 안전한 위치에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-p112">Next, you create a new virtual network and the WIN10 virtual machine with these commands. When prompted, provide the name and password of the local administrator account for WIN10 and store these in a secure location.</span></span>
  
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
$storageAcc=Get-AzureRMStorageAccount -ResourceGroupName $rgName -Name $saName
$cred=Get-Credential -Message "Type the name and password of the local administrator account for WIN10."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName WIN10 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftVisualStudio -Offer Windows -Skus Windows-10-N-x64 -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$osDiskUri=$storageAcc.PrimaryEndpoints.Blob.ToString() + "vhds/WIN10-TestLab-OSDisk.vhd"
$vm=Set-AzureRMVMOSDisk -VM $vm -Name WIN10-TestLab-OSDisk -VhdUri $osDiskUri -CreateOption fromImage
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

## <a name="phase-4-join-your-windows-10-computer-to-azure-ad"></a><span data-ttu-id="4b15a-164">4 단계: Azure AD를 Windows 10 컴퓨터를 가입 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-164">Phase 4: Join your Windows 10 computer to Azure AD</span></span>

<span data-ttu-id="4b15a-165">실제 또는 가상 컴퓨터를 만든 Windows 10 Enterprise를 사용 하 여 구성 하 고 실행 되 고, 로컬 관리자 계정을 사용 하 여 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-165">After the physical or virtual machine is created, configured with Windows 10 Enterprise, and is running, sign in with a local administrator account.</span></span>
  
> [!NOTE]
> <span data-ttu-id="4b15a-p113">Azure에 가상 컴퓨터에 대 한 [다음이 지침](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon)을 사용 하 여 연결 합니다. 로컬 관리자 계정의 자격 증명을 사용 하 여 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-p113">For a virtual machine in Azure, connect to it using [these instructions](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon). Sign in with the credentials of the local administrator account.</span></span> 
  
<span data-ttu-id="4b15a-168">다음으로, Office 365 및 EMS 구독의 Azure AD 테 넌 트 WIN10 컴퓨터에 가입 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-168">Next, join the WIN10 computer to the Azure AD tenant of your Office 365 and EMS subscriptions.</span></span>
  
1. <span data-ttu-id="4b15a-169">WIN10 컴퓨터의 바탕 화면에서 클릭 **시작 > 설정 > 계정 > 액세스 작업 또는 학교 > 연결**합니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-169">At the desktop of the WIN10 computer, click **Start > Settings > Accounts > Access work or school > Connect**.</span></span>
    
2. <span data-ttu-id="4b15a-170">**작업이 나 교육용 계정 설정** 대화 상자에서 **Azure Active Directory에이 장치에 참가**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-170">In the **Set up a work or school account** dialog box, click **Join this device to Azure Active Directory**.</span></span>
    
3. <span data-ttu-id="4b15a-171">**작업 또는 학교 계정**, Office 365 구독의 전역 관리자 계정 이름을 입력 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-171">In **Work or school account**, type the global administrator account name of your Office 365 subscription, and then click **Next**.</span></span>
    
4. <span data-ttu-id="4b15a-172">**암호 입력**전역 관리자 계정의 암호를 입력 하 고 **로그인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-172">In **Enter password**, type the password for your global administrator account, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="4b15a-173">이 조직 있는지 확인 대화 상자가 나타나면 **참가**클릭 하 고 **완료**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-173">When prompted to make sure this is your organization, click **Join**, and then click **Done**.</span></span>
    
6. <span data-ttu-id="4b15a-174">설정 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-174">Close the settings window.</span></span>
    
<span data-ttu-id="4b15a-175">다음으로, Office 2016 WIN10 컴퓨터에 설치</span><span class="sxs-lookup"><span data-stu-id="4b15a-175">Next, install Office 2016 on the WIN10 computer</span></span>
  
1. <span data-ttu-id="4b15a-p114">Microsoft에 지 브라우저를 열고 전역 관리자 계정 자격 증명을 사용 하 여 Office 365 포털에 로그인 합니다. 도움말을 보려면 [Office 365에 로그인 할 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="4b15a-p114">Open the Microsoft Edge browser and sign in to the Office 365 portal with your global administrator account credentials. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="4b15a-178">**Microsoft Office 홈** 탭에서 **Office 2016 설치**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-178">On the **Microsoft Office Home** tab, click **Install Office 2016**.</span></span>
    
3. <span data-ttu-id="4b15a-179">수행할 작업을 함께 대화 상자가 나타나면 **실행**을 차례로 클릭 하 고 **사용자 계정 컨트롤**에 대 한 **예** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-179">When prompted with what to do, click **Run**, and then click **Yes** for **User Account Control**.</span></span>
    
4. <span data-ttu-id="4b15a-p115">Office 설치를 완료 될 때까지 기다립니다. 참조 하는 경우 **모두 설정 하 고 있는!**를 두번 **닫기** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-p115">Wait for Office to complete its installation. When you see **You're all set!**, click **Close** twice.</span></span>
    
<span data-ttu-id="4b15a-182">그림 3에는 Office 365 및 EMS 구독의 Azure AD 테 넌 트에 참가 하는 WIN10 컴퓨터를 포함 하는 결과 환경을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-182">Figure 3 shows your resulting environment, which includes the WIN10 computer that has joined the Azure AD tenant of your Office 365 and EMS subscriptions.</span></span>
  
<span data-ttu-id="4b15a-183">**그림 3: Azure AD 테 넌 트에 WIN10 컴퓨터 계정 추가**</span><span class="sxs-lookup"><span data-stu-id="4b15a-183">**Figure 3: Adding the WIN10 computer account to the Azure AD tenant**</span></span>

![Microsoft 3656 Enterprise 개발/테스트 환경 4단계](images/20680f6a-f77e-4333-aaa9-f7cf5e4b0d03.png)
  
<span data-ttu-id="4b15a-185">이제 [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise)의 추가 기능을 테스트해 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-185">You are now ready to experiment with additional features of [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise).</span></span>
  
## <a name="next-steps"></a><span data-ttu-id="4b15a-186">다음 단계</span><span class="sxs-lookup"><span data-stu-id="4b15a-186">Next steps</span></span>

<span data-ttu-id="4b15a-187">이러한 추가 문서를 사용 하 여 Microsoft 365 Enterprise의 기능에 알아보십시오.</span><span class="sxs-lookup"><span data-stu-id="4b15a-187">Use these additional articles to explore features of Microsoft 365 Enterprise:</span></span>
  
- [<span data-ttu-id="4b15a-188">모바일 응용 프로그램 관리 (MAM) 정책 추가</span><span class="sxs-lookup"><span data-stu-id="4b15a-188">Add mobile application management (MAM) policies</span></span>](https://technet.microsoft.com/library/mt764059.aspx)
    
- [<span data-ttu-id="4b15a-189">IOS 및 Android 장치 등록</span><span class="sxs-lookup"><span data-stu-id="4b15a-189">Enroll iOS and Android devices</span></span>](https://technet.microsoft.com/library/mt743077.aspx)
    
- [<span data-ttu-id="4b15a-190">구성 및 테스트 고급 보안 관리</span><span class="sxs-lookup"><span data-stu-id="4b15a-190">Configure and test Advanced Security Management</span></span>](https://technet.microsoft.com/library/mt757250.aspx)
    
- [<span data-ttu-id="4b15a-191">구성 하 고 고급 위협 보호를 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b15a-191">Configure and test Advanced Threat Protection</span></span>](https://technet.microsoft.com/library/mt490479.aspx)
    
## <a name="see-also"></a><span data-ttu-id="4b15a-192">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b15a-192">See Also</span></span>

[<span data-ttu-id="4b15a-193">하나의 Microsoft 클라우드 개발/테스트 환경</span><span class="sxs-lookup"><span data-stu-id="4b15a-193">The One Microsoft Cloud dev/test environment</span></span>](the-one-microsoft-cloud-dev-test-environment.md)

[<span data-ttu-id="4b15a-194">Microsoft 365 Enterprise 설명서</span><span class="sxs-lookup"><span data-stu-id="4b15a-194">Microsoft 365 Enterprise documentation</span></span>](https://docs.microsoft.com/microsoft-365-enterprise/)




