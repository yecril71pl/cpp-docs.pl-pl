---
title: Błąd kompilatora C2065
ms.date: 09/01/2017
f1_keywords:
- C2065
helpviewer_keywords:
- C2065
ms.assetid: 78093376-acb7-45f5-9323-5ed7e0aab1dc
ms.openlocfilehash: 3daf2cd532cd07225b822c80b46fc28274d4e2a8
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59779404"
---
# <a name="compiler-error-c2065"></a>Błąd kompilatora C2065

> "*identyfikator*": niezadeklarowany identyfikator

Kompilator nie może odnaleźć deklaracji dla identyfikatora. Istnieje wiele możliwych przyczyn tego błędu. Najbardziej typowe przyczyny C2065 są, identyfikator nie została zadeklarowana, identyfikator jest błędna, nagłówka, w którym zadeklarowano identyfikator nie znajduje się w pliku lub identyfikator Brak kwalifikatora zakresu, na przykład `cout` zamiast `std::cout`. Aby uzyskać więcej informacji na temat deklaracji w języku C++, zobacz [deklaracje i definicje (C++)](../../cpp/declarations-and-definitions-cpp.md).

Poniżej przedstawiono niektóre typowe problemy i rozwiązania większej liczby szczegółów.

## <a name="the-identifier-is-undeclared"></a>Identyfikator jest niezadeklarowany

Jeśli identyfikator jest zmienną lub nazwą funkcji, należy zadeklarować ją przed jego użyciem. Przed użyciem funkcji, deklarację funkcji należy również uwzględnić typy jego parametrów. Jeśli zmienna jest zadeklarowana za pomocą `auto`, kompilator musi być w stanie do wywnioskowania typu z jego inicjatora.

Jeśli identyfikator jest elementem członkowskim klasy lub struktury lub deklarowane w przestrzeni nazw, musi być kwalifikowana przez nazwę klasy lub struktury lub nazwa przestrzeni nazw, gdy jest używana poza zakresem struktury, klasy lub przestrzeni nazw. Alternatywnie przestrzeni nazw musi być włączone do zakresu przez `using` dyrektywy, takie jak `using namespace std;`, lub nazwę elementu członkowskiego muszą być dostosowane do zakresu `using` deklaracji, takich jak `using std::string;`. W przeciwnym razie niekwalifikowana nazwa jest uważany niezadeklarowany identyfikator w bieżącym zakresie.

Jeśli identyfikator tagu dla typu zdefiniowanego przez użytkownika, na przykład `class` lub `struct`, musi być zadeklarowany typ znacznika, zanim będzie można jej używać. Na przykład deklaracja `struct SomeStruct { /*...*/ };` można zadeklarować zmienną, musi istnieć `SomeStruct myStruct;` w kodzie.

Jeśli identyfikator ma alias typu, typ musi być zadeklarowany za pomocą `using` deklaracji lub `typedef` zanim będzie można jej używać. Na przykład, należy zadeklarować `using my_flags = std::ios_base::fmtflags;` przed użyciem `my_flags` jako alias typu `std::ios_base::fmtflags`.

## <a name="example-misspelled-identifier"></a>Przykład: błędnie identyfikator

Ten błąd zazwyczaj występuje, gdy nazwa identyfikatora jest błędnie wpisana lub identyfikator używa niewłaściwego wielkie i małe litery. Nazwa w deklaracji musi dokładnie odpowiadać nazwie, którego używasz.

```cpp
// C2065_spell.cpp
// compile with: cl /EHsc C2065_spell.cpp
#include <iostream>
using namespace std;
int main() {
    int someIdentifier = 42;
    cout << "Some Identifier: " << SomeIdentifier << endl;
    // C2065: 'SomeIdentifier': undeclared identifier
    // To fix, correct the spelling:
    // cout << "Some Identifier: " << someIdentifier << endl;
}
```

## <a name="example-use-an-unscoped-identifier"></a>Przykład: Użyj identyfikatora poza zakresem

Ten błąd może wystąpić, jeśli identyfikator użytkownika nie jest w poprawnym zakresie. Jeśli widzisz C2065, gdy używasz `cout`, to stanowi przyczynę. Gdy standardowej biblioteki języka C++, funkcje i operatory nie są w pełni kwalifikowany według przestrzeni nazw lub nie korzystać `std` przestrzeni nazw w bieżącym zakresie za pomocą `using` dyrektywy, kompilator nie można go znaleźć. Aby rozwiązać ten problem, należy całkowicie kwalifikowania nazwy identyfikatorów, lub Określ przestrzeń nazw o `using` dyrektywy.

W tym przykładzie nie zostanie skompilowany, ponieważ `cout` i `endl` są zdefiniowane w `std` przestrzeni nazw:

```cpp
// C2065_scope.cpp
// compile with: cl /EHsc C2065_scope.cpp
#include <iostream>
// using namespace std;   // Uncomment this line to fix

int main() {
    cout << "Hello" << endl;   // C2065 'cout': undeclared identifier
                               // C2065 'endl': undeclared identifier
    // Or try the following line instead
    std::cout << "Hello" << std::endl;
}
```

Identyfikatory, które są zadeklarowane wewnątrz `class`, `struct`, lub `enum class` typy również musi być kwalifikowana przez nazwę ich obejmującego zakresu, podczas korzystania z nich poza tym zakresem.

## <a name="example-precompiled-header-isnt-first"></a>Przykład: prekompilowanego pliku nagłówkowego nie jest pierwszym

Ten błąd może wystąpić, jeśli wszystkie dyrektywy preprocesora, takich jak #include, #define, lub #pragma, przed #include prekompilowanego pliku nagłówkowego. Jeśli plik źródłowy używa prekompilowanego pliku nagłówkowego (to znaczy, jeśli jest kompilowany przy użyciu **/Yu** — opcja kompilatora), a następnie wszystkie dyrektywy preprocesora przed prekompilowanego pliku nagłówkowego, są ignorowane.

W tym przykładzie nie zostanie skompilowany, ponieważ `cout` i `endl` są zdefiniowane w \<iostream > nagłówka, który jest ignorowana, ponieważ znajduje się przed prekompilowanego pliku nagłówkowego. Skompilować ten przykład, utworzyć wszystkie trzy pliki, a następnie skompilować stdafx.cpp, a następnie skompilować C2065_pch.cpp.

```cpp
// stdafx.h
#include <stdio.h>
```

```cpp
// stdafx.cpp
// Compile by using: cl /EHsc /W4 /c /Ycstdafx.h stdafx.cpp
#include <stdafx.h>
```

```cpp
// C2065_pch.cpp
// compile with: cl /EHsc /W4 /Yustdafx.h C2065_pch.cpp
#include <iostream>
#include "stdafx.h"
using namespace std;

int main() {
    cout << "Hello" << endl;   // C2065 'cout': undeclared identifier
                               // C2065 'endl': undeclared identifier
}
```

Aby rozwiązać ten problem, Dodaj #include \<iostream > do wstępnie skompilowanego pliku nagłówkowego lub przenieś je po prekompilowanego pliku nagłówkowego znajduje się w pliku źródłowym.

## <a name="example-missing-header-file"></a>Przykład: Brak nagłówka pliku

Plik nagłówkowy, która deklaruje identyfikator nie zostały uwzględnione. Upewnij się, że plik, który zawiera deklarację identyfikatora znajduje się w każdy plik źródłowy, który korzysta z niego.

```cpp
// C2065_header.cpp
// compile with: cl /EHsc C2065_header.cpp

//#include <stdio.h>
int main() {
    fpos_t file_position = 42; // C2065: 'fpos_t': undeclared identifier
    // To fix, uncomment the #include <stdio.h> line
    // to include the header where fpos_t is defined
}
```

Inną możliwą przyczyną jest użycie listy inicjalizatora bez uwzględniania \<initializer_list > nagłówka.

```cpp
// C2065_initializer.cpp
// compile with: cl /EHsc C2065_initializer.cpp

// #include <initializer_list>
int main() {
    for (auto strList : {"hello", "world"})
        if (strList == "hello") // C2065: 'strList': undeclared identifier
            return 1;
    // To fix, uncomment the #include <initializer_list> line
}
```

Może zostać wyświetlony ten błąd w plikach źródłowych aplikację pulpitu Windows, jeśli zdefiniujesz `VC_EXTRALEAN`, `WIN32_LEAN_AND_MEAN`, lub `WIN32_EXTRA_LEAN`. Te makra preprocesora wykluczyć pliki nagłówkowe z windows.h i afxv\_kompiluje w32.h szybkość działania. Poszukaj w windows.h i afxv_w32.h aktualne opis co to jest wykluczona.

## <a name="example-missing-closing-quote"></a>Przykład: Brak cudzysłowu zamykającego

Ten błąd może wystąpić, jeśli brakuje zamykającego po stałą typu string. Jest to prosty sposób mylić kompilator. Należy zauważyć, że brak cudzysłowu zamykającego może być kilka wierszy przed lokalizacja zgłoszonego błędu.

```cpp
// C2065_quote.cpp
// compile with: cl /EHsc C2065_quote.cpp
#include <iostream>

int main() {
    // Fix this issue by adding the closing quote to "Aaaa"
    char * first = "Aaaa, * last = "Zeee";
    std::cout << "Name: " << first
        << " " << last << std::endl; // C2065: 'last': undeclared identifier
}
```

## <a name="example-use-iterator-outside-for-loop-scope"></a>Przykład: Użyj iteratora poza w zakresie pętli for

Ten błąd może wystąpić, jeśli zadeklarujesz zmienną iteratora w `for` pętli, a następnie spróbuj użyć tej zmiennej iteratora poza zakresem `for` pętli. Umożliwia kompilatorowi [/Zc: forscope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) — opcja kompilatora domyślnie. Zobacz [Debug Iterator Support](../../standard-library/debug-iterator-support.md) Aby uzyskać więcej informacji.

```cpp
// C2065_iter.cpp
// compile with: cl /EHsc C2065_iter.cpp
#include <iostream>
#include <string>

int main() {
    // char last = '!';
    std::string letters{ "ABCDEFGHIJKLMNOPQRSTUVWXYZ" };
    for (const char& c : letters) {
        if ('Q' == c) {
            std::cout << "Found Q!" << std::endl;
        }
        // last = c;
    }
    std::cout << "Last letter was " << c << std::endl; // C2065
    // Fix by using a variable declared in an outer scope.
    // Uncomment the lines that declare and use 'last' for an example.
    // std::cout << "Last letter was " << last << std::endl; // C2065
}
```

## <a name="example-preprocessor-removed-declaration"></a>Przykład: preprocesora usunięto deklaracji

Ten błąd może wystąpić, jeśli odwołujesz się do funkcji lub zmienna, która warunkowo skompilowany kod, który nie jest kompilowany dla bieżącej konfiguracji. Może to także wystąpić, jeśli wywołasz funkcję w pliku nagłówkowym, który nie jest obecnie obsługiwane w środowisku kompilacji. W przypadku niektórych zmiennych lub funkcje są dostępne tylko, gdy zdefiniowano określonego makro preprocesora, upewnij się, że kod, który wywołuje te funkcje może być kompilowane, gdy definiowany jest tym samym makro preprocesora. Ten problem jest ułatwiają w IDE, ponieważ deklaracja funkcji jest nieaktywny, jeśli nie zdefiniowano wymaganego makra preprocesora dla bieżącej konfiguracji kompilacji.

To jest przykładowy kod, który działa w przypadku, gdy kompilacji podczas debugowania, ale nie w sieci sprzedaży:

```cpp
// C2065_defined.cpp
// Compile with: cl /EHsc /W4 /MT C2065_defined.cpp
#include <iostream>
#include <crtdbg.h>
#ifdef _DEBUG
    _CrtMemState oldstate;
#endif
int main() {
    _CrtMemDumpStatistics(&oldstate);
    std::cout << "Total count " << oldstate.lTotalCount; // C2065
    // Fix by guarding references the same way as the declaration:
    // #ifdef _DEBUG
    //    std::cout << "Total count " << oldstate.lTotalCount;
    // #endif
}
```

## <a name="example-ccli-type-deduction-failure"></a>Przykład: C++/ Błąd wnioskowanie typów interfejsu wiersza polecenia

Ten błąd może wystąpić podczas wywoływania funkcji ogólne, jeśli argument zamierzony typu nie można wywnioskować z parametrów użytych. Aby uzyskać więcej informacji, zobacz [funkcje ogólne (C++sposób niezamierzony)](../../extensions/generic-functions-cpp-cli.md).

```cpp
// C2065_b.cpp
// compile with: cl /clr C2065_b.cpp
generic <typename ItemType>
void G(int i) {}

int main() {
   // global generic function call
   G<T>(10);     // C2065
   G<int>(10);   // OK - fix with a specific type argument
}
```

## <a name="example-ccli-attribute-parameters"></a>Przykład: C++/ Interfejs wiersza polecenia parametry atrybutów

Ten błąd może być też wygenerowany w wyniku pracy zgodności kompilatora, która została wykonana dla programu Visual C++ 2005: Sprawdzanie parametrów dla atrybutów języka Visual C++.

```cpp
// C2065_attributes.cpp
// compile with: cl /c /clr C2065_attributes.cpp
[module(DLL, name=MyLibrary)];   // C2065
// try the following line instead
// [module(dll, name="MyLibrary")];

[export]
struct MyStruct {
   int i;
};
```
