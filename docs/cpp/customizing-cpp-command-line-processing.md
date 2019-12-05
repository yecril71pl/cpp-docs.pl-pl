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
ms.openlocfilehash: 1541840521695658b5c4d809ba7e11767b1330a2
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857557"
---
# <a name="customizing-c-command-line-processing"></a>Dostosowywanie przetwarzania w wierszu polecenia języka C++

**Microsoft Specific**

Jeśli program nie przyjmuje argumentów wiersza polecenia, można zaoszczędzić małą ilość miejsca, pomijając użycie procedury biblioteki, która wykonuje przetwarzanie wiersza polecenia. Ta procedura jest nazywana `_setargv` i jest opisana w [rozwinięciu symboli wieloznacznych](../cpp/wildcard-expansion.md). Aby pominąć jego użycie, zdefiniuj procedurę, która nie wykonuje żadnych operacji w pliku zawierającym funkcję `main` i nadaj jej nazwę `_setargv`. Wywołanie `_setargv` jest następnie spełnione przez definicję `_setargv`, a wersja biblioteki nie została załadowana.

Podobnie, jeśli nie masz dostępu do tabeli środowiska za pomocą argumentu `envp`, możesz podać własną pustą procedurę, która będzie używana zamiast `_setenvp`, procedury przetwarzania środowiska. Podobnie jak w przypadku funkcji `_setargv`, `_setenvp` musi być zadeklarowany jako **extern "C"** .

Program może nawiązywać wywołania do `spawn` lub `exec` z rodziny procedur w bibliotece wykonawczej C. W takim przypadku nie należy pomijać procedury przetwarzania środowiska, ponieważ ta procedura jest używana do przekazywania środowiska z procesu nadrzędnego do procesu podrzędnego.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[main: uruchamianie programu](../cpp/main-program-startup.md)