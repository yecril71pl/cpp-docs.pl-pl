---
title: false (C++)
ms.date: 11/04/2016
f1_keywords:
- false_cpp
helpviewer_keywords:
- false keyword [C++]
ms.assetid: cc13aec5-1f02-4d38-8dbf-5473ea2b354f
ms.openlocfilehash: f363e309b91e44472447d040aa36752750afec6f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188938"
---
# <a name="false-c"></a>false (C++)

Słowo kluczowe jest jedną z dwóch wartości dla zmiennej typu [bool](../cpp/bool-cpp.md) lub wyrażenia warunkowego (wyrażenie warunkowe to teraz **prawdziwe** wyrażenie logiczne). Na przykład jeśli `i` jest zmienną typu **bool**, instrukcja `i = false;` przypisuje **Fałsz** do `i`.

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

## <a name="see-also"></a>Zobacz też

[Słowa kluczowe](../cpp/keywords-cpp.md)
