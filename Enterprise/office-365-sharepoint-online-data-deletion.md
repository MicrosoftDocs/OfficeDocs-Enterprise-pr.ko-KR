---
title: Office 365 SharePoint Online 데이터 삭제
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
description: SharePoint Online의 데이터 삭제에 대 한 설명
ms.openlocfilehash: 94b70d34cb05f98dfa560761dec87a919720dca9
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/09/2019
ms.locfileid: "38078157"
---
# <a name="sharepoint-online-data-deletion-in-office-365"></a>Office 365에서 SharePoint Online 데이터 삭제

SharePoint Online은 개체를 응용 프로그램 데이터베이스 내에서 추상화 된 코드로 저장 합니다. 사용자가 SharePoint Online에 파일을 업로드 하면 해당 파일이 분해 되어 응용 프로그램 코드로 변환 되어 여러 데이터베이스에 걸쳐 여러 테이블에 저장 됩니다. SharePoint Online에서 고객이 업로드 하는 모든 콘텐츠는 청크, 암호화 (여러 AES 256 비트 키 사용 가능)로 분할 되 고 데이터 센터 전체에 분산 됩니다. 청크 및 암호화 프로세스에 대 한 구체적인 정보는 [Microsoft 클라우드에서 암호화](https://docs.microsoft.com/microsoft-365/compliance/office-365-encryption-in-the-microsoft-cloud-overview)를 참조 하세요. 

SharePoint Online에서 항목은 원래 위치에서 삭제 한 시간부터 93 일 동안 보존 됩니다. 일부 사용자가 휴지통에서 삭제 한 경우를 제외 하 고는 전체 시간으로 사이트 휴지통에 유지 됩니다. 이 경우 항목은 나머지 93 일 동안 유지 되는 사이트 모음 휴지통으로 이동 합니다. 삭제 된 항목을 복원 하는 방법에 대 한 자세한 내용은 [SharePoint 사이트의 휴지통에서 항목 복원](https://support.office.com/article/6df466b6-55f2-4898-8d6e-c0dff851a0be#ID0EAADAAA=Online
) 및 [사이트 모음 휴지통에서 삭제 된 항목 복원을](https://support.office.com/article/5fa924ee-16d7-487b-9a0a-021b9062d14b)참조 하십시오. 휴지통 보존 시간은 SharePoint Online에서 구성할 수 없습니다.

사이트 모음을 삭제 하면 모음에 있는 사이트의 계층 구조와 모든 콘텐츠가 삭제 됩니다.

- 문서 및 문서 라이브러리
- 목록 및 목록 데이터
- 사이트 구성 설정
- 사이트나 해당 사이트와 관련 된 역할 및 보안 정보
- 최상위 웹 사이트, 해당 콘텐츠 및 사용자 정보 하위 사이트

실수로 사이트 모음을 삭제 한 경우에는 SharePoint 관리 센터를 사용 하 여 전역 관리자 또는 SharePoint 관리에 의해 복원 될 수 있습니다. 

하드 삭제는 사용자가 사이트 모음 휴지통에서 삭제 된 항목을 제거 하거나, 보존 및 백업 기간이 만료 되거나, 관리자가 [remove-spodeletedsite cmdlet](/powershell/module/sharepoint-online/Remove-SPODeletedSite?view=sharepoint-ps)을 사용 하 여 사이트 모음을 영구적으로 삭제할 때 발생 합니다. 사용자가 SharePoint Online에서 콘텐츠를 영구적으로 삭제 하거나 제거 하면 삭제 된 청크의 모든 암호화 키도 삭제 됩니다. 이전에 삭제 한 청크를 저장 한 디스크의 블록은 사용 되지 않는 것으로 표시 되며 다시 사용할 수 있습니다.
