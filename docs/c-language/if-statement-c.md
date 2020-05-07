---
title: if — instrukcja (C)
ms.date: 11/04/2016
f1_keywords:
- else
- if
helpviewer_keywords:
- if keyword [C]
- else clauses
- else keyword [C]
- if keyword [C], if statement syntax
- nested statements
ms.assetid: d7fc16a0-fdbc-4f39-b596-76e1ca4ad4a5
ms.openlocfilehash: b6df50d483a6e2958de3100a07c18b89b0c4f12f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233063"
---
# <a name="if-statement-c"></a>if — instrukcja (C)

Instrukcja **if** kontroluje rozgałęzienie warunkowe. Treść instrukcji **if** jest wykonywana, jeśli wartość wyrażenia jest różna od zera. Składnia instrukcji **if** ma dwa formy.

## <a name="syntax"></a>Składnia

SELECT *-Statement*: **if (***wyrażenie***)***instrukcja*      

**if (***wyrażenie***)***instrukcja***else***statement*          

W obu formach instrukcji **if** , wyrażenia, które mogą mieć dowolną wartość z wyjątkiem struktury, są oceniane, łącznie ze wszystkimi efektami ubocznymi.

W pierwszej postaci składni, jeśli *wyrażenie* jest prawdziwe (niezerowe), *instrukcja* jest wykonywana. Jeśli *wyrażenie* ma wartość false, *instrukcja* jest ignorowana. W drugiej formie składni, która używa **innych**, druga *instrukcja* jest wykonywana, jeśli *wyrażenie* ma wartość false. W obu formularzach kontrolki są przekazywane z instrukcji **if** do następnej instrukcji w programie, chyba że jedna z instrukcji zawiera **Break**, **Continue**lub `goto`.

Poniżej przedstawiono przykłady instrukcji **if** :

```
if ( i > 0 )
    y = x / i;
else
{
    x = i;
    y = f( x );
}
```

W tym przykładzie instrukcja `y = x/i;` jest wykonywana, jeśli `i` jest większa niż 0. Jeśli `i` jest mniejsza lub `i` równa 0, jest przypisana do `x` i `f( x )` jest przypisywana `y`do. Należy zauważyć, że instrukcja tworząca klauzulę **if** kończą się średnikiem.

Podczas zagnieżdżania instrukcji **if** i **else** klauzule, należy użyć nawiasów klamrowych, aby zgrupować instrukcje i klauzule do złożonych instrukcji, które wyjaśniają zamiar. Jeśli nie ma żadnych nawiasów klamrowych, kompilator rozpoznaje niejasności, kojarząc każdy **inny** z najbliższy, **Jeśli** nie ma **innych**.

```
if ( i > 0 )           /* Without braces */
    if ( j > i )
        x = j;
    else
        x = i;
```

Klauzula **else** jest skojarzona z wewnętrzną instrukcją **if** w tym przykładzie. Jeśli `i` jest mniejsza lub równa 0, żadna wartość nie jest przypisana `x`do.

```
if ( i > 0 )
{                      /* With braces */
    if ( j > i )
        x = j;
}
else
    x = i;
```

Nawiasy otaczające wewnętrzną instrukcję **if** w tym przykładzie tworzą klauzulę **else** instrukcji Outer **if** . Jeśli `i` jest mniejsza lub równa 0, `i` jest przypisana do `x`.

## <a name="see-also"></a>Zobacz też

[if-else — instrukcja (C++)](../cpp/if-else-statement-cpp.md)
