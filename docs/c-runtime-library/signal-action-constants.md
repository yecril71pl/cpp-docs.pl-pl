---
title: Stałe akcji sygnałów
ms.date: 11/04/2016
f1_keywords:
- SIG_IGN
- SIG_DFL
helpviewer_keywords:
- signal action constants
- SIG_IGN constant
- SIG_DFL constant
ms.assetid: c3cb4f15-d39e-4d9d-84f9-0d33e3eb5993
ms.openlocfilehash: a7448730501d6f3b50008966134f708ae99ddb5b
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88830764"
---
# <a name="signal-action-constants"></a>Stałe akcji sygnałów

Akcja podejmowana po odebraniu sygnału przerwania zależy od wartości `func` .

## <a name="syntax"></a>Składnia

```
#include <signal.h>
```

## <a name="remarks"></a>Uwagi

`func`Argument musi być adresem funkcji lub jedną ze stałych manifestu wymienionych poniżej i zdefiniowanym w sygnale. C.

|Stała|Opis|
|-|-|
| `SIG_DFL`  | Używa domyślnej odpowiedzi systemowej. Jeśli program wywołujący korzysta ze strumienia we/wy, bufory utworzone przez bibliotekę wykonawczą nie są opróżniane.  |
| `SIG_IGN`  | Ignoruje sygnał przerwania. Ta wartość nigdy nie powinna być określona `SIGFPE` , ponieważ stan zmiennoprzecinkowy procesu jest niezdefiniowany.  |
| `SIG_SGE`  | Wskazuje, że w sygnale Wystąpił błąd.  |
| `SIG_ACK`  | Wskazuje, że Odebrano potwierdzenie.  |
| `SIG_ERR`  | Wystąpił zwracany typ z sygnału wskazującego na błąd.  |

## <a name="see-also"></a>Zobacz też

[sygnał](../c-runtime-library/reference/signal.md)<br/>
[Stałe globalne](../c-runtime-library/global-constants.md)
