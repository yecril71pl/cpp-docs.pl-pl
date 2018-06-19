---
title: Tworzenie. Plik SBR | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bdada1f4d07d02988da388e39e332c832f633adb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32371086"
---
# <a name="creating-an-sbr-file"></a>Tworzenie pliku .Sbr
Pliki wejściowe dla BSCMAKE są pliki .sbr. Kompilator tworzy plik SBR dla każdego pliku obiektu (.obj) skompilowany. Podczas tworzenia lub zaktualizuj plik informacji o przeglądaniu wszystkich plików SBR dla projektu musi być dostępny na dysku.  
  
 Aby utworzyć plik .sbr wszystkie możliwe informacje, należy określić [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md).  
  
 Aby utworzyć plik SBR, który nie zawiera symbole lokalne, określ [/Fr](../../build/reference/fr-fr-create-dot-sbr-file.md). Jeśli pliki SBR zawierają symbole lokalne, można nadal pominąć je w pliku .bsc przy użyciu jego BSCMAKE [/El — opcja](../../build/reference/bscmake-options.md)`.`  
  
 Można utworzyć pliku .sbr bez wykonywania pełnej kompilacji. Na przykład można określić /Zs — opcja kompilatora, aby sprawdzić składnię, a następnie nadal Wygeneruj plik SBR, jeśli określono /FR lub /Fr.  
  
 Proces kompilacji może być bardziej wydajne, jeśli pliki SBR najpierw są pakować usunąć nieużywane definicje. Kompilator automatycznie pakietów pliki .sbr.  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilowanie pliku .Bsc](../../build/reference/building-a-dot-bsc-file.md)