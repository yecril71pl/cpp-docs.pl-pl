---
title: Ostrzeżenie LNK4237 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4237
helpviewer_keywords:
- LNK4237
ms.assetid: 87bfec39-5241-464f-9feb-517b49f352ea
ms.openlocfilehash: 62ce0a0edc7f15bc5a19e4630133976f413da35a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588620"
---
# <a name="linker-tools-warning-lnk4237"></a>Ostrzeżenie LNK4237 narzędzi konsolidatora

Subsystem określony podczas importowania pozycji z 'dll'; Użyj opcji lub/Subsystem: Windows.

[Subsystem](../../build/reference/subsystem-specify-subsystem.md) została określona podczas tworzenia aplikacji systemu windows (Win32), który bezpośrednio korzysta z co najmniej jeden z następujących czynności:

- Kernel32.dll.

- Gdi32.dll

- User32.dll

- jedną z msvcrt\* biblioteki dll.

Rozwiązanie to ostrzeżenie, nie określając **Subsystem**.