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
ms.openlocfilehash: 03fa8e0a4e8d90fcb834eeb2491d3dd39b67ff05
ms.sourcegitcommit: 771f227d3049498fcbd7cfbeaf649e3d77e73c86
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
ms.locfileid: "19178650"
---
# <a name="the-microsoft-365-enterprise-devtest-environment"></a>Microsoft 365 Enterprise 개발/테스트 환경

 **요약:** 이 테스트 랩 가이드를 사용하여 Office 365 E5, EMS(Enterprise Mobility + Security) E5 및 Windows 10 Enterprise를 실행하는 컴퓨터가 포함되는 개발/테스트 환경을 만듭니다.
  
이 문서에서는 [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise)의 특성 및 기능을 테스트하는 간소화된 환경을 만들기 위한 단계별 지침을 제공합니다.
  
## <a name="phase-1-create-your-office-365-e5-subscription"></a>1단계: Office 365 E5 구독 만들기

그림 1과 같이 [Office 365 개발/테스트 환경](office-365-dev-test-environment.md)의 2, 3단계의 세부 단계를 수행하여 경량의 Office 365 개발/테스트 환경을 만듭니다.
  
**그림 1: 해당 Azure AD(Active Directory) 테넌트 및 사용자 계정을 사용하는 Office 365 E5 구독**

![Microsoft 3656 Enterprise 개발/테스트 환경 1단계](images/65bb027b-fb59-46eb-aec2-38c0af425168.png)

> [!NOTE]
> Office 365 E5 평가판 구독 기간은 30일이며, 60일까지 쉽게 연장할 수 있습니다. 영구 개발/테스트 환경의 경우 소수의 라이선스를 사용해서 유료 구독을 새로 만듭니다. 
  
## <a name="phase-2-add-ems"></a>2단계: EMS 추가

이 단계에서는 EMS E5 평가판 구독을 등록하고 Office 365 E5 평가판 구독과 동일한 조직에 추가합니다.
  
먼저, EMS E5 평가판 구독을 추가하고 전역 관리자 계정에 EMS 라이선스를 할당합니다.
  
1. 인터넷 브라우저의 개인 인스턴스를 사용하고 전역 관리자 계정 자격 증명으로 Office 365 포털에 로그인합니다. 도움을 받으려면 [Office 365에 로그인하는 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조하세요.
    
2. **관리** 타일을 클릭합니다.
    
3. 브라우저의 **Office 관리 센터** 탭에 있는 왼쪽 탐색 영역에서 **대금 청구 > 서비스 구매**를 차례로 클릭합니다.
    
4. 
            **구매 서비스** 페이지에서 **Enterprise Mobility + Security E5** 항목을 찾습니다. 마우스 포인터를 가져간 후 **평가판 시작**을 클릭합니다.
    
5. **주문 확인** 페이지에서 **지금 평가판 사용**을 클릭합니다.
    
6. **주문 접수** 페이지에서 **계속**을 클릭합니다.
    
7. 브라우저의 **Office 365 관리 센터** 탭에 있는 왼쪽 탐색 영역에서 **사용자 > 활성 사용자**를 차례로 클릭합니다.
    
8. 전역 관리자 계정을 클릭한 다음, **제품 라이선스**에 대해 **편집**을 클릭합니다.
    
9. **제품 라이선스** 창에서 **Enterprise Mobility + Security E5**에 대한 제품 라이선스를 **설정**으로 바꾸고 **저장**을 클릭한 후 **닫기**를 두 번 클릭합니다.
    
> [!NOTE]
> Enterprise Mobility + Security E5 평가판 구독 기간은 90일입니다. 영구 개발/테스트 환경의 경우 소수의 라이선스를 사용해서 유료 구독을 새로 만듭니다. 
  
 [Office 365 개발/테스트 환경](office-365-dev-test-environment.md)의 ***3단계를 완료한 경우,*** 다른 모든 계정(사용자 2, 사용자 3, 사용자 4 및 사용자 5)에 대해 이전 절차의 8 및 9단계를 반복합니다.
  
이제 개발/테스트 환경에는 다음이 구현됩니다.
  
- 사용자 계정 목록과 동일한 Azure AD 테넌트를 공유하는 Office 365 E5 Enterprise 및 EMS E5 평가판 구독
- 모든 해당 사용자 계정(전역 관리자만 또는 5개의 사용자 계정 모두)이 Office 365 E5 및 EMS E5를 사용하도록 설정됩니다.
    
그림 2는 EMS를 추가하는 구성 결과를 보여줍니다.
  
**그림 2: EMS 평가판 구독 추가**

![Microsoft 3656 Enterprise 개발/테스트 환경 2단계](images/8a01a483-3de2-41f3-a845-141c7edd0cb0.png)
  
## <a name="phase-3-create-a-windows-10-enterprise-computer"></a>3단계: Windows 10 Enterprise 컴퓨터 만들기

이 단계에서는 Windows 10 Enterprise를 실행하는 독립 실행형 컴퓨터를 만듭니다.
  
### <a name="physical-computer"></a>실제 컴퓨터

개인용 컴퓨터를 구한 후 Windows 10 Enterprise를 설치합니다. Windows 10 Enterprise 평가판을 [여기](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise)에서 다운로드할 수 있습니다.
  
### <a name="virtual-machine"></a>가상 컴퓨터

사용자가 선택한 하이퍼바이저를 사용하여 가상 머신을 만들고 Windows 10 Enterprise를 설치합니다. Windows 10 Enterprise 평가판을 [여기](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise)에서 다운로드할 수 있습니다.
  
### <a name="virtual-machine-in-azure"></a>Azure의 가상 머신

Microsoft Azure에서 Windows 10 가상 머신을 만들려면 Windows 10 Enterprise에 대한 이미지에 액세스할 수 있는 ***Visual Studio 기반 구독이 있어야 합니다***. 다른 유형의 Azure 구독(예: 평가판 및 유료 구독)으로는 이 이미지에 액세스할 수 없습니다. 최신 정보를 보려면 [개발/테스트 시나리오에 Azure의 Windows 클라이언트 사용](https://docs.microsoft.com/azure/virtual-machines/windows/client-images)을 참조하세요.
  
> [!NOTE]
> 다음 명령에서는 최신 버전의 Azure PowerShell을 사용합니다. [Azure PowerShell cmdlet 시작](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/)을 참조하세요. 이러한 명령 집합은 WIN10이라는 Windows 10 Enterprise 가상 머신과 리소스 그룹, 저장소 계정 및 가상 네트워크를 포함하는 모든 필수 인프라를 빌드합니다. Azure 인프라 서비스에 이미 익숙한 경우 혅 배포된 인프라에 맞게 이러한 지침을 조정하세요. 
  
먼저 Microsoft PowerShell 프롬프트를 시작합니다.
  
다음 명령을 사용하여 Azure 계정에 로그인합니다.
  
```
Login-AzureRMAccount
```

다음 명령을 사용하여 구독 이름을 가져옵니다.
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

Azure 구독을 설정합니다. \< 및 > 문자를 포함하여 따옴표 안에 있는 모든 것을 올바른 이름으로 바꿉니다.
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

다음으로 새 리소스 그룹을 만듭니다. 고유한 리소스 그룹 이름을 확인하려면 이 명령을 사용하여 기존 리소스 그룹을 나열합니다.
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

이러한 명령을 사용하여 새 리소스 그룹을 만듭니다. \< 및 > 문자를 포함하여 따옴표 안에 있는 모든 내용을 올바른 이름으로 바꿉니다.
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

그런 후 다음 명령을 사용하여 새 가상 네트워크와 WIN10 가상 머신을 만듭니다. 메시지가 표시되면 WIN10의 로컬 관리자 계정에 대한 이름 및 암호를 제공하고 이러한 항목을 안전한 장소에 저장합니다.
  
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

## <a name="phase-4-join-your-windows-10-computer-to-azure-ad"></a>4단계: Azure AD에 Windows 10 컴퓨터 가입

Windows 10 Enterprise가 있는 실제 또는 가상 머신을 만든 후에 로컬 관리자 계정으로 로그인합니다.
  
> [!NOTE]
> Azure의 가상 머신은 [다음 지침](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon)을 사용하여 연결합니다. 로컬 관리자 계정의 자격 증명을 사용하여 로그인합니다. 
  
다음으로, WIN10 컴퓨터를 Office 365 및 EMS 구독의 Azure 테넌트에 가입합니다.
  
1. WIN10 컴퓨터의 데스크톱에서 **시작 > 설정 > 계정 > 회사 또는 학교 액세스 > 연결**을 클릭합니다.
    
2. **회사 또는 학교 계정 설정** 대화 상자에서 **Azure Active Directory에 이 장치 가입**을 클릭합니다.
    
3. **회사 또는 학교 계정**에서 Office 365 구독의 전역 관리자 계정 이름을 입력하고 **다음**을 클릭합니다.
    
4. **암호 입력**에 전역 관리자 계정의 암호를 입력하고 **로그인**을 클릭합니다.
    
5. 사용자의 조직이 맞는지 묻는 메시지가 표시되면 **가입**을 클릭하고 **완료**를 클릭합니다.
    
6. 설정 창을 닫습니다.
    
다음으로, WIN10 컴퓨터에 Office 365 ProPlus를 설치합니다.
  
1. Microsoft Edge 브라우저를 열고 전역 관리자 계정 자격 증명으로 Office 365 포털에 로그인합니다. 도움을 받으려면 [Office 365에 로그인하는 위치](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)를 참조하세요.
    
2. **Microsoft Office 홈** 탭에서 **Office 2016 설치**를 클릭합니다.
    
3. 수행할 작업을 묻는 메시지가 표시되면 **실행**을 클릭하고 **사용자 계정 컨트롤**에 대해 **예**를 클릭합니다.
    
4. Office 설치가 완료될 때까지 기다립니다. **모두 완료되었습니다.** 가 표시되면 **닫기**를 두 번 차례로 클릭합니다.
    
그림 3에서는 다음에 해당하는 WIN10 컴퓨터를 포함하는 결과 환경을 보여줍니다.

- Office 365 및 EMS 구독의 Azure 테넌트에 가입되어 있습니다.
- Intune(EMS)에 Azure AD 장치로 등록되어 있습니다.
- Office 365 ProPlus가 설치되어 있습니다.
  
**그림 3: Microsoft 365 개발/테스트 환경의 최종 구성**

![Microsoft 3656 Enterprise 개발/테스트 환경 4단계](images/20680f6a-f77e-4333-aaa9-f7cf5e4b0d03.png)
  
이제 [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise)의 추가 기능을 사용해볼 준비가 되었습니다.
  
## <a name="next-steps"></a>다음 단계

다음 추가 문서를 사용하여 Microsoft 365 Enterprise의 기능을 알아봅니다.
  
- [MAM(모바일 응용 프로그램 관리) 정책 추가](https://technet.microsoft.com/library/mt764059.aspx)
    
- [iOS 및 Android 장치 등록](https://technet.microsoft.com/library/mt743077.aspx)
    
- [Advanced Security Management 구성 및 테스트](https://technet.microsoft.com/library/mt757250.aspx)
    
- [Advanced Threat Protection 구성 및 테스트](https://technet.microsoft.com/library/mt490479.aspx)
    
## <a name="see-also"></a>참고 항목

- [Microsoft 365 Enterprise 설명서](https://docs.microsoft.com/microsoft-365-enterprise/)
- [Microsoft 365 Enterprise 배포](https://docs.microsoft.com/microsoft-365/enterprise/deploy-microsoft-365-enterprise)
- [One Microsoft Cloud 개발/테스트 환경](the-one-microsoft-cloud-dev-test-environment.md)
- [클라우드 도입 TLG(테스트 랩 가이드)](cloud-adoption-test-lab-guides-tlgs.md)
