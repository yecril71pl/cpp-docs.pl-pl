---
title: continue — instrukcja (C)
ms.date: 11/04/2016
f1_keywords:
- continue
helpviewer_keywords:
- loop structures, continue keyword
- continue keyword [C]
ms.assetid: 969f293a-45fe-48a7-b4c6-287ba27a631d
ms.openlocfilehash: 983775e6fe9887afa5784358ede1de9583b3afba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62312566"
---
# <a name="continue-statement-c"></a>continue — instrukcja (C)

`continue` Instrukcji przekazuje kontrolę do następnej iteracji najbliższej otaczającej `do`, `for`, lub `while` instrukcji, w której występuje, dowolnej pozostałych instrukcji z pominięciem `do`, `for`, lub `while` treść instrukcji.

## <a name="syntax"></a>Składnia

*Instrukcja skoku*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Kontynuuj;**

Następnej iteracji `do`, `for`, lub `while` instrukcji jest określany w następujący sposób:

- W ramach `do` lub `while` instrukcji następnej iteracji należy zacząć od reevaluating wyrażenie `do` lub `while` instrukcji.

- A `continue` instrukcji w `for` instrukcji powoduje, że wyrażenie pętli `for` instrukcji, które ma zostać obliczone. Następnie kompilator reevaluates wyrażenia warunkowego, w zależności od wyniku albo kończy się i wykonuje iterację w treści instrukcji. Zobacz [dla instrukcji](../c-language/for-statement-c.md) więcej informacji na temat `for` instrukcji i jego symboli nieterminalnych.

Jest to przykład `continue` instrukcji:

```
while ( i-- > 0 )
{
    x = f( i );
    if ( x == 1 )
        continue;
    y += x * x;
}
```

W tym przykładzie zostaje wykonana instrukcja podczas `i` jest większa niż 0. Pierwszy `f(i)` jest przypisany do `x`; a, w przypadku `x` jest równa 1, `continue` instrukcja jest wykonywana. Resztę instrukcji w treści są ignorowane i wykonanie zostanie wznowione u góry pętli z oceną test pętli.

## <a name="see-also"></a>Zobacz także

[continue, instrukcja](../cpp/continue-statement-cpp.md)
