---
title: "Ostrzeżenie LNK4099 narzędzi konsolidatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4099
dev_langs: C++
helpviewer_keywords: LNK4099
ms.assetid: 358170a4-07cd-43fe-918f-82c32757ffc5
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 364c2f9303707328ebf3bdf3284398e6d4f9f0d7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4099"></a>Ostrzeżenie LNK4099 narzędzi konsolidatora
Nie można odnaleźć pliku PDB "filename", "bibliotek/obiektów" lub w 'path'; Łączenie obiekt zostanie skonsolidowany bez informacji debugowania  
  
 Nie można znaleźć pliku PDB konsolidator. Skopiuj go do katalogu zawierającego `object/library`.  
  
 Aby znaleźć nazwę pliku .pdb skojarzone z pliku obiektu:  
  
1.  Wyodrębnij plik obiektu z biblioteki z [lib](../../build/reference/lib-reference.md) **/extract:**`objectname`**.obj** `xyz` **.lib**.  
  
2.  Sprawdź ścieżkę do pliku .pdb **dumpbin /section:.debug$ T /rawdata** `objectname` **.obj**.  
  
 Możesz również można skompilować z [/z7](../../build/reference/z7-zi-zi-debug-information-format.md), więc pliku pdb nie musi być używane, lub usuń [/DEBUG](../../build/reference/debug-generate-debug-info.md) opcji konsolidatora, jeśli nie masz .pdb, pliki dla obiektów jest nawiązywane połączenie.