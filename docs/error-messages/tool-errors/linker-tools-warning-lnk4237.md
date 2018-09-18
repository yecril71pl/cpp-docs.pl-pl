---
title: Ostrzeżenie LNK4237 narzędzi konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4237
dev_langs:
- C++
helpviewer_keywords:
- LNK4237
ms.assetid: 87bfec39-5241-464f-9feb-517b49f352ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 479bd4ff8a4f48da679c9e17ec100668de84d089
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46113711"
---
# <a name="linker-tools-warning-lnk4237"></a>Ostrzeżenie LNK4237 narzędzi konsolidatora

Subsystem określony podczas importowania pozycji z 'dll'; Użyj opcji lub/Subsystem: Windows.

[Subsystem](../../build/reference/subsystem-specify-subsystem.md) została określona podczas tworzenia aplikacji systemu windows (Win32), który bezpośrednio korzysta z co najmniej jeden z następujących czynności:

- Kernel32.dll.

- Gdi32.dll

- User32.dll

- jedną z msvcrt\* biblioteki dll.

Rozwiązanie to ostrzeżenie, nie określając **Subsystem**.