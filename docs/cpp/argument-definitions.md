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
ms.openlocfilehash: 92e213b5accbf8fd5f48ac2111a169e585d82a1d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62184449"
---
# <a name="argument-definitions"></a>Definicje argumentu

Argumenty w prototypie

```cpp
int main( int argc, char* argv[], char* envp[]);
int wmain( int argc, wchar_t* argv[], wchar_t* envp[]);
```

umożliwiają wygodne przetwarzanie argumentów z poziomu wiersza polecenia oraz, opcjonalnie, dostęp do zmiennych środowiskowych. Definicje argumentów są następujące:

*argc —*<br/>
Liczba całkowita, która zawiera liczbę argumentów, które należy wykonać w *argv*. *Argc —* parametru jest zawsze większa lub równa 1.

*ARGV*<br/>
Tablica ciągów zakończonych znakiem null, która reprezentuje argumenty wiersza polecenia wprowadzone przez użytkownika programu. Zgodnie z Konwencją `argv[0]` jest poleceniem, z którym wywoływany jest program `argv[1]` jest pierwszym argumentem wiersza polecenia i tak dalej, aż do `argv[argc]`, która zawsze ma wartość NULL. Zobacz [Dostosowywanie przetwarzania wiersza polecenia](../cpp/customizing-cpp-command-line-processing.md) uzyskać informacje dotyczące pomijania przetwarzania w wierszu polecenia.

Pierwszym argumentem wiersza polecenia jest zawsze `argv[1]` i jest ostatni z nich `argv[argc - 1]`.

> [!NOTE]
> Zgodnie z Konwencją `argv[0]` jest poleceniem, z którym wywoływany jest program.  Jednak jest możliwe, aby utworzyć proces przy użyciu [CreateProcess](/windows/desktop/api/libloaderapi/nf-libloaderapi-getmodulefilenamea) i jeśli korzystasz z pierwszego i drugiego argumentu (*lpApplicationName* i *lpCommandLine*), `argv[0]` nie może być nazwą pliku wykonywalnego; Użyj [Funkcja GetModuleFileName](/windows/desktop/api/libloaderapi/nf-libloaderapi-getmodulefilenamea) można pobrać nazwy pliku wykonywalnego oraz jego w pełni kwalifikowanej ścieżki.

## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft

*envp*<br/>
*Envp* tablicy, która jest typowym rozszerzeniem w wielu systemach UNIX, jest używany w Microsoft C++. Jest to tablica ciągów reprezentujących zestaw zmiennych w środowisku użytkownika. Tablica jest zakończona wpisem o wartości NULL. Mogą być deklarowane jako tablica wskaźników do **char** (`char *envp[]`) lub jako wskaźnik do wskaźników do **char** (`char **envp`). Jeśli program używa `wmain` zamiast `main`, użyj **wchar_t** typu danych zamiast **char**. Blok środowiska przekazany do `main` i `wmain` jest "zamrożoną" kopią bieżącego środowiska. Jeśli następnie zmienisz środowisko przez wywołanie `putenv` lub `_wputenv`, bieżące środowisko (zwrócone przez `getenv` lub `_wgetenv` i `_environ` lub `_wenviron` zmiennej) ulegnie zmianie, ale blok wskazywany przez envp nie ulegnie zmianie. Zobacz [Dostosowywanie przetwarzania wiersza polecenia](../cpp/customizing-cpp-command-line-processing.md) uzyskać informacje dotyczące pomijania przetwarzania środowiska. Ten argument jest zgodny ze standardem ANSI w języku C, ale nie w języku C++.

**END specyficzny dla Microsoft**

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać *argc —*, *argv*, i *envp* argumenty `main`:

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