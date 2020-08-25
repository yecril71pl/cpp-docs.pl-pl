---
title: Zaznaczone iteratory
ms.date: 11/04/2016
f1_keywords:
- _SECURE_SCL_THROWS
helpviewer_keywords:
- Safe Libraries
- Safe Libraries, C++ Standard Library
- Safe C++ Standard Library
- iterators, checked
- checked iterators
ms.assetid: cfc87df8-e3d9-403b-ab78-e9483247d940
ms.openlocfilehash: 4918cd9df34e5c728c4aa2d90d4eb7f55784e4c2
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845695"
---
# <a name="checked-iterators"></a>Zaznaczone iteratory

Iteratory sprawdzane zapewniają, że granice kontenera nie ulegają nadpisaniu. Sprawdzone Iteratory dotyczą zarówno kompilacji wydania, jak i kompilacji debugowania. Więcej informacji o sposobach korzystania z iteratorów debugowania podczas kompilowania w trybie debugowania znajduje się w temacie [Obsługa iteratora debugowania](../standard-library/debug-iterator-support.md).

## <a name="remarks"></a>Uwagi

Aby uzyskać informacje dotyczące sposobu wyłączania ostrzeżeń generowanych przez sprawdzone Iteratory, zobacz [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).

Aby włączyć lub wyłączyć funkcję zaewidencjonowanych iteratorów, można użyć makra preprocesora [ \_ \_ \_ poziomu debugowania iteratora](../standard-library/iterator-debug-level.md) . Jeśli _ITERATOR_DEBUG_LEVEL jest zdefiniowany jako 1 lub 2, niebezpieczne użycie iteratorów powoduje błąd w czasie wykonywania, a program zostaje przerwany. Jeśli jest zdefiniowana jako 0, iteratory sprawdzane są wyłączone. Domyślnie wartość _ITERATOR_DEBUG_LEVEL to 0 w przypadku kompilacji wydania i 2 dla kompilacji debugowania.

> [!IMPORTANT]
> Starsza dokumentacja i kod źródłowy mogą odwoływać się do [_SECURE_SCL](../standard-library/secure-scl.md) makra. Użyj _ITERATOR_DEBUG_LEVEL, aby kontrolować _SECURE_SCL. Aby uzyskać więcej informacji, zobacz [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).

Gdy _ITERATOR_DEBUG_LEVEL jest zdefiniowany jako 1 lub 2, są wykonywane następujące testy iteratora:

- Wszystkie Iteratory standardowe (na przykład [Vector:: iterator](../standard-library/vector-class.md#iterator)) są sprawdzane.

- Jeśli iterator wyjściowy jest iteratorem sprawdzonym, wywołania funkcji biblioteki standardowej, takie jak [std:: Copy](../standard-library/algorithm-functions.md#copy) Get Behavior.

- Jeśli iterator wyjściowy jest iteratorem niesprawdzonym, wywołania funkcji biblioteki standardowej powodują ostrzeżenia kompilatora.

- Poniższe funkcje generują błąd środowiska uruchomieniowego, jeśli istnieje dostęp poza granicami kontenera:

:::row:::
   :::column span="":::
      &emsp;&emsp;[`basic_string::operator[]`](../standard-library/basic-string-class.md#op_at)\
      &emsp;&emsp;[`bitset::operator[]`](../standard-library/bitset-class.md#op_at)\
      &emsp;&emsp;[`deque::back`](../standard-library/deque-class.md#back)\
      &emsp;&emsp;[`deque::front`](../standard-library/deque-class.md#front)
   :::column-end:::
   :::column span="":::
      [`deque::operator[]`](../standard-library/deque-class.md#op_at)\
      [`list::back`](../standard-library/list-class.md#back)\
      [`list::front`](../standard-library/list-class.md#front)\
      [`queue::back`](../standard-library/queue-class.md#back)
   :::column-end:::
   :::column span="":::
      [`queue::front`](../standard-library/queue-class.md#front)\
      [`vector::back`](../standard-library/vector-class.md#back)\
      [`vector::front`](../standard-library/vector-class.md#front)\
      [`vector::operator[]`](../standard-library/vector-class.md#op_at)
   :::column-end:::
:::row-end:::

Gdy _ITERATOR_DEBUG_LEVEL jest zdefiniowany jako 0:

- Wszystkie Iteratory standardowe są niezaznaczone. Iteratory mogą poruszać się poza granice kontenera, co prowadzi do niezdefiniowanego zachowania.

- Jeśli iterator wyjściowy jest iteratorem sprawdzonym, wywołania funkcji biblioteki standardowej, takich jak `std::copy` zachowanie sprawdzone.

- Jeśli iterator wyjściowy jest iteratorem niesprawdzonym, wywołania funkcji biblioteki standardowej uzyskują niesprawdzone zachowanie.

Sprawdzony iterator odwołuje się do iteratora, który wywołuje się, `invalid_parameter_handler` Jeśli próbujesz przenieść poprzednią granicę kontenera. Aby uzyskać więcej informacji na temat `invalid_parameter_handler` , zobacz [Walidacja parametrów](../c-runtime-library/parameter-validation.md).

Adaptery iteratorów obsługujące sprawdzone Iteratory są klasami klasy [checked_array_iterator](../standard-library/checked-array-iterator-class.md) i [unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md).

## <a name="example"></a>Przykład

Podczas kompilowania przy użyciu _ITERATOR_DEBUG_LEVEL ustawionej na 1 lub 2, wystąpi błąd czasu wykonywania, jeśli spróbujesz uzyskać dostęp do elementu, który znajduje się poza granicami kontenera przy użyciu operatora indeksowania niektórych klas.

```cpp
// checked_iterators_1.cpp
// cl.exe /Zi /MDd /EHsc /W4

#define _ITERATOR_DEBUG_LEVEL 1

#include <vector>
#include <iostream>

using namespace std;

int main()
{
   vector<int> v;
   v.push_back(67);

   int i = v[0];
   cout << i << endl;

   i = v[1]; //triggers invalid parameter handler
}
```

Ten program drukuje "67", a następnie wyświetla okno dialogowe niepowodzenia potwierdzenia z dodatkowymi informacjami o błędzie.

## <a name="example"></a>Przykład

Podobnie, gdy kompilujesz przy użyciu _ITERATOR_DEBUG_LEVEL ustawionej na 1 lub 2, wystąpi błąd czasu wykonywania, jeśli spróbujesz uzyskać dostęp do elementu przy użyciu `front` lub `back` w klasach kontenera, gdy kontener jest pusty.

```cpp
// checked_iterators_2.cpp
// cl.exe /Zi /MDd /EHsc /W4
#define _ITERATOR_DEBUG_LEVEL 1

#include <vector>
#include <iostream>

using namespace std;

int main()
{
   vector<int> v;

   int& i = v.front(); // triggers invalid parameter handler
}
```

Ten program wyskakujące okno dialogowe niepowodzenia potwierdzenia z dodatkowymi informacjami o błędzie.

## <a name="example"></a>Przykład

Poniższy kod demonstruje różne scenariusze użycia iteratorów wraz z komentarzami dotyczącymi każdego z nich. Domyślnie _ITERATOR_DEBUG_LEVEL jest ustawiona na 2 w kompilacjach debugowania, a do 0 w kompilacjach detalicznych.

```cpp
// checked_iterators_3.cpp
// cl.exe /MTd /EHsc /W4

#include <algorithm>
#include <array>
#include <iostream>
#include <iterator>
#include <numeric>
#include <string>
#include <vector>

using namespace std;

template <typename C>
void print(const string& s, const C& c)
{
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    vector<int> v(16);
    iota(v.begin(), v.end(), 0);
    print("v: ", v);

    // OK: vector::iterator is checked in debug mode
    // (i.e. an overrun causes a debug assertion)
    vector<int> v2(16);
    transform(v.begin(), v.end(), v2.begin(), [](int n) { return n * 2; });
    print("v2: ", v2);

    // OK: back_insert_iterator is marked as checked in debug mode
    // (i.e. an overrun is impossible)
    vector<int> v3;
    transform(v.begin(), v.end(), back_inserter(v3), [](int n) { return n * 3; });
    print("v3: ", v3);

    // OK: array::iterator is checked in debug mode
    // (i.e. an overrun causes a debug assertion)
    array<int, 16> a4;
    transform(v.begin(), v.end(), a4.begin(), [](int n) { return n * 4; });
    print("a4: ", a4);

    // OK: Raw arrays are checked in debug mode
    // (an overrun causes a debug assertion)
    // NOTE: This applies only when raw arrays are given to C++ Standard Library algorithms!
    int a5[16];
    transform(v.begin(), v.end(), a5, [](int n) { return n * 5; });
    print("a5: ", a5);

    // WARNING C4996: Pointers cannot be checked in debug mode
    // (an overrun causes undefined behavior)
    int a6[16];
    int * p6 = a6;
    transform(v.begin(), v.end(), p6, [](int n) { return n * 6; });
    print("a6: ", a6);

    // OK: stdext::checked_array_iterator is checked in debug mode
    // (an overrun causes a debug assertion)
    int a7[16];
    int * p7 = a7;
    transform(v.begin(), v.end(), stdext::make_checked_array_iterator(p7, 16), [](int n) { return n * 7; });
    print("a7: ", a7);

    // WARNING SILENCED: stdext::unchecked_array_iterator is marked as checked in debug mode
    // (it performs no checking, so an overrun causes undefined behavior)
    int a8[16];
    int * p8 = a8;
    transform(v.begin(), v.end(), stdext::make_unchecked_array_iterator(p8), [](int n) { return n * 8; });
    print("a8: ", a8);
}
```

Podczas kompilowania tego kodu przy użyciu `cl.exe /EHsc /W4 /MTd checked_iterators_3.cpp` kompilatora emituje ostrzeżenie, ale kompiluje bez błędu do pliku wykonywalnego:

```Output
algorithm(1026) : warning C4996: 'std::_Transform1': Function call with parameters
that may be unsafe - this call relies on the caller to check that the passed values
are correct. To disable this warning, use -D_SCL_SECURE_NO_WARNINGS. See documentation
on how to use Visual C++ 'Checked Iterators'
```

Po uruchomieniu w wierszu polecenia plik wykonywalny generuje następujące dane wyjściowe:

```Output
v: 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15
v2: 0 2 4 6 8 10 12 14 16 18 20 22 24 26 28 30
v3: 0 3 6 9 12 15 18 21 24 27 30 33 36 39 42 45
a4: 0 4 8 12 16 20 24 28 32 36 40 44 48 52 56 60
a5: 0 5 10 15 20 25 30 35 40 45 50 55 60 65 70 75
a6: 0 6 12 18 24 30 36 42 48 54 60 66 72 78 84 90
a7: 0 7 14 21 28 35 42 49 56 63 70 77 84 91 98 105
a8: 0 8 16 24 32 40 48 56 64 72 80 88 96 104 112 120
```

## <a name="see-also"></a>Zobacz też

[Omówienie standardowej biblioteki języka C++](../standard-library/cpp-standard-library-overview.md)\
[Obsługa iteratora debugowania](../standard-library/debug-iterator-support.md)
