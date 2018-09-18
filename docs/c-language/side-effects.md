---
title: Efekty uboczne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- expression evaluation, side effects
- side effects in expression evaluation
ms.assetid: d9b3004a-830e-43a0-bea5-8989d501d670
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6edd636ddb4f59ea0df32846869afc5400edb6dc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46020109"
---
# <a name="side-effects"></a>Efekty uboczne

Kolejność obliczania wyrażeń jest definiowany przez konkretnej implementacji, z wyjątkiem sytuacji, gdy język gwarantuje określonej kolejności obliczania (zgodnie z opisem w [hierarchia i kolejność oceny](../c-language/precedence-and-order-of-evaluation.md)). Na przykład efekty uboczne wystąpić w następujących wywołania funkcji:

```
add( i + 1, i = j + 2 );
myproc( getc(), getc() );
```

Argumenty wywołania funkcji może zostać oceniony w dowolnej kolejności. Wyrażenie `i + 1` może zostać ocenione przed `i = j + 2`, lub `i = j + 2` może zostać ocenione przed `i + 1`. Wynik różni się w każdym przypadku. Podobnie nie jest możliwe w celu zagwarantowania, jakie znaki są faktycznie przekazywane do `myproc`. Ponieważ jednoargumentowe inkrementacja i dekrementacja operacje obejmują przypisania, takich operacji może spowodować efekty uboczne, jak pokazano w poniższym przykładzie:

```
x[i] = i++;
```

W tym przykładzie wartość `x` to znaczy zmodyfikowany, będzie nieprzewidywalny. Wartość indeksu dolnego może być nowej lub starej wartości `i`. Wynik może różnić się w różnych kompilatorach i różnych poziomach optymalizacji.

Ponieważ C nie definiuje kolejność oceniania efekty uboczne, obie metody oceny omówione powyżej są poprawne, i albo mogą być wykonywane. Aby upewnić się, że kod jest przenośny i przejrzysty, unikaj instrukcji, które są zależne od określonej kolejności obliczania uzyskać efekty uboczne.

## <a name="see-also"></a>Zobacz też

[Obliczanie wyrażeń](../c-language/expression-evaluation-c.md)