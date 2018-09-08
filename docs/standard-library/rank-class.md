---
title: Rank — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::rank
dev_langs:
- C++
helpviewer_keywords:
- rank class
- rank
ms.assetid: bc9f1b8f-800f-46ca-b6f4-d8579ed5406a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b46806367ebe09f2b04aa05943277177d6e40671
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44105747"
---
# <a name="rank-class"></a>rank — Klasa

Pobiera liczbę wymiarów tablicy.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct rank;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Zapytanie typu przechowuje wartość liczbę wymiarów tablicy *Ty*, lub 0, jeśli *Ty* nie jest typem tablicy.

## <a name="example"></a>Przykład

```cpp
// std__type_traits__rank.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main()
    {
    std::cout << "rank<int> == "
        << std::rank<int>::value << std::endl;
    std::cout << "rank<int[5]> == "
        << std::rank<int[5]>::value << std::endl;
    std::cout << "rank<int[5][10]> == "
        << std::rank<int[5][10]>::value << std::endl;

    return (0);
    }

```

```Output
rank<int> == 0
rank<int[5]> == 1
rank<int[5][10]> == 2
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
[extent, klasa](../standard-library/extent-class.md)<br/>
