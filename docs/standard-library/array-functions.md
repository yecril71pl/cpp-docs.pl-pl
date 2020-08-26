---
title: '&lt;&gt;funkcje tablicy'
ms.date: 11/04/2016
f1_keywords:
- array/std::array::get
- array/std::get
- array/std::swap
ms.assetid: e0700a33-a833-4655-8735-16e71175efc8
helpviewer_keywords:
- std::array [C++], get
- std::get [C++]
- std::swap [C++]
ms.openlocfilehash: 3389ba769d6b61a363e8cbfcf5f6a4e9ec679469
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844707"
---
# <a name="ltarraygt-functions"></a>&lt;&gt;funkcje tablicy

\<array>Nagłówek zawiera dwie funkcje, które nie są elementami członkowskimi, `get` i `swap` , które działają na obiektach **Array** .

[Pobierz](#get)\
[wymiany](#swap)

## <a name="get"></a><a name="get"></a> Pobierz

Zwraca odwołanie do określonego elementu tablicy.

```cpp
template <int Index, class T, size_t N>
constexpr T& get(array<T, N>& arr) noexcept;

template <int Index, class T, size_t N>
constexpr const T& get(const array<T, N>& arr) noexcept;

template <int Index, class T, size_t N>
constexpr T&& get(array<T, N>&& arr) noexcept;
```

### <a name="parameters"></a>Parametry

*Indeks*\
Przesunięcie elementu.

*&*\
Typ elementu.

*Azotan*\
Liczba elementów w tablicy.

*Genotyp*\
Tablica do wyboru.

### <a name="example"></a>Przykład

```cpp
#include <array>
#include <iostream>

using namespace std;

typedef array<int, 4> MyArray;

int main()
{
    MyArray c0 { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& e : c0)
    {
        cout << " " << e;
    }
    cout << endl;

    // display odd elements " 1 3"
    cout << " " << get<1>(c0);
    cout << " " << get<3>(c0) << endl;
}
```

```Output
0 1 2 3
1 3
```

## <a name="swap"></a><a name="swap"></a> wymiany

Specjalizacja szablonu nieczłonkowskiego `std::swap` , który zamienia dwa obiekty **tablicy** .

```cpp
template <class Ty, std::size_t N>
void swap(array<Ty, N>& left, array<Ty, N>& right);
```

### <a name="parameters"></a>Parametry

*Br*\
Typ elementu.

*Azotan*\
Rozmiar tablicy.

*lewym*\
Pierwsza tablica do zamiany.

*Kliknij*\
Druga tablica do zamiany.

### <a name="remarks"></a>Uwagi

Funkcja szablonu jest wykonywana `left.swap(right)` .

### <a name="example"></a>Przykład

```cpp
// std__array__swap.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    Myarray c1 = { 4, 5, 6, 7 };
    c0.swap(c1);

    // display swapped contents " 4 5 6 7"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    swap(c0, c1);

    // display swapped contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
4 5 6 7
0 1 2 3
```

## <a name="see-also"></a>Zobacz też

[\<array>](../standard-library/array.md)
