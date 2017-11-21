---
title: "-PDBALTPATH (Użyj alternatywnej ścieżki PDB) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /pdbaltpath
dev_langs: C++
helpviewer_keywords:
- .pdb files, path
- PDBALTPATH dumpbin option
- -PDBALTPATH dumpbin option
- /PDBALTPATH dumpbin option
- PDB files, path
ms.assetid: 72e200aa-e2c3-4ad8-b687-25528da1aaaf
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1a35e83f28a78acf199e74118cc1fef359666cf1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="pdbaltpath-use-alternate-pdb-path"></a>/PDBALTPATH (Użyj alternatywnej ścieżki PDB)
```  
/PDBALTPATH:pdb_file_name  
```  
  
## <a name="remarks"></a>Uwagi  
 gdzie:  
  
 *pdb_file_name*  
 Nazwa i ścieżka pliku dla pliku PDB.  
  
## <a name="remarks"></a>Uwagi  
 Użyj tej opcji, aby dostarczyć alternatywną lokalizację pliku bazy danych programu (PDB) w skompilowanym plikiem binarnym. Zwykle konsolidator rejestruje lokalizację pliku PDB w generuje pliki binarne. Ta opcja umożliwia Podaj inną ścieżkę i nazwę pliku dla pliku PDB. Z informacji podanych z /PDBALTPATH nie zmienia się lokalizacja lub nazwa pliku PDB rzeczywiste; Zmienia informacje, które konsolidator zapisuje w pliku binarnym. Dzięki temu można wprowadzić ścieżkę, która jest niezależna od struktury plików komputerze kompilacji. Podaj ścieżkę sieciową lub plik, który nie ma ścieżki informacji są dwie typowe zastosowania tej opcji.  
  
 Wartość *pdb_file_name* może być dowolny ciąg, wartość zmiennej środowiskowej lub **_PDB %**. Konsolidator rozwinie zmiennej środowiskowej, takich jak **katalogu % SystemRoot %**, jego wartość. Zmienne środowiskowe definiuje konsolidator **_PDB %** i **_EXT %**. **_PDB %** rozszerza na nazwę pliku bez żadnych danych ścieżki pliku .pdb rzeczywiste i **_EXT %** jest rozszerzeniem wygenerowanego pliku wykonywalnego.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje DUMPBIN](../../build/reference/dumpbin-options.md)   
 [/ PDBPATH](../../build/reference/pdbpath.md)