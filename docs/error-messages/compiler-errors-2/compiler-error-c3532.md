---
title: Błąd kompilatora C3532
ms.date: 11/04/2016
f1_keywords:
- C3532
helpviewer_keywords:
- C3532
ms.assetid: 51067853-eda8-4f59-86e8-8924e16d3a95
ms.openlocfilehash: 91d8e28e053d8ce1b307f9345ab3249386bdf1ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50568896"
---
# <a name="compiler-error-c3532"></a>Błąd kompilatora C3532

"type": nieprawidłowe użycie "auto"

Wskazany typ nie może być zadeklarowana z `auto` — słowo kluczowe. Na przykład nie można użyć `auto` — słowo kluczowe do deklarowania tablicą lub metoda typ zwracany.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Upewnij się, że wyrażenia inicjowania daje prawidłowego typu.

1. Upewnij się, że nie są deklarowane tablicą lub typem zwracanym metody.

## <a name="example"></a>Przykład

Poniższy przykład daje C3532, ponieważ `auto` — słowo kluczowe nie mogą deklarować zwracanego typu metody.

```
// C3532a.cpp
// Compile with /Zc:auto
auto f(){}   // C3532
```

## <a name="example"></a>Przykład

Poniższy przykład daje C3532, ponieważ `auto` — słowo kluczowe nie można zadeklarować tablicy.

```
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

## <a name="see-also"></a>Zobacz też

[Auto, słowo kluczowe](../../cpp/auto-keyword.md)