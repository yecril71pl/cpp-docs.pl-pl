---
title: Definicje argumentu
ms.date: 11/04/2016
helpviewer_keywords:
- envp argument
- main function, arguments
- arguments [C++], for main function
- argv argument
- argc argument
ms.assetid: 6148cbf3-ebe8-44f2-b277-de4b723991c7
ms.openlocfilehash: 14e5ea3a051d81828c5f88ac16df60b6ebb5b559
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498814"
---
# <a name="argument-definitions"></a>Definicje argumentu

Argumenty w prototypie

```cpp
int main( int argc, char* argv[], char* envp[]);
int wmain( int argc, wchar_t* argv[], wchar_t* envp[]);
```

umożliwiają wygodne przetwarzanie argumentów z poziomu wiersza polecenia oraz, opcjonalnie, dostęp do zmiennych środowiskowych. Definicje argumentów są następujące:

*argc*<br/>
Liczba całkowita, która zawiera liczbę argumentów, które obserwują w *argv*. Parametr *argc* jest zawsze większy lub równy 1.

*argv*<br/>
Tablica ciągów zakończonych znakiem null, która reprezentuje argumenty wiersza polecenia wprowadzone przez użytkownika programu. Według Konwencji `argv[0]` jest poleceniem, z którym wywoływany jest program, `argv[1]` jest pierwszym argumentem wiersza polecenia i tak dalej, do `argv[argc]`, który jest zawsze równy null. Zobacz [Dostosowywanie przetwarzania wiersza polecenia](../cpp/customizing-cpp-command-line-processing.md) , aby uzyskać informacje dotyczące pomijania przetwarzania w wierszu polecenia.

Pierwszy argument wiersza polecenia jest zawsze `argv[1]` i ostatnim z nich jest. `argv[argc - 1]`

> [!NOTE]
> Według Konwencji jest `argv[0]` poleceniem, z którym wywoływany jest program.  Istnieje jednak możliwość duplikowania procesu przy użyciu metody [CreateProcess](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) , a jeśli używasz zarówno pierwszego, jak i drugiego argumentu (*lpApplicationName* i *lpCommandLine*), `argv[0]` nie może być nazwą pliku wykonywalnego; Użyj [Funkcja GetModuleFileName ](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew)aby pobrać nazwę pliku wykonywalnego i jego w pełni kwalifikowaną ścieżkę.

## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft

*envp*<br/>
Tablica *envp* , która jest typowym rozszerzeniem w wielu systemach UNIX, jest używana w firmie Microsoft C++. Jest to tablica ciągów reprezentujących zestaw zmiennych w środowisku użytkownika. Ta tablica została zakończona przez wpis o wartości NULL. Może być zadeklarowany jako tablica wskaźników do **char** (`char *envp[]`) lub jako wskaźnik do wskaźników do **char** (`char **envp`). Jeśli `wmain` program używa `main`zamiast tego, użyj typu danych **wchar_t** zamiast **char**. Blok środowiska przeszedł do `main` i `wmain` jest "zamrożoną" kopią bieżącego środowiska. Jeśli później zmienisz środowisko za pośrednictwem wywołania do `putenv` lub `_wputenv`, bieżące środowisko ( `_environ` zwracane przez `getenv` lub `_wgetenv` i zmienna or `_wenviron` ) ulegnie zmianie, ale blok wskazywany przez envp nie zmieni się. Zobacz [Dostosowywanie przetwarzania wiersza polecenia](../cpp/customizing-cpp-command-line-processing.md) , aby uzyskać informacje dotyczące pomijania przetwarzania środowiska. Ten argument jest zgodny ze standardem ANSI w języku C, ale nie w języku C++.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać argumentów *argc*, *argv*i *envp* do `main`:

```cpp
// argument_definitions.cpp
// compile with: /EHsc
#include <iostream>
#include <string.h>

using namespace std;
int main( int argc, char *argv[], char *envp[] ) {
    int iNumberLines = 0;    // Default is no line numbers.

    // If /n is passed to the .exe, display numbered listing
    // of environment variables.

    if ( (argc == 2) && _stricmp( argv[1], "/n" ) == 0 )
         iNumberLines = 1;

    // Walk through list of strings until a NULL is encountered.
    for( int i = 0; envp[i] != NULL; ++i ) {
        if( iNumberLines )
            cout << i << ": " << envp[i] << "\n";
    }
}
```

## <a name="see-also"></a>Zobacz także

[main: uruchamianie programu](../cpp/main-program-startup.md)