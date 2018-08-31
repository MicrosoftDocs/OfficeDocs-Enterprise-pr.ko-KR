---
title: Office 365 IdFix 도구 설치 및 실행
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: get-started-article
f1_keywords:
- O365E_HRCSetupAADConnectIDFixLM617036
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: 설치 하 고 Office 365로 동기화 하기 전에 active directory 정리를 위해 Office 365 IdFix 도구를 실행 하는 방법입니다.
ms.openlocfilehash: 642273c0171603d627a19273a78fe66662f4caaf
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541929"
---
# <a name="install-and-run-the-office-365-idfix-tool"></a>Office 365 IdFix 도구 설치 및 실행

Office 365로 동기화 하기 전에 IdFix 예: 중복 항목 및 디렉터리 서식에 문제가 발생 하는 오류를 식별 합니다. 
  
이 작업을 성공적으로 완료 하려면 사용자, 그룹 및 Active Directory에서 연락처 개체를 사용 하는 방법을 알고 있어야 합니다.
  
이 작업을 완료할 수 없으면, 메시지를 몇 다른 작업을 수행할 수 있습니다. 이러한 방법을 쉽게, 될 수 있지만 시간이 오래 걸릴 또는 다른 단점이 수도 있습니다. 와 같습니다.
  
- **IdFix를 실행 하지 않고 디렉터리 동기화를 실행 합니다.** IdFix 도구를 실행 하지 않고 디렉터리를 동기화 할 수 있지만 좋습니다. 동기화 하기 전에 오류를 수정 시간이 적게 걸립니다 하 고 자주 클라우드로 원활 하 게 전환을 제공 합니다. 
- **컨설턴트를 고용합니다.** 전문가를 영입하면 사용자가 빠르게 시스템을 작동하고 디렉터리를 동기화하는 데 도움이 될 수 있습니다. 
    
## <a name="what-you-need-to-run-idfix"></a>IdFix를 실행하는 데 필요한 사항

IdFix를 준비 하는 방식으로 작업을 쉽게 수행 및 실행 중인 사용자의 도메인에 가입 된 컴퓨터에 설치 하는 것입니다. 하려고 하지만 필요 없는 경우 도메인 컨트롤러에서 해당를 실행할 수 있습니다.
  
### <a name="idfix-hardware-requirements"></a>IdFix 하드웨어 요구 사항

IdFix를 설치하는 컴퓨터는 다음과 같은 하드웨어 요구 사항을 충족해야 합니다.
  
- 4GB RAM(최소)
- 2GB의 하드 디스크 공간(최소)
    
### <a name="idfix-software-requirements"></a>IdFix 소프트웨어 요구 사항

IdFix 요구를 설치할 컴퓨터 사용자를 Office 365에 동기화 하려는 동일한 Active Directory 도메인에 가입 해야 합니다. 또한 컴퓨터.NET Framework 4.0을 설치 해야 합니다. 
  
Windows Server 2008 또는 Windows Server 2012를 실행 하는.NET Framework 설치 이미 됩니다. [다운로드 센터에서.NET 4.0을 다운로드할](https://go.microsoft.com/fwlink/p/?LinkId=400475) 수 그렇지 않은 경우 또는 Windows Update를 사용 하 여 합니다. 
  
### <a name="idfix-permissions-requirements"></a>IdFix 권한 요구 사항

IdFix를 실행하는 데 사용하는 사용자 계정은 디렉터리에 대해 읽기/쓰기 액세스 권한이 있어야 합니다.
  
이러한 요구를 충족 하는 사용자 계정 하 고 확인 하는 방법을 모를 경우 확실 하지 않은, 하는 경우 여전히를 설치 하 고 실행할 수 IdFix 엔터티입니다. 사용자 계정에 적절 한 사용 권한이 없으면 스크립트를 실행 하려고 하면 IdFix 오류가 표시 하면 됩니다.
  
## <a name="install-idfix"></a>IdFix 설치

IdFix를 설치하려면 다음 단계에 설명된 대로 **IdFix.exe**를 다운로드하고 압축을 풉니다. 
  
1. IdFix 도구를 설치하려는 컴퓨터에 로그온합니다.
    
2. [IdFix DirSync 오류 수정 도구](https://go.microsoft.com/fwlink/?linkid=867219)에 대 한 Microsoft 다운로드 사이트로 이동 합니다.
    
3. **다운로드**를 선택합니다.
    
4. 대화 상자가 나타나면 **실행**을 선택 합니다.
    
5. **WinZip Self-extractor** 대화 상자의 **폴더로 Unzip** 텍스트 상자에 입력 하거나 IdFix 도구를 설치 하려는 위치를 찾습니다. 기본적으로 IdFix C:\Deployment 도구에 설치\. 
    
6. **압축을 풉니다**를 선택 합니다.
    
## <a name="run-the-idfix-tool"></a>IdFix 도구 실행

IdFix를 설치한 후 이 도구를 실행하여 디렉터리의 문제를 검색합니다.
  
1. 해당 디렉터리에 대해 읽기/쓰기 액세스 권한이 있는 계정을 사용하여 IdFix를 설치한 컴퓨터에 로그온합니다.
    
2. 파일 탐색기에서 IdFix를 설치한 위치로 이동합니다. 설치 중에 기본 폴더를 선택한 경우 C:\Deployment Tools\IdFix로 이동합니다.
    
3. **IdFix.exe**를 두 번 클릭합니다. 
    
    ![IdFix.exe 파일을 선택 합니다.](media/a9387bbc-991f-41c2-a500-45e3ce574285.JPG)
  
4. 기본적으로 IdFix 디렉터리에 있는 항목을 테스트로 설정 하는 다중 테 넌 트 규칙을 사용 합니다. 대부분의 Office 365 고객에 대 한 설정 오른쪽 규칙입니다. 그러나 Office 365 전용 또는 ITAR (팔 규정에 국제 트래픽) 고객 인 경우 대신 설정 하는 전용된 규칙을 사용 하 여 IdFix를 구성할 수 있습니다. 확실치 않은 경우 어떤 유형의 하는 고객을 안전 하 게이 단계를 건너뛸 수 있습니다. 전용으로 설정 하는 규칙을 설정 하는 메뉴 모음에서 기어 아이콘을 클릭 하 고 **전용**을 선택 합니다.
    
5. **쿼리**를 선택 합니다.
    
    ![IdFix에서 쿼리를 선택 합니다.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. 기본적으로 IdFix는 전체 디렉터리에서 오류를 검색합니다.
    
    디렉터리의 크기에 따라 쿼리를 실행 하는 시간이 걸릴 수 있습니다. 도구의 주 창의 맨 아래에 진행 상황을 볼 수 있습니다. **취소**를 클릭 하는 경우 처음부터 다시 시작 해야 합니다.
    
    ![IdFix 쿼리 및 오류 수입니다.](media/da0198a0-7d4d-4afe-a256-e82f1330ada5.JPG)
  
7. IdFix가 쿼리를 완료하고 디렉터리에 오류가 없으면 계속해서 디렉터리를 동기화할 수 있습니다. 디렉터리에 문제가 있는 경우 먼저 수정한 후 동기화하는 것이 좋습니다. 오류 유형에 대한 보다 구체적인 정보와 각 오류를 수정하는 최선의 방법에 대한 권장 지침을 보려면 이 항목 끝에 제공되는 링크를 참고하세요. 
    
    동기화하기 전에 오류를 반드시 수정해야 하는 것은 아니지만 적어도 IdFix에서 반환한 오류를 모두 검토하는 것이 좋습니다.
    
    각 오류 도구의 주 창에서 별도 행에 표시 됩니다. 
    
8. **UPDATE** 열에 표시되는 제안 변경 내용에 동의하는 경우 **ACTION** 열에서 IdFix를 통해 구현할 변경 내용을 선택하고 **적용**을 클릭합니다. **적용**을 클릭하면 디렉터리가 변경됩니다.
    
    각 업데이트 한 후 **적용** 을 클릭 필요가 없습니다. 대신, **적용** 을 클릭 하 고 IdFix 동시에 모든 변경 됩니다 전에 여러 오류를 해결할 수 있습니다. 오류 형식을 나열 하는 열의 위쪽에 **오류** 클릭 하 여 오류 유형별 오류를 정렬할 수 있습니다. 
    
    한 가지 전략은 동일한 유형의 모든 오류를 수정 하려면 예: 모든 중복을 먼저, 수정 및 적용 합니다. 다음으로 문자 형식 오류를 수정 하 고 등. 변경 내용을 적용 하는 각 시간 IdFix 도구 실수 하는 경우에 변경 내용을 취소할를 사용할 수 있는 별도 로그 파일을 만듭니다. [트랜잭션 로그](idfix-transaction-log.md) 에서 IdFix를 설치한 폴더에 저장 됩니다.  기본적으로 _C:\Deployment Tools\IdFix_ 을 선택 합니다. 
    
    ![IdFix에서 오류를 수정 합니다.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. 모든 변경 내용을의 내용을 픽스 새 오류를 도입 하지 않았으므로 확인을 다시 IdFix를 실행 하는 디렉터리에 적용 됩니다. 이러한 단계에 필요한 횟수 만큼 반복할 수 있습니다. 통과 하도록 하는 프로세스는 몇 번 동기화 하기 전에 것이 좋습니다.
    
## <a name="i-want-to-refine-my-search-or-dig-deeper-into-the-errors-what-else-can-i-do-with-idfix"></a>검색을 구체화하거나 오류를 보다 깊이 분석하려는 경우 IdFix로 어떤 작업을 할 수 있습니까?

좀 더 자세한 정보는 다음 항목에서 찾아볼 수 있습니다.
  
- [IdFix 도구를 사용 하 여 Office 365와 동기화를 위한 디렉터리 특성 준비](prepare-directory-attributes-for-synch-with-idfix.md) 합니다. 점프 도구를 실행 하는 방법에 대 한 자세한 내용은이 항목에는 도구를 설치한 후 발생 하 게 하는 일반적인 오류 픽스, 예제 및 많은 오류가 있는 경우 취해야 할 조치에 대 한 모범 사례를 제시 합니다. 
- [참조: IdFix 제외 및 지원 개체/특성](idfix-excluded-and-supported-objects-and-attributes.md)  
- [참조: Office 365 IdFix 트랜잭션 로그](idfix-transaction-log.md)
    
## <a name="video-training"></a>비디오 교육

자세한 내용은 LinkedIn 학습에 의해 제공자 단원 [설치 및 사용 하 여 IDFix 도구를](https://support.office.com/article/4d81d73c-f172-4fd5-8542-f601c0c96aa9.aspx)참조 합니다.
  

