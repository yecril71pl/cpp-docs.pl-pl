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
ms.openlocfilehash: 4558294da52577e1ed490be537e92665ce6b15f1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50592767"
---
# <a name="checked-iterators"></a>Zaznaczone iteratory

Iteratory sprawdzane zapewniają, że granice kontenera nie ulegają nadpisaniu. Iteratory sprawdzane mają zastosowanie zarówno kompilacje wydania i kompilacji debugowania. Aby uzyskać więcej informacji o sposobach używania iteratorów debugowania, podczas kompilacji w trybie debugowania, zobacz [Debug Iterator Support](../standard-library/debug-iterator-support.md).

## <a name="remarks"></a>Uwagi

Aby uzyskać informacje na temat sposobu wyłączania ostrzeżeń generowanych przez Iteratory sprawdzane, zobacz [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).

Możesz użyć [ \_ITERATORA\_debugowania\_poziom](../standard-library/iterator-debug-level.md) makro preprocesora Aby włączyć lub wyłączyć funkcję Iteratory sprawdzane. Jeśli _ITERATOR_DEBUG_LEVEL jest zdefiniowana jako 1 lub 2, niebezpieczne używanie iteratorów powoduje błąd w czasie wykonywania, a program jest zamykany. Jeśli jest zdefiniowana jako 0, iteratory sprawdzane są wyłączone. Domyślnie wartość _ITERATOR_DEBUG_LEVEL jest 0 dla kompilacji oficjalnych i 2 kompilacji debugowania.

> [!IMPORTANT]
> Starsze dokumentację i kod źródłowy może odwoływać się do [_SECURE_SCL](../standard-library/secure-scl.md) makra. Używaj _ITERATOR_DEBUG_LEVEL do kontrolowania _SECURE_SCL. Aby uzyskać więcej informacji, zobacz [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).

Jeśli _ITERATOR_DEBUG_LEVEL jest zdefiniowana jako 1 lub 2, wykonywane są kontrole iteratora:

- Wszystkie standardowe Iteratory (na przykład [vector::iterator](../standard-library/vector-class.md#iterator)) są sprawdzane.

- Jeśli iterator wyjściowy jest iteratorem, wywołania do biblioteki standardowej funkcji takich jak [std::copy](../standard-library/algorithm-functions.md#copy) uzyskać sprawdzane zachowanie.

- Jeśli iterator wyjściowy jest iteratorem niesprawdzonym, wywołań funkcji standardowej biblioteki powodują ostrzeżenia kompilatora.

- Następujące funkcje generuje błąd w czasie wykonywania, jeśli nastąpi dostęp poza granicami kontenera:

|||||
|-|-|-|-|
|[basic_string::operator\[\]](../standard-library/basic-string-class.md#op_at)|[bitset::operator\[\]](../standard-library/bitset-class.md#op_at)|[back](../standard-library/deque-class.md#back)|[Frontonu](../standard-library/deque-class.md#front)|
|[deque::operator\[\]](../standard-library/deque-class.md#op_at)|[back](../standard-library/list-class.md#back)|[Frontonu](../standard-library/list-class.md#front)|[back](../standard-library/queue-class.md#back)|
|[Frontonu](../standard-library/queue-class.md#front)|[Vector::operator\[\]](../standard-library/vector-class.md#op_at)|[back](../standard-library/vector-class.md#back)|[Frontonu](../standard-library/vector-class.md#front)|

Jeśli _ITERATOR_DEBUG_LEVEL jest zdefiniowana jako 0:

- Wszystkie standardowe Iteratory są niesprawdzane. Iteratory można przenosić poza granice kontenera, co prowadzi do niezdefiniowanego zachowania.

- Jeśli iterator wyjściowy jest iteratorem, wywołania do biblioteki standardowej funkcji takich jak `std::copy` uzyskać sprawdzane zachowanie.

- Jeśli iterator wyjściowy jest iteratorem niesprawdzonym, wywołań funkcji standardowej biblioteki Uzyskaj niesprawdzone zachowanie.

Iterator sprawdzony odnosi się do iteratora, który wywołuje `invalid_parameter_handler` Jeśli próbujesz wyjść poza granice kontenera. Aby uzyskać więcej informacji na temat `invalid_parameter_handler`, zobacz [Parameter Validation](../c-runtime-library/parameter-validation.md).

Adaptery iteratora, które obsługują sprawdzane Iteratory są [klasy checked_array_iterator](../standard-library/checked-array-iterator-class.md) i [unchecked_array_iterator — klasa](../standard-library/unchecked-array-iterator-class.md).

## <a name="example"></a>Przykład

Podczas kompilowania przy użyciu _ITERATOR_DEBUG_LEVEL równa 1 lub 2 występuje błąd w czasie wykonywania, jeśli użytkownik podejmie próbę uzyskania dostępu do elementu, który znajduje się poza granicami kontenera za pomocą operatora indeksowania niektórych klas.

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

Ten program wyświetli "67", a następnie pojawi się okno dialogowe błędu asercji z dodatkowymi informacjami dotyczącymi błędu.

## <a name="example"></a>Przykład

Podobnie, gdy kompilujesz przy użyciu _ITERATOR_DEBUG_LEVEL równa 1 lub 2, wystąpi błąd czasu wykonywania przy próbie uzyskania dostępu do elementu za pomocą `front` lub `back` w klasach kontenera, gdy kontener jest pusty.

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

Ten program pojawi się okno dialogowe błędu asercji z dodatkowymi informacjami dotyczącymi błędu.

## <a name="example"></a>Przykład

Poniższy kod demonstruje różne scenariusze użycia iteratorów wraz z komentarzami dotyczącymi każdego z nich. Domyślnie _ITERATOR_DEBUG_LEVEL ustawiono na 2 w kompilacjach do debugowania i do 0 w sprzedaży detalicznej.

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

Gdy skompilować ten kod przy użyciu `cl.exe /EHsc /W4 /MTd checked_iterators_3.cpp` kompilator emituje ostrzeżenie, ale skompiluje się bez błędów do pliku wykonywalnego:

```Output
algorithm(1026) : warning C4996: 'std::_Transform1': Function call with parameters
that may be unsafe - this call relies on the caller to check that the passed values
are correct. To disable this warning, use -D_SCL_SECURE_NO_WARNINGS. See documentation
on how to use Visual C++ 'Checked Iterators'
```

Po uruchomieniu w wierszu polecenia pliku wykonywalnego, który generuje te dane wyjściowe:

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

## <a name="see-also"></a>Zobacz także

[Standardowa biblioteka C++ — przegląd](../standard-library/cpp-standard-library-overview.md)<br/>
[Obsługa iteratora debugowania](../standard-library/debug-iterator-support.md)<br/>
