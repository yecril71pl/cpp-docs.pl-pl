---
title: Stałe akcji sygnałów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- SIG_IGN
- SIG_DFL
dev_langs:
- C++
helpviewer_keywords:
- signal action constants
- SIG_IGN constant
- SIG_DFL constant
ms.assetid: c3cb4f15-d39e-4d9d-84f9-0d33e3eb5993
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f2cb8e8ca907081e85be03d7576d0252cdf20ad
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081321"
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
| `SIG_IGN`  | Ignoruje sygnał przerwania. Ta wartość nigdy nie powinien być podawany dla `SIGFPE`, ponieważ stan zapisu zmiennoprzecinkowego procesu zostanie pozostawiony niezdefiniowane.  |
| `SIG_SGE`  | Wskazuje, że wystąpił błąd w sygnale.  |
| `SIG_ACK`  | Wskazuje, że otrzymano potwierdzenia.  |
| `SIG_ERR`  | Typem zwracanym od sygnałów, co wskazuje na błąd wystąpił.  |

## <a name="see-also"></a>Zobacz też

[signal](../c-runtime-library/reference/signal.md)<br/>
[Stałe globalne](../c-runtime-library/global-constants.md)