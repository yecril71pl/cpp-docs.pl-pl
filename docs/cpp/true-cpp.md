---
title: wartość true (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- true_cpp
dev_langs:
- C++
helpviewer_keywords:
- true keyword [C++]
ms.assetid: 96be2a70-51c3-4250-9752-874d25a5a11e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8e43fbfd9b3cff9ea617238ed7b4cccd08f780cc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018707"
---
# <a name="true-c"></a>true (C++)

## <a name="syntax"></a>Składnia

```
bool-identifier = true ;
bool-expression logical-operator true ;
```

## <a name="remarks"></a>Uwagi

To słowo kluczowe jest jedną z dwóch wartości do zmiennej typu [bool](../cpp/bool-cpp.md) lub wyrażenia warunkowego (wyrażenia warunkowego jest teraz wyrażenie logiczne true). Jeśli `i` typu **bool**, then — instrukcja `i = true;` przypisuje **true** do `i`.

## <a name="example"></a>Przykład

```cpp
// bool_true.cpp
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