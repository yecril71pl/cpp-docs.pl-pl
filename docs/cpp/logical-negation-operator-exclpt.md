---
title: 'Operator logiczny negacji: ! | Microsoft Docs'
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- '!'
- Not
dev_langs:
- C++
helpviewer_keywords:
- '! operator'
- NOT operator
- logical negation
ms.assetid: 650add9f-a7bc-426c-b01d-5fc6a81c8b62
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4594a8b1a881b6fa92909e7c7014087ff6240de8
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211821"
---
# <a name="logical-negation-operator-"></a>Operator logiczny negacji: !

## <a name="syntax"></a>Składnia

```
! cast-expression
```

## <a name="remarks"></a>Uwagi

Operator logiczny negacji (**!**) odwraca znaczenie swojego operandu. Argument musi być typu arytmetycznego lub wskaźnikowego (lub na wyrażenie obliczane do typu arytmetycznego lub wskaźnikowego). Operand jest niejawnie konwertowany na typ **bool**. Wynik to TRUE, jeśli przekonwertowanego ma wartość FAŁSZ; wynik to FALSE, jeśli przekonwertowanego operand ma wartość TRUE. Wynik jest typu **bool**.

Wyrażenie *e*, wyrażenie jednoargumentowe `!e` jest równoważne wyrażeniu `(e == 0)`, z wyjątkiem sytuacji, gdy przeciążone operatory są zaangażowani.

## <a name="operator-keyword-for-"></a>Operator — słowo kluczowe dla!

**Nie** operator jest alternatywną pisownię **!**. Istnieją dwa sposoby dostępu do **nie** operatora w programach: uwzględnić plik nagłówka \<iso646.h >, lub kompilowanie z [/Za](../build/reference/za-ze-disable-language-extensions.md) — opcja kompilatora (Wyłącz rozszerzenia językowe).

## <a name="example"></a>Przykład

```cpp
// expre_Logical_NOT_Operator.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main() {
    int i = 0;
    if (!i)
        cout << "i is zero" << endl;
}
```

## <a name="see-also"></a>Zobacz także

[Wyrażenia z operatorami jednoargumentowymi](../cpp/expressions-with-unary-operators.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Jednoargumentowe operatory arytmetyczne](../c-language/unary-arithmetic-operators.md)<br/>
