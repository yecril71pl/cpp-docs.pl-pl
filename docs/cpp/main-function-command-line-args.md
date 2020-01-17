---
title: argumenty funkcji main i wiersza polecenia (C++)
description: Funkcja main jest punktem wejścia dla C++ programu.
ms.date: 01/15/2019
ms.assetid: c6568ee6-40ab-4ae8-aa44-c99e232f64ac
no-loc:
- main
- wmain
- inline
- static
- _tmain
- void
- exit
- argc
- argv
- envp
- CreateProcess
- GetModuleFileName
- char
- wchar_t
- extern
ms.openlocfilehash: 33753e30304a9bb63c135979d3f20098e6b6401a
ms.sourcegitcommit: e93f3e6a110fe38bc642055bdf4785e620d4220f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76123906"
---
# <a name="opno-locmain-function-and-command-line-arguments"></a>main funkcje i argumenty wiersza polecenia

Wszystkie C++ programy muszą mieć funkcję `main`. Jeśli spróbujesz skompilować C++ projekt *. exe* bez funkcji main, kompilator zgłosi błąd. (Biblioteki dołączane dynamicznie i biblioteki static nie mają funkcji `main`). Funkcja `main` to miejsce, w którym kod źródłowy rozpoczyna wykonywanie, ale zanim program przejdzie do funkcji `main`, wszyscy członkowie klasy static bez jawnych inicjatorów mają ustawioną wartość zero. W firmie C++Microsoft obiekty globalne static są również inicjowane przed wprowadzeniem do `main`. Kilka ograniczeń dotyczy funkcji `main`, która nie ma zastosowania do innych C++ funkcji. Funkcja `main`:

- Nie może być przeciążony (zobacz [przeciążanie funkcji](function-overloading.md)).
- Nie można zadeklarować jako **inline** .
- Nie można zadeklarować jako **static** .
- Nie można pobrać adresu.
- Nie można wywołać.

Funkcja main nie ma deklaracji, ponieważ jest wbudowana w język. Jeśli tak, Składnia deklaracji dla `main` wyglądać następująco:

```cpp
int main();
int main(int argc, char *argv[], char *envp[]);
```

**Microsoft Specific**

Jeśli pliki źródłowe używają znaków Unicode, można użyć `wmain`, która jest wersją znaków dwubajtowych `main`. Składnia deklaracji dla `wmain` jest następująca:

```cpp
int wmain( );
int wmain(int argc, wchar_t *argv[], wchar_t *envp[]);
```

Można również użyć `_tmain`, który jest zdefiniowany w używanie TCHAR. h. `_tmain` jest rozpoznawana jako `main`, chyba że _UNICODE jest zdefiniowany. W takim przypadku `_tmain` jest rozpoznawana jako `wmain`.

Jeśli nie określono wartości zwracanej, kompilator dostarcza wartość zwracaną zero. Alternatywnie można zadeklarować `main` i `wmain` funkcje jako zwracające **void** (brak wartości zwracanej). Jeśli zadeklarujesz `main` lub `wmain` jako zwracające **void** , nie można zwrócić kodu exit do procesu nadrzędnego lub systemu operacyjnego za pomocą instrukcji [Return](../cpp/return-statement-in-program-termination-cpp.md) . Aby zwrócić kod exit, gdy `main` lub `wmain` jest zadeklarowana jako **void** , należy użyć funkcji [exit](../cpp/exit-function.md) .

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="command-line-arguments"></a>Argumenty wiersza polecenia

Argumenty dla `main` lub `wmain` umożliwiają wygodne analizowanie wiersza polecenia argumentów i, opcjonalnie, dostęp do zmiennych środowiskowych. Typy dla `argc` i `argv` są definiowane przez język. Nazwy `argc`, `argv`i `envp` są tradycyjne, ale można je nazwać w dowolny sposób.

```cpp
int main( int argc, char* argv[], char* envp[]);
int wmain( int argc, wchar_t* argv[], wchar_t* envp[]);
```

Definicje argumentów są następujące:

*argc*<br/>
Liczba całkowita, która zawiera liczbę argumentów, które obowiązują w *argv* . Parametr *argc* jest zawsze większy lub równy 1.

*argv*<br/>
Tablica ciągów zakończonych znakiem null, która reprezentuje argumenty wiersza polecenia wprowadzone przez użytkownika programu. Zgodnie z Konwencją `argv[0]` jest poleceniem, z którym wywoływany jest program, `argv[1]` jest pierwszym argumentem wiersza polecenia i tak dalej, aż do `argv[argc]`, który ma zawsze wartość NULL. Zobacz [Dostosowywanie przetwarzania wiersza polecenia](../cpp/customizing-cpp-command-line-processing.md) , aby uzyskać informacje dotyczące pomijania przetwarzania w wierszu polecenia.

Pierwszy argument wiersza polecenia jest zawsze `argv[1]`, a ostatni z nich jest `argv[argc - 1]`.

> [!NOTE]
> Zgodnie z Konwencją `argv[0]` jest poleceniem, z którym wywoływany jest program. Istnieje jednak możliwość duplikowania procesu przy użyciu [CreateProcess](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) , a jeśli używasz zarówno pierwszego, jak i drugiego argumentu (*lpApplicationName* i *lpCommandLine*), `argv[0]` nie może być nazwą pliku wykonywalnego; Użyj [GetModuleFileName](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) , aby pobrać nazwę pliku wykonywalnego i jego w pełni kwalifikowaną ścieżkę.

**Microsoft Specific**

*envp*<br/>
Tablica *envp* , która jest typowym rozszerzeniem w wielu systemach UNIX, jest używana w firmie Microsoft C++. Jest to tablica ciągów reprezentujących zestaw zmiennych w środowisku użytkownika. Tablica jest zakończona wpisem o NULL. Może być zadeklarowany jako tablica wskaźników do **char** (`char *envp[]`) lub jako wskaźnik do wskaźników do **char** (`char **envp`). Jeśli program używa `wmain` zamiast `main`, użyj typu danych **wchar_t** zamiast **char** . Blok środowiska przeszedł do `main` i `wmain` jest kopią zamrożoną bieżącego środowiska. Jeśli następnie zmienisz środowisko za pośrednictwem wywołania do `putenv` lub `_wputenv`, bieżące środowisko (zwracane przez `getenv` lub `_wgetenv` oraz zmienna `_environ` lub `_wenviron`) ulegnie zmianie, ale blok wskazywany przez envp nie ulegnie zmianie. Zobacz [Dostosowywanie przetwarzania wiersza polecenia](../cpp/customizing-cpp-command-line-processing.md) , aby uzyskać informacje dotyczące pomijania przetwarzania środowiska. Ten argument jest zgodny ze standardem ANSI w języku C, ale nie w języku C++.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

### <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać argumentów *argc* , *argv* i *envp* do `main`:

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

## <a name="parsing-c-command-line-arguments"></a>Analizowanie C++ argumentów wiersza polecenia

**Microsoft Specific**

Kod uruchamiania MicrosoftC++ C/uruchomieniowy używa następujących reguł podczas interpretacji argumentów podanych w wierszu polecenia systemu operacyjnego:

- Argumenty są rozdzielane znakami odstępu, który jest spacją lub tabulatorem.

- Znak karetki (^) nie jest rozpoznawany jako znak ucieczki lub ogranicznik. Znak jest całkowicie obsługiwany przez analizator wiersza polecenia w systemie operacyjnym przed przekazaniem do tablicy `argv` w programie.

- Ciąg ujęty w znaki podwójnego cudzysłowu ("*String*") jest interpretowany jako pojedynczy argument, bez względu na biały znak zawarty w. Ciąg w cudzysłowie może być osadzony w argumencie.

- Podwójny cudzysłów poprzedzony ukośnikiem odwrotnym (\\") jest interpretowany jako literał podwójnego znaku cudzysłowu (").

- Ukośniki odwrotne są interpretowane dosłownie, chyba że od razu poprzedzają podwójny cudzysłów.

- Jeśli parzysta liczba kresek ułamkowych jest poprzedzona podwójnym cudzysłowem, jeden ukośnik odwrotny jest umieszczany w tablicy `argv` dla każdej pary ukośników odwrotnych, a podwójny cudzysłów jest interpretowany jako ogranicznik ciągu.

- Jeśli po parzystej liczbie ukośników odwrotnych następuje znak podwójnego cudzysłowu, jedna kreska ułamkowa odwrócona jest umieszczana w tablicy `argv` dla każdej pary ukośników odwrotnych, a podwójne cudzysłowy są "ucieczkd" przez pozostały ukośnik odwrotny, co powoduje, że znak podwójnego cudzysłowu (") ma być umieszczony w `argv`.

### <a name="example"></a>Przykład

Następujący program ilustruje sposób przekazywania argumentów wiersza polecenia:

```cpp
// command_line_arguments.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
int main( int argc,      // Number of strings in array argv
          char *argv[],   // Array of command-line argument strings
          char *envp[] )  // Array of environment variable strings
{
    int count;

    // Display each command-line argument.
    cout << "\nCommand-line arguments:\n";
    for( count = 0; count < argc; count++ )
         cout << "  argv[" << count << "]   "
                << argv[count] << "\n";
}
```

W poniższej tabeli przedstawiono przykładowe dane wejściowe i oczekiwane dane wyjściowe, ukazując reguły z powyższej listy.

### <a name="results-of-parsing-command-lines"></a>Wyniki analizy wierszy poleceń

|Wprowadzanie w wierszu polecenia|argv[1]|argv[2]|argv[3]|
|-------------------------|---------------|---------------|---------------|
|`"abc" d e`|`abc`|`d`|`e`|
|`a\\b d"e f"g h`|`a\\b`|`de fg`|`h`|
|`a\\\"b c d`|`a\"b`|`c`|`d`|
|`a\\\\"b c" d e`|`a\\b c`|`d`|`e`|

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="wildcard-expansion"></a>Rozwijanie symbolu wieloznacznego

**Microsoft Specific**

Możesz użyć symboli wieloznacznych — znaku zapytania (?) i gwiazdki (*), aby określić argumenty filename i Path w wierszu polecenia.

Argumenty wiersza polecenia są obsługiwane przez procedurę o nazwie `_setargv` (lub `_wsetargv` w środowisku szerokich znaków), która domyślnie nie rozszerza symboli wieloznacznych na oddzielne ciągi w `argv` tablicy ciągów. Aby uzyskać więcej informacji na temat włączania rozszerzania symboli wieloznacznych, zobacz [rozszerzanie symboli wieloznacznych](../c-language/expanding-wildcard-arguments.md).

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="customizing-c-command-line-processing"></a>Dostosowywanie przetwarzania w wierszu polecenia języka C++

**Microsoft Specific**

Jeśli program nie przyjmuje argumentów wiersza polecenia, można zaoszczędzić małą ilość miejsca, pomijając użycie procedury biblioteki, która wykonuje przetwarzanie wiersza polecenia. Ta procedura jest nazywana `_setargv` i jest opisana w [rozwinięciu symboli wieloznacznych](../cpp/wildcard-expansion.md). Aby pominąć jego użycie, zdefiniuj procedurę, która nie wykonuje żadnych operacji w pliku zawierającym funkcję `main` i nadaj jej nazwę `_setargv`. Wywołanie `_setargv` jest następnie spełnione przez definicję `_setargv`, a wersja biblioteki nie została załadowana.

Podobnie, jeśli nie masz dostępu do tabeli środowiska za pomocą argumentu `envp`, możesz podać własną pustą procedurę, która będzie używana zamiast `_setenvp`, procedury przetwarzania środowiska. Podobnie jak w przypadku funkcji `_setargv`, `_setenvp` musi być zadeklarowany jako **extern "C"** .

Program może nawiązywać wywołania do `spawn` lub `exec` z rodziny procedur w bibliotece wykonawczej C. Jeśli tak nie jest, nie należy pomijać procedury przetwarzania środowiska, ponieważ ta procedura jest używana do przekazywania środowiska z procesu nadrzędnego do procesu podrzędnego.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Podstawowe pojęcia](../cpp/basic-concepts-cpp.md)
