---
title: Dostosowywanie przetwarzania w wierszu polecenia języka C
ms.date: 11/04/2016
helpviewer_keywords:
- _spawn functions
- command line, processing
- command-line processing
- startup code, customizing command-line processing
- environment, environment-processing routine
- _setargv function
- command line, processing arguments
- suppressing environment processing
- _exec function
ms.assetid: c20fa11d-b35b-4f3e-93b6-2cd5a1c3c993
ms.openlocfilehash: 9f7bc78c20aee4b91bf00fefd2615ba1a6611010
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50623603"
---
# <a name="customizing-c-command-line-processing"></a>Dostosowywanie przetwarzania w wierszu polecenia języka C

Jeśli program nie przyjmuje argumentów wiersza polecenia, można zapisać małej ilości miejsca, z pominięciem użyj procedury biblioteki, która wykonuje przetwarzania w wierszu polecenia. Ta procedura jest wywoływana **_setargv —** (lub **_wsetargv** w środowisku znaków dwubajtowych), zgodnie z opisem w [rozszerzanie argumentów z symbolami wieloznacznymi](../c-language/expanding-wildcard-arguments.md). Aby pominąć jego użycia, należy zdefiniować procedurę, która nie wykonuje żadnych działań w pliku zawierającego **głównego** funkcji i nadaj mu nazwę **_setargv —** (lub **_wsetargv** w znaków dwubajtowych Środowisko). Wywołanie **_setargv —** lub **_wsetargv** następnie jest spełniony, definicja **_setargv —** lub **_wsetargv** , i jest w wersji biblioteki Nie załadowano.

Podobnie jeśli nigdy nie dostępu do tabeli środowiska za pomocą `envp` argument, możesz podać własne pusty procedura ma być używany zamiast **_setenvp —** (lub **_wsetenvp**), Procedura przetwarzania w środowisku.

Jeśli program wykonywania wywołań do **_spawn** lub **_exec** rodziny procedury biblioteki wykonawczej C, użytkownik powinien pomija procedura przetwarzania w środowisku, ponieważ ta procedura służy do przekazywania środowisko z procesu ikrę do nowego procesu.

## <a name="see-also"></a>Zobacz też

[Funkcja main i wykonywanie programu](../c-language/main-function-and-program-execution.md)