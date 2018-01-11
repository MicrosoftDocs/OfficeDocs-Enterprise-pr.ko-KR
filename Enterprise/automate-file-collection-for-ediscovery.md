---
title: "EDiscovery에 대 한 파일 컬렉션을 자동화 합니다."
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: 
ms.assetid: 8d751419-d81b-4eb7-a2e5-8b03ccbf670c
description: "요약: eDiscovery에 대 한 사용자의 컴퓨터에서 파일 컬렉션을 자동화 하는 방법에 알아봅니다."
ms.openlocfilehash: bb93bed80ec95511c6bbf4307d1f0c9e1d4f82cb
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/11/2018
---
# <a name="automate-file-collection-for-ediscovery"></a>EDiscovery에 대 한 파일 컬렉션을 자동화 합니다.

 **요약:** EDiscovery에 대 한 사용자의 컴퓨터에서 파일 컬렉션을 자동화 하는 방법에 알아봅니다.
  
모든 회사의 소송 또는 다른 유형의 법적 조치 액에 직면해 있습니다. 법률 부서 해당 노출 감소를 작동 하는 동안 소송 보존은 비즈니스 수명 주기의 사실입니다. 회사 법률 동작, 직면 하는 경우 모든 관련 된 법적 상황에서 승소 자료는 court을 상대 자문에 게 제공 하려면 법적 개시 하는 프로세스를 통해 필요한 있습니다. 
  
eDiscovery은 기준이 회사 인벤토리에 포함, 검색, 식별, 보존, 필터링, 하 고 전자 양식으로 존재 하는 관련 된 법적 상황에서 승소 자료 수 있게 하는 프로세스입니다. SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online 및 Exchange Online에 많은 양의 법적 상황에서 승소 콘텐츠를 보관할 수 있습니다. 버전에 따라 이러한 제품 eDiscovery를 지원할 수 있습니다 날짜와 전체에서 (Exchange Server를 통해 Lync) 포함 하 고, 보다 쉽게 인덱싱하려 법적 팀에 대 한 식별, 기다리는 주어진된 사례에 대 한 가장 관련성이 높은 콘텐츠를 필터링 합니다.
  
많은 수의 문서는 사용자의 (Custodians)에 저장 된 중앙 집중화 된 위치에 없는 로컬 컴퓨터입니다. 기본적으로 검색 하도록 SharePoint 2013에 대 한 없게 하 고 검색 될 수 없는 경우 eDiscovery에 포함 될 수 없습니다. 이 솔루션에서는 로그온 스크립트를 식별 하 고 사용자 컴퓨터에서 법적 상황에서 승소 자료 (영문)의 컬렉션을 자동화 하기 위한 System Center 조정자 2012 R2 및 Exchange 서버에 대 한 Windows PowerShell을 사용 하는 방법을 보여줍니다.
  
## <a name="what-this-solution-does"></a>이 솔루션에서 수행 하는 작업

이 솔루션을 사용 하 여 글로벌 보안 그룹, 그룹 정책 및 Windows PowerShell 스크립트를 찾고, 조사 하 고, 하 고, 숨겨진된 파일 공유에 사용자가 로컬 컴퓨터에서 콘텐츠 및 Outlook 개인 저장소 (PST) 파일을 수집 합니다. 여기에서 PST 파일을 Exchange Server 2013 또는 Exchange Online으로 가져올 수 있습니다. 모든 파일을 사용 하 여 다른 파일 공유에 실행 되는 System Center 조정자 2012 r 2 서 Microsoft Azure 장기 저장 및 SharePoint 2013 indexing 이동 후 됩니다. 다음에서는 eDiscovery 센터의 온-프레미스 SharePoint 2013 배포에서 또는 SharePoint Online에서 정기적으로 eDiscovery를 수행 하는 것 처럼 합니다. 
  
> [!IMPORTANT]
> 이 솔루션 robocopy를 사용 하 여 중앙된 파일 공유에 더불어의 컴퓨터에서 파일을 복사 합니다. Robocopy에서는 해당 하는 파일 열기 또는 잠긴 것으로 모든 파일을 복사 하지 않으므로 더불어 열기 되어있는지 PST 파일을 비롯 한 수집 되지 않습니다. 해당 작업을 수동으로 수집 해야 합니다. 이 솔루션에서는 명시적으로 복사할 수 없는 파일을 식별 하는 목록 및 각 파일의 전체 경로와 제공지 않습니다. 
  
다음 다이어그램에서는 모든 단계 및 솔루션의 요소 안내합니다.
  
![자동화된 파일 컬렉션 솔루션 개요](images/dbb447b5-c74c-4956-986c-10a1d047ac99.png)
  
|범례 * * *||
|:-----|:-----|
|![자홍색 설명선 1](images/000026a3-2bf0-4678-b468-ccb5f81da6f1.png)|그룹 정책 개체 (GPO)를 만들고 컬렉션 로그온 스크립트와 연결 합니다.  <br/> |
|![자홍색 설명선 2](images/a31b11e2-3597-42a4-933e-b6af11ed6ef1.png)| Custodians 그룹에만 GPO를 적용할 GPO 보안 필터를 구성 합니다. <br/> |
|![자홍색 설명선 3](images/3ced060c-daec-460d-a9b5-260a3dfcae36.png)|프로그램 관리자가 로그온 하 고 컬렉션 로그온 스크립트를 호출 하는 GPO가 실행 합니다.  <br/> |
|![자홍색 설명선 4](images/6f269d84-2559-49e3-b18e-af6ac94d0419.png)|컬렉션 로그온 스크립트는 재고를 파일에 대 한 검색 하 고 해당 위치를 녹음/녹화 Custodians 컴퓨터에서 모든 로컬에 연결 된 드라이브에 사용 합니다.  <br/> |
|![자홍색 설명선 5](images/4bf8898c-44ad-4524-b983-70175804eb85.png)|컬렉션 로그온 스크립트는 준비 서버에서 숨겨진된 파일 공유에 인벤토리에 파일을 복사합니다.  <br/> |
|![자홍색 설명선 6](images/99589726-0c7e-406b-a276-44301a135768.png)| (옵션 A) Exchange Server 2013에 수집 된 PST 파일을 가져오려면 PST 가져오기 스크립트를 수동으로 실행 합니다. <br/> |
|![자홍색 설명선 7](images/ff15e89c-d2fd-4614-9838-5e18287d578b.png)|(옵션 B) Office 365 가져오기 도구 및 프로세스를 사용, Exchange Online에 수집 된 PST 파일을 가져올.  <br/> |
|![자홍색 설명선 8](images/aaf3bd3d-9508-4aaf-a3af-44ba501da63a.png)|MoveToColdStorage System Center 조정자 2012 R2 실행 서와 장기 저장소에 대 한 Azure 파일 공유에 수집 된 모든 파일을 이동 합니다. <br/> |
|![자홍색 설명선 9](images/b354642e-445e-4723-a84a-b41f7ac6e774.png)|SharePoint 2013과 함께 콜드 저장소 파일 공유에서 파일을 인덱스입니다.  <br/> |
|![자홍색 설명선 10](images/cebf7de5-7525-413b-9e52-638a4f8b2f74.png)|콘텐츠 콜드 저장소 및 온-프레미스 Exchange Server 2013에서 eDiscovery를 수행 합니다.  <br/> |
|![자홍색 설명선 11](images/e59ab403-2f19-497a-92a5-549846dded66.png)|Office 365의 내용에 대해 eDiscovery를 수행 합니다.  <br/> |
   
## <a name="prerequisites"></a>필수 구성 요소

이 솔루션의 구성 하는의 가능성이 전체에서 및 구성 되어 있다고 eDiscovery에 대 한 생각 하는 경우 많은 요소를 가장 필요 합니다. 빌드 필요 없을 수도 있습니다 또는 특정 구성을 필요로 하는 것과 하겠습니다 제공 링크는 요소에 대 한 기본 구성을 수행 합니다. 솔루션 자체를 구성 하기 전에 현재 위치에서의 기본 구성은 있어야 합니다.
  
### <a name="base-configuration"></a>기본 구성

|**요소**|**링크**|
|:-----|:-----|
|Active Directory 도메인 서비스 (AD DS) 도메인  <br/> ||
|온-프레미스 네트워크에서 인터넷에 연결  <br/> ||
|SharePoint 2013 및 System Center 조정자 2012 r 2를 지원 하기 위해 SQL Server 2012  <br/> |[System Center 조정자-2012 배포](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
| 온-프레미스 또는 Azure eDiscovery (A 옵션에 대 한 필수)에 대 한 SharePoint 2013 기반 <br/> ||
|준비 단계에 대 한 온-프레미스 파일 공유 서버  <br/> ||
|온-프레미스 Exchange Server 2013 옵션 A PST 가져오기에 대 한  <br/> |C u 5 (15.913.22) [c u 5](https://go.microsoft.com/fwlink/p/?LinkId=613426)에서 사용할 수 있습니다.  <br/> |
|System Center Orchestrator 2012 R2  <br/> |[System Center 조정자-2012 배포](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
|Office 365 (계획 E3) Exchange Online 및 SharePoint Online (옵션 B에 필요)  <br/> |Office 365 E3 구독에 대 한 등록 하려면 [Office 365 E3 구독](https://go.microsoft.com/fwlink/p/?LinkId=613504)을 참조 하십시오.  <br/> |
|가상 컴퓨터를 사용 하 여 azure 구독  <br/> |Azure를 등록 하려면 [Windows Azure에 가입](https://go.microsoft.com/fwlink/p/?LinkId=512010) 를 참조 하십시오. <br/> |
|온-프레미스 네트워크 및 Azure 구독 간에 VPN 연결  <br/> |Azure 구독 및 온-프레미스 네트워크 간에 VPN 터널을 설정 하려면 [Microsoft Azure 가상 네트워크에 연결 하는 온-프레미스 네트워크 연결](https://go.microsoft.com/fwlink/p/?LinkId=613507)을 참조 합니다.  <br/> |
|SharePoint 및 Exchange Server 2013와 선택적으로 Lync Server 2013에서 검색을 구성 하는 SharePoint 2013 eDiscovery  <br/> |이 방식 eDiscovery를 구성 하려면 [Configure eDiscovery in SharePoint Server 2013을](https://go.microsoft.com/fwlink/p/?LinkId=613508) 참조 하 고[테스트 랩 가이드: eDiscovery Exchange, Lync, SharePoint 및 Windows 파일 공유 테스트 랩에 대 한 구성](https://go.microsoft.com/fwlink/p/?LinkId=393130)합니다.  <br/> |
|SharePoint Online 및 Exchange Online에 대 한 Office 365의 eDiscovery  <br/> |Office 365에서 eDiscovery를 구성 하려면 [SharePoint Online에서 eDiscovery 센터 설정](https://go.microsoft.com/fwlink/p/?LinkId=613628)을 참조 하십시오.  <br/> |
   
## <a name="configure-the-environment"></a>환경 구성

현재 위치에서의 기본 구성은 추가한 다음에 솔루션 자체를 구성 하려면 차지 코드로 미리 차 이동할 수 있습니다. 
  
### <a name="staging-file-share"></a>준비 파일 공유

1. 온-프레미스 도메인에서 Custodians 라는 글로벌 보안 그룹을 만듭니다.
    
2. Custodians 컴퓨터에서 수집 되는 파일에 대 한 숨겨진된 파일 공유를 만듭니다. 온-프레미스 서버에 표시 되어야 합니다. 예, 준비를 호출 하는 서버에서의 경우 $ 라는 파일 공유를 만듭니다. **$** 이 숨겨진된 공유를 확인 하려면가 필요 합니다.
    
3. 다음과 같은 공유 사용 권한을 설정 합니다.
    
  - Custodians: 변경, 읽기
    
  - 관리자: 모든 권한
    
  - Exchange 신뢰할 수 있는 하위: 변경, 읽기
    
4. **보안** 탭을 열고 Custodians 그룹 추가 **고급**을 클릭 합니다. Custodians 그룹에 대 한 다음 사용 권한을 설정 합니다.
    
  - **종류: 거부**
    
  - **적용 대상:이 폴더, 하위 폴더 및 파일**
    
5. **고급 사용 권한** 을 클릭 하 고 다음을 선택 합니다.
    
  - **읽기 특성**
    
  - **확장된 특성 읽기**
    
  - **읽기 권한**
    
6. 다음을 수행 하 여의 경우 $ 파일 공유에 액세스를 테스트 합니다.
    
1. Custodians 그룹에 사용자를 추가 합니다.
    
2. 프로그램 파일의 경우 $ 폴더에 넣습니다.
    
3. 사용자로 준비 서버를 찾은 다음를 이동 예는 \\ \\에 어떤 공유를 사용할 수 있는 참조에 대 한 공유를 준비 합니다. 나열 된 **경우 $** 공유를 참조 하면 안됩니다.
    
4. 탐색기로의 경우 $ 공유의 전체 경로 수동으로 입력 합니다. 이 경우 $ 공유를 열려야 합니다.
    
5. 이전에 공유에 배치 파일을 열려고 시도 합니다. 이 작업은 실패 합니다.
    
### <a name="logon-script"></a>로그온 스크립트

1. 복사 하 여이 Windows PowerShell 스크립트를 메모장에 붙여넣습니다.
    
  ```
  # Automated file collection script
# Substantial error processing should be added for robust execution and troubleshooting opportunities
# All commented out write-hosts are for debugging only and are commented out for regular execution

# Functions 

Function CreateCaseFolder() {

#Check to see if case folder already exists
$CaseFolderCheck = Test-Path $CaseLocation

try {

    if (!$CaseFolderCheck) {
    # Case folder doesn't exist.  Create the case folder and the log file location
    # Write-Host -ForegroundColor Cyan "Creating Case Folder $CaseLocation"
    New-Item "$CaseLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case Log Folder $CaseLogLocation"
    New-Item "$CaseLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case PST folder $CasePSTLocation"
    New-Item "$CasePSTLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue

    }
    else {

    # do nothing since the target case folder already exists

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

Function CopyFileToCaseFolder($SourcePath, $TargetPath, $FileName) {
    
    # Check to see if the file already exists
    $TargetFileCheck = Test-Path $TargetPath\\$FileName

try {

    if (!$TargetFileCheck) {
    # Copy the file to the case folder
    Write-Host $SourcePath $TargetPath $FileName
    robocopy "$SourcePath" "$TargetPath" "$FileName" /COPY:DATSO /TEE /LOG+:$LoggingFile /R:10 /W:10 | Out-Null

    }
    else {

    # do nothing since file is already in the target case folder

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

# Global variable initializations

# Error log
$Loggederrors=@()

# The array to contain the file types we collect
$FileTypes = @("*.doc","*.docx","*.pst","*.txt")

# We'll set the case number to be a combination of the date and user name
# For example, a case for John Doe on Dec 14, 2014 at 2:38pm would be:
# 201412141438_jdoe
$CaseNo = get-date -Format yyyyMMddHHmm
$CaseNo = $CaseNo + "_" + [Environment]::UserName

# Target location to copy case files
$CaseRootLocation = "\\\\staging\\Cases$" 

# File copy location, log file location, PST file location and temporary log file location
$CaseLocation = $CaseRootLocation + "\\" + $CaseNo
$CaseLogLocation = $CaseRootLocation + "\\" + $CaseNo + "\\_Log"
$CasePSTLocation = $CaseRootLocation + "\\" + $CaseNo + "\\_PSTs"
$TemporaryLogLocation = [Environment]::getfolderpath('ApplicationData') + "\\" + $CaseNo

# Inventory of local drives
$LocalDrives = Get-PSDrive -PSProvider FileSystem -Scope Global

$LoggingFile = "$CaseLogLocation\\FileCopyErrors.log"

# Main script

# Create the case folder if it doesn't already exist
CreateCaseFolder

# Create the list of files to be copied
# First create the temporary directory in the AppData\\Roaming folder
New-Item "$TemporaryLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
$LocalDrives | foreach {

    # Write-Host -ForeGroundColor Cyan "Collecting Files for Drive: " $_
    Get-ChildItem -Path $_.Root -Recurse -Include $FileTypes -ErrorAction SilentlyContinue -ErrorVariable +Loggederrors | Export-Clixml $TemporaryLogLocation\\\\$_.xml -Force
    # Needs try catch and logged collection error file
}

# Now let's read each file and copy any files we need to the case folder
# We will also copy these XMLs to the case log files folder as we go along
# We only want to process XML files, just in case something else got in there as the script ran
$CaseDriveFiles = Get-ChildItem $TemporaryLogLocation -Filter '*.xml'
$CaseDriveFiles | foreach {
    # Copy the XML file to the case log location
    CopyFileToCaseFolder $_.Directory.FullName $CaseLogLocation $_.Name
    $DriveFile = $_.FullName
    # Write-Host -ForegroundColor Cyan "Copying Files specified in the XML file: $DriveFile"
    $CurrentDriveFile = Import-Clixml $DriveFile
    $CurrentDriveFile | foreach {
        # write-host $_.FullName
        # if it's a PST, add to the PSTs folder. otherwise add it to case folder
        if ($_.Extension -match '.PST')
        {
            CopyFileToCaseFolder $_.Directory.FullName $CasePSTLocation $_.Name
            write-host "this is a PST"
        }
        else
        {
            CopyFileToCaseFolder $_.Directory.FullName $CaseLocation $_.Name
        }
    }
}

# Now delete the temporary log file
Remove-Item $TemporaryLogLocation -Recurse 

Write-Host -ForegroundColor Cyan "Finished."

  ```

2. 위의 스크립트를 쉽게 c: 등을 찾을 수 있는 위치에 CollectionScript.ps1로 저장\\AFCScripts 합니다.
    
3. 메모장에서 이동 기능을 사용 합니다. 필요에 따라 다음 변경 내용을 확인 합니다.
    
|**# 선**|**필요한 변경 하려면**|**필수/선택**|
|:-----|:-----|:-----|
|71  <br/> |**$FileTypes** 변수입니다. 스크립트를 조사 하 고 배열 변수에서를 수집 하려는 모든 파일 형식 확장명을 포함 합니다.<br/> |선택  <br/> |
|76 및 77  <br/> |요구에 맞게 변경 **$CaseNo** 변수 방식으로 작성 됩니다. 스크립트는 현재 날짜와 시간 캡처하고 사용자 이름을 추가 합니다.<br/> |선택  <br/> |
|80  <br/> |**$CaseRootLocation** 변수를 설정 해야 준비 서버 컬렉션 파일 공유 ** \\ \\준비\\$의 경우**합니다. <br/> |필수  <br/> |
   
4. 도메인 컨트롤러의 Netlogon 파일 공유에 CollectionScript.ps1 파일을 넣습니다. 
    
### <a name="configure-gpo-for-the-logon-script-and-custodians-group"></a>로그온 스크립트 및 Custodians 그룹에 대 한 GPO를 구성 합니다.

1. 항목을 [사용 하 여 시작, 종료, 로그온 및 그룹 정책에서 로그 오프 스크립트에서](https://go.microsoft.com/fwlink/p/?LinkId=614844)"사용자 로그온 스크립트를 할당 하는 방법" 섹션을 수행 하 여 Custodians 그룹에 대 한 로그온 스크립트를 구성 합니다.
    
2. **보안 필터링**에서 인증 된 사용자를 제거 하 고 Custodians 그룹을 추가 합니다.
    
### <a name="pst-import-option-a-script-for-exchange-server-2013"></a>PST 가져오기 옵션 A, Exchange Server 2013에 대 한 스크립트

1.  복사한 다음 Windows PowerShell 스크립트를 메모장에 붙여넣습니다.
    
  ```
  # Script to import all PSTs in a given folder to a target mailbox
#
# This is for on-prem Exchange only
# Input parameters
# When you run the script, you call it with two parameters, PST source path and target mailbox alias
# For example:  .\\PSTImport.ps1 \\\\FileShare\\PSTFiles jdoe

param ([String]$SourcePath,[String]$MailboxAlias)

# Folder identifier is the string we want to show in the mailbox that we import the PSTs to

$FolderIdentifier = "zzImportedPSTs_"

# Connect to Exchange remote powershell using the connection Uri below
# This would be the format http://<exchange server FQDN>/Powershell

$ConnectionUri = 'http://h10-exch/PowerShell'
$RemoteEx2013Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri $ConnectionUri -Authentication Kerberos
Import-PSSession $RemoteEx2013Session

# Get all the files in the source path

$AllFiles = Get-ChildItem $SourcePath -Recurse

# Go through each file and if it's a PST launch a mailbox import request for it

$AllFiles | ForEach-Object {
    If ($_.Extension -eq ".pst") {
        $ImportName = $MailboxAlias + "_" + $_.Name
        $FolderName = $FolderIdentifier + $_.Name
        New-MailboxImportRequest -Name $ImportName -Mailbox $MailboxAlias -FilePath $_.FullName -TargetRootFolder $FolderName
    }
}
  ```

2. 쉽게 찾을 수 있는 위치에 PSTImportScript.ps1로 스크립트를 저장 합니다. 예제 및 손쉬운 사용에 대 한 호출 하 여 준비 서버에 폴더를 만들어 \\ \\준비\\AFCScripts에서 저장 해야 합니다.
    
3. 메모장에서 이동 기능을 사용 하 고 필요에 따라 다음 변경 내용을 확인 하십시오.
    
|**# 선**|**필요한 변경 하려면**|**필수/선택**|
|:-----|:-----|:-----|
|12  <br/> |**$FolderIdentifier** 태그 Pst로 가져오는 사서함 폴더를 지정 합니다. 필요한 경우이 변경 합니다.<br/> |선택  <br/> |
|17  <br/> |**$ConnectionUri** 를 자체 서버를 설정 해야 합니다. <br/> > [!IMPORTANT]> 다음을 확인 하면 **$ConnectionUri** 하지 https http 위치를 가리킵니다. Https로 작동 하지 않음:.          |필수  <br/> |
   
4. 권한이 있는지 확인 Exchange 신뢰할 수 있는 하위 시스템 계정 읽기, 쓰기 및 실행 하는 \\ \\준비\\의 경우 $ 공유 합니다.
    
5. PST 가져오기 스크립트에는 다음 두 입력된 매개 변수가 필요합니다.
    
  - **$SourcePath** 같이 가져올 수 있도록 PST 파일의 위치 \\ \\준비\\$의 경우.
    
  - **$MailboxAlias** 가져온된 전자 메일 항목을 받을 수 있는 대상 사서함의 별칭입니다.
    
6. 예: 경로에서 모든 PST 파일을 가져오려는 경우 \\ \\준비\\의 경우 $ 별칭 eDiscoveryMailbox 인 사서함으로, 다음과 같은 스크립트를 실행할 것 `\\\\staging\\AFCscripts\\PSTImportScript.ps1 \\\\Staging\\cases$ eDiscoveryMailbox`합니다.
    
### <a name="pst-import-option-b-for-exchange-online"></a>Exchange Online에 대 한 B, PST 가져오기 옵션

-  사서함 구조에 가져온된 PST 파일을 배치를 만듭니다. Exchange Online의 사용자 사서함을 만드는 방법에 대 한 자세한 내용은[Exchange Online에서 사용자 사서함 만들기](https://go.microsoft.com/fwlink/p/?LinkId=615118)를 참조 하십시오.
    
### <a name="cold-storage"></a>콜드 저장소

1. 파일 공유에는 Azure 가상 컴퓨터 만들기, 수집된 된 모든 파일을 넣을, 예 \\ \\AZFile1\\ContentColdStorage 합니다.
    
2. 기본 콘텐츠 액세스 계정에 최소한 부여 공유 및 모든 하위 폴더 및 파일에 읽기 권한을 합니다. SharePoint 2013의 검색을 구성 하는 방법에 대 한 자세한 내용은 참조 [Create SharePoint Server 2013에서 검색 서비스 응용 프로그램을 구성 하 고](https://go.microsoft.com/fwlink/p/?LinkId=614940)합니다.
    
3. PST 파일을 가져오는 것으로 예상 되는 경우 \\ \\AZFile1\\ContentColdStorage, 쓰기 및 실행 권한을 공유에 Exchange 신뢰할 수 있는 하위 시스템 읽기 권한을 부여 합니다.
    
### <a name="orchestrator"></a>조정자

1. Microsoft 다운로드 센터에서[ MoveToColdStorage 실행 서](https://go.microsoft.com/fwlink/?LinkId=616095) 를 다운로드 합니다.
    
2. Open 되는 **실행 서 디자이너**의 **연결** 창에서로 실행 서 가져올 폴더를 클릭 합니다. **가져오기**를 클릭 하 고 **작업** 메뉴를 클릭 합니다. **가져오기** 대화 상자가 나타납니다.
    
3. **파일 위치** 상자에서 가져올, 실행 서의 경로 파일 이름을 입력 하거나 가져올 파일을 찾습니다 ( **...**) 줄임표 단추를 클릭 합니다. 
    
4. **가져오기 실행 서** 및 **암호화 된 데이터를 가져오기 조정자를**선택 합니다. **카운터**, **일정**, **변수**, **컴퓨터 그룹**, **전역 구성 가져오기**및 **덮어쓰기 기존 전역 구성**의 선택을 취소 합니다.
    
5. **완료 날짜**를 클릭 합니다.
    
6. **MoveFilesToColdStorage** 실행 서를 다음과 같이 편집 합니다.
    
1. **파일 이동** 작업- **원본 파일** 경로를 설정 컬렉션 파일 공유를 사용 하는 예 \\ \\준비\\$의 경우. 콜드 저장소 파일을 **대상 폴더** 를 공유, Azure의 예는 집합 \\ \\AZFile1\\ContentColdStorage 합니다. **고유한 이름으로 파일 만들기**를 선택 합니다.
    
2. **폴더 삭제** 활동-설정의 **경로:** 컬렉션에 파일 공유, 예 \\ \\준비\\$의 경우\\*, 하 고 **모든 파일 및 하위 폴더를 삭제**를 선택 합니다. 
    
7. [실행 서 배포](https://go.microsoft.com/fwlink/p/?LinkId=615120)의 절차를 사용 하 여 **MoveToColdStorage** 실행 서를 배포 합니다.
    
### <a name="sharepoint-on-premises-search-for-cold-storage"></a>SharePoint 온-프레미스 콜드 저장소에 대 한 검색

1. 예 Azure에서 콜드 저장소 공유에 대 한 SharePoint 2013 팜에서 새 콘텐츠 원본을 만들고 \\ \\AZFile1\\ContentColdStorage 합니다. 콘텐츠 원본 관리 하는 방법에 대 한 자세한 내용은 [추가, 편집 또는 SharePoint Server 2013에서 콘텐츠 원본을 삭제](https://go.microsoft.com/fwlink/p/?LinkId=615004) 를 참조 하십시오.
    
2. 전체 크롤링을 시작 합니다. 자세한 내용은 참조, [시작, 일시 중지, 다시 시작 또는 SharePoint Server 2013에서 크롤링 중지](https://go.microsoft.com/fwlink/p/?LinkId=615005)합니다.
    
## <a name="using-the-solution"></a>솔루션을 사용 하 여

Exchange Server 2013 및 Exchange Online 모두로 PST 파일을 가져오려면 않으려면 가정 하 고,이 솔루션을 사용 하 여 다섯 가지 주요 단계로 있습니다. 이 섹션에서는 모두에 대 한 절차와 함께 제공 합니다. 다음을 수행 하는 솔루션 기본 상호 수 있습니다.
  
1. Custodians 그룹의 사용자 멤버 자격을 관리 합니다.
    
2. 로그온 스크립트에 의해 생성 된 로그 파일을 검토 합니다. FileCopyErrors.log 성공적으로 복사 되지 않은 모든 파일을 나열 합니다. 작업을 결정할 필요가
    
3. PST 가져오기 프로세스를 관리 합니다.
    
4. 콜드 저장소 모음 파일을 이동합니다.
    
다른 모든 단계를이 솔루션에 특정 없습니다. SharePoint 2013 및 Office 365와 Azure에서 수행 하는 표준 관리 작업 됩니다. 이 솔루션 작동 회사의 요구에 따라 다음과 같이 해야하는 모든 지침을 제공 하지 않는 항목 가지가 있습니다.
  
1. 사용자의 eDiscovery 사례 및 Custodians는 대/소문자와 연결 된 추적 합니다.
    
2. 파일 컬렉션의 어떤 집합은 어떤 eDiscovery 사례와 연결을 추적 합니다.
    
3. 가져오기 및 콜드 저장소 단계로 이동의 타이밍을 조정 합니다.
    
4. Azure에서 사용 되는 파일 공간을 관리 합니다.
    
5. Pst로 가져오는 사서함을 관리 합니다.
    
6. 백업 및 모든 온-프레미스 데이터를 복원 합니다.
    
### <a name="custodian-management"></a>더불어 관리

- 개별 사용자에 대 한 자동화 된 파일 수집 프로세스를 시작 하려면 Custodians 그룹에 추가 합니다. 다음에 사용자가 로그온 하는 그룹 정책을 통해 Custodians 그룹에 할당 된 로그온 스크립트는 실행 됩니다. 
    
### <a name="monitor-collected-files-and-review-log-files"></a>수집 된 파일을 모니터링 하 고 로그 파일 검토

1. 컬렉션 파일 공유, 예를 시청 \\ \\준비\\$의 경우\\*, 사용자 로부터 컬렉션 폴더에 대 한 합니다. 다음과 같은 서식이 지정 될 폴더의 이름: *yyyyMMddHHmm_UserName* 합니다.
    
2. 컬렉션 완료 되 면 컬렉션 폴더를 열고 _Log 폴더로 이동 합니다. _Log 폴더에는 다음이 표시 됩니다.
    
  - 사용자의 컴퓨터에서 같은 **A.xml**, **C.xml**모든 로컬 드라이브에 대 한 XML 파일입니다. 이 파일에는 after, 명명 된 robocopy 작업에 사용 되는 하는 인벤토리 드라이브에 포함 합니다.
    
    > [!NOTE]
    > 만 수집 스크립트 스크립트 자체에 정의 된 파일 형식에 대 한 인벤토리 파일에서 항목을 생성 합니다. 사용자의 컴퓨터에 있는 모든 파일에 대 한 인벤토리 항목을 만들지 않습니다. 
  
  - 하나의 로그 파일을 실행 하는 각 컬렉션에 대 한 FileCopyErrors.log를 지정 합니다. 이 파일에 포함 파일 목록을 해당 robocopy 수 파일 컬렉션에 복사본이 아닌 공유, 등 \\ \\준비\\$의 경우\\*. 이 검토 하 고 이러한 누락 된 파일에 대해 수행할 동작을 결정 해야 합니다. 일반적으로 하나 수집 해야하는 수동으로 하려는 경우, 또는 필요 하지 않은 자신이 및 컬렉션에서 생략할 수 있습니다를 결정할 수 있습니다.
    
### <a name="pst-import-option-a-for-exchange-server-2013"></a>Exchange Server 2013에 대 한 PST 가져오기 옵션 A

1. 로그온 서버를 호스트 하는 컬렉션 파일 공유 같은 **준비**하 고 Windows PowerShell을 엽니다. Windows PowerShell을 시작 하는 방법에 대 한 자세한 내용은[Windows 서버에서 Windows PowerShell 시작](https://go.microsoft.com/fwlink/p/?LinkId=615115)을 참조 하십시오.
    
2. 제한 없음 실행 정책을 설정 합니다. 형식은 `Set-ExecutionPolicy Unrestricted -Scope Process` 에 Windows PowerShell 하 고 Enter 키를 누릅니다.
    
3. PSTImportScript.ps1 파일을 실행 하 고 **$SourcePath** 및 **$MailboxAlias** 매개 변수를 제공 합니다. Windows PowerShell 스크립트를 실행 하는 방법에 대 한 자세한 내용은[스크립트 실행](https://go.microsoft.com/fwlink/p/?LinkID=615117)을 참조 하십시오.
    
4. 오류에 대 한 출력을 검토 합니다.
    
5. 동일한 사서함으로 동일 하 게 명명 된 PST 파일을 가져오려면 시도 하기 전에 사서함 가져오기 요청을 제거 해야 합니다. 이렇게 하려면 다음 명령을 실행: `Get-MailboxImportRequest | Remove-MailboxImportRequest`합니다. 큐에서 각 개별 요청을 제거 하 라는 메시지가 표시 됩니다. 필요에 따라 응답 합니다.
    
### <a name="pst-import-option-b-for-exchange-online"></a>Exchange Online에 대 한 PST 가져오기 옵션 B

- Exchange Online에 수집 된 PST 파일을 시키려면 [Office 365 가져오기 서비스](https://go.microsoft.com/fwlink/p/?LinkId=614938)의 네트워크 업로드 섹션을 통해 Office 365에 가져오기 파일의 절차를 따르십시오.
    
### <a name="move-to-cold-storage"></a>콜드 저장소로 이동 합니다.

1. 절차를 사용 하 여[실행 중인 실행 서](https://go.microsoft.com/fwlink/p/?LinkId=615123)에 **MoveToColdStorage** 실행 서를 실행 합니다.
    
2. 조사식 같이 긴 용어 저장소에 대 한 사용 하는 Azure 파일 공유 \\ \\AZFile1\\ContentColdStorage 및 온-프레미스 컬렉션 파일 공유, \\ \\준비\\$의 경우. 확인할 수 있는 파일 및 폴더 콜드 저장소 파일 공유에 표시 되 고 컬렉션 파일 공유에서 사라집니다.
    
### <a name="ediscovery"></a>eDiscovery

1. 일정으로 실행 하는 콜드 저장소 파일 공유의 전체 크롤링을 허용 하거나 크롤링을 시작 합니다. 전체 또는 증분 크롤링을 시작에 대 한 자세한 내용은 [시작, 일시 중지, 다시 시작 또는 SharePoint Server 2013에서 크롤링 중지](https://go.microsoft.com/fwlink/p/?LinkId=615005)를 참조 하십시오.
    
2. PST 파일 가져오기에 대 한 A 옵션을 사용 하는 경우 SharePoint 2013에서 eDiscovery 사례 만들기 또는 B. 옵션을 사용 하는 경우 SharePoint Online에서 eDiscovery 사례를 만들려면
    

