---
title: alignof i alignas (C++)
ms.date: 11/04/2016
ms.assetid: 1d18aa8a-9621-4fb5-86e5-4cc86d5187f4
ms.openlocfilehash: 825df25494497e13d29212f7f951be8247b6f136
ms.sourcegitcommit: 185b8ee6dd4e10045df730c5b957b9729813da2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53411926"
---
# <a name="alignof-and-alignas-c"></a>alignof i alignas (C++)

**Alignas** Specyfikator typu jest przenośny, C++ standardowy sposób określić niestandardowe wyrównania zmiennych i typów zdefiniowanych przez użytkownika. **Alignof** operator podobnie jest standardowa, przenośne sposobem uzyskania wyrównanie określonego typu lub zmiennej.

## <a name="example"></a>Przykład

Możesz użyć **alignas** na klasy, struktury lub Unii lub na poszczególnych elementów członkowskich. Gdy wiele **alignas** specyfikatory zostaną napotkane, kompilator wybierze najbardziej rygorystyczne z nich (jedna o największej wartości).

```cpp
// alignas_alignof.cpp
// compile with: cl /EHsc alignas_alignof.cpp
#include <iostream>

struct alignas(16) Bar
{
    int i;       // 4 bytes
    int n;      // 4 bytes
    alignas(4) char arr[3];
    short s;          // 2 bytes
};

int main()
{
    std::cout << alignof(Bar) << std::endl; // output: 16
}
```

## <a name="see-also"></a>Zobacz także

[Wyrównanie](../cpp/alignment-cpp-declarations.md)
