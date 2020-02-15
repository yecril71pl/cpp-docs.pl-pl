---
title: /ERRORREPORT (dumpbin.exe)
description: Dokumentacja opcji wiersza polecenia narzędzia Microsoft polecenia DUMPBIN/ERRORREPORT.
ms.date: 02/09/2020
f1_keywords:
- /ERRORREPORT
helpviewer_keywords:
- -ERRORREPORT dumpbin option
- ERRORREPORT dumpbin option
- /ERRORREPORT dumpbin option
ms.assetid: 51178c43-4f95-4fda-8f97-50a257d1c948
ms.openlocfilehash: 665b4b1e7c01de4a1fcd848a9e6b36ddbf2944c9
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257679"
---
# <a name="errorreport-dumpbinexe"></a>/ERRORREPORT (dumpbin.exe)

> [!NOTE]
> Opcja/ERRORREPORT jest przestarzała. Począwszy od systemu Windows Vista, raportowanie błędów jest kontrolowane przez ustawienia [raportowanie błędów systemu Windows (wer)](/windows/win32/wer/windows-error-reporting) .

## <a name="syntax"></a>Składnia

> **/ERRORREPORT**\[**NONE** \| **monit** \| **kolejki** \| **send** ]

## <a name="remarks"></a>Uwagi

Argumenty **/errorreport** są zastępowane przez ustawienia usługi Raportowanie błędów systemu Windows. POLECENIA DUMPBIN automatycznie wysyła raporty o błędach wewnętrznych do firmy Microsoft, jeśli raportowanie jest włączone przez Raportowanie błędów systemu Windows. Nie jest wysyłany raport, jeśli jest wyłączony przez Raportowanie błędów systemu Windows.

## <a name="see-also"></a>Zobacz też

[Opcje DUMPBIN](dumpbin-options.md)
