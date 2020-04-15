---
title: '&lt;funkcje tablicowe&gt;'
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
ms.openlocfilehash: d54e430853959c77b4042092409a8640a169e4c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364938"
---
# <a name="ltarraygt-functions"></a>&lt;funkcje tablicowe&gt;

Tablica \<> nagłówek zawiera dwie funkcje `get` niebędące elementami członkowskimi i `swap`, które działają na obiektach **tablicy.**

|||
|-|-|
|[get](#get)|[Wymiany](#swap)|

## <a name="get"></a><a name="get"></a>Pobierz

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

*T*\
Typ elementu.

*N*\
Liczba elementów w tablicy.

*Arr*\
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

## <a name="swap"></a><a name="swap"></a>Wymiany

Specjalizacja szablonu `std::swap` niebędącego elementem członkowskim, która zamienia dwa obiekty **tablicy.**

```cpp
template <class Ty, std::size_t N>
void swap(array<Ty, N>& left, array<Ty, N>& right);
```

### <a name="parameters"></a>Parametry

*Ty (ty)*\
Typ elementu.

*N*\
Rozmiar tablicy.

*Lewej*\
Pierwsza tablica do wymiany.

*Prawo*\
Druga tablica do wymiany.

### <a name="remarks"></a>Uwagi

Funkcja szablonu `left.swap(right)`wykonuje program .

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

[\<>tablicowe](../standard-library/array.md)
