---
title: main argumenty funkcji i wiersza polecenia (C++)
description: mainFunkcja jest punktem wejścia dla programu C++.
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
ms.openlocfilehash: b27668c3c7ce77e4369af144bb8be4efb695e522
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499816"
---
# <a name="no-locmain-function-and-command-line-arguments"></a>main argumenty funkcji i wiersza polecenia

Wszystkie programy C++ muszą mieć `main` funkcję. Jeśli spróbujesz skompilować projekt C++ *. exe* bez main funkcji, kompilator zgłosi błąd. (Biblioteki i biblioteki dołączane dynamicznie static nie mają `main` funkcji). `main` Funkcja jest, gdzie kod źródłowy rozpoczyna wykonywanie, ale zanim program przejdzie do `main` funkcji, wszystkie static elementy członkowskie klasy bez jawnych inicjatorów mają ustawioną wartość zero. W programie Microsoft C++ static obiekty globalne są również inicjowane przed wpisem do `main` . Kilka ograniczeń ma zastosowanie do `main` funkcji, która nie dotyczy żadnych innych funkcji języka C++. `main`Funkcja:

- Nie może być przeciążony (zobacz [przeciążanie funkcji](function-overloading.md)).
- Nie można zadeklarować jako **`inline`** .
- Nie można zadeklarować jako **`static`** .
- Nie można pobrać adresu.
- Nie można wywołać.

mainFunkcja nie ma deklaracji, ponieważ jest wbudowana w język. Jeśli tak, Składnia deklaracji dla `main` będzie wyglądać następująco:

```cpp
int main();
int main(int argc, char *argv[], char *envp[]);
```

**Specyficzne dla firmy Microsoft**

Jeśli pliki źródłowe używają acters Unicode char , można użyć programu `wmain` , który jest w wersji szerokiej char acter `main` . Składnia deklaracji dla `wmain` jest następująca:

```cpp
int wmain( );
int wmain(int argc, wchar_t *argv[], wchar_t *envp[]);
```

Można również użyć `_tmain` , który jest zdefiniowany w t char . h. `_tmain` jest rozpoznawana do, `main` chyba że _UNICODE jest zdefiniowany. W takim przypadku jest `_tmain` rozpoznawany jako `wmain` .

Jeśli nie określono wartości zwracanej, kompilator dostarcza wartość zwracaną zero. Alternatywnie, `main` funkcje i `wmain` mogą być zadeklarowane jako Return **`void`** (brak wartości zwracanej). Jeśli deklarujesz `main` lub `wmain` jako Return **`void`** , nie można zwrócić exit kodu do procesu nadrzędnego lub systemu operacyjnego za pomocą instrukcji [Return](./program-termination.md) . Aby zwrócić exit kod, gdy `main` lub `wmain` jest zadeklarowany jako **`void`** , należy użyć [exit](./program-termination.md) funkcji.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="command-line-arguments"></a>Argumenty wiersza polecenia

Argumenty dla `main` lub `wmain` umożliwiają wygodne analizowanie wierszy poleceń argumentów i, opcjonalnie, dostęp do zmiennych środowiskowych. Typy dla `argc` i `argv` są zdefiniowane przez język. Nazwy `argc` , `argv` i `envp` są tradycyjnie, ale możesz je nazwać w dowolny sposób.

```cpp
int main( int argc, char* argv[], char* envp[]);
int wmain( int argc, wchar_t* argv[], wchar_t* envp[]);
```

Definicje argumentów są następujące:

*argc*<br/>
Liczba całkowita, która zawiera liczbę argumentów, które są następujące po elemencie *argv* . *argc* Parametr jest zawsze większy lub równy 1.

*argv*<br/>
Tablica ciągów zakończonych znakiem null, która reprezentuje argumenty wiersza polecenia wprowadzone przez użytkownika programu. Według Konwencji `argv[0]` jest poleceniem, z którym wywoływany jest program, `argv[1]` jest pierwszym argumentem wiersza polecenia i tak dalej, do `argv[argc]` , który jest zawsze równy null. Zobacz [Dostosowywanie przetwarzania wiersza polecenia]() , aby uzyskać informacje dotyczące pomijania przetwarzania w wierszu polecenia.

Pierwszy argument wiersza polecenia jest zawsze `argv[1]` i ostatnim z nich jest `argv[argc - 1]` .

> [!NOTE]
> Według Konwencji `argv[0]` jest poleceniem, z którym wywoływany jest program. Istnieje jednak możliwość duplikowania procesu przy użyciu [CreateProcess](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) i, jeśli używasz zarówno pierwszego, jak i drugiego argumentu (*LpApplicationName* i *lpCommandLine*), `argv[0]` nie może być nazwą pliku wykonywalnego; Użyj [GetModuleFileName](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) , aby pobrać nazwę pliku wykonywalnego i jego w pełni kwalifikowaną ścieżkę.

**Specyficzne dla firmy Microsoft**

*envp*<br/>
*envp* Tablica, która jest typowym rozszerzeniem w wielu systemach UNIX, jest używana w programie Microsoft C++. Jest to tablica ciągów reprezentujących zestaw zmiennych w środowisku użytkownika. Ta tablica została zakończona przez wpis o wartości NULL. Może być zadeklarowany jako tablica wskaźników do **`char`** ( `char *envp[]` ) lub jako wskaźnik do wskaźników **`char`** ( `char **envp` ). Jeśli program używa `wmain` zamiast tego `main` , użyj **`wchar_t`** typu danych zamiast **`char`** . Blok środowiska przeszedł do `main` i `wmain` jest "zamrożoną" kopią bieżącego środowiska. Jeśli później zmienisz środowisko za pośrednictwem wywołania do `putenv` lub `_wputenv` , bieżące środowisko (zwracane przez `getenv` lub `_wgetenv` i `_environ` lub  `_wenviron` zmienna) ulegnie zmianie, ale blok wskazywany przez envp nie zmieni się. Zobacz [Dostosowywanie przetwarzania wiersza polecenia]() , aby uzyskać informacje dotyczące pomijania przetwarzania środowiska. Ten argument jest zgodny ze standardem ANSI w języku C, ale nie w języku C++.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

### <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać *argc* *argv* argumentów, i *envp* do `main` :

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

## <a name="parsing-c-command-line-arguments"></a>Analizowanie argumentów wiersza polecenia języka C++

**Specyficzne dla firmy Microsoft**

Kod uruchamiania Microsoft C/C++ używa następujących reguł podczas interpretacji argumentów podanych w wierszu polecenia systemu operacyjnego:

- Argumenty są rozdzielane znakami odstępu, który jest spacją lub tabulatorem.

- Acter karetki char (^) nie jest rozpoznawany jako acter ucieczki char lub ogranicznika. charActer jest obsługiwany całkowicie przez analizator wiersza polecenia w systemie operacyjnym przed przekazaniem do `argv` tablicy w programie.

- Ciąg ujęty w znaki podwójnego cudzysłowu ("*String*") jest interpretowany jako pojedynczy argument, bez względu na biały znak zawarty w. Ciąg w cudzysłowie może być osadzony w argumencie.

- Podwójny cudzysłów poprzedzony ukośnikiem odwrotnym ( \\ ") jest interpretowany jako literał podwójnego znaku cudzysłowu char acter (").

- Ukośniki odwrotne są interpretowane dosłownie, chyba że od razu poprzedzają podwójny cudzysłów.

- Jeśli parzysta liczba kresek ułamkowych jest poprzedzona znakiem podwójnego cudzysłowu, jeden ukośnik odwrotny jest umieszczany w `argv` tablicy dla każdej pary ukośników odwrotnych, a podwójny cudzysłów jest interpretowany jako ogranicznik ciągu.

- Jeśli po parzystej liczbie ukośników odwrotnych następuje znak podwójnego cudzysłowu, jeden ukośnik odwrotny jest umieszczany w `argv` tablicy dla każdej pary ukośników odwrotnych, a podwójne cudzysłowy to "ucieczkd" przez przekroczenie main ukośnika odwrotnego, powodującego znak podwójnego cudzysłowu (") `argv` .

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

|Wprowadzanie w wierszu polecenia|argvjedno|argvdwóch|argvr.3|
|-------------------------|---------------|---------------|---------------|
|`"abc" d e`|`abc`|`d`|`e`|
|`a\\b d"e f"g h`|`a\\b`|`de fg`|`h`|
|`a\\\"b c d`|`a\"b`|`c`|`d`|
|`a\\\\"b c" d e`|`a\\b c`|`d`|`e`|

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="wildcard-expansion"></a>Rozwijanie symbolu wieloznacznego

**Specyficzne dla firmy Microsoft**

Możesz użyć symboli wieloznacznych — znaku zapytania (?) i gwiazdki (*), aby określić argumenty filename i Path w wierszu polecenia.

Argumenty wiersza polecenia są obsługiwane przez procedurę o nazwie `_setargv` (lub `_wsetargv` w środowisku szerokiej char acter), która domyślnie nie rozszerza symboli wieloznacznych na oddzielne ciągi w `argv` tablicy ciągów. Aby uzyskać więcej informacji na temat włączania rozszerzania symboli wieloznacznych, zobacz [rozszerzanie symboli wieloznacznych](../c-language/expanding-wildcard-arguments.md).

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="customizing-c-command-line-processing"></a>Dostosowywanie przetwarzania w wierszu polecenia języka C++

**Specyficzne dla firmy Microsoft**

Jeśli program nie przyjmuje argumentów wiersza polecenia, można zaoszczędzić małą ilość miejsca, pomijając użycie procedury biblioteki, która wykonuje przetwarzanie wiersza polecenia. Ta procedura jest wywoływana `_setargv` i jest opisana w [rozwinięciu symboli wieloznacznych](). Aby pominąć jego użycie, zdefiniuj procedurę, która nie wykonuje żadnych operacji w pliku zawierającym `main` funkcję, i nadaj jej nazwę `_setargv` . Wywołanie `_setargv` jest następnie spełnione przez definicję `_setargv` , a wersja biblioteki nie jest załadowana.

Podobnie, jeśli nie masz dostępu do tabeli środowiska za pomocą `envp` argumentu, możesz podać własną pustą procedurę, która będzie używana zamiast `_setenvp` procedury przetwarzania środowiska. Podobnie jak w przypadku `_setargv` funkcji, `_setenvp` musi być zadeklarowana jako ** extern "C"**.

Program może wykonywać wywołania do `spawn` lub `exec` z rodziny procedur w bibliotece wykonawczej C. Jeśli tak nie jest, nie należy pomijać procedury przetwarzania środowiska, ponieważ ta procedura jest używana do przekazywania środowiska z procesu nadrzędnego do procesu podrzędnego.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Podstawowe pojęcia](../cpp/basic-concepts-cpp.md)
