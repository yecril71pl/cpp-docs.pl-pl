---
title: Ostrzeżenie LNK4104 narzędzi konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4104
dev_langs:
- C++
helpviewer_keywords:
- LNK4104
ms.assetid: ca6728db-d616-419a-a570-65e8445c6079
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6304f3ea928c89f4756a4594270ebb7914324f85
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057265"
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