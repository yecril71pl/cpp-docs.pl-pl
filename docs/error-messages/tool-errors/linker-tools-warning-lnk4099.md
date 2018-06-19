---
title: Ostrzeżenie LNK4099 narzędzi konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4099
dev_langs:
- C++
helpviewer_keywords:
- LNK4099
ms.assetid: 358170a4-07cd-43fe-918f-82c32757ffc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 22764705b35b2e882c5a03e819c9812d084dc118
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300816"
---
# <a name="linker-tools-warning-lnk4099"></a>Ostrzeżenie LNK4099 narzędzi konsolidatora
Nie można odnaleźć pliku PDB "filename", "bibliotek/obiektów" lub w 'path'; Łączenie obiekt zostanie skonsolidowany bez informacji debugowania  
  
 Nie można znaleźć pliku PDB konsolidator. Skopiuj go do katalogu zawierającego `object/library`.  
  
 Aby znaleźć nazwę pliku .pdb skojarzone z pliku obiektu:  
  
1.  Wyodrębnij plik obiektu z biblioteki z [lib](../../build/reference/lib-reference.md) **/extract:**`objectname`**.obj** `xyz` **.lib**.  
  
2.  Sprawdź ścieżkę do pliku .pdb **dumpbin /section:.debug$ T /rawdata** `objectname` **.obj**.  
  
 Możesz również można skompilować z [/z7](../../build/reference/z7-zi-zi-debug-information-format.md), więc pliku pdb nie musi być używane, lub usuń [/DEBUG](../../build/reference/debug-generate-debug-info.md) opcji konsolidatora, jeśli nie masz .pdb, pliki dla obiektów jest nawiązywane połączenie.