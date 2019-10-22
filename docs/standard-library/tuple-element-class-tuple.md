---
title: tuple_element — Klasa
ms.date: 11/04/2016
f1_keywords:
- utility/std::tuple_element
helpviewer_keywords:
- std::tuple_element
ms.assetid: 4c51a6c1-ce81-462f-8c6c-291d69f2b77c
ms.openlocfilehash: 21efed39fdaabe0f95f83e9dc5cdfcc508a147c5
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72684458"
---
# <a name="tuple_element-class"></a>tuple_element — Klasa

Zawija element `tuple`. Specjalizacje zawijają `array` elementów i `pair` elementów.

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

@No__t_1 *indeksu*
Indeks wyoznaczonego elementu.

@No__t_1 *krotek*
Typ krotki.

*Elem* \
Typ elementu tablicy.

@No__t_1 *rozmiaru*
Rozmiar tablicy.

@No__t_1 *T1*
Typ pierwszego elementu w parze.

@No__t_1 *T2*
Typ drugiego elementu w parze.

## <a name="remarks"></a>Uwagi

@No__t_0 szablonu klasy zawiera zagnieżdżony element typedef `type`, który jest synonimem dla typu w *indeksie* indeksu *krotki*typu krotki.

Element typedef `tuple_element_t` jest wygodnym aliasem dla `tuple_element<Index, Tuple>::type`.

Specjalizacja szablonu klasy dla tablic zawiera interfejs do `array` jako spójna kolekcja elementów `Size`, z których każdy ma ten sam typ. Każda specjalizacja ma zagnieżdżony element typedef `type`, który jest synonimem dla typu elementu *indeksu* `array`, z dowolnymi nietrwałymi zastrzeżeniami const.

Specjalizacje szablonów dla `pair` typy każdy zapewniają jeden element członkowski typedef, `type`, który jest synonimem dla typu elementu w określonej pozycji w parze, z dowolnymi nieprawidłowymi nieprawidłowymi kwalifikacjami. Element typedef `tuple_element_t` jest wygodnym aliasem dla `tuple_element<N, pair<T1, T2>>::type`.

Użyj [funkcji get &lt;utility &gt;](../standard-library/utility-functions.md#get) , aby zwrócić element w określonej pozycji lub o określonym typie.

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

**Nagłówek:** \<tuple >

**Nagłówek:** \<array > (dla specjalizacji macierzy)

**Nagłówek:** \<utility > (dla specjalizacji par)

**Przestrzeń nazw:** std
