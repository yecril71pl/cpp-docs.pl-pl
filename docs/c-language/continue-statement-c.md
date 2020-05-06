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

`continue` Instrukcja przekazuje formant `do`do następnej iteracji najbliższej otaczającej, `for`lub `while` instrukcji, w której występuje, pomijając wszystkie pozostałe instrukcje w treści instrukcji `do`, `for`, lub. `while`

## <a name="syntax"></a>Składnia

*skok-instrukcja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**utrzymać**

Kolejna iteracja instrukcji `do`, `for`, lub `while` jest określona w następujący sposób:

- W `do` `while` instrukcji lub, następna iteracja jest uruchamiana przez ponowną ocenę wyrażenia instrukcji `do` or. `while`

- `continue` Instrukcja w `for` instrukcji powoduje, że wyrażenie pętli `for` instrukcji jest oceniane. Następnie kompilator ponownie oblicza wyrażenie warunkowe i, w zależności od wyniku, kończy lub iteruje treść instrukcji. Zapoznaj [się z instrukcją](../c-language/for-statement-c.md) for, aby `for` uzyskać więcej informacji na temat instrukcji i jej nieterminalu.

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

W tym przykładzie treść instrukcji jest wykonywana, gdy `i` wartość jest większa niż 0. Pierwszy `f(i)` jest przypisany do `x`; następnie, jeśli `x` jest równa 1, `continue` instrukcja zostanie wykonana. Pozostałe instrukcje w treści są ignorowane, a wykonywanie jest wznawiane w górnej części pętli z oceną testu pętli.

## <a name="see-also"></a>Zobacz też

[Continue — instrukcja](../cpp/continue-statement-cpp.md)
