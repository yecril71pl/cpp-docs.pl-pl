---
title: extent — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::extent
helpviewer_keywords:
- extent class
- extent
ms.assetid: 6d16263d-90b2-4330-9ec7-b59ed898792d
ms.openlocfilehash: 7463b424d15ee86f851b7d81953abf3fe1c98fee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393977"
---
# <a name="extent-class"></a>extent — Klasa

Pobiera wymiaru tablicy.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty, unsigned I = 0>
struct extent;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ do zapytania.

*I*<br/>
Tablica jest powiązany z zapytania.

## <a name="remarks"></a>Uwagi

Jeśli *Ty* jest typem tablicy, który ma co najmniej *I* wymiarów, zapytania typu przechowuje liczbę elementów w wymiarze określony przez *I*. Jeśli *Ty* nie jest typem tablicowym lub rangę jest mniejsza niż *I*, lub jeśli *I* wynosi zero i *Ty* jest typu "granica tablicy nieznany `U` ", typu zapytania zawiera wartość 0.

## <a name="example"></a>Przykład

```cpp
// std__type_traits__extent.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main()
    {
    std::cout << "extent 0 == "
        << std::extent<int[5][10]>::value << std::endl;
    std::cout << "extent 1 == "
        << std::extent<int[5][10], 1>::value << std::endl;

    return (0);
    }
```

```Output
extent 0 == 5
extent 1 == 10
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
[remove_all_extents, klasa](../standard-library/remove-all-extents-class.md)<br/>
[remove_extent, klasa](../standard-library/remove-extent-class.md)<br/>
