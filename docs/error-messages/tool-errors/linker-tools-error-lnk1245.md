---
title: Błąd narzędzi konsolidatora LNK1245
ms.date: 11/04/2016
f1_keywords:
- LNK1245
helpviewer_keywords:
- LNK1245
ms.assetid: 179c8165-ffbb-44cd-9f24-5250f29577cc
ms.openlocfilehash: 19e3f820b5bd7fdd8eac2f7b5a96fb5923ae0b92
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183803"
---
# <a name="linker-tools-error-lnk1245"></a>Błąd narzędzi konsolidatora LNK1245

określono nieprawidłowy podsystem "Subsystem"; /SUBSYSTEM musi być WINDOWS, WINDOWSCE lub KONSOLą

do skompilowania obiektu użyto [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) , a jeden z następujących warunków został spełniony:

- Zdefiniowano niestandardowy punkt wejścia ([/entry](../../build/reference/entry-entry-point-symbol.md)), który nie może wywnioskować podsystemu przez konsolidator.

- Wartość została przeniesiona do opcji konsolidatora [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) , która nie jest prawidłowa dla obiektów/CLR.

W obu przypadkach rozdzielczość jest określona dla opcji konsolidatora/SUBSYSTEM.
