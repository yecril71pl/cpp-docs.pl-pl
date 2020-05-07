---
title: Rozszerzanie argumentów z symbolami wieloznacznymi
ms.date: 11/04/2016
helpviewer_keywords:
- asterisk wildcard
- question mark, wildcard
- expanding wildcard arguments
- wildcards, expanding
ms.assetid: 80a11c4b-0199-420e-a342-cf1d803be5bc
ms.openlocfilehash: f1fb964fe98223fb7187b83c7101027ed1f9cbea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233817"
---
# <a name="expanding-wildcard-arguments"></a>Rozszerzanie argumentów z symbolami wieloznacznymi

**Specyficzne dla firmy Microsoft**

Po uruchomieniu programu C można użyć jednego z dwóch symboli wieloznacznych — znaku zapytania (?) i gwiazdki (*), aby określić argumenty filename i Path w wierszu polecenia.

Domyślnie symbole wieloznaczne nie są rozwinięte w argumentach wiersza polecenia. Można zastąpić normalną procedurę ładowania wektora `argv` argumentu z wersją, która rozszerza symbole wieloznaczne, łącząc się z plikiem setargv. obj lub Wsetargv. obj. Jeśli program używa `main` funkcji, Połącz z setargv. obj. Jeśli program używa `wmain` funkcji, Połącz z Wsetargv. obj. Oba te elementy mają równoważne zachowanie.

Aby połączyć się z setargv. obj lub Wsetargv. obj, użyj opcji **/link** . Przykład:

**CL przykład. c/link setargv. obj**

Symbole wieloznaczne są rozwinięte w taki sam sposób, jak polecenia systemu operacyjnego. (Jeśli nie znasz symboli wieloznacznych, zapoznaj się z podręcznikiem użytkownika systemu operacyjnego).

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Opcje łącza](../c-runtime-library/link-options.md)<br/>
[Funkcja main i wykonywanie programu](../c-language/main-function-and-program-execution.md)
