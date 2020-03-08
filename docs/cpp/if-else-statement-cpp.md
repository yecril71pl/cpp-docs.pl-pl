---
title: if-else — instrukcja (C++)
ms.date: 07/20/2019
description: Użyj instrukcji if-else w C++ programie w celu kontrolowania warunkowego rozgałęzienia.
f1_keywords:
- else_cpp
- if_cpp
helpviewer_keywords:
- if keyword [C++]
- else keyword [C++]
ms.assetid: f8c45cde-6bce-42ae-81db-426b3dbd4caa
ms.openlocfilehash: 0e9de2d39e09e148c7e4f3ea82c3dadb173c2d0c
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78884165"
---
# <a name="if-else-statement-c"></a>if-else — instrukcja (C++)

Kontroluje rozgałęzienie warunkowe. Instrukcje w *bloku if-Block* są wykonywane tylko wtedy, gdy *wyrażenie IF* zwraca wartość różną od zera (lub true). Jeśli wartość *wyrażenia* jest różna od zera, *instrukcja1* i wszystkie inne instrukcje w bloku są wykonywane i blok else, jeśli jest obecny, jest pomijany. Jeśli wartość *wyrażenia* jest równa zero, wówczas blok IF jest pomijany i jest wykonywany blok else, jeśli jest obecny. Wyrażenia, które mają wartość różną od zera, są

- TRUE
- wskaźnik o wartości innej niż null,
- dowolna wartość arytmetyczna niezerowa lub
- Typ klasy, który definiuje niejednoznaczną konwersję na typ arytmetyczny, Boolean lub typu wskaźnika. (Aby uzyskać informacje na temat konwersji, zobacz [Konwersje standardowe](../cpp/standard-conversions.md)).

## <a name="syntax"></a>Składnia

```cpp
if ( expression )
{
   statement1;
   ...
}
else  // optional
{
   statement2;
   ...
}

// C++17 - Visual Studio 2017 version 15.3 and later:
if ( initialization; expression )
{
   statement1;
   ...
}
else  // optional
{
   statement2;
   ...
}

// C++17 - Visual Studio 2017 version 15.3 and later:
if constexpr (expression)
{
    statement1;
    ...
}
else  // optional
{
   statement2;
   ...
}
```

## <a name="example"></a>Przykład

```cpp
// if_else_statement.cpp
#include <iostream>

using namespace std;

class C
{
    public:
    void do_something(){}
};
void init(C){}
bool is_true() { return true; }
int x = 10;

int main()
{
    if (is_true())
    {
        cout << "b is true!\n";  // executed
    }
    else
    {
        cout << "b is false!\n";
    }

    // no else statement
    if (x == 10)
    {
        x = 0;
    }

    C* c;
    init(c);
    if (c)
    {
        c->do_something();
    }
    else
    {
        cout << "c is null!\n";
    }
}
```

## <a name="if_with_init"></a>Instrukcja if z inicjatorem

**Visual Studio 2017 w wersji 15,3 lub nowszej** (dostępny w [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)): instrukcja **if** może również zawierać wyrażenie, które deklaruje i inicjuje nazwaną zmienną. Użyj tej postaci instrukcji if-Statement, gdy zmienna jest wymagana tylko w zakresie bloku if.

## <a name="example"></a>Przykład

```cpp
#include <iostream>
#include <mutex>
#include <map>
#include <string>
#include <algorithm>

using namespace std;

map<int, string> m;
mutex mx;
bool shared_flag; // guarded by mx
void unsafe_operation() {}

int main()
{

    if (auto it = m.find(10); it != m.end())
    {
        cout << it->second;
        return 0;
    }

    if (char buf[10]; fgets(buf, 10, stdin))
    {
        m[0] += buf;
    }

    if (lock_guard<mutex> lock(mx); shared_flag)
    {
        unsafe_operation();
        shared_flag = false;
    }

    string s{ "if" };
    if (auto keywords = { "if", "for", "while" }; any_of(keywords.begin(), keywords.end(), [&s](const char* kw) { return s == kw; }))
    {
        cout << "Error! Token must not be a keyword\n";
    }
}
```

We wszystkich formach instrukcji **if** , *wyrażenie*, które może mieć dowolną wartość z wyjątkiem struktury, jest oceniane, łącznie ze wszystkimi efektami ubocznymi. Kontrolka jest przekazywana z instrukcji **if** do następnej instrukcji w programie, chyba że jedna z *instrukcji*s zawiera [Break](../cpp/break-statement-cpp.md), [Continue](../cpp/continue-statement-cpp.md)lub [goto](../cpp/goto-statement-cpp.md).

Klauzula **else** instrukcji `if...else` jest skojarzona z najbliższą poprzednią instrukcją **if** w tym samym zakresie, który nie ma odpowiedniej instrukcji **else** .

## <a name="a-nameif_constexpr-if-constexpr-statements"></a><a name="if_constexpr"> jeśli instrukcje constexpr

**Visual Studio 2017 w wersji 15,3 i nowszej** (dostępny w [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)): w szablonach funkcji można użyć instrukcji **if constexpr** , aby podejmować decyzje dotyczące rozgałęziania czasu kompilowania bez konieczności stosowania wielu przeciążeń funkcji. Można na przykład napisać pojedynczą funkcję, która obsługuje rozpakowywanie parametrów (nie jest potrzebne Przeciążenie o wartości zero parametrów):

```cpp
template <class T, class... Rest>
void f(T&& t, Rest&&... r)
{
    // handle t
    do_something(t);

    // handle r conditionally
    if constexpr (sizeof...(r))
    {
        f(r...);
    }
    else
    {
        g(r...);
    }
}
```

## <a name="see-also"></a>Zobacz też

[Instrukcje wyboru](../cpp/selection-statements-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[switch, instrukcja (C++)](../cpp/switch-statement-cpp.md)