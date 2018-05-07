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
ms.openlocfilehash: d9ea3e074cc0db9591cd0ffe9329ff7f1936563f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4104"></a>Ostrzeżenie LNK4104 narzędzi konsolidatora
Eksport symbolu "symbol" powinien mieć atrybut PRIVATE  
  
 `symbol` Może być jedną z następujących czynności:  
  
-   `DllCanUnloadNow`  
  
-   `DllGetClassObject`  
  
-   `DllGetClassFactoryFromClassString`  
  
-   `DllGetDocumentation`  
  
-   `DllInitialize`  
  
-   `DllInstall`  
  
-   `DllRegisterServer`  
  
-   `DllRegisterServerEx`  
  
-   `DllRegisterServerExW`  
  
-   `DllUnload`  
  
-   `DllUnregisterServer`  
  
-   `RasCustomDeleteEntryNotify`  
  
-   `RasCustomDial`  
  
-   `RasCustomDialDlg`  
  
-   `RasCustomEntryDlg`  
  
 To ostrzeżenie jest emitowany podczas tworzenia biblioteki importowanej dla biblioteki DLL i eksportowanie jednego z powyższych funkcji bez określania go jako prywatny w pliku definicji modułu. Ogólnie rzecz biorąc te funkcje zostaną wyeksportowane do użycia tylko przez OLE. Umieszczenie ich w bibliotece importu może prowadzić do nietypowych zachowań po niepoprawnie połączona z biblioteką programu wywołań do nich. Aby uzyskać więcej informacji na temat PRIVATE — słowo kluczowe, zobacz [EKSPORTÓW](../../build/reference/exports.md).