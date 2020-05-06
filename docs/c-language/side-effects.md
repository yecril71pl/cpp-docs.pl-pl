---
title: Efekty uboczne
ms.date: 11/04/2016
helpviewer_keywords:
- expression evaluation, side effects
- side effects in expression evaluation
ms.assetid: d9b3004a-830e-43a0-bea5-8989d501d670
ms.openlocfilehash: de5e398afd8b95cfe5596f487a36b6a2d27e3287
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62158476"
---
# <a name="side-effects"></a>Efekty uboczne

Kolejność obliczania wyrażeń jest definiowana przez określoną implementację, z wyjątkiem sytuacji, gdy język gwarantuje określoną kolejność oceny (zgodnie z [pierwszeństwem i kolejnością oceny](../c-language/precedence-and-order-of-evaluation.md)). Na przykład efekty uboczne występują w następujących wywołaniach funkcji:

```
add( i + 1, i = j + 2 );
myproc( getc(), getc() );
```

Argumenty wywołania funkcji można ocenić w dowolnej kolejności. Wyrażenie `i + 1` może być oceniane przed `i = j + 2`, lub `i = j + 2` może być oceniane przed. `i + 1` W każdym przypadku wynik jest różny. Podobnie nie jest możliwe zagwarantowanie, jakie znaki są faktycznie przesyłane do `myproc`. Ponieważ operacje przyrostu jednoargumentowego i zmniejszania obejmują przydziały, operacje te mogą powodować efekty uboczne, jak pokazano w następującym przykładzie:

```
x[i] = i++;
```

W tym przykładzie wartość `x` modyfikowana jest nieprzewidywalne. Wartość indeksu dolnego może być nową lub starą wartością `i`. Wyniki mogą się różnić w zależności od różnych kompilatorów lub różnych poziomów optymalizacji.

Ponieważ C nie definiuje kolejności oceny efektów ubocznych, obie metody oceny omówione powyżej są poprawne i mogą być zaimplementowane. Aby upewnić się, że kod jest przenośny i czysty, należy unikać instrukcji, które są zależne od określonej kolejności oceny efektów ubocznych.

## <a name="see-also"></a>Zobacz też

[Obliczanie wyrażeń](../c-language/expression-evaluation-c.md)
