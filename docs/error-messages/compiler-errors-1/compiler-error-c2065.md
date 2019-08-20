---
title: Błąd kompilatora C2065
ms.date: 08/19/2019
f1_keywords:
- C2065
helpviewer_keywords:
- C2065
ms.assetid: 78093376-acb7-45f5-9323-5ed7e0aab1dc
ms.openlocfilehash: 40d1d0744588c4b7911e84f5e57a6b40372b48cf
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630135"
---
# <a name="compiler-error-c2065"></a>Błąd kompilatora C2065

> "*Identyfikator*": niezadeklarowany identyfikator

Kompilator nie może znaleźć deklaracji identyfikatora. Istnieje wiele możliwych przyczyn tego błędu. Najczęstszymi przyczynami C2065 jest to, że identyfikator nie został zadeklarowany, identyfikator jest błędnie wpisany, nagłówek, w którym zadeklarowany jest identyfikator, nie jest uwzględniony w pliku lub w identyfikatorze brakuje kwalifikatora zakresu, na przykład `cout` zamiast `std::cout`. Aby uzyskać więcej informacji na temat C++deklaracji w, zobacz [deklaracjeC++i definicje ()](../../cpp/declarations-and-definitions-cpp.md).

Poniżej przedstawiono kilka typowych problemów i rozwiązań bardziej szczegółowych.

## <a name="the-identifier-is-undeclared"></a>Identyfikator jest niezadeklarowany

Jeśli identyfikator jest zmienną lub nazwą funkcji, należy ją zadeklarować przed użyciem. Aby można było użyć funkcji, deklaracja funkcji musi również zawierać typy parametrów. Jeśli zmienna jest zadeklarowana przy `auto`użyciu, kompilator musi mieć możliwość wywnioskowania typu z inicjatora.

Jeśli identyfikator jest składową klasy lub struktury lub jest zadeklarowany w przestrzeni nazw, musi być kwalifikowana przez nazwę klasy lub struktury lub nazwę przestrzeni nazw, gdy jest używana poza strukturą, klasą lub zakresem przestrzeni nazw. Alternatywnie, przestrzeń nazw musi zostać przeprowadzona do zakresu przez `using` dyrektywę, taką `using namespace std;`jak, lub nazwa elementu członkowskiego musi być `using` wprowadzona do zakresu przez deklarację, `using std::string;`taką jak. W przeciwnym razie Niekwalifikowana nazwa jest uznawana za niezadeklarowany identyfikator w bieżącym zakresie.

Jeśli identyfikator jest tagiem dla typu zdefiniowanego przez użytkownika, na przykład, `class` lub `struct`, typ znacznika musi być zadeklarowany, zanim będzie można go użyć. Na przykład deklaracja `struct SomeStruct { /*...*/ };` musi istnieć, aby można było zadeklarować zmienną `SomeStruct myStruct;` w kodzie.

Jeśli identyfikator jest aliasem typu, typ musi być zadeklarowany za pomocą `using` deklaracji lub `typedef` zanim będzie można go użyć. Na przykład należy zadeklarować `using my_flags = std::ios_base::fmtflags;` , aby można było użyć `my_flags` jako aliasu typu dla. `std::ios_base::fmtflags`

## <a name="example-misspelled-identifier"></a>Przykład: Błędny identyfikator

Ten błąd występuje często, gdy nazwa identyfikatora jest błędna, lub identyfikator używa nieprawidłowych wielkich liter. Nazwa w deklaracji musi być dokładnie zgodna z używaną nazwą.

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

## <a name="example-use-an-unscoped-identifier"></a>Przykład: Użyj identyfikatora nieobjętego zakresem

Ten błąd może wystąpić, jeśli identyfikator nie został prawidłowo objęty zakresem. Jeśli podczas korzystania `cout`z programu zobaczysz C2065, jest to przyczyna. Gdy C++ standardowe funkcje i operatory biblioteki nie są w pełni kwalifikowane przez przestrzeń nazw lub nie `std` przełączysz przestrzeni nazw do bieżącego `using` zakresu przy użyciu dyrektywy, kompilator nie może go znaleźć. Aby rozwiązać ten problem, należy w pełni zakwalifikować nazwy identyfikatorów lub określić przestrzeń nazw za pomocą `using` dyrektywy.

Nie można skompilować tego przykładu `cout` , `endl` ponieważ i są zdefiniowane `std` w przestrzeni nazw:

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

Identyfikatory, które są zadeklarowane `class`wewnątrz `struct`,, `enum class` lub, muszą być również kwalifikowane według nazwy zakresu otaczającego, gdy są używane poza tym zakresem.

## <a name="example-precompiled-header-isnt-first"></a>Przykład: prekompilowany nagłówek nie jest pierwszy

Ten błąd może wystąpić, jeśli przed #include prekompilowanego pliku nagłówkowego zostanie umieszczona dyrektywa preprocesora, taka jak #include, #define lub #pragma. Jeśli plik źródłowy używa prekompilowanego pliku nagłówkowego (czyli jeśli jest kompilowany przy użyciu opcji kompilatora **/Yu** ), wszystkie dyrektywy preprocesora przed prekompilowanym plikiem nagłówkowym zostaną zignorowane.

Nie można skompilować tego przykładu `cout` , `endl` ponieważ i są zdefiniowane \<w nagłówku > iostream, który jest ignorowany, ponieważ jest zawarty przed prekompilowanym plikiem nagłówkowym. Aby skompilować ten przykład, Utwórz wszystkie trzy pliki, a następnie Skompiluj stdafx. cpp, a następnie Skompiluj C2065_pch. cpp.

```cpp
// pch.h (stdafx.h in Visual Studio 2017 and earlier)
#include <stdio.h>
```

```cpp
// pch.cpp (stdafx.cpp in Visual Studio 2017 and earlier)
// Compile by using: cl /EHsc /W4 /c /Ycstdafx.h stdafx.cpp
#include "pch.h"
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

Aby rozwiązać ten problem, Dodaj #include \<iostream > do prekompilowanego pliku nagłówkowego lub przenieś go po umieszczeniu prekompilowanego pliku nagłówkowego w pliku źródłowym.

## <a name="example-missing-header-file"></a>Przykład: Brak pliku nagłówkowego

Nie dołączono pliku nagłówkowego, który deklaruje identyfikator. Upewnij się, że plik, który zawiera deklarację identyfikatora, znajduje się w każdym pliku źródłowym, który go używa.

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

Inną możliwą przyczyną jest użycie listy inicjatora bez uwzględnienia \<nagłówka > initializer_list.

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

Ten błąd może pojawić się w plikach źródłowych aplikacji klasycznych systemu Windows `VC_EXTRALEAN`, `WIN32_LEAN_AND_MEAN`jeśli zdefiniujesz, lub `WIN32_EXTRA_LEAN`. Te makra preprocesora wykluczają niektóre pliki nagłówkowe z systemów Windows. h\_i afxv W32. h, aby przyspieszyć kompilacje. Zapoznaj się z informacjami w systemach Windows. h i afxv_w32. h, aby uzyskać aktualne opisy elementów wykluczonych.

## <a name="example-missing-closing-quote"></a>Przykład: brak cudzysłowu zamykającego

Ten błąd może wystąpić, jeśli brakuje cudzysłowu zamykającego po stałej ciągu. Jest to prosty sposób odróżnienia kompilatora. Zwróć uwagę, że brak cudzysłowu zamykającego może być kilka wierszy przed zgłoszoną lokalizacją błędu.

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

## <a name="example-use-iterator-outside-for-loop-scope"></a>Przykład: Użyj iteratora na zewnątrz dla zakresu pętli

Ten błąd może wystąpić, Jeśli zadeklarujesz zmienną iteratora `for` w pętli, a następnie spróbujesz użyć tej zmiennej iteratora poza zakresem `for` pętli. Kompilator domyślnie włącza opcję kompilatora [/Zc: forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) . Aby uzyskać więcej informacji, zobacz [Obsługa iteratora debugowania](../../standard-library/debug-iterator-support.md) .

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

## <a name="example-preprocessor-removed-declaration"></a>Przykład: Deklaracja preprocesora została usunięta

Ten błąd może wystąpić, jeśli odwołujesz się do funkcji lub zmiennej, która jest w warunkowo skompilowanym kodzie, który nie jest kompilowany dla bieżącej konfiguracji. Może to również wystąpić, jeśli wywołujesz funkcję w pliku nagłówkowym, który nie jest obecnie obsługiwany w środowisku kompilacji. Jeśli pewne zmienne lub funkcje są dostępne tylko wtedy, gdy zdefiniowane jest określone makro preprocesora, upewnij się, że kod, który wywołuje te funkcje, można skompilować tylko wtedy, gdy zdefiniowane jest to samo makro preprocesora. Ten problem jest łatwo dostępny w środowisku IDE, ponieważ deklaracja funkcji jest wyszarzona, jeśli wymagane makra preprocesora nie są zdefiniowane dla bieżącej konfiguracji kompilacji.

Jest to przykładowy kod, który działa podczas kompilowania w programie Debug, ale nie do sprzedaży detalicznej:

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

## <a name="example-ccli-type-deduction-failure"></a>Przykład: C++Błąd odejmowania typu/CLI

Ten błąd może wystąpić podczas wywoływania funkcji ogólnej, jeśli nie można wywnioskować typu argumentu zamierzonego z użytych parametrów. Aby uzyskać więcej informacji, zobacz [funkcje ogólneC++(/CLI)](../../extensions/generic-functions-cpp-cli.md).

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

## <a name="example-ccli-attribute-parameters"></a>Przykład: C++/CLI — parametry atrybutów

Ten błąd może być również wygenerowany jako wynik zgodności kompilatora, który został wykonany dla programu Visual Studio 2005: sprawdzanie parametrów wizualizacji C++ .

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
