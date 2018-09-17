---
title: MxCsr | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 4f3c229d-0862-4733-acc7-9ed7a0b870ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0d18a4247d36e6894230d74322d52cd5854e42fb
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726508"
---
# <a name="mxcsr"></a>MxCsr

Stan Rejestr zawiera również MxCsr. Konwencja wywoływania dzieli tego rejestru na volatile części i nieulotnej części. Część volatile składa się z flagi stanu 6, MXCSR [0:5], a w pozostałej części rejestru MXCSR [6:15] jest uznawany za nieulotnej.

Na początku wykonywania programu nieulotnej część ma wartość standardowe następujące wartości:

```
MXCSR[6]         : Denormals are zeros - 0
MXCSR[7:12]      : Exception masks all 1's (all exceptions masked)
MXCSR[13:14]   : Rounding  control - 0 (round to nearest)
MXCSR[15]      : Flush to zero for masked underflow - 0 (off)
```

/ / Wywoływany, który modyfikuje znajdujących się w nieulotnej pól w mxcsr rejestru należy przywrócić je przed zwróceniem do obiektu wywołującego. Ponadto obiekt wywołujący, który zmodyfikował tych pól należy przywrócić ich standardowe wartości przed wywołaniem / / wywoływany, chyba że umowie wywoływany oczekuje zmodyfikowane wartości.

Istnieją dwa wyjątki reguł dotyczących innych zmienności flagi kontrolne:

- W funkcjach, gdzie jest udokumentowane celem daną funkcję do modyfikowania nieulotnej MxCsr flag.

- Gdy jest zgodność poprawne, że programy, które zachowuje się/oznacza, że taka sama jak program, gdy te zasady są nie naruszone, na przykład dzięki analizie całego programu powoduje naruszenie niniejszych zasad.

Nie można wykonać o stanie volatile część MXCSR granicę funkcji, chyba że wyraźnie określonych w dokumentacji funkcji.

## <a name="see-also"></a>Zobacz też

[Konwencja wywoływania](../build/calling-convention.md)