---
title: Wyrażenia w nawiasach | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- parentheses
- expression evaluation, evaluation order
- expressions [C++], evaluating
- parentheses, expressions
ms.assetid: b8636147-6982-408c-9e64-29e40678ee43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a052dbc666be05d05753c7408b1d09643f09dc8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022880"
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