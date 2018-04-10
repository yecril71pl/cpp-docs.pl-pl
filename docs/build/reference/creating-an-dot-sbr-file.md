---
title: Tworzenie. Plik SBR | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- SBR files
- BSCMAKE, input files
- .sbr files
- source browser files
- local symbols in browse information
- symbols
ms.assetid: bdb4b93c-a88a-441a-84fd-01087d03be25
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d87b71daaf5d7b37e67c2c0e56e844bd5251a490
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="creating-an-sbr-file"></a>Tworzenie pliku .Sbr
Pliki wejściowe dla BSCMAKE są pliki .sbr. Kompilator tworzy plik SBR dla każdego pliku obiektu (.obj) skompilowany. Podczas tworzenia lub zaktualizuj plik informacji o przeglądaniu wszystkich plików SBR dla projektu musi być dostępny na dysku.  
  
 Aby utworzyć plik .sbr wszystkie możliwe informacje, należy określić [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md).  
  
 Aby utworzyć plik SBR, który nie zawiera symbole lokalne, określ [/Fr](../../build/reference/fr-fr-create-dot-sbr-file.md). Jeśli pliki SBR zawierają symbole lokalne, można nadal pominąć je w pliku .bsc przy użyciu jego BSCMAKE [/El — opcja](../../build/reference/bscmake-options.md)`.`  
  
 Można utworzyć pliku .sbr bez wykonywania pełnej kompilacji. Na przykład można określić /Zs — opcja kompilatora, aby sprawdzić składnię, a następnie nadal Wygeneruj plik SBR, jeśli określono /FR lub /Fr.  
  
 Proces kompilacji może być bardziej wydajne, jeśli pliki SBR najpierw są pakować usunąć nieużywane definicje. Kompilator automatycznie pakietów pliki .sbr.  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilowanie pliku .Bsc](../../build/reference/building-a-dot-bsc-file.md)