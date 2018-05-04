---
title: -PDBPATH | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 274c4a3742d99b1e4702ed332206b78dacebccbd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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