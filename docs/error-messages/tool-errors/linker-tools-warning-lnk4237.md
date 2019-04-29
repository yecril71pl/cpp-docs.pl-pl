---
title: Ostrzeżenie LNK4237 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4237
helpviewer_keywords:
- LNK4237
ms.assetid: 87bfec39-5241-464f-9feb-517b49f352ea
ms.openlocfilehash: 62ce0a0edc7f15bc5a19e4630133976f413da35a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352661"
---
# <a name="linker-tools-warning-lnk4237"></a>Ostrzeżenie LNK4237 narzędzi konsolidatora

Subsystem określony podczas importowania pozycji z 'dll'; Użyj opcji lub/Subsystem: Windows.

[Subsystem](../../build/reference/subsystem-specify-subsystem.md) została określona podczas tworzenia aplikacji systemu windows (Win32), który bezpośrednio korzysta z co najmniej jeden z następujących czynności:

- kernel32.dll

- gdi32.dll

- user32.dll

- jedną z msvcrt\* biblioteki dll.

Rozwiązanie to ostrzeżenie, nie określając **Subsystem**.