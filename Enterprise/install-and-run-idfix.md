---
title: Office 365 IdFix 도구 설치 및 실행
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: get-started-article
f1_keywords:
- O365E_HRCSetupAADConnectIDFixLM617036
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: Office 365 IdFix 도구를 설치 하 고 실행 하 여 Office 365로 동기화 하기 전에 active directory를 정리 하는 방법을 알아봅니다.
ms.openlocfilehash: 4197694ce90ab600652aa729809ef0ddb0647e03
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067294"
---
# <a name="install-and-run-the-office-365-idfix-tool"></a>Office 365 IdFix 도구 설치 및 실행

IdFix는 Office 365로 동기화 하기 전에 디렉터리의 중복 및 서식 문제와 같은 오류를 식별 합니다. 
  
이 작업을 성공적으로 완료 하려면 Active Directory에서 사용자, 그룹 및 연락처 개체를 사용 하 여 작업 하는 것이 좋습니다.
  
이 작업을 완료할 수 없는 경우에는 몇 가지 다른 작업을 수행할 수 있습니다. 이러한 방법을 사용 하는 것이 쉬울 수도 있지만 더 오래 걸리거나 다른 단점이 있을 수 있습니다. 출력은 다음과 같습니다.
  
- **IdFix를 실행 하지 않고 디렉터리 동기화를 실행 합니다.** IdFix 도구를 실행 하지 않고 디렉터리를 동기화 할 수는 있지만 권장 하지는 않습니다. 동기화 하기 전에 오류를 수정 하면 시간이 더 오래 걸리고 클라우드로 보다 원활한 전환이 제공 되는 경우가 많습니다. 
- **컨설턴트를 고용 합니다.** 전문가의 도움을 받아 사용자의 작업을 빠르게 수행 하 고 디렉터리를 동기화 할 수 있습니다. 
    
## <a name="what-you-need-to-run-idfix"></a>IdFix를 실행 하는 데 필요한 사항

IdFix를 다운로드 하 고 실행 하는 가장 쉬운 방법은 도메인에 가입 된 컴퓨터에 설치 하는 것입니다. 필요한 경우 도메인 컨트롤러에서이를 실행할 수 있습니다.
  
### <a name="idfix-hardware-requirements"></a>IdFix 하드웨어 요구 사항

IdFix를 설치 하는 컴퓨터는 다음과 같은 최소 하드웨어 요구 사항을 충족 해야 합니다.
  
- 4GB RAM
- 2gb의 하드 디스크 공간
    
### <a name="idfix-software-requirements"></a>IdFix 소프트웨어 요구 사항

IdFix를 설치 하는 컴퓨터는 사용자를 Office 365와 동기화 하려는 동일한 Active Directory 도메인에 가입 되어 있어야 합니다. 또한 컴퓨터에 .NET Framework 4.0이 설치 되어 있어야 합니다. 
  
Windows Server 2008 또는 Windows Server 2012를 실행 하는 경우에는 .NET Framework가 이미 설치 되어 있을 것입니다. 그렇지 않으면 [다운로드 센터에서](https://go.microsoft.com/fwlink/p/?LinkId=400475) 또는 Windows Update를 통해 .net 4.0을 다운로드할 수 있습니다. 
  
### <a name="idfix-permissions-requirements"></a>IdFix 사용 권한 요구 사항

IdFix를 실행 하는 데 사용 하는 사용자 계정에는 디렉터리에 대 한 읽기/쓰기 권한이 있어야 합니다.
  
사용자 계정이 이러한 요구 사항을 충족 하는지 확인 하는 방법을 모르는 경우에도 IdFix를 설치 하 고 실행할 수 있습니다. 사용자 계정에 적절 한 사용 권한이 없는 경우에는 IdFix에서 오류를 실행 하려고 하면 오류가 표시 됩니다.
  
## <a name="install-idfix"></a>IdFix 설치

IdFix를 설치 하려면 **idfix**를 다운로드 하 고 압축을 풉니다. 
  
1. IdFix 도구를 설치 하려는 컴퓨터에 로그온 합니다.
    
2. [Idfix DirSync 오류 수정 도구](https://go.microsoft.com/fwlink/?linkid=867219)에 대 한 Microsoft 다운로드 사이트로 이동 합니다.
    
3. **다운로드**를 선택합니다.
    
4. 메시지가 표시 되 면 **실행**을 선택 합니다.
    
5. **WinZip 자동 추출** 대화 상자의 **폴더에 대 한 압축 풀기** 텍스트 상자에서 idfix 도구를 설치 하려는 위치를 입력 하거나 찾습니다. 기본적으로 IdFix는에 `C:\Deployment Tools\`설치 됩니다. 
    
6. **압축 풀기를**선택 합니다.
    
## <a name="run-the-idfix-tool"></a>IdFix 도구 실행

IdFix를 설치한 후이 도구를 실행 하 여 디렉터리에서 문제를 검색 합니다.
  
1. 디렉터리에 대 한 읽기/쓰기 권한이 있는 계정을 사용 하 여 IdFix를 설치한 컴퓨터에 로그온 합니다.
    
2. 파일 탐색기에서 IdFix를 설치한 위치로 이동 합니다. 설치 중에 기본 폴더를 선택한 경우로 이동 `C:\Deployment Tools\IdFix`합니다.
    
3. **Idfix .exe**를 두 번 클릭 합니다. 
    
    ![IdFix .exe 파일을 선택 합니다.](media/a9387bbc-991f-41c2-a500-45e3ce574285.JPG)
  
4. 기본적으로 IdFix에서는 다중 테 넌 트 규칙 집합을 사용 하 여 디렉터리의 항목을 테스트 합니다. 이는 대부분의 Office 365 고객에 게 적합 한 규칙 집합입니다. 그러나 Office 365 전용 또는 ITAR (Arm 규정의 해외 트래픽) 고객의 경우에는 대신 전용 규칙 집합을 사용 하도록 IdFix를 구성할 수 있습니다. 어떤 종류의 고객 인지 잘 모르는 경우이 단계를 무시 해도 됩니다. 규칙 집합을 전용으로 설정 하려면 메뉴 모음에서 톱니 바퀴 아이콘을 클릭 한 다음 **전용**을 선택 합니다.
    
5. **쿼리**를 선택 합니다.
    
    ![IdFix에서 쿼리를 선택 합니다.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. 기본적으로 IdFix는 전체 디렉터리에서 오류를 검색 합니다.
    
    디렉터리 크기에 따라 쿼리를 실행 하는 데 다소 시간이 걸릴 수 있습니다. 도구 주 창의 아래쪽에 있는 진행률을 볼 수 있습니다. **취소**를 클릭 한 경우 처음부터 다시 시작 해야 합니다.
    
    ![IdFix 쿼리 및 오류 수입니다.](media/da0198a0-7d4d-4afe-a256-e82f1330ada5.JPG)
  
7. IdFix에서 쿼리를 완료 한 후 오류가 없으면 디렉터리를 동기화 할 수 있습니다. 디렉터리에 오류가 있는 경우 동기화 하기 전에 문제를 해결 하는 것이 좋습니다. 오류 유형과 각 문제를 해결 하는 데 가장 적합 한 방법에 대 한 구체적인 정보를 보려면이 항목 끝부분에 있는 링크를 참조 하십시오. 
    
    동기화 하기 전에 오류를 반드시 수정 해야 하는 것은 아니며, IdFix에서 반환한 오류를 모두 검토 하는 것이 좋습니다.
    
    각 오류는 도구의 주 창에 별도의 행으로 표시 됩니다. 
    
8. **업데이트** 열에 제안 된 변경 내용에 동의 하는 경우 **작업** 열에서 idfix에서 변경을 구현 하기 위해 수행할 작업을 선택 하 고 **적용**을 클릭 합니다. **적용**을 클릭 하면 도구에서 디렉터리를 변경 합니다.
    
    각 업데이트 후에는 **적용** 을 클릭할 필요가 없습니다. 대신, IdFix를 클릭 하기 전에 몇 가지 **** 오류를 수정 하 여이를 모두 동시에 변경할 수 있습니다. 오류 유형을 나열 하는 열 맨 위에 있는 **오류** 를 클릭 하 여 오류 유형별로 오류를 정렬할 수 있습니다. 
    
    한 가지 전략은 동일한 유형의 모든 오류를 수정 하는 것입니다. 예를 들어 먼저 모든 중복 항목을 수정 하 고 적용 합니다. 그런 다음 문자 서식 오류 등을 수정 합니다. IdFix 도구는 변경 내용을 적용할 때마다 사용자가 실수 한 경우 변경 내용을 취소 하는 데 사용할 수 있는 별도의 로그 파일을 만듭니다. [트랜잭션 로그](idfix-transaction-log.md) 는 idfix를 설치한 폴더에 저장 됩니다.  _C:\deployment_ 도구 \ id 기본적으로 수정 합니다. 
    
    ![IdFix에서 오류를 수정.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. 디렉터리를 변경한 후에는 IdFix를 다시 실행 하 여 수정한 내용에 새 오류가 발생 하지 않았는지 확인 합니다. 필요한 횟수 만큼 이러한 단계를 반복할 수 있습니다. 동기화 하기 전에 몇 번까지 프로세스를 진행 하는 것이 좋습니다.
    
## <a name="i-want-to-refine-my-search-or-dig-deeper-into-the-errors-what-else-can-i-do-with-idfix"></a>검색을 구체화 하거나 오류를 자세히 살펴보고 IdFix에서는 어떤 작업을 수행할 수 있나요?

자세한 내용은 다음 항목에서 확인할 수 있습니다.
  
- [IdFix 도구를 사용 하 여 Office 365과 동기화 하기 위한 디렉터리 특성을 준비](prepare-directory-attributes-for-synch-with-idfix.md) 합니다. 이 도구를 설치한 후에는이 항목으로 이동 하 여 도구 실행에 대 한 자세한 지침, 발생 하는 일반적인 오류, 제안 되는 수정 작업, 예제 및 많은 오류가 발생 했을 때 수행 해야 하는 상황에 대 한 모범 사례를 확인할 수 있습니다. 
- [참조: IdFix 제외 및 지원 개체/특성](idfix-excluded-and-supported-objects-and-attributes.md)  
- [참조: Office 365 IdFix 트랜잭션 로그](idfix-transaction-log.md)
    
## <a name="video-training"></a>동영상 교육

자세한 내용은 LinkedIn 학습을 통해 제공 되는이과에서 [IDFix 도구 설치 및 사용](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US)을 참조 하세요.
  

