---
title: :::no-loc(main):::argumenty funkcji i wiersza polecenia (C++)
description: :::no-loc(main):::Funkcja jest punktem wejścia dla programu C++.
ms.date: 01/15/2019
ms.assetid: c6568ee6-40ab-4ae8-aa44-c99e232f64ac
no-loc:
- ':::no-loc(main):::'
- ':::no-loc(wmain):::'
- ':::no-loc(inline):::'
- ':::no-loc(static):::'
- ':::no-loc(_tmain):::'
- ':::no-loc(void):::'
- ':::no-loc(exit):::'
- ':::no-loc(argc):::'
- ':::no-loc(argv):::'
- ':::no-loc(envp):::'
- ':::no-loc(CreateProcess):::'
- ':::no-loc(GetModuleFileName):::'
- ':::no-loc(char):::'
- ':::no-loc(wchar_t):::'
- ':::no-loc(extern):::'
ms.openlocfilehash: 9fe7c7a0808584a70bffa541903866b3de364e5f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213323"
---
# <a name="no-locmain-function-and-command-line-arguments"></a>:::no-loc(main):::argumenty funkcji i wiersza polecenia

Wszystkie programy C++ muszą mieć `:::no-loc(main):::` funkcję. Jeśli spróbujesz skompilować projekt C++ *. exe* bez :::no-loc(main)::: funkcji, kompilator zgłosi błąd. (Biblioteki i biblioteki dołączane dynamicznie :::no-loc(static)::: nie mają `:::no-loc(main):::` funkcji). `:::no-loc(main):::`Funkcja jest, gdzie kod źródłowy rozpoczyna wykonywanie, ale zanim program przejdzie do `:::no-loc(main):::` funkcji, wszystkie :::no-loc(static)::: elementy członkowskie klasy bez jawnych inicjatorów mają ustawioną wartość zero. W programie Microsoft C++ :::no-loc(static)::: obiekty globalne są również inicjowane przed wpisem do `:::no-loc(main):::` . Kilka ograniczeń ma zastosowanie do `:::no-loc(main):::` funkcji, która nie dotyczy żadnych innych funkcji języka C++. `:::no-loc(main):::`Funkcja:

- Nie może być przeciążony (zobacz [przeciążanie funkcji](function-overloading.md)).
- Nie można zadeklarować jako **`:::no-loc(inline):::`** .
- Nie można zadeklarować jako **`:::no-loc(static):::`** .
- Nie można pobrać adresu.
- Nie można wywołać.

:::no-loc(main):::Funkcja nie ma deklaracji, ponieważ jest wbudowana w język. Jeśli tak, Składnia deklaracji dla `:::no-loc(main):::` będzie wyglądać następująco:

```cpp
int :::no-loc(main):::();
int :::no-loc(main):::(int :::no-loc(argc):::, :::no-loc(char)::: *:::no-loc(argv):::[], :::no-loc(char)::: *:::no-loc(envp):::[]);
```

**Specyficzne dla firmy Microsoft**

Jeśli pliki źródłowe używają acters Unicode :::no-loc(char)::: , można użyć programu `:::no-loc(wmain):::` , który jest w wersji szerokiej :::no-loc(char)::: acter `:::no-loc(main):::` . Składnia deklaracji dla `:::no-loc(wmain):::` jest następująca:

```cpp
int :::no-loc(wmain):::( );
int :::no-loc(wmain):::(int :::no-loc(argc):::, :::no-loc(wchar_t)::: *:::no-loc(argv):::[], :::no-loc(wchar_t)::: *:::no-loc(envp):::[]);
```

Można również użyć `:::no-loc(_tmain):::` , który jest zdefiniowany w t :::no-loc(char)::: . h. `:::no-loc(_tmain):::`jest rozpoznawana do, `:::no-loc(main):::` chyba że _UNICODE jest zdefiniowany. W takim przypadku jest `:::no-loc(_tmain):::` rozpoznawany jako `:::no-loc(wmain):::` .

Jeśli nie określono wartości zwracanej, kompilator dostarcza wartość zwracaną zero. Alternatywnie, `:::no-loc(main):::` funkcje i `:::no-loc(wmain):::` mogą być zadeklarowane jako Return **`:::no-loc(void):::`** (brak wartości zwracanej). Jeśli deklarujesz `:::no-loc(main):::` lub `:::no-loc(wmain):::` jako Return **`:::no-loc(void):::`** , nie można zwrócić :::no-loc(exit)::: kodu do procesu nadrzędnego lub systemu operacyjnego za pomocą instrukcji [Return](../cpp/return-statement-in-program-termination-cpp.md) . Aby zwrócić :::no-loc(exit)::: kod, gdy `:::no-loc(main):::` lub `:::no-loc(wmain):::` jest zadeklarowany jako **`:::no-loc(void):::`** , należy użyć [:::no-loc(exit):::](../cpp/:::no-loc(exit):::-function.md) funkcji.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="command-line-arguments"></a>Argumenty wiersza polecenia

Argumenty dla `:::no-loc(main):::` lub `:::no-loc(wmain):::` umożliwiają wygodne analizowanie wierszy poleceń argumentów i, opcjonalnie, dostęp do zmiennych środowiskowych. Typy dla `:::no-loc(argc):::` i `:::no-loc(argv):::` są zdefiniowane przez język. Nazwy `:::no-loc(argc):::` , `:::no-loc(argv):::` i `:::no-loc(envp):::` są tradycyjnie, ale możesz je nazwać w dowolny sposób.

```cpp
int :::no-loc(main):::( int :::no-loc(argc):::, :::no-loc(char):::* :::no-loc(argv):::[], :::no-loc(char):::* :::no-loc(envp):::[]);
int :::no-loc(wmain):::( int :::no-loc(argc):::, :::no-loc(wchar_t):::* :::no-loc(argv):::[], :::no-loc(wchar_t):::* :::no-loc(envp):::[]);
```

Definicje argumentów są następujące:

*:::no-loc(argc):::*<br/>
Liczba całkowita, która zawiera liczbę argumentów, które są następujące po elemencie *:::no-loc(argv):::* . *:::no-loc(argc):::* Parametr jest zawsze większy lub równy 1.

*:::no-loc(argv):::*<br/>
Tablica ciągów zakończonych znakiem null, która reprezentuje argumenty wiersza polecenia wprowadzone przez użytkownika programu. Według Konwencji `:::no-loc(argv):::[0]` jest poleceniem, z którym wywoływany jest program, `:::no-loc(argv):::[1]` jest pierwszym argumentem wiersza polecenia i tak dalej, do `:::no-loc(argv):::[:::no-loc(argc):::]` , który jest zawsze równy null. Zobacz [Dostosowywanie przetwarzania wiersza polecenia](../cpp/customizing-cpp-command-line-processing.md) , aby uzyskać informacje dotyczące pomijania przetwarzania w wierszu polecenia.

Pierwszy argument wiersza polecenia jest zawsze `:::no-loc(argv):::[1]` i ostatnim z nich jest `:::no-loc(argv):::[:::no-loc(argc)::: - 1]` .

> [!NOTE]
> Według Konwencji `:::no-loc(argv):::[0]` jest poleceniem, z którym wywoływany jest program. Istnieje jednak możliwość duplikowania procesu przy użyciu [:::no-loc(CreateProcess):::](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) i, jeśli używasz zarówno pierwszego, jak i drugiego argumentu (*LpApplicationName* i *lpCommandLine*), `:::no-loc(argv):::[0]` nie może być nazwą pliku wykonywalnego; Użyj [:::no-loc(GetModuleFileName):::](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) , aby pobrać nazwę pliku wykonywalnego i jego w pełni kwalifikowaną ścieżkę.

**Specyficzne dla firmy Microsoft**

*:::no-loc(envp):::*<br/>
*:::no-loc(envp):::* Tablica, która jest typowym rozszerzeniem w wielu systemach UNIX, jest używana w programie Microsoft C++. Jest to tablica ciągów reprezentujących zestaw zmiennych w środowisku użytkownika. Ta tablica została zakończona przez wpis o wartości NULL. Może być zadeklarowany jako tablica wskaźników do **`:::no-loc(char):::`** ( `:::no-loc(char)::: *:::no-loc(envp):::[]` ) lub jako wskaźnik do wskaźników **`:::no-loc(char):::`** ( `:::no-loc(char)::: **:::no-loc(envp):::` ). Jeśli program używa `:::no-loc(wmain):::` zamiast tego `:::no-loc(main):::` , użyj **`:::no-loc(wchar_t):::`** typu danych zamiast **`:::no-loc(char):::`** . Blok środowiska przeszedł do `:::no-loc(main):::` i `:::no-loc(wmain):::` jest "zamrożoną" kopią bieżącego środowiska. Jeśli później zmienisz środowisko za pośrednictwem wywołania do `putenv` lub `_wputenv` , bieżące środowisko (zwracane przez `getenv` lub `_wgetenv` i `_environ` lub `_wenviron` zmienna) ulegnie zmianie, ale blok wskazywany przez :::no-loc(envp)::: nie zmieni się. Zobacz [Dostosowywanie przetwarzania wiersza polecenia](../cpp/customizing-cpp-command-line-processing.md) , aby uzyskać informacje dotyczące pomijania przetwarzania środowiska. Ten argument jest zgodny ze standardem ANSI w języku C, ale nie w języku C++.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

### <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać *:::no-loc(argc):::* *:::no-loc(argv):::* argumentów, i *:::no-loc(envp):::* do `:::no-loc(main):::` :

```cpp
// argument_definitions.cpp
// compile with: /EHsc
#include <iostream>
#include <string.h>

using namespace std;
int :::no-loc(main):::( int :::no-loc(argc):::, :::no-loc(char)::: *:::no-loc(argv):::[], :::no-loc(char)::: *:::no-loc(envp):::[] ) {
    int iNumberLines = 0;    // Default is no line numbers.

    // If /n is passed to the .exe, display numbered listing
    // of environment variables.

    if ( (:::no-loc(argc)::: == 2) && _stricmp( :::no-loc(argv):::[1], "/n" ) == 0 )
         iNumberLines = 1;

    // Walk through list of strings until a NULL is encountered.
    for( int i = 0; :::no-loc(envp):::[i] != NULL; ++i ) {
        if( iNumberLines )
            cout << i << ": " << :::no-loc(envp):::[i] << "\n";
    }
}
```

## <a name="parsing-c-command-line-arguments"></a>Analizowanie argumentów wiersza polecenia języka C++

**Specyficzne dla firmy Microsoft**

Kod uruchamiania Microsoft C/C++ używa następujących reguł podczas interpretacji argumentów podanych w wierszu polecenia systemu operacyjnego:

- Argumenty są rozdzielane znakami odstępu, który jest spacją lub tabulatorem.

- Acter karetki :::no-loc(char)::: (^) nie jest rozpoznawany jako acter ucieczki :::no-loc(char)::: lub ogranicznika. :::no-loc(char):::Acter jest obsługiwany całkowicie przez analizator wiersza polecenia w systemie operacyjnym przed przekazaniem do `:::no-loc(argv):::` tablicy w programie.

- Ciąg ujęty w znaki podwójnego cudzysłowu ("*String*") jest interpretowany jako pojedynczy argument, bez względu na biały znak zawarty w. Ciąg w cudzysłowie może być osadzony w argumencie.

- Podwójny cudzysłów poprzedzony ukośnikiem odwrotnym ( \\ ") jest interpretowany jako literał podwójnego znaku cudzysłowu :::no-loc(char)::: acter (").

- Ukośniki odwrotne są interpretowane dosłownie, chyba że od razu poprzedzają podwójny cudzysłów.

- Jeśli parzysta liczba kresek ułamkowych jest poprzedzona znakiem podwójnego cudzysłowu, jeden ukośnik odwrotny jest umieszczany w `:::no-loc(argv):::` tablicy dla każdej pary ukośników odwrotnych, a podwójny cudzysłów jest interpretowany jako ogranicznik ciągu.

- Jeśli po parzystej liczbie ukośników odwrotnych następuje znak podwójnego cudzysłowu, jeden ukośnik odwrotny jest umieszczany w `:::no-loc(argv):::` tablicy dla każdej pary ukośników odwrotnych, a podwójne cudzysłowy to "ucieczkd" przez przekroczenie :::no-loc(main)::: ukośnika odwrotnego, powodującego znak podwójnego cudzysłowu (") `:::no-loc(argv):::` .

### <a name="example"></a>Przykład

Następujący program ilustruje sposób przekazywania argumentów wiersza polecenia:

```cpp
// command_line_arguments.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
int :::no-loc(main):::( int :::no-loc(argc):::,      // Number of strings in array :::no-loc(argv):::
          :::no-loc(char)::: *:::no-loc(argv):::[],   // Array of command-line argument strings
          :::no-loc(char)::: *:::no-loc(envp):::[] )  // Array of environment variable strings
{
    int count;

    // Display each command-line argument.
    cout << "\nCommand-line arguments:\n";
    for( count = 0; count < :::no-loc(argc):::; count++ )
         cout << "  :::no-loc(argv):::[" << count << "]   "
                << :::no-loc(argv):::[count] << "\n";
}
```

W poniższej tabeli przedstawiono przykładowe dane wejściowe i oczekiwane dane wyjściowe, ukazując reguły z powyższej listy.

### <a name="results-of-parsing-command-lines"></a>Wyniki analizy wierszy poleceń

|Wprowadzanie w wierszu polecenia|:::no-loc(argv):::jedno|:::no-loc(argv):::dwóch|:::no-loc(argv):::r.3|
|-------------------------|---------------|---------------|---------------|
|`"abc" d e`|`abc`|`d`|`e`|
|`a\\b d"e f"g h`|`a\\b`|`de fg`|`h`|
|`a\\\"b c d`|`a\"b`|`c`|`d`|
|`a\\\\"b c" d e`|`a\\b c`|`d`|`e`|

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="wildcard-expansion"></a>Rozwijanie symbolu wieloznacznego

**Specyficzne dla firmy Microsoft**

Możesz użyć symboli wieloznacznych — znaku zapytania (?) i gwiazdki (*), aby określić argumenty filename i Path w wierszu polecenia.

Argumenty wiersza polecenia są obsługiwane przez procedurę o nazwie `_set:::no-loc(argv):::` (lub `_wset:::no-loc(argv):::` w środowisku szerokiej :::no-loc(char)::: acter), która domyślnie nie rozszerza symboli wieloznacznych na oddzielne ciągi w `:::no-loc(argv):::` tablicy ciągów. Aby uzyskać więcej informacji na temat włączania rozszerzania symboli wieloznacznych, zobacz [rozszerzanie symboli wieloznacznych](../c-language/expanding-wildcard-arguments.md).

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="customizing-c-command-line-processing"></a>Dostosowywanie przetwarzania w wierszu polecenia języka C++

**Specyficzne dla firmy Microsoft**

Jeśli program nie przyjmuje argumentów wiersza polecenia, można zaoszczędzić małą ilość miejsca, pomijając użycie procedury biblioteki, która wykonuje przetwarzanie wiersza polecenia. Ta procedura jest wywoływana `_set:::no-loc(argv):::` i jest opisana w [rozwinięciu symboli wieloznacznych](../cpp/wildcard-expansion.md). Aby pominąć jego użycie, zdefiniuj procedurę, która nie wykonuje żadnych operacji w pliku zawierającym `:::no-loc(main):::` funkcję, i nadaj jej nazwę `_set:::no-loc(argv):::` . Wywołanie `_set:::no-loc(argv):::` jest następnie spełnione przez definicję `_set:::no-loc(argv):::` , a wersja biblioteki nie jest załadowana.

Podobnie, jeśli nie masz dostępu do tabeli środowiska za pomocą `:::no-loc(envp):::` argumentu, możesz podać własną pustą procedurę, która będzie używana zamiast `_set:::no-loc(envp):::` procedury przetwarzania środowiska. Podobnie jak w przypadku `_set:::no-loc(argv):::` funkcji, `_set:::no-loc(envp):::` musi być zadeklarowana jako ** :::no-loc(extern)::: "C"**.

Program może wykonywać wywołania do `spawn` lub `exec` z rodziny procedur w bibliotece wykonawczej C. Jeśli tak nie jest, nie należy pomijać procedury przetwarzania środowiska, ponieważ ta procedura jest używana do przekazywania środowiska z procesu nadrzędnego do procesu podrzędnego.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Podstawowe pojęcia](../cpp/basic-concepts-cpp.md)
