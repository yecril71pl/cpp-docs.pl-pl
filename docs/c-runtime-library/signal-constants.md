---
title: sygnał — Stałe
ms.date: 11/04/2016
f1_keywords:
- SIGTERM
- SIGFPE
- SIGABRT
- SIGILL
- SIGINT
- SIGSEGV
helpviewer_keywords:
- SIGTERM constant
- SIGABRT constant
- SIGSEGV constant
- SIGFPE constant
- SIGINT constant
- signal constants
- SIGILL constant
ms.assetid: a3b39281-dae7-4e44-8d68-e6a610c669dd
ms.openlocfilehash: 1046a12fa0f250b348e6ff171c8865e3eb5ff4b3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482674"
---
# <a name="signal-constants"></a>sygnał — Stałe

## <a name="syntax"></a>Składnia

```
#include <signal.h>
```

## <a name="remarks"></a>Uwagi

`sig` Argument musi być w jednej ze stałych manifestu, wymienionych poniżej (zdefiniowana na sygnał. GODZ.).

|||
|-|-|
|SIGABRT|Nienormalne zakończenie. Domyślna akcja kończy program wywołujący kodem zakończenia 3.  |
|SIGABRT_COMPAT|Taka sama jak SIGABRT. Zgodność z innymi platformami.  |
|SIGFPE|Błąd zmiennoprzecinkowy, takich jak przepełnienia, dzielenie przez zero lub nieprawidłowa operacja. Domyślna akcja kończy program wywołujący.  |
|SIGILL|Niedozwolona instrukcja. Domyślna akcja kończy program wywołujący.  |
|SIGINT|CTRL + C przerywa. Domyślna akcja kończy program wywołujący kodem zakończenia 3.  |
|SIGSEGV|Niedozwolony dostęp do magazynu. Domyślna akcja kończy program wywołujący.  |
|SIGTERM|Zakończenie żądania wysłanego do programu. Domyślna akcja kończy program wywołujący kodem zakończenia 3.  |
|SIG_ERR|Typem zwracanym od sygnałów, co wskazuje na błąd wystąpił.  |

## <a name="see-also"></a>Zobacz też

[signal](../c-runtime-library/reference/signal.md)<br/>
[raise](../c-runtime-library/reference/raise.md)<br/>
[Stałe globalne](../c-runtime-library/global-constants.md)