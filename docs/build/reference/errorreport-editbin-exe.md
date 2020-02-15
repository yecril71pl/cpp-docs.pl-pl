---
title: /ERRORREPORT (editbin.exe)
description: Dokumentacja opcji wiersza polecenia narzędzia Microsoft polecenia EDITBIN/ERRORREPORT.
ms.date: 02/09/2020
f1_keywords:
- /ERRORREPORT
helpviewer_keywords:
- -ERRORREPORT editbin option
- ERRORREPORT editbin option
- /ERRORREPORT editbin option
ms.assetid: eca66ac3-b754-4bd7-9dd4-e04fc79a71b6
ms.openlocfilehash: 6c2ec8b6cda7b794114ed38cfb72b885bf2e38a1
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257599"
---
# <a name="errorreport-editbinexe"></a>/ERRORREPORT (editbin.exe)

> [!NOTE]
> Opcja/ERRORREPORT jest przestarzała. Począwszy od systemu Windows Vista, raportowanie błędów jest kontrolowane przez ustawienia [raportowanie błędów systemu Windows (wer)](/windows/win32/wer/windows-error-reporting) .

## <a name="syntax"></a>Składnia

> **/ERRORREPORT** \[ **NONE** \| **monit** \| **kolejki** \| **send** ]

## <a name="remarks"></a>Uwagi

Argumenty **/errorreport** są zastępowane przez ustawienia usługi Raportowanie błędów systemu Windows. POLECENIA EDITBIN automatycznie wysyła raporty o błędach wewnętrznych do firmy Microsoft, jeśli raportowanie jest włączone przez Raportowanie błędów systemu Windows. Nie jest wysyłany raport, jeśli jest wyłączony przez Raportowanie błędów systemu Windows.

## <a name="see-also"></a>Zobacz też

[Opcje EDITBIN](editbin-options.md)
