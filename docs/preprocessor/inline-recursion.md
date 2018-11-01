---
title: inline_recursion
ms.date: 11/04/2016
f1_keywords:
- inline_recursion_CPP
- vc-pragma.inline_recursion
helpviewer_keywords:
- pragmas, inline_recursion
- inline_recursion pragma
ms.assetid: cfef5791-63b7-45ac-9574-623747b9b9c9
ms.openlocfilehash: 635d33d91e779d88b56e353d0cddf6b34b313855
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523857"
---
# <a name="inlinerecursion"></a>inline_recursion
Kontroluje wbudowane rozwijanie bezpośrednich lub wzajemnie rekursywne wywołania funkcji.

## <a name="syntax"></a>Składnia

```
#pragma inline_recursion( [{on | off}] )
```

## <a name="remarks"></a>Uwagi

Użyj tej pragmie do funkcji kontroli oznaczone jako [wbudowane](../cpp/inline-functions-cpp.md) i [__inline](../cpp/inline-functions-cpp.md) lub funkcje, które kompilator automatycznie rozszerza się w obszarze `/Ob2` opcji. Korzystanie z tej pragmie wymaga [/Ob](../build/reference/ob-inline-function-expansion.md) ustawienia opcji kompilatora, 1 lub 2. Domyślny stan dla **inline_recursion** jest wyłączona. Ta dyrektywa pragma staje się skuteczny przy pierwszym wywołaniu funkcji po pragmy jest widoczne, a nie ma wpływu na definicji funkcji.

**Inline_recursion** pragma Określa, jak zostaną rozwinięte funkcji rekursywnych. Jeśli **inline_recursion** jest wyłączona, a jeśli funkcja śródwierszowa wywołuje sam siebie (bezpośrednio lub pośrednio), funkcja jest rozwinięty tylko jeden raz. Jeśli **inline_recursion** jest włączona, funkcja jest rozwinięty wielokrotnie, dopóki nie osiągnie wartość ustawioną przy użyciu [inline_depth](../preprocessor/inline-depth.md) pragma, wartością domyślną dla funkcji cyklicznych, który jest definiowany przez `inline_depth` pragma lub pojemność ograniczyć.

## <a name="see-also"></a>Zobacz też

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)<br/>
[inline_depth](../preprocessor/inline-depth.md)<br/>
[/Ob (Rozszerzenie funkcji wbudowanej)](../build/reference/ob-inline-function-expansion.md)