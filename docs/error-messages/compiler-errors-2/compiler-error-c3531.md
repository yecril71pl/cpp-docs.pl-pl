---
title: Błąd kompilatora C3531
ms.date: 11/04/2016
f1_keywords:
- C3531
helpviewer_keywords:
- C3531
ms.assetid: 2bdb9fdc-9ddf-403e-8b92-02763d434487
ms.openlocfilehash: 0f6094daddf40b0899dc7f341f50a31daf7a999b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50435454"
---
# <a name="compiler-error-c3531"></a>Błąd kompilatora C3531

'symbol': symbol, którego typ zawiera "auto" musi mieć inicjator

Określona zmienna nie ma wyrażenia inicjatora.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Określ wyrażenie inicjatora, takich jak przypisanie proste, w której używana jest składnia znaku równości, kiedy Deklarujesz zmienną.

## <a name="example"></a>Przykład

Poniższy przykład daje C3531, ponieważ zmienne `x1`, `y1, y2, y3`, i `z2` nie jest zainicjowany.

```
// C3531.cpp
// Compile with /Zc:auto
int main()
{
   auto x1;                  // C3531
   auto y1, y2, y3;          // C3531
   auto z1 = 1, z2, z3 = -1; // C3531
   return 0;
}
```

## <a name="see-also"></a>Zobacz też

[Auto, słowo kluczowe](../../cpp/auto-keyword.md)