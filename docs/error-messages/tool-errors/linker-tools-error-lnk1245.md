---
title: Błąd narzędzi konsolidatora LNK1245
ms.date: 11/04/2016
f1_keywords:
- LNK1245
helpviewer_keywords:
- LNK1245
ms.assetid: 179c8165-ffbb-44cd-9f24-5250f29577cc
ms.openlocfilehash: 4cf9a6c4356872b727a10a360396e51e38928b29
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505485"
---
# <a name="linker-tools-error-lnk1245"></a>Błąd narzędzi konsolidatora LNK1245

Nieprawidłowy podsystem "podsystemu" określone; / SUBSYSTEM musi być WINDOWS, WINDOWSCE lub CONSOLE

[/ CLR](../../build/reference/clr-common-language-runtime-compilation.md) został użyty do kompilowania obiektu, ale jeden z następujących warunków true:

- Został zdefiniowany punkt wejścia niestandardowe ([/Entry](../../build/reference/entry-entry-point-symbol.md)), w taki sposób, że konsolidator nie można wywnioskować podsystemu.

- Wartość został przekazany do [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) opcji konsolidatora, która nie jest prawidłowa dla obiektów w/CLR.

Dla obu sytuacjach rozwiązania jest Określ prawidłową wartość, aby opcja/Subsystem — opcja konsolidatora.