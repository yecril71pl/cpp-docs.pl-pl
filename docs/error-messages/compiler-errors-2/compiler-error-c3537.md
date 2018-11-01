---
title: Błąd kompilatora C3537
ms.date: 11/04/2016
f1_keywords:
- C3537
helpviewer_keywords:
- C3537
ms.assetid: f537ebd1-4fb0-4e09-a453-4f38db2c6881
ms.openlocfilehash: 22387470019b0118d06b4cacd82a1df5c3e505fb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50576127"
---
# <a name="compiler-error-c3537"></a>Błąd kompilatora C3537

"type": nie można rzutować na typ, który zawiera "auto"

Nie można rzutować zmienną do wskazanego typu, ponieważ zawiera typ `auto` — słowo kluczowe i domyślnego [/Zc: Auto](../../build/reference/zc-auto-deduce-variable-type.md) — opcja kompilatora jest aktywna.

## <a name="example"></a>Przykład

Poniższy kod daje C3537, ponieważ zmienne są rzutowane na typ, który zawiera `auto` — słowo kluczowe.

```
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

## <a name="see-also"></a>Zobacz też

[Auto, słowo kluczowe](../../cpp/auto-keyword.md)