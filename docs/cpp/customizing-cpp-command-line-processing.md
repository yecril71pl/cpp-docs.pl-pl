---
title: Dostosowywanie przetwarzania w wierszu polecenia języka C++
ms.date: 11/04/2016
f1_keywords:
- _setenvp
- _setargv
helpviewer_keywords:
- command line [C++], processing
- command-line processing
- startup code, customizing command-line processing
- environment, environment-processing routine
- _setargv function
- command line [C++], processing arguments
- suppressing environment processing
- _setenvp function
ms.assetid: aae01cbb-892b-48b8-8e1f-34f22421f263
ms.openlocfilehash: da1b3bdd6392b144f9315add4c19de14c1d14d41
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154694"
---
# <a name="customizing-c-command-line-processing"></a>Dostosowywanie przetwarzania w wierszu polecenia języka C++

## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft

Jeśli program nie przyjmuje argumentów wiersza polecenia, można zapisać małej ilości miejsca, z pominięciem użyj procedury biblioteki, która wykonuje przetwarzania w wierszu polecenia. Ta procedura jest wywoływana `_setargv` i jest opisany w [rozwijanie symbolu wieloznacznego](../cpp/wildcard-expansion.md). Aby pominąć jego użycia, należy zdefiniować procedurę, która nie wykonuje żadnych działań w pliku zawierającego `main` funkcji i nadaj mu nazwę `_setargv`. Wywołanie `_setargv` następnie jest spełniony, definicja `_setargv`, oraz wersji biblioteki nie jest załadowany.

Podobnie jeśli nigdy nie dostępu do tabeli środowiska za pomocą `envp` argument, możesz podać własne pusty procedura ma być używany zamiast `_setenvp`, procedura przetwarzania w środowisku. Podobnie jak `_setargv` funkcji `_setenvp` musi być zadeklarowany jako **extern "C"**.

Program może wykonywać wywołania `spawn` lub `exec` rodziny procedury biblioteki wykonawczej C. Jeśli jest to możliwe, nie ma pomijać procedura przetwarzania w środowisku, ponieważ ta procedura służy do przekazywania środowisko z procesu nadrzędnego do procesu podrzędnego.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[main: uruchamianie programu](../cpp/main-program-startup.md)