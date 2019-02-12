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
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152615"
---
# <a name="if-statement-c"></a>if — instrukcja (C)

**Jeśli** instrukcji kontroluje rozgałęzień warunkowych. Treść **Jeśli** instrukcja jest wykonywana w przypadku wartości wyrażenia jest różna od zera. Składnia **Jeśli** instrukcji ma dwie formy.

## <a name="syntax"></a>Składnia

*Wybór instrukcji*: **Jeśli (***wyrażenie***)***— instrukcja*

**Jeśli (***wyrażenie***)***instrukcji***else***— instrukcja*

W obu formach **Jeśli** instrukcji i wyrażeń, które mogą mieć dowolną wartość z wyjątkiem struktury, są oceniane, łącznie ze wszystkimi efektami ubocznymi.

W pierwszej formie składni Jeśli *wyrażenie* ma wartość true (niezerową), *instrukcji* jest wykonywany. Jeśli *wyrażenie* ma wartość FAŁSZ, *instrukcji* jest ignorowana. W drugim formularzu składni, który używa **else**, drugi *instrukcji* jest wykonywana w przypadku *wyrażenie* ma wartość false. Za pomocą obie formy kontrolować następnie — dostęp próbny od **Jeśli** instrukcji do następnej instrukcji w programie dopóki jedno z oświadczeń zawiera **podziału**, **nadal**, lub `goto`.

Poniżej przedstawiono przykłady **Jeśli** instrukcji:

```
if ( i > 0 )
    y = x / i;
else
{
    x = i;
    y = f( x );
}
```

W tym przykładzie instrukcja `y = x/i;` jest wykonywana w przypadku `i` jest większa niż 0. Jeśli `i` jest mniejsza niż lub równe 0, `i` jest przypisany do `x` i `f( x )` jest przypisany do `y`. Należy pamiętać, że instrukcja tworzących **Jeśli** klauzuli kończy się średnikiem.

Podczas zagnieżdżania **Jeśli** instrukcji i **else** klauzule ujmować w nawiasy klamrowe do instrukcji i klauzule w złożonej instrukcji, które Sprecyzuj usługi. Jeśli istnieją nie nawiasów klamrowych, kompilator rozwiązuje niejasności, kojarząc każdego **else** z najbliższą **Jeśli** bez **else**.

```
if ( i > 0 )           /* Without braces */
    if ( j > i )
        x = j;
    else
        x = i;
```

**Else** klauzula jest skojarzony z wewnętrzny **Jeśli** instrukcji w tym przykładzie. Jeśli `i` jest mniejszy niż lub równy 0, zostanie przypisana żadna wartość, aby `x`.

```
if ( i > 0 )
{                      /* With braces */
    if ( j > i )
        x = j;
}
else
    x = i;
```

Nawiasów klamrowych otaczających wewnętrzny **Jeśli** instrukcji w tym przykładzie wprowadź **else** klauzuli część zewnętrzny **Jeśli** instrukcji. Jeśli `i` jest mniejsza niż lub równe 0, `i` jest przypisany do `x`.

## <a name="see-also"></a>Zobacz także

[if-else, instrukcja (C++)](../cpp/if-else-statement-cpp.md)
