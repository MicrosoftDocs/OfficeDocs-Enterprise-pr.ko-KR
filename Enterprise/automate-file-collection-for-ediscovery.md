---
title: EDiscovery에 대 한 파일 컬렉션 자동화
ms.author: chrfox
author: chrfox
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: ''
ms.assetid: 8d751419-d81b-4eb7-a2e5-8b03ccbf670c
search.appverid:
- MET150
description: '요약: eDiscovery를 위해 사용자 컴퓨터에서 파일 컬렉션을 자동화 하는 방법을 알아봅니다.'
ms.openlocfilehash: cc6018f65174e142710c71c7f820fc728cd1dc3e
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844739"
---
# <a name="automate-file-collection-for-ediscovery"></a>EDiscovery에 대 한 파일 컬렉션 자동화

 **요약:** EDiscovery에 대 한 사용자 컴퓨터에서 파일 컬렉션을 자동화 하는 방법을 알아봅니다.
  
모든 회사에는 소송 또는 기타 법적 작업 유형이 있습니다. 법적 부서는 이러한 노출을 줄이기 위해 노력 하지만, 소송은 비즈니스 수명에 대 한 사실입니다. 회사는 법적 조치를 취할 때 법률 검색 프로세스를 통해 모든 관련 documentary 자료를 경기장 및 상반 되는 자문 위원에 게 제공 해야 합니다. 
  
eDiscovery는 회사에서 전자 양식에 있는 관련 documentary 자료를 재고, 검색, 식별, 보존, 필터링 및 사용 가능 하 게 하는 프로세스입니다. SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online 및 Exchange Online에는 많은 양의 documentary 콘텐츠가 포함 될 수 있습니다. 버전에 따라 이러한 제품은 eDiscovery 및 현재 위치 유지 (Lync to Exchange Server)를 지원할 수 있으므로 법률 팀이 지정 된 사례에 대해 가장 관련성이 높은 콘텐츠를 보다 쉽게 색인화 하 고 식별 하 고 유지 하 고 필터링 합니다.
  
많은 문서가 사용자 (Custodians) 로컬 컴퓨터에 중앙 위치에 저장 되어 있지 않습니다. 이를 통해 SharePoint 2013에서 검색을 수행할 수 없으며, 검색이 불가능 한 경우 eDiscovery에 포함할 수 없습니다. 이 솔루션은 Exchange Server 용 로그온 스크립트, System Center Orchestrator 2012 R2 및 Windows PowerShell을 사용 하 여 사용자 컴퓨터에서 documentary 자료의 식별 및 컬렉션을 자동화 하는 방법을 보여 줍니다.
  
## <a name="what-this-solution-does"></a>솔루션에서 수행 하는 작업

이 솔루션은 전역 보안 그룹, 그룹 정책 및 Windows PowerShell 스크립트를 사용 하 여 사용자 로컬 컴퓨터에서 숨겨진 파일 공유로의 콘텐츠 및 Outlook 개인 저장소 (PST) 파일을 찾고, 재고를 관리 하 고 수집 합니다. 여기서는 PST 파일을 Exchange Server 2013 또는 Exchange Online으로 가져올 수 있습니다. 그런 다음 SharePoint 2013에서 장기간 저장 하 고 인덱싱하기 위해 System Center Orchestrator 2012 R2 runbook을 사용 하 여 Microsoft Azure의 다른 파일 공유로 모든 파일을 이동 합니다. 그런 다음 정기적으로 eDiscovery를 수행 하는 동안 온-프레미스 SharePoint 2013 배포 또는 SharePoint Online에서 eDiscovery 센터를 사용 합니다. 
  
> [!IMPORTANT]
> 이 솔루션은 robocopy를 사용 하 여 custodian의 컴퓨터에서 중앙 집중식 파일 공유로 파일을 복사 합니다. Robocopy는 열려 있거나 잠겨 있는 파일을 복사 하지 않으므로 PST 파일을 포함 하 여 custodian에서 열린 파일은 수집 되지 않습니다. 이러한 항목은 수동으로 수집 해야 합니다. 이 솔루션은 복사할 수 없는 파일과 각 파일의 전체 경로를 명시적으로 식별 하는 목록을 제공 합니다. 
  
다음 다이어그램에서는 솔루션의 모든 단계와 요소를 보여 줍니다.
  
![자동화 된 파일 모음 솔루션 개요](media/dbb447b5-c74c-4956-986c-10a1d047ac99.png)
  
|범례 * * * *||
|:-----|:-----|
|![자홍 설명선 1](media/000026a3-2bf0-4678-b468-ccb5f81da6f1.png)|GPO (그룹 정책 개체)를 만든 후 컬렉션 로그온 스크립트와 연결 합니다.  <br/> |
|![자홍 설명선 2](media/a31b11e2-3597-42a4-933e-b6af11ed6ef1.png)| Gpo 보안 필터를 구성 하 여 Custodians 그룹에만 GPO를 적용 합니다. <br/> |
|![자홍 설명선 3](media/3ced060c-daec-460d-a9b5-260a3dfcae36.png)|Custodian가 로그온 되 고 GPO가 실행 되어 컬렉션 로그온 스크립트를 호출 합니다.  <br/> |
|![자홍 설명선 4](media/6f269d84-2559-49e3-b18e-af6ac94d0419.png)|컬렉션 로그온 스크립트는 Custodians 컴퓨터의 로컬로 연결 된 모든 드라이브를 인벤토리 하 고, 원하는 파일을 검색 하 고, 해당 위치를 기록 합니다.  <br/> |
|![자홍 설명선 5](media/4bf8898c-44ad-4524-b983-70175804eb85.png)|컬렉션 로그온 스크립트는 인벤토리에 포함 된 파일을 준비 서버에 있는 숨겨진 파일 공유에 복사 합니다.  <br/> |
|![자홍 통화](media/99589726-0c7e-406b-a276-44301a135768.png)| (옵션 A) PST 가져오기 스크립트를 수동으로 실행 하 여 수집 된 PST 파일을 Exchange Server 2013로 가져옵니다. <br/> |
|![자홍 설명선 7](media/ff15e89c-d2fd-4614-9838-5e18287d578b.png)|(옵션 B) Office 365 가져오기 도구와 프로세스를 사용 하 여 수집 된 PST 파일을 Exchange Online으로 가져옵니다.  <br/> |
|![자홍 설명선 8](media/aaf3bd3d-9508-4aaf-a3af-44ba501da63a.png)|MoveToColdStorage System Center Orchestrator 2012 R2 runbook을 사용 하 여 수집 된 모든 파일을 장기 저장소에 대 한 Azure 파일 공유로 이동 합니다. <br/> |
|![자홍 설명선 9](media/b354642e-445e-4723-a84a-b41f7ac6e774.png)|SharePoint 2013의 콜드 저장소 파일 공유에 있는 파일을 인덱싱합니다.  <br/> |
|![자홍 설명선 10](media/cebf7de5-7525-413b-9e52-638a4f8b2f74.png)|콜드 저장소 및 온-프레미스 Exchange Server 2013의 콘텐츠에서 eDiscovery를 수행 합니다.  <br/> |
|![자홍 설명선 11](media/e59ab403-2f19-497a-92a5-549846dded66.png)|Office 365에서 콘텐츠에 대 한 eDiscovery를 수행 합니다.  <br/> |
   
## <a name="prerequisites"></a>필수 구성 요소

이 솔루션을 구성 하려면 대부분의 요소가 필요 하며, eDiscovery에 대해 생각 하는 경우에는 대부분의 요소를 사용 하 고 구성 해야 합니다. 특정 구성이 필요 하지 않을 수 있는 요소에 대해서는 기본 구성을 구축 하는 데 필요한 링크를 제공 합니다. 솔루션 자체를 구성 하기 전에 기본 구성을 그대로 유지 해야 합니다.
  
### <a name="base-configuration"></a>기본 구성

|**요소**|**링크**|
|:-----|:-----|
|AD DS (Active Directory 도메인 서비스) 도메인  <br/> ||
|온-프레미스 네트워크 로부터의 인터넷 연결  <br/> ||
|SharePoint 2013 및 System Center Orchestrator 2012 R2를 지원 하기 위한 SQL Server 2012  <br/> |[System Center Orchestrator-2012 배포](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
| EDiscovery에 대 한 온-프레미스 또는 Azure 기반 SharePoint 2013 (옵션 A에 필요) <br/> ||
|준비를 위해 온-프레미스 파일 공유 서버  <br/> ||
|PST 가져오기를 위한 온-프레미스 Exchange Server 2013  <br/> |CU5 (15.913.22)은 [CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426)에서 사용할 수 있습니다.  <br/> |
|System Center Orchestrator 2012 R2  <br/> |[System Center Orchestrator-2012 배포](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
|Exchange Online 및 SharePoint Online을 사용 하는 Office 365 (E3 계획) (옵션 B에 필요 함)  <br/> |Office 365 E3 구독에 등록 하려면 [office 365 e3 구독](https://go.microsoft.com/fwlink/p/?LinkId=613504)을 참조 하세요.  <br/> |
|가상 컴퓨터를 사용한 Azure 구독  <br/> |Azure에 등록 하려면 [Windows Azure 구독을](https://go.microsoft.com/fwlink/p/?LinkId=512010) 참조 하세요. <br/> |
|온-프레미스 네트워크와 Azure 구독 간의 VPN 연결  <br/> |Azure 구독과 온-프레미스 네트워크 간에 VPN 터널을 설정 하려면 [온-프레미스 네트워크를 Microsoft Azure virtual network에 연결](https://go.microsoft.com/fwlink/p/?LinkId=613507)을 참조 하십시오.  <br/> |
|Sharepoint 2013 eDiscovery는 SharePoint 및 Exchange Server 2013 및 선택적 Lync Server 2013에서 검색 하도록 구성 되어 있습니다.  <br/> |이 방식으로 eDiscovery를 구성 하려면 [Configure ediscovery In SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) 및[test Lab Guide: Exchange, Lync, SharePoint 및 Windows 파일 공유 테스트 랩에 대해](https://go.microsoft.com/fwlink/p/?LinkId=393130)ediscovery 구성을 참조 하십시오.  <br/> |
|SharePoint Online 및 Exchange Online에 대 한 Office 365의 eDiscovery  <br/> |Office 365에서 eDiscovery를 구성 하려면 [SharePoint Online에서 Ediscovery 센터 설정을](https://go.microsoft.com/fwlink/p/?LinkId=613628)참조 하세요.  <br/> |
   
## <a name="configure-the-environment"></a>환경 구성

기본 구성을 설정 했으므로 이제 솔루션 자체를 구성 하기 전에 이동할 수 있습니다. 
  
### <a name="staging-file-share"></a>준비 파일 공유

1. 온-프레미스 도메인에서 Custodians 라는 전역 보안 그룹을 만듭니다.
    
2. Custodians 컴퓨터에서 수집 된 파일에 대 한 숨겨진 파일 공유를 만듭니다. 이는 온-프레미스 서버에 있어야 합니다. 예를 들어 준비 라는 서버에서 Case $ 라는 파일 공유를 만듭니다. **$** 은이를 숨겨진 공유로 설정 하는 데 필요 합니다.
    
3. 다음 공유 사용 권한을 설정 합니다.
    
  - Custodians: Change, Read
    
  - 관리자: 모든 권한
    
  - 신뢰할 수 있는 Exchange 하위 시스템: 변경, 읽기
    
4. **보안** 탭을 열고 Custodians 그룹을 추가한 다음 **고급**을 클릭 합니다. Custodians 그룹에 대해 다음 사용 권한을 설정 합니다.
    
  - **유형: Deny**
    
  - **적용 대상: 현재 폴더, 하위 폴더 및 파일**
    
5. **고급 사용 권한을** 클릭 하 고 다음을 선택 합니다.
    
  - **특성 읽기**
    
  - **확장 된 특성 읽기**
    
  - **사용 권한 읽기**
    
6. 다음을 수행 하 여 사례 $ 파일 공유에 대 한 액세스를 테스트 합니다.
    
1. Custodians 그룹에 사용자를 추가 합니다.
    
2. 서비스 케이스 $ 폴더에 파일을 저장 합니다.
    
3. 사용자는 준비 서버로 이동 하 여 (예: \\ \\준비 공유로 이동) 사용 가능한 공유를 확인 합니다. $ Share가 나열 되어 있는 **경우** 는 표시 되지 않습니다.
    
4. 서비스 케이스 공유에 대 한 전체 경로를 탐색기에 수동으로 입력 합니다. 그러면 사례 $ 공유가 열립니다.
    
5. 이전에 공유에 추가한 파일을 열어 봅니다. 이는 실패 합니다.
    
### <a name="logon-script"></a>로그온 스크립트

1. 다음 Windows PowerShell 스크립트를 복사 하 여 메모장에 붙여 넣습니다.
    
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
    $TargetFileCheck = Test-Path $TargetPath\$FileName

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
$CaseRootLocation = "\\staging\Cases$" 

# File copy location, log file location, PST file location and temporary log file location
$CaseLocation = $CaseRootLocation + "\" + $CaseNo
$CaseLogLocation = $CaseRootLocation + "\" + $CaseNo + "\_Log"
$CasePSTLocation = $CaseRootLocation + "\" + $CaseNo + "\_PSTs"
$TemporaryLogLocation = [Environment]::getfolderpath('ApplicationData') + "\" + $CaseNo

# Inventory of local drives
$LocalDrives = Get-PSDrive -PSProvider FileSystem -Scope Global

$LoggingFile = "$CaseLogLocation\FileCopyErrors.log"

# Main script

# Create the case folder if it doesn't already exist
CreateCaseFolder

# Create the list of files to be copied
# First create the temporary directory in the AppData\Roaming folder
New-Item "$TemporaryLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
$LocalDrives | foreach {

    # Write-Host -ForeGroundColor Cyan "Collecting Files for Drive: " $_
    Get-ChildItem -Path $_.Root -Recurse -Include $FileTypes -ErrorAction SilentlyContinue -ErrorVariable +Loggederrors | Export-Clixml $TemporaryLogLocation\$_.xml -Force
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

2. 위의 스크립트를 CollectionScript로 저장 합니다. \ C:\\afcscripts와 같이 쉽게 찾을 수 있는 위치에 있습니다.
    
3. 메모장에서 이동 기능을 사용 합니다. 필요에 따라 다음 사항을 변경 합니다.
    
|**줄 번호**|**변경 해야 하는 내용**|**Required/optional**|
|:-----|:-----|:-----|
|71  <br/> |**$FileTypes** 변수입니다. 스크립트에서 인벤토리 및 수집할 모든 파일 형식 확장명을 배열 변수에 포함 합니다. <br/> |선택  <br/> |
|76 및 77  <br/> |사용자의 요구에 맞게 **$CaseNo** 변수가 작성 되는 방식을 변경 합니다. 이 스크립트는 현재 날짜와 시간을 캡처하여 사용자 이름을 추가 합니다. <br/> |선택  <br/> |
|80  <br/> |** \\ \\준비\\사례 $** 와 같은 **$CaseRootLocation** 변수를 준비 서버 모음 파일 공유로 설정 해야 합니다. <br/> |필수  <br/> |
   
4. 도메인 컨트롤러의 Netlogon 파일 공유에 CollectionScript. ps1 파일을 배치 합니다. 
    
### <a name="configure-gpo-for-the-logon-script-and-custodians-group"></a>로그온 스크립트 및 Custodians 그룹에 대해 GPO를 구성 합니다.

1. [그룹 정책의 시작, 종료, 로그온 및 로그 오프 스크립트 사용](https://go.microsoft.com/fwlink/p/?LinkId=614844)항목의 "사용자 로그온 스크립트를 할당 하는 방법" 섹션을 따라 Custodians 그룹에 대 한 로그온 스크립트를 구성 합니다.
    
2. **보안 필터링**에서 인증 된 사용자를 제거 하 고 Custodians 그룹을 추가 합니다.
    
### <a name="pst-import-option-a-script-for-exchange-server-2013"></a>PST 가져오기 옵션 A, Exchange Server 2013에 대 한 스크립트

1.  다음 Windows PowerShell 스크립트를 복사 하 여 메모장에 붙여 넣습니다.
    
  ```
  # Script to import all PSTs in a given folder to a target mailbox
#
# This is for on-prem Exchange only
# Input parameters
# When you run the script, you call it with two parameters, PST source path and target mailbox alias
# For example:  .\PSTImport.ps1 \\FileShare\PSTFiles jdoe

param ([String]$SourcePath,[String]$MailboxAlias)

# Folder identifier is the string we want to show in the mailbox that we import the PSTs to

$FolderIdentifier = "zzImportedPSTs_"

# Connect to Exchange remote powershell using the connection Uri below
# This would be the format https://<exchange server FQDN>/Powershell

$ConnectionUri = 'https://h10-exch/PowerShell'
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

2. 스크립트를 쉽게 찾을 수 있는 위치에 PSTImportScript로 저장 합니다. 예를 들어 간편 하 게 사용할 수 있도록 준비 서버에서 준비 \\ \\\\afcscripts 라는 폴더를 만들고 저장 합니다.
    
3. 필요에 따라 메모장에서 이동 기능을 사용 하 고 다음 사항을 변경 합니다.
    
|**줄 번호**|**변경 해야 하는 내용**|**Required/optional**|
|:-----|:-----|:-----|
|12  <br/> |**$FolderIdentifier** pst를 가져올 사서함 폴더에 태그를 붙여 넣습니다. 필요한 경우이를 변경 합니다. <br/> |선택  <br/> |
|17   <br/> |**$ConnectionUri** 를 자체 서버로 설정 해야 합니다. <br/> > [!IMPORTANT]**$ConnectionUri**> https가 아닌 http 위치를 가리키는지 확인 합니다. Https:로 작동 하지 않습니다.          |필수  <br/> |
   
4. Exchange 신뢰할 수 있는 하위 시스템 계정에 \\ \\준비\\사례 $ 공유에 대 한 읽기, 쓰기 및 실행 권한이 있는지 확인 합니다.
    
5. PST 가져오기 스크립트에는 다음과 같은 두 개의 입력 매개 변수가 필요 합니다.
    
  - **$SourcePath** 가져올 PST 파일의 위치 (예: \\ \\Staging\\사례 $)입니다.
    
  - **$MailboxAlias** 가져온 전자 메일 항목을 받을 대상 사서함의 별칭입니다.
    
6. 예를 들어 Staging\Cases $ 경로 \\에서 별칭이 ediscoverymailbox 인 사서함으로 모든 PST 파일을 가져오려면 다음과 같은 스크립트를 실행 합니다. `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`
    
### <a name="pst-import-option-b-for-exchange-online"></a>PST 가져오기 옵션 B, Exchange Online

-  가져온 PST 파일을 배치할 사서함 구조를 만듭니다. Exchange Online에서 사용자 사서함을 만드는 방법에 대 한 자세한 내용은[Exchange online에서 사용자 사서함 만들기](https://go.microsoft.com/fwlink/p/?LinkId=615118)를 참조 하세요.
    
### <a name="cold-storage"></a>콜드 저장소

1. 수집 된 모든 파일이 저장 될 Azure Virtual Machine 파일 공유 (예: \\ \\AZFile1\\contentcoldstorage)를 만듭니다.
    
2. 기본 콘텐츠 액세스 계정에 최소한 공유 및 모든 하위 폴더와 파일에 대 한 읽기 권한을 부여 합니다. SharePoint 2013 검색을 구성 하는 방법에 대 한 자세한 내용은 [Create and configure a Search service application In Sharepoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940)을 참조 하십시오.
    
3. \\ \\AZFile1\\contentcoldstorage에서 PST 파일을 가져오는 것이 예상 되는 경우 Exchange의 신뢰할 수 있는 하위 시스템 읽기, 쓰기 및 실행 권한을 공유에 부여 합니다.
    
### <a name="orchestrator"></a>자가

1. Microsoft 다운로드 센터에서[ MoveToColdStorage runbook](https://go.microsoft.com/fwlink/?LinkId=616095) 을 다운로드 합니다.
    
2. **Runbook Designer**를 열고 **연결** 창에서 runbook을 가져올 폴더를 클릭 합니다. **작업** 메뉴를 클릭 하 고 **가져오기를**클릭 합니다. **가져오기** 대화 상자가 표시 됩니다.
    
3. **파일 위치** 상자에 가져올 runbook의 경로 및 파일 이름을 입력 하거나, 줄임표 ( **...**)를 클릭 하 여 가져올 파일을 찾습니다. 
    
4. **Runbook 가져오기를** 선택 하 고 **Orchestrator Encrypted data를 가져옵니다**. **카운터**, **일정**, **변수**, **컴퓨터 그룹**, **전역 구성 가져오기**및 **기존 전역 구성 덮어쓰기**의 선택을 취소 합니다.
    
5. **마침**을 클릭합니다.
    
6. **MoveFilesToColdStorage** runbook을 다음과 같이 편집 합니다.
    
1. **파일 이동** 작업- **원본 파일** 경로를 모음 파일 공유 (예: \\ \\준비\\사례 $)로 설정 합니다. Azure에서 **대상 폴더** 를 콜드 저장소 파일 공유 (예: \\ \\AZFile1\\contentcoldstorage)로 설정 합니다. **고유한 이름을 사용 하 여 파일 만들기를**선택 합니다.
    
2. **폴더 활동 삭제** - **경로** 를 모음 파일 공유 ( \\ \\예:\\준비 사례 $\\*)로 설정 하 고 **모든 파일 및 하위 폴더 삭제**를 선택 합니다. 
    
7. [Runbook 배포](https://go.microsoft.com/fwlink/p/?LinkId=615120)의 절차에 따라 **MoveToColdStorage** runbook을 배포 합니다.
    
### <a name="sharepoint-on-premises-search-for-cold-storage"></a>콜드 저장소에 대 한 SharePoint 온-프레미스 검색

1. Azure의 콜드 저장소 공유에 대 한 SharePoint 2013 팜에서 새 콘텐츠 원본을 만듭니다 (예: \\ \\AZFile1\\contentcoldstorage). 콘텐츠 원본을 관리 하는 방법에 대 한 자세한 내용은 [Add, edit, or delete a content source In SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004) 을 참조 하세요.
    
2. 전체 크롤링을 시작 합니다. 자세한 내용은 [SharePoint Server 2013에서 크롤링 시작, 일시 중지, 다시 시작 또는 중지](https://go.microsoft.com/fwlink/p/?LinkId=615005)를 참조 하세요.
    
## <a name="using-the-solution"></a>솔루션 사용

이 솔루션을 사용 하는 경우에는 다섯 가지 주요 단계로, PST 파일을 Exchange Server 2013 및 Exchange Online 둘 다로 가져오지 않으려고 합니다. 이 섹션에서는 모든 기능에 대 한 절차를 제공 합니다. 솔루션과의 기본 상호 작용은 다음과 같은 작업을 수행 합니다.
  
1. Custodians 그룹에서 사용자 구성원 자격을 관리 합니다.
    
2. 로그온 스크립트에 의해 생성 된 로그 파일을 검토 합니다. FileCopyErrors에는 성공적으로 복사 되지 않은 모든 파일이 나열 됩니다. 원하는 작업을 결정 해야 합니다.
    
3. PST 가져오기 프로세스 관리
    
4. 모음 파일을 콜드 저장소로 이동
    
다른 모든 단계는이 솔루션에 국한 되지 않습니다. SharePoint 2013 및 Office 365 및 Azure에서 수행 하는 표준 관리 작업입니다. 이 솔루션은 회사의 요구 사항에 따라 다음과 같이 작업을 수행 하는 데 필요한 지침을 제공 하지 않습니다.
  
1. EDiscovery 사례 및 해당 사례와 연결 된 Custodians을 추적 합니다.
    
2. EDiscovery 사례와 연결 되는 파일 모음 집합 추적
    
3. 가져오기 타이밍을 조정 하 고 콜드 저장소 단계로 이동 합니다.
    
4. Azure에서 사용 되는 파일 공간 관리
    
5. Pst를 가져올 사서함 관리
    
6. 모든 온-프레미스 데이터의 백업 및 복원
    
### <a name="custodian-management"></a>Custodian 관리

- 개별 사용자에 대 한 자동 파일 수집 프로세스를 시작 하려면 Custodians 그룹에 추가 합니다. 다음 번에 사용자가 로그온 하면 그룹 정책을 통해 Custodians 그룹에 할당 된 로그온 스크립트가 실행 됩니다. 
    
### <a name="monitor-collected-files-and-review-log-files"></a>수집 된 파일 모니터링 및 로그 파일 검토

1. 사용자의 컬렉션 폴더에 대 한 모음 \\ \\파일\\공유 (\\예: 준비 사례 $ *)를 시청 합니다. 폴더의 이름은 *yyyyMMddHHmm_UserName* 다음과 같이 지정 됩니다.
    
2. 수집이 완료 되 면 모음 폴더를 열고 _Log 폴더로 이동 합니다. _Log 폴더에는 다음이 표시 됩니다.
    
  - 사용자 컴퓨터의 모든 로컬 드라이브 (예: **.xml**, **C .xml**)에 대 한 XML 파일 하나 이러한 파일에는 이름이 다음과 같이 지정 된 인벤토리 드라이브가 포함 되며 robocopy 작업에 사용 됩니다.
    
    > [!NOTE]
    > 컬렉션 스크립트는 스크립트 자체에 정의한 파일 형식에 대 한 인벤토리 파일에만 항목을 만듭니다. 사용자 컴퓨터의 모든 파일에 대 한 인벤토리 항목을 만들지는 않습니다. 
  
  - 각 컬렉션에 대해 FileCopyErrors 라는 로그 파일 하나를 실행 합니다. 이 \\ \\파일에는\\서비스 케이스 $\\*와 같이 robocopy에서 파일 모음 공유로 복사할 수 없는 파일 목록이 포함 되어 있습니다. 이를 검토 하 고 이러한 누락 된 파일에 대해 수행할 작업을 결정 해야 합니다. 일반적으로 필요한 경우 수동으로 수집 해야 하며, 필요 하지 않을 수 있으므로 컬렉션에서 생략할 수도 있습니다.
    
### <a name="pst-import-option-a-for-exchange-server-2013"></a>Exchange Server 2013에 대 한 PST 가져오기 옵션

1. 모음 파일 공유를 호스트 하는 서버에 로그온 하 고 (예: **Staging**) Windows PowerShell을 엽니다. Windows PowerShell을 시작 하는 방법에 대 한 자세한 내용은[Windows Server에서 Windows Powershell 시작](https://go.microsoft.com/fwlink/p/?LinkId=615115)을 참조 하십시오.
    
2. 실행 정책을 무제한으로 설정 합니다. Windows `Set-ExecutionPolicy Unrestricted -Scope Process` PowerShell에 입력 한 다음 enter 키를 누릅니다.
    
3. PSTImportScript 파일을 실행 하 고 **$SourcePath** 및 **$MailboxAlias** 매개 변수를 제공 합니다. Windows PowerShell 스크립트를 실행 하는 방법에 대 한 자세한 내용은[실행 스크립트](https://go.microsoft.com/fwlink/p/?LinkID=615117)를 참조 하십시오.
    
4. 오류에 대 한 출력을 검토 합니다.
    
5. 같은 이름의 PST 파일을 같은 사서함에 가져오기 전에 사서함 가져오기 요청을 제거 해야 합니다. 다음 명령을 실행 하 여이 작업을 `Get-MailboxImportRequest | Remove-MailboxImportRequest`수행 합니다. 큐에서 개별 요청을 모두 제거할지 묻는 메시지가 표시 됩니다. 필요에 따라 응답 합니다.
    
### <a name="pst-import-option-b-for-exchange-online"></a>PST 가져오기 옵션 B, Exchange Online

- 수집 된 PST 파일을 Exchange Online에 배치 하려면 [office 365 가져오기 서비스](https://go.microsoft.com/fwlink/p/?LinkId=614938)의 네트워크 업로드 섹션에서 파일을 office 365로 가져오기의 절차를 따릅니다.
    
### <a name="move-to-cold-storage"></a>콜드 저장소로 이동

1. [실행 중인 runbook](https://go.microsoft.com/fwlink/p/?LinkId=615123)의 절차에 따라 **MoveToColdStorage** runbook을 실행 합니다.
    
2. 장기 저장소 (예 \\ \\\\: AZFile1 contentcoldstorage 및 온-프레미스 모음 파일 공유)에 사용 중인 Azure 파일 공유 (예: \\ \\준비\\사례 $)를 시청 하세요. 파일 및 폴더가 콜드 저장소 파일 공유에 표시 되 고 모음 파일 공유에서 사라집니다.
    
### <a name="ediscovery"></a>eDiscovery

1. 콜드 저장소 파일 공유의 전체 크롤링을 일정으로 실행 하거나 크롤링을 시작할 수 있습니다. 전체 또는 증분 크롤링 시작에 대 한 자세한 내용은 [SharePoint Server 2013에서 크롤링 시작, 일시 중지, 다시 시작 또는 중지](https://go.microsoft.com/fwlink/p/?LinkId=615005)를 참조 하세요.
    
2. PST 파일에 A 옵션을 사용 하 여 SharePoint 2013에서 eDiscovery 사례를 만들거나, 옵션 B를 사용한 경우 SharePoint Online에서 eDiscovery 사례를 만듭니다.
    

