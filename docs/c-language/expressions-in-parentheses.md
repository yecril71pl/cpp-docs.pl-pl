---
title: Wyrażenia w nawiasach
ms.date: 11/04/2016
helpviewer_keywords:
- parentheses
- expression evaluation, evaluation order
- expressions [C++], evaluating
- parentheses, expressions
ms.assetid: b8636147-6982-408c-9e64-29e40678ee43
ms.openlocfilehash: 0b58ed2483b404df957b8e9e95e41442403036c9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505550"
---
# <a name="expressions-in-parentheses"></a>Wyrażenia w nawiasach

Wszelkie operand można ująć w nawiasy, bez zmiany typu lub wartości wyrażenie w nawiasach. Na przykład w wyrażeniu:

```
( 10 + 5 ) / 5
```

nawiasy wokół `10 + 5` oznaczają, że wartość `10 + 5` jest stosowana jako pierwsza i staje się lewy argument operacji podziału (**/**) — operator. Wynik `( 10 + 5 ) / 5` to 3. Bez nawiasów `10 + 5 / 5` używane do oceny do 11.

Mimo że nawiasy wpływa na sposób operandy są grupowane w wyrażeniu, ich nie gwarantuje określonej kolejności obliczania we wszystkich przypadkach. Na przykład nawiasów ani grupowanie od lewej do prawej następujące wyrażenie nie gwarantuje, jakie wartości `i` będą znajdować się w jednej z podwyrażenia:

```
( i++ +1 ) * ( 2 + i )
```

Kompilator jest bezpłatny do oceny partnerami mnożenia w dowolnej kolejności. Jeśli wartość początkową `i` wynosi zero, całe wyrażenie można go obliczyć jako jedną z tych dwóch instrukcji:

```
( 0 + 1 + 1 ) * ( 2 + 1 )
( 0 + 1 + 1 ) * ( 2 + 0 )
```

Wyjątki wynikłe ze efekty uboczne są omówione w [efekty uboczne](../c-language/side-effects.md).

## <a name="see-also"></a>Zobacz też

[Wyrażenia podstawowe języka C](../c-language/c-primary-expressions.md)