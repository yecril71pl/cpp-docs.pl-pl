---
title: "Ostrzeżenie LNK4104 narzędzi konsolidatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4104
dev_langs:
- C++
helpviewer_keywords:
- LNK4104
ms.assetid: ca6728db-d616-419a-a570-65e8445c6079
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b26286f375f54a20e1d3db534576f692179ade24
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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