---
title: Błąd kompilatora C3532
ms.date: 11/04/2016
f1_keywords:
- C3532
helpviewer_keywords:
- C3532
ms.assetid: 51067853-eda8-4f59-86e8-8924e16d3a95
ms.openlocfilehash: 2ef5eb3c2bedd9defbd0b80e6d8c5c8912fcf16d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761936"
---
# <a name="compiler-error-c3532"></a>Błąd kompilatora C3532

"Type": Niepoprawne użycie elementu "Auto"

Nie można zadeklarować wskazanego typu za pomocą słowa kluczowego `auto`. Na przykład nie można użyć słowa kluczowego `auto` do deklarowania tablicy lub typu zwracanego przez metodę.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Upewnij się, że wyrażenie inicjowania zwraca prawidłowy typ.

1. Upewnij się, że nie deklarujesz tablicy lub typu zwracanego przez metodę.

## <a name="example"></a>Przykład

Poniższy przykład daje C3532, ponieważ słowo kluczowe `auto` nie może deklarować zwracanego typu metody.

```cpp
// C3532a.cpp
// Compile with /Zc:auto
auto f(){}   // C3532
```

## <a name="example"></a>Przykład

Poniższy przykład daje C3532, ponieważ słowo kluczowe `auto` nie może deklarować tablicy.

```cpp
// C3532b.cpp
// Compile with /Zc:auto
int main()
{
   int x[5];
   auto a[5];            // C3532
   auto b[1][2];         // C3532
   auto y[5] = x;        // C3532
   auto z[] = {1, 2, 3}; // C3532
   auto w[] = x;         // C3532
   return 0;
}
```

## <a name="see-also"></a>Zobacz także

[Auto, słowo kluczowe](../../cpp/auto-keyword.md)
