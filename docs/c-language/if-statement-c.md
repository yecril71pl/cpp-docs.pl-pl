---
title: Jeśli Statement (C) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- else
- if
dev_langs:
- C++
helpviewer_keywords:
- if keyword [C]
- else clauses
- else keyword [C]
- if keyword [C], if statement syntax
- nested statements
ms.assetid: d7fc16a0-fdbc-4f39-b596-76e1ca4ad4a5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 98b01db4d842775dcb239aef9d40c661328d1544
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46107882"
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

## <a name="see-also"></a>Zobacz też

[if-else, instrukcja (C++)](../cpp/if-else-statement-cpp.md)