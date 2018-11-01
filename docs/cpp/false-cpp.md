---
title: false (C++)
ms.date: 11/04/2016
f1_keywords:
- false_cpp
helpviewer_keywords:
- false keyword [C++]
ms.assetid: cc13aec5-1f02-4d38-8dbf-5473ea2b354f
ms.openlocfilehash: 5fc27c7f1dfde7d1f686f0a752652773ade9cc0e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464067"
---
# <a name="false-c"></a>false (C++)

Słowo kluczowe jest jedną z dwóch wartości do zmiennej typu [bool](../cpp/bool-cpp.md) lub wyrażenia warunkowego (wyrażenia warunkowego jest teraz **true** wyrażenia logicznego). Na przykład jeśli `i` jest zmienną typu **bool**, `i = false;` instrukcja przypisuje **false** do `i`.

## <a name="example"></a>Przykład

```cpp
// bool_false.cpp
#include <stdio.h>

int main()
{
    bool bb = true;
    printf_s("%d\n", bb);
    bb = false;
    printf_s("%d\n", bb);
}
```

```Output
1
0
```

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)