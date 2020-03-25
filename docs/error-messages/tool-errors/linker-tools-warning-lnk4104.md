---
title: Ostrzeżenie LNK4104 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4104
helpviewer_keywords:
- LNK4104
ms.assetid: ca6728db-d616-419a-a570-65e8445c6079
ms.openlocfilehash: 604dccf01b3dffc0060546bebf19d64c16ebf965
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193969"
---
# <a name="linker-tools-warning-lnk4104"></a>Ostrzeżenie LNK4104 narzędzi konsolidatora

Eksport symbolu "symbol" powinien być prywatny

`symbol` może być jedną z następujących:

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

To ostrzeżenie jest emitowane podczas tworzenia biblioteki importu dla biblioteki DLL i eksportowania jednej z powyższych funkcji bez określania jej jako prywatnego w pliku definicji modułu. Ogólnie rzecz biorąc, te funkcje są eksportowane do użycia tylko przez OLE. Umieszczenie ich w bibliotece import może prowadzić do nietypowego zachowania, gdy program połączony z biblioteką niepoprawnie wywołuje te wywołania. Aby uzyskać więcej informacji na temat prywatnego słowa kluczowego, zobacz [eksporty](../../build/reference/exports.md).
