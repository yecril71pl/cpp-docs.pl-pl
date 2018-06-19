---
title: Rozszerzanie argumentów z symbolami wieloznacznymi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- asterisk wildcard
- question mark, wildcard
- expanding wildcard arguments
- wildcards, expanding
ms.assetid: 80a11c4b-0199-420e-a342-cf1d803be5bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 69d7a9fc75e23a03e4db232bc798c89f89083e62
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32383634"
---
# <a name="expanding-wildcard-arguments"></a>Rozszerzanie argumentów z symbolami wieloznacznymi
**Microsoft Specific**  
  
 Po uruchomieniu programu C, można użyć jednej z dwóch symboli wieloznacznych — znak zapytania (?) i gwiazdki (*), aby określić nazwę pliku i ścieżkę argumenty wiersza polecenia.  
  
 Symbole wieloznaczne nie zostaną domyślnie rozwinięte w argumentach wiersza polecenia. Można zastąpić wektora normalnego argument `argv` ładowania procedury z wersją rozwiń symboli wieloznacznych, łącząc się z plikiem setargv.obj lub wsetargv.obj. Jeśli używany przez program `main` funkcji, Połącz z biblioteką setargv.obj. Jeśli używany przez program `wmain` funkcji, Połącz z biblioteką wsetargv.obj. Oba te mają równoważne zachowanie.  
  
 Aby połączyć się z setargv.obj lub wsetargv.obj, należy użyć **/link** opcji. Na przykład:  
  
 **setargv.obj/Link example.c cl**  
  
 Symbole wieloznaczne są rozwijane w taki sam sposób jak poleceń systemu operacyjnego. (Zobacz Podręcznik użytkownika systemu operacyjnego, jeśli nie znasz z symbolami wieloznacznymi).  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje łącz](../c-runtime-library/link-options.md)   
 [Funkcja main i wykonywanie programu](../c-language/main-function-and-program-execution.md)