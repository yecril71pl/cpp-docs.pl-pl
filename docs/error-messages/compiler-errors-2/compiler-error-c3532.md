---
title: Błąd kompilatora C3532
ms.date: 11/04/2016
f1_keywords:
- C3532
helpviewer_keywords:
- C3532
ms.assetid: 51067853-eda8-4f59-86e8-8924e16d3a95
ms.openlocfilehash: e2329111e916df9eac99d156bcf58a58e148cb08
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228820"
---
# <a name="compiler-error-c3532"></a>Błąd kompilatora C3532

"Type": Niepoprawne użycie elementu "Auto"

Nie można zadeklarować wskazanego typu za pomocą **`auto`** słowa kluczowego. Na przykład nie można użyć **`auto`** słowa kluczowego do deklarowania tablicy lub typu zwracanego przez metodę.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Upewnij się, że wyrażenie inicjowania zwraca prawidłowy typ.

1. Upewnij się, że nie deklarujesz tablicy lub typu zwracanego przez metodę.

## <a name="example"></a>Przykład

Poniższy przykład daje C3532, ponieważ **`auto`** słowo kluczowe nie może deklarować zwracanego typu metody.

```cpp
// C3532a.cpp
// Compile with /Zc:auto
auto f(){}   // C3532
```

## <a name="example"></a>Przykład

Poniższy przykład daje C3532, ponieważ **`auto`** słowo kluczowe nie może deklarować tablicy.

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

[Słowo kluczowe "Autouzupełnianie"](../../cpp/auto-keyword.md)
