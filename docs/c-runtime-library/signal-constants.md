---
title: sygnał — stałe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- SIGTERM
- SIGFPE
- SIGABRT
- SIGILL
- SIGINT
- SIGSEGV
dev_langs:
- C++
helpviewer_keywords:
- SIGTERM constant
- SIGABRT constant
- SIGSEGV constant
- SIGFPE constant
- SIGINT constant
- signal constants
- SIGILL constant
ms.assetid: a3b39281-dae7-4e44-8d68-e6a610c669dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: defd5f630f1d3832014e2cc7e9746c0e00e8d816
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070668"
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