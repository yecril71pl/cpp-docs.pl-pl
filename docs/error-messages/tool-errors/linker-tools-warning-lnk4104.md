---
title: Ostrzeżenie LNK4104 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4104
helpviewer_keywords:
- LNK4104
ms.assetid: ca6728db-d616-419a-a570-65e8445c6079
ms.openlocfilehash: 3d89b27c32b33b917abb7fc140eebf5924142423
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298545"
---
# <a name="linker-tools-warning-lnk4104"></a>Ostrzeżenie LNK4104 narzędzi konsolidatora

Eksport symbolu "symbol" powinien mieć atrybut PRIVATE

`symbol` Może być jedną z następujących czynności:

- `DllCanUnloadNow`

- `DllGetClassObject`

- `DllGetClassFactoryFromClassString`

- `DllGetDocumentation`

- `DllInitialize`

- `DllInstall`

- `DllRegisterServer`

- `DllRegisterServerEx`

- `DllRegisterServerExW`

- `DllUnload`

- `DllUnregisterServer`

- `RasCustomDeleteEntryNotify`

- `RasCustomDial`

- `RasCustomDialDlg`

- `RasCustomEntryDlg`

To ostrzeżenie jest emitowane podczas kompilowania biblioteki importowanej dla biblioteki DLL i eksportowanie jednej z powyższych funkcji bez określania jako prywatny, w pliku definicji modułu. Ogólnie rzecz biorąc te funkcje są eksportowane do użytku tylko przez OLE. Umieszczenie ich w bibliotece importu może prowadzić do nietypowych zachowań, po program, nieprawidłowo połączona z biblioteką wywołań do nich. Aby uzyskać więcej informacji na temat PRIVATE — słowo kluczowe, zobacz [EKSPORTY](../../build/reference/exports.md).