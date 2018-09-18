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
ms.openlocfilehash: 9d78b23f81b72d04e9299616b0273bc97bb7a4e0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078156"
---
# <a name="expanding-wildcard-arguments"></a>Rozszerzanie argumentów z symbolami wieloznacznymi

**Microsoft Specific**

Kiedy uruchamiasz C program, można użyć jednej z dwóch symboli wieloznacznych — znak zapytania (?) i gwiazdki (*), aby określić nazwę pliku i ścieżkę argumenty wiersza polecenia.

Symbole wieloznaczne nie zostaną domyślnie rozwinięte w argumentach wiersza polecenia. Możesz zastąpić wektor normalne argument `argv` ładowania procedury przy użyciu obowiązującej wersji rozwiń symboli wieloznacznych, łącząc się z plikiem setargv.obj lub wsetargv.obj. Jeśli program używa `main` funkcji, Połącz z biblioteką setargv.obj. Jeśli program używa `wmain` funkcji, Połącz z biblioteką wsetargv.obj. Oba te mają równoważne zachowanie.

Aby połączyć z setargv.obj lub wsetargv.obj, użyj **/link** opcji. Na przykład:

**setargv.obj/Link example.c cl**

Symbole wieloznaczne są rozwijane w taki sam sposób jak poleceń systemu operacyjnego. (Zobacz Podręcznik użytkownika systemu operacyjnego, jeśli nie jesteś zaznajomiony z symbolami wieloznacznymi).

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Opcje łącz](../c-runtime-library/link-options.md)<br/>
[Funkcja main i wykonywanie programu](../c-language/main-function-and-program-execution.md)