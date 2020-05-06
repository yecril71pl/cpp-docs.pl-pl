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
ms.openlocfilehash: 1abdb0c104755efc86543ac4773359078e855999
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62290693"
---
# <a name="customizing-c-command-line-processing"></a>Dostosowywanie przetwarzania w wierszu polecenia języka C

Jeśli program nie przyjmuje argumentów wiersza polecenia, można zaoszczędzić małą ilość miejsca, pomijając użycie procedury biblioteki, która wykonuje przetwarzanie wiersza polecenia. Ta procedura jest nazywana **_setargv** (lub **_wsetargv** w środowisku o szerokim znaku), zgodnie z opisem w [rozwijaniu argumentów z symbolami wieloznacznymi](../c-language/expanding-wildcard-arguments.md). Aby pominąć jego użycie, zdefiniuj procedurę, która nie wykonuje żadnych operacji w pliku zawierającym **główną** funkcję i nadaj jej nazwę **_setargv** (lub **_wsetargv** w środowisku znaków dwubajtowych). Wywołanie **_setargv** lub **_wsetargv** jest następnie spełnione przez definicję **_setargv** lub **_wsetargv** , a wersja biblioteki nie została załadowana.

Podobnie, jeśli nie masz dostępu do tabeli środowiska za pomocą `envp` argumentu, możesz podać własną pustą procedurę, która będzie używana zamiast **_setenvp** (lub **_wsetenvp**), procedury przetwarzania środowiska.

Jeśli program wykonuje wywołania do **_spawn** lub **_exec** z rodziny procedur w bibliotece wykonawczej C, nie należy pomijać procedury przetwarzania środowiska, ponieważ ta procedura służy do przekazywania środowiska z procesu duplikowania do nowego procesu.

## <a name="see-also"></a>Zobacz też

[Funkcja main i wykonywanie programu](../c-language/main-function-and-program-execution.md)
