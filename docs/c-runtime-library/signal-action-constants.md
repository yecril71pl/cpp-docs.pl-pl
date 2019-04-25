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
ms.openlocfilehash: 4ff79626d576a05744336d36f99caf95d9b9902d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62267992"
---
# <a name="signal-action-constants"></a>Stałe akcji sygnałów

Akcję wykonywaną po odebraniu sygnału przerwania zależy od wartości `func`.

## <a name="syntax"></a>Składnia

```
#include <signal.h>
```

## <a name="remarks"></a>Uwagi

`func` Argument musi mieć adres funkcji lub jeden stałych manifestu wymienionych poniżej i zdefiniowane w sygnału. H.

|||
|-|-|
| `SIG_DFL`  | Używa domyślnej system odpowiedzi. Jeśli program wywołujący używa strumienia we/wy, buforów utworzonych przez bibliotekę uruchomieniową nie zostały przesłane.  |
| `SIG_IGN`  | Ignores interrupt signal. Ta wartość nigdy nie powinien być podawany dla `SIGFPE`, ponieważ stan zapisu zmiennoprzecinkowego procesu zostanie pozostawiony niezdefiniowane.  |
| `SIG_SGE`  | Wskazuje, że wystąpił błąd w sygnale.  |
| `SIG_ACK`  | Wskazuje, że otrzymano potwierdzenia.  |
| `SIG_ERR`  | Typem zwracanym od sygnałów, co wskazuje na błąd wystąpił.  |

## <a name="see-also"></a>Zobacz także

[signal](../c-runtime-library/reference/signal.md)<br/>
[Stałe globalne](../c-runtime-library/global-constants.md)
