---
title: Wyrażenia w nawiasach
ms.date: 11/04/2016
helpviewer_keywords:
- parentheses
- expression evaluation, evaluation order
- expressions [C++], evaluating
- parentheses, expressions
ms.assetid: b8636147-6982-408c-9e64-29e40678ee43
ms.openlocfilehash: d0105556530161991b46c5ee25cd73f2f995063f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233751"
---
# <a name="expressions-in-parentheses"></a>Wyrażenia w nawiasach

Każdy operand można ująć w nawiasy bez zmiany typu lub wartości wyrażenia ujętego. Na przykład w wyrażeniu:

```
( 10 + 5 ) / 5
```

nawiasy wokół `10 + 5` oznaczają, że wartość `10 + 5` jest szacowana jako pierwsza, a następnie przechodzi do lewego operandu operatora dzielenia (**/**). Wynik `( 10 + 5 ) / 5` wynosi 3. Bez nawiasów, `10 + 5 / 5` wynikiem będzie 11.

Chociaż nawiasy mają wpływ na sposób grupowania argumentów operacji w wyrażeniu, nie mogą one zagwarantować określonej kolejności oceny we wszystkich przypadkach. Na przykład ani nawiasy, ani grupowanie od lewej do prawej w następującym wyrażeniu gwarantuje, jakie wartości `i` będą znajdować się w dowolnym z podwyrażeń:

```
( i++ +1 ) * ( 2 + i )
```

Kompilator jest bezpłatny, aby oszacować dwie strony mnożenia w dowolnej kolejności. Jeśli wartość początkowa `i` wynosi zero, całe wyrażenie może być oceniane jako jedna z tych dwóch instrukcji:

```
( 0 + 1 + 1 ) * ( 2 + 1 )
( 0 + 1 + 1 ) * ( 2 + 0 )
```

Wyjątki pochodzące z efektów ubocznych są omawiane w [efektach ubocznych](../c-language/side-effects.md).

## <a name="see-also"></a>Zobacz też

[Wyrażenia podstawowe języka C](../c-language/c-primary-expressions.md)
