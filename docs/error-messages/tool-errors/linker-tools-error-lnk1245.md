---
title: Błąd narzędzi konsolidatora LNK1245 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1245
dev_langs:
- C++
helpviewer_keywords:
- LNK1245
ms.assetid: 179c8165-ffbb-44cd-9f24-5250f29577cc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef7bace5cec937399d7a2ed440e21b9b751f4141
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041795"
---
# <a name="linker-tools-error-lnk1245"></a>Błąd narzędzi konsolidatora LNK1245

Nieprawidłowy podsystem "podsystemu" określone; / SUBSYSTEM musi być WINDOWS, WINDOWSCE lub CONSOLE

[/ CLR](../../build/reference/clr-common-language-runtime-compilation.md) został użyty do kompilowania obiektu, ale jeden z następujących warunków true:

- Został zdefiniowany punkt wejścia niestandardowe ([/Entry](../../build/reference/entry-entry-point-symbol.md)), w taki sposób, że konsolidator nie można wywnioskować podsystemu.

- Wartość został przekazany do [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) opcji konsolidatora, która nie jest prawidłowa dla obiektów w/CLR.

Dla obu sytuacjach rozwiązania jest Określ prawidłową wartość, aby opcja/Subsystem — opcja konsolidatora.