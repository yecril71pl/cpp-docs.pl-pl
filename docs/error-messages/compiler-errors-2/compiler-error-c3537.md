---
title: Błąd kompilatora C3537
ms.date: 11/04/2016
f1_keywords:
- C3537
helpviewer_keywords:
- C3537
ms.assetid: f537ebd1-4fb0-4e09-a453-4f38db2c6881
ms.openlocfilehash: 663ef761d6c52aeb4c3cc9ce109079c647904e36
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87197556"
---
# <a name="compiler-error-c3537"></a>Błąd kompilatora C3537

"Type": nie można rzutować na typ, który zawiera wartość "Auto"

Nie można rzutować zmiennej do wskazanego typu, ponieważ typ zawiera **`auto`** słowo kluczowe i domyślną wartość [/Zc:](../../build/reference/zc-auto-deduce-variable-type.md) autokompilator jest włączona.

## <a name="example"></a>Przykład

Poniższy kod daje C3537, ponieważ zmienne są rzutowane na typ, który zawiera **`auto`** słowo kluczowe.

```cpp
// C3537.cpp
// Compile with /Zc:auto
int main()
{
   int value = 123;
   auto(value);                        // C3537
   (auto)value;                        // C3537
   auto x1 = auto(value);              // C3537
   auto x2 = (auto)value;              // C3537
   auto x3 = static_cast<auto>(value); // C3537
   return 0;
}
```

## <a name="see-also"></a>Zobacz także

[Słowo kluczowe "Autouzupełnianie"](../../cpp/auto-keyword.md)
