---
title: -PDBPATH | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /pdbpath
dev_langs:
- C++
helpviewer_keywords:
- .pdb files, path
- -PDBPATH dumpbin option
- /PDBPATH dumpbin option
- PDBPATH dumpbin option
- PDB files, path
ms.assetid: ccf67dcd-0b23-4250-ad47-06c48acbe82b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0ccbcedbf9cdd376fa7d9bced5c9d49542cee9f6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="pdbpath"></a>/PDBPATH
```  
/PDBPATH[:VERBOSE] filename  
```  
  
## <a name="remarks"></a>Uwagi  
 gdzie:  
  
 *Nazwa pliku*  
 Nazwa pliku .dll lub .exe, dla której chcesz znaleźć odpowiedniego pliku PDB.  
  
 PEŁNE (opcjonalnie)  
 Raportuje wszystkie katalogi, gdy nastąpiła próba można znaleźć pliku PDB.  
  
## <a name="remarks"></a>Uwagi  
 / PDBPATH umożliwia wyszukiwanie komputera wzdłuż tej samej ścieżki, które debuger będzie wyszukiwać plik PDB i zgłasza odpowiadające, jeśli taki występuje, .pdb, pliki określonego w pliku *filename*.  
  
 Korzystając z debuger programu Visual Studio, może wystąpić problem z faktu, że debuger jest używany plik PDB dla innej wersji pliku, który debugowania.  
  
 / PDBPATH wyszuka .pdb, pliki wzdłuż następujących ścieżkach:  
  
-   Sprawdź lokalizację, w której znajduje się plik wykonywalny.  
  
-   Sprawdź lokalizację pliku PDB zapisana w pliku wykonywalnego. Jest to zwykle lokalizacji w momencie obraz był połączony.  
  
-   Sprawdź na ścieżce wyszukiwania skonfigurowane w programie Visual Studio IDE.  
  
-   Sprawdź wzdłuż ścieżki _NT_SYMBOL_PATH i _NT_ALT_SYMBOL_PATH zmiennych środowiskowych.  
  
-   Sprawdź w katalogu systemu Windows.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje DUMPBIN](../../build/reference/dumpbin-options.md)   
 [/PDBALTPATH (Użyj alternatywnej ścieżki PDB)](../../build/reference/pdbaltpath-use-alternate-pdb-path.md)