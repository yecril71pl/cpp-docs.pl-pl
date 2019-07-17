---
title: tuple_element — Klasa
ms.date: 11/04/2016
f1_keywords:
- utility/std::tuple_element
helpviewer_keywords:
- std::tuple_element
ms.assetid: 4c51a6c1-ce81-462f-8c6c-291d69f2b77c
ms.openlocfilehash: 0836ed683b398981e95e401a73ded6367c7ab472
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68241818"
---
# <a name="tupleelement-class"></a>tuple_element — Klasa

Opakowuje `tuple` elementu. OPAKOWYWANIE specjalizacje `array` elementy i `pair` elementów.

## <a name="syntax"></a>Składnia

```cpp
// CLASS tuple_element (find element by index)
template <size_t Index, class Tuple>
   struct tuple_element;

// tuple_element for const
template <size_t Index, class Tuple>
   struct tuple_element<Index, const Tuple>;

// tuple_element for volatile
template <size_t Index, class Tuple>
   struct tuple_element<Index, volatile Tuple>;

// tuple_element for const volatile
template <size_t Index, class Tuple>
   struct tuple_element<Index, const volatile Tuple>;

// Helper typedef
template <size_t Index, class Tuple>
   using tuple_element_t = typename tuple_element<Index, Tuple>::type;

// Specialization for arrays
template <size_t Index, class Elem, size_t Size>
   struct tuple_element<Index, array<Elem, Size>>;

// Specializations for pairs
// struct to determine type of element 0 in pair
template <class T1, class T2>
   struct tuple_element<0, pair<T1, T2>>;

// struct to determine type of element 1 in pair
template <class T1, class T2>
   struct tuple_element<1, pair<T1, T2>>;
```

### <a name="parameters"></a>Parametry

*Indeks*\
Indeks elementu wyznaczonym.

*Krotki*\
Typ spójnej kolekcji.

*Elem*\
Typ elementu tablicy.

*Rozmiar*\
Rozmiar tablicy.

*T1*\
Typ pierwszego elementu w parę.

*T2*\
Typ drugiego elementu w parze.

## <a name="remarks"></a>Uwagi

Klasa szablonu `tuple_element` zawiera zagnieżdżony typedef `type` czyli synonimem typu pod indeksem *indeksu* typu krotki *krotki*.

Typedef `tuple_element_t` jest wygodne alias dla `tuple_element<Index, Tuple>::type`.

Specjalizacja klasy szablonów dla tablic udostępnia interfejs dla `array` jako krotka o `Size` elementów, z których każdy ma tego samego typu. Każda specjalizacja zawiera zagnieżdżony typedef `type` oznacza to synonim dla typu *indeksu* elementu `array`, za pomocą dowolnego kwalifikacji const-volatile zachowane.

Specjalizacje szablonu dla `pair` typy każdego Podaj element typedef jeden element członkowski `type`, który jest synonimem dla typu elementu w określonej pozycji w parze, za pomocą dowolnego kwalifikacji const i/lub volatile zachowane. Typedef `tuple_element_t` jest wygodne alias dla `tuple_element<N, pair<T1, T2>>::type`.

Użyj [get — funkcja &lt;narzędzie&gt; ](../standard-library/utility-functions.md#get) celu zwrócenia elementu w określonym położeniu lub określonego typu.

## <a name="example"></a>Przykład

```cpp
#include <tuple>
#include <string>
#include <iostream>

using namespace std;
typedef tuple<int, double, string> MyTuple;

int main() {
    MyTuple c0{ 0, 1.5, "Tail" };

    tuple_element_t<0, MyTuple> val = get<0>(c0); //get by index
    tuple_element_t<1, MyTuple> val2 = get<1>(c0);
    tuple_element_t<2, MyTuple> val3 = get<string>(c0); // get by type

    cout << val << " " << val2 << " " << val3 << endl;
}
```

```Output
0 1.5 Tail
```

## <a name="example"></a>Przykład

```cpp
#include <array>
#include <iostream>

using namespace std;
typedef array<int, 4> MyArray;

int main()
{
    MyArray c0 { 0, 1, 2, 3 };

    for (const auto& e : c0)
    {
        cout << e << " ";
    }
    cout << endl;

    // display first element "0"
    tuple_element<0, MyArray>::type val = c0.front();
    cout << val << endl;
}
```

```Output
0 1 2 3
0
```

## <a name="example"></a>Przykład

```cpp
#include <utility>
#include <iostream>

using namespace std;

typedef pair<int, double> MyPair;
int main() {
    MyPair c0(0, 1.333);

    // display contents "0 1"
    cout << get<0>(c0) << " ";
    cout << get<1>(c0) << endl;

    // display first element "0 " by index
    tuple_element<0, MyPair>::type val = get<0>(c0);
    cout << val << " ";

    // display second element by type
    tuple_element<1, MyPair>::type val2 = get<double>(c0);
    cout << val2 << endl;
}
```

```Output
0 1.333
0 1.333
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<krotki >

**Nagłówek:** \<array > (dla specjalizacji array)

**Nagłówek:** \<Narzędzia > (dla pary specjalizacje)

**Namespace:** standardowe
