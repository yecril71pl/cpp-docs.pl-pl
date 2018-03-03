---
title: "Rozszerzanie argumentów z symbolami wieloznacznymi | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- asterisk wildcard
- question mark, wildcard
- expanding wildcard arguments
- wildcards, expanding
ms.assetid: 80a11c4b-0199-420e-a342-cf1d803be5bc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f710cc1695579bf1a6f873229c347966888bc745
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="expanding-wildcard-arguments"></a>Rozszerzanie argumentów z symbolami wieloznacznymi
**Dotyczące firmy Microsoft**  
  
 Po uruchomieniu programu C, można użyć jednej z dwóch symboli wieloznacznych — znak zapytania (?) i gwiazdki (*), aby określić nazwę pliku i ścieżkę argumenty wiersza polecenia.  
  
 Symbole wieloznaczne nie zostaną domyślnie rozwinięte w argumentach wiersza polecenia. Można zastąpić wektora normalnego argument `argv` ładowania procedury z wersją rozwiń symboli wieloznacznych, łącząc się z plikiem setargv.obj lub wsetargv.obj. Jeśli używany przez program `main` funkcji, Połącz z biblioteką setargv.obj. Jeśli używany przez program `wmain` funkcji, Połącz z biblioteką wsetargv.obj. Oba te mają równoważne zachowanie.  
  
 Aby połączyć się z setargv.obj lub wsetargv.obj, należy użyć **/link** opcji. Na przykład:  
  
 **setargv.obj/Link example.c cl**  
  
 Symbole wieloznaczne są rozwijane w taki sam sposób jak poleceń systemu operacyjnego. (Zobacz Podręcznik użytkownika systemu operacyjnego, jeśli nie znasz z symbolami wieloznacznymi).  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje łącz](../c-runtime-library/link-options.md)   
 [Funkcja main i wykonywanie programu](../c-language/main-function-and-program-execution.md)