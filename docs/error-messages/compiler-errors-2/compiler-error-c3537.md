---
title: Błąd kompilatora C3537
ms.date: 11/04/2016
f1_keywords:
- C3537
helpviewer_keywords:
- C3537
ms.assetid: f537ebd1-4fb0-4e09-a453-4f38db2c6881
ms.openlocfilehash: ef3e954987b84ea128342b38307769903df4b346
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740484"
---
# <a name="compiler-error-c3537"></a>Błąd kompilatora C3537

"Type": nie można rzutować na typ, który zawiera wartość "Auto"

Nie można rzutować zmiennej do wskazanego typu, ponieważ typ zawiera słowo kluczowe `auto` i domyślna opcja [/Zc:](../../build/reference/zc-auto-deduce-variable-type.md) autocompiler.

## <a name="example"></a>Przykład

Poniższy kod daje C3537, ponieważ zmienne są rzutowane na typ, który zawiera słowo kluczowe `auto`.

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

[Auto, słowo kluczowe](../../cpp/auto-keyword.md)
