---
title: Ostrzeżenie LNK4237 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4237
helpviewer_keywords:
- LNK4237
ms.assetid: 87bfec39-5241-464f-9feb-517b49f352ea
ms.openlocfilehash: aaa26393f1ce76d3e1bc40e5ba4978d1bcdb4fc9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193761"
---
# <a name="linker-tools-warning-lnk4237"></a>Ostrzeżenie LNK4237 narzędzi konsolidatora

/SUBSYSTEM: NATYWNy określony podczas importowania z "dll"; Użyj/SUBSYSTEM: CONSOLE lub/SUBSYSTEM: WINDOWS.

[/SUBSYSTEM:](../../build/reference/subsystem-specify-subsystem.md) podczas kompilowania aplikacji systemu Windows (Win32) został określony kod natywny, który bezpośrednio używa co najmniej jednego z następujących elementów:

- kernel32.dll

- gdi32.dll

- user32.dll

- Jedna z msvcrt\* biblioteki DLL.

Usuń to ostrzeżenie, nie określając **/SUBSYSTEM: Native**.
