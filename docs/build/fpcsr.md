---
title: FpCsr
ms.date: 11/04/2016
ms.assetid: dff95d5d-7589-4432-82db-64b459c24352
ms.openlocfilehash: 018ce39a194d5153f73fa452990844362190e6bd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472825"
---
# <a name="fpcsr"></a>FpCsr

Stan Rejestr zawiera również x87 FPU słowa sterującego. Konwencja wywoływania nakazują tego Zarejestruj się w nieulotnej.

Wykonywanie programu x87 rejestr słowo sterowania FPU jest ustawiony na następujące standardowe wartości na początku:

```
FPCSR[0:6]: Exception masks all 1's (all exceptions masked)
FPCSR[7]: Reserved - 0
FPCSR[8:9]: Precision Control - 10B (double precision)
FPCSR[10:11]: Rounding  control - 0 (round to nearest)
FPCSR[12]: Infinity control - 0 (not used)
```

/ / Wywoływany modyfikującego pól w FPCSR należy przywrócić je przed zwróceniem do obiektu wywołującego. Ponadto obiekt wywołujący, który zmodyfikował tych pól należy przywrócić ich standardowe wartości przed wywołaniem / / wywoływany, chyba że umowie wywoływany oczekuje zmodyfikowane wartości.

Istnieją dwa wyjątki reguł dotyczących innych zmienności flagi kontrolne:

1. W funkcjach, gdzie jest udokumentowane celem daną funkcję do modyfikowania nieulotnej FpCsr flag.

1. Gdy jest zgodność poprawne, że programy, które zachowuje się/oznacza, że taka sama jak program, gdy te zasady są nie naruszone, na przykład dzięki analizie całego programu powoduje naruszenie niniejszych zasad.

## <a name="see-also"></a>Zobacz też

[Konwencja wywoływania](../build/calling-convention.md)