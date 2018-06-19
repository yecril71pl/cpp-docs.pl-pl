---
title: C2065 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/01/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2065
dev_langs:
- C++
helpviewer_keywords:
- C2065
ms.assetid: 78093376-acb7-45f5-9323-5ed7e0aab1dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5e67fcac9593dc4ad11dbff0cc479ac24d624110
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33172793"
---
# <a name="compiler-error-c2065"></a>C2065 błąd kompilatora

> "*identyfikator*": niezadeklarowanego identyfikatora

Kompilator nie można odnaleźć deklaracji dla identyfikatora. Istnieje wiele możliwych przyczyn tego błędu. Najczęstszymi przyczynami C2065 są czy identyfikator nie została zadeklarowana, identyfikator jest błędna, nagłówek, w którym jest zadeklarowany jako identyfikator nie znajduje się w pliku lub identyfikator brakuje kwalifikator zakresu, na przykład `cout` zamiast `std::cout`. Aby uzyskać więcej informacji na deklaracje języka C++, zobacz [deklaracje i definicje (C++)](../../cpp/declarations-and-definitions-cpp.md).

Poniżej przedstawiono niektóre typowe problemy i rozwiązania większej liczby szczegółów.

## <a name="the-identifier-is-undeclared"></a>Identyfikator jest niezadeklarowany

Jeśli identyfikator jest zmienną lub nazwę funkcji, należy zadeklarować zanim będzie można go używać. Przed użyciem funkcji, deklaracji funkcji musi także obejmować typy parametrów. Jeśli zmienna została zadeklarowana przy użyciu `auto`, kompilator musi mieć możliwość wnioskować o typie z jego inicjatora.

Jeśli identyfikator jest elementem członkowskim klasy lub struktury lub zadeklarowana w przestrzeni nazw, musi być kwalifikowana przez nazwę klasy lub struktury, lub nazwę przestrzeni nazw stosowania poza zakresem struktury, klasa lub obszaru nazw. Alternatywnie przestrzeni nazw musi być wejścia zakresu `using` dyrektywy takich jak `using namespace std;`, lub nazwę elementu członkowskiego musi być dostosowane do zakresu `using` deklaracji, takich jak `using std::string;`. W przeciwnym razie niekwalifikowana nazwa jest uważany za niezadeklarowanego identyfikatora w bieżącym zakresie.

Jeśli na przykład identyfikator tagu dla typu zdefiniowane przez użytkownika jest `class` lub `struct`, musi być zadeklarowany typ znacznika, zanim będzie można go używać. Na przykład deklaracja `struct SomeStruct { /*...*/ };` muszą istnieć przed można zadeklarować zmiennej `SomeStruct myStruct;` w kodzie.

Aby identyfikator jest alias typu, typ musi być zadeklarowana jako przy użyciu `using` deklaracji lub `typedef` zanim będzie można go używać. Na przykład należy zadeklarować `using my_flags = std::ios_base::fmtflags;` przed użyciem `my_flags` jako alias typu dla `std::ios_base::fmtflags`.

## <a name="example-misspelled-identifier"></a>Przykład: identyfikator błędnie

Ten błąd występuje zazwyczaj, gdy jest błędna nazwa identyfikatora lub identyfikator używa niewłaściwego wielkie i małe litery. Nazwa w deklaracji musi dokładnie odpowiadać nazwy, którego używasz.

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

## <a name="example-use-an-unscoped-identifier"></a>Przykład: Użyj identyfikatora niewystępującego w zakresie

Ten błąd może wystąpić, jeśli identyfikator użytkownika nie jest poprawnie objęty zakresem. Jeśli widzisz C2065, korzystając z `cout`, jest to przyczyną. Jeśli funkcje standardowej biblioteki C++ i operatory są nie w pełni kwalifikowana według przestrzeni nazw lub nie zostały wprowadzone `std` przestrzeni nazw w bieżącym zakresie za pomocą `using` dyrektywy, kompilator nie są one dostępne. Aby rozwiązać ten problem, należy całkowicie zakwalifikować nazwy identyfikatora, lub Określ obszar nazw o `using` dyrektywy.

W tym przykładzie nie powiedzie się skompilować, ponieważ `cout` i `endl` są zdefiniowane w `std` przestrzeni nazw:

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

Identyfikatory, które są zadeklarowane wewnątrz `class`, `struct`, lub `enum class` typy również musi być kwalifikowana przez nazwę ich otaczającym zakresie używania poza tym zakresem.

## <a name="example-precompiled-header-isnt-first"></a>Przykład: prekompilowanego nagłówka nie jest pierwszym

Ten błąd może wystąpić, jeśli wszystkie dyrektywy preprocesora, takie jak #include, #define, lub #pragma, przed #include prekompilowanego pliku nagłówkowego. Jeśli plik źródłowy używa prekompilowanego pliku nagłówkowego (to znaczy, jeśli ma być kompilowana przy użyciu **/Yu** — opcja kompilatora), a następnie wszystkie dyrektywy preprocesora przed prekompilowanego pliku nagłówkowego są ignorowane.

W tym przykładzie nie powiedzie się skompilować, ponieważ `cout` i `endl` są zdefiniowane w \<iostream > Nagłówek, który jest ignorowany, ponieważ znajduje się przed prekompilowanego pliku nagłówkowego. Do tworzenia w tym przykładzie, Utwórz wszystkie trzy pliki, a następnie skompilować stdafx.cpp, a następnie skompilować C2065_pch.cpp.

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

Aby rozwiązać ten problem, Dodaj #include \<iostream > do prekompilowany plik nagłówka, lub przenieś je po prekompilowanego pliku nagłówkowego znajduje się w pliku źródłowego.

## <a name="example-missing-header-file"></a>Przykład: Brak pliku nagłówka

Plik nagłówka, który deklaruje identyfikator nie zostały uwzględnione. Upewnij się, że plik, który zawiera deklarację identyfikatora znajduje się w każdym pliku źródłowego, który korzysta z niego.

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

Inną przyczyną może być użycie listy inicjatorów bez uwzględniania \<initializer_list > nagłówka.

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

W przypadku definiowania może zostać wyświetlony ten błąd w plikach źródłowych aplikacji Windows Desktop `VC_EXTRALEAN`, `WIN32_LEAN_AND_MEAN`, lub `WIN32_EXTRA_LEAN`. Makro preprocesora wykluczyć pewne pliki nagłówka z windows.h i afxv\_kompiluje w32.h szybkość działania. Szukaj w windows.h i afxv_w32.h aktualne opis co to jest wyłączone.

## <a name="example-missing-closing-quote"></a>Przykład: Brak zamykającego cudzysłowu

Ten błąd może wystąpić, jeśli brakuje zamykającego cudzysłowu po stałą typu string. Jest to prosty sposób należy mylić kompilatora. Należy pamiętać, że brakuje cudzysłowu zamykającego może zostać kilka wierszy przed lokalizacja zgłoszonego błędu. 

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

Ten błąd może wystąpić, jeśli zadeklarować zmiennej iteracyjnej w `for` pętli, a następnie spróbuj użyć tej zmiennej iteratora poza zakresem `for` pętli. Włącza kompilator [/Zc: forscope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) — opcja kompilatora domyślnie. Zobacz [Obsługa iteratora debugowania](../../standard-library/debug-iterator-support.md) Aby uzyskać więcej informacji.

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

## <a name="example-preprocessor-removed-declaration"></a>Przykład: preprocesora usuniętych deklaracji

Ten błąd może wystąpić, jeśli można odwoływać się do funkcji lub zmienna, która jest warunkowo skompilowany kod, który nie jest skompilowany dla bieżącej konfiguracji. Może to także wystąpić, jeśli wywołujesz funkcję w nagłówku pliku, który nie jest obecnie obsługiwane w środowisku kompilacji. Jeśli określonych zmiennych lub funkcje są dostępne tylko, gdy zdefiniowano określonego makro preprocesora, upewnij się, że kod, który wywołuje funkcje mogą być kompilowane tylko, gdy definiowany jest tym samym makro preprocesora. Tego problemu jest ułatwiają w IDE, ponieważ deklaracja funkcji jest nieaktywna, jeśli nie zdefiniowano wymaganego makra preprocesora w bieżącej konfiguracji kompilacji.

To jest przykład kodu, który działa w przypadku, gdy kompilacji podczas debugowania, ale nie sprzedaży detalicznej:

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

## <a name="example-ccli-type-deduction-failure"></a>Przykład: C + +/ błąd wnioskowanie typów interfejsu wiersza polecenia

Ten błąd może wystąpić podczas wywoływania funkcji ogólne, jeśli argument danego typu nie można wywnioskować z parametrów używana. Aby uzyskać więcej informacji, zobacz [funkcje ogólne (C + +/ CLI)](../../windows/generic-functions-cpp-cli.md).

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

## <a name="example-ccli-attribute-parameters"></a>Przykład: C + +/ CLI parametrów atrybutu

Ten błąd może być również generowany w wyniku pracy zgodność kompilatora, która została wykonana dla Visual C++ 2005: parametr sprawdzanie dla atrybutów języka Visual C++.

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
