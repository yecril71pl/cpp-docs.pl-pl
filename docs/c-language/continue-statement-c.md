---
title: continue — instrukcja (C)
ms.date: 11/04/2016
f1_keywords:
- continue
helpviewer_keywords:
- loop structures, continue keyword
- continue keyword [C]
ms.assetid: 969f293a-45fe-48a7-b4c6-287ba27a631d
ms.openlocfilehash: 27d1d0aa0e49c5c46e4ea4e010635ca0057c3f85
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684836"
---
# <a name="continue-statement-c"></a>continue — instrukcja (C)

**`continue`** Instrukcja przekazuje formant do następnej iteracji najbliższej otaczającej **`do`** , **`for`** lub **`while`** instrukcji, w której występuje, pomijając wszystkie pozostałe instrukcje w **`do`** **`for`** treści instrukcji,, lub **`while`** .

## <a name="syntax"></a>Składnia

*skok-instrukcja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**utrzymać**

Kolejna iteracja **`do`** **`for`** instrukcji,, lub **`while`** jest określona w następujący sposób:

- W **`do`** **`while`** instrukcji lub, następna iteracja jest uruchamiana przez ponowną ocenę wyrażenia **`do`** **`while`** instrukcji or.

- **`continue`** Instrukcja w **`for`** instrukcji powoduje, że wyrażenie pętli **`for`** instrukcji jest oceniane. Następnie kompilator ponownie oblicza wyrażenie warunkowe i, w zależności od wyniku, kończy lub iteruje treść instrukcji. Zapoznaj [się z instrukcją](../c-language/for-statement-c.md) for, aby uzyskać więcej informacji na temat **`for`** instrukcji i jej nieterminalu.

Jest to przykład **`continue`** instrukcji:

```C
while ( i-- > 0 )
{
    x = f( i );
    if ( x == 1 )
        continue;
    y += x * x;
}
```

W tym przykładzie treść instrukcji jest wykonywana, gdy `i` wartość jest większa niż 0. Pierwszy `f(i)` jest przypisany do `x` , a następnie, jeśli `x` jest równa 1, **`continue`** instrukcja jest wykonywana. Pozostałe instrukcje w treści są ignorowane, a wykonywanie jest wznawiane w górnej części pętli z oceną testu pętli.

## <a name="see-also"></a>Zobacz także

[Continue — instrukcja](../cpp/continue-statement-cpp.md)
