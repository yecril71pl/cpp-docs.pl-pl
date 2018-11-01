---
title: Znaki specjalne w makrach
ms.date: 11/04/2016
helpviewer_keywords:
- special characters, in NMAKE macros
ms.assetid: c0a06cfc-7103-4ee2-a585-e8f6e85dccd7
ms.openlocfilehash: bc40a4d2c3197f0cc85099d0a89ab511f3acf81c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555093"
---
# <a name="special-characters-in-macros"></a>Znaki specjalne w makrach

Numer Zaloguj (#), po definicji określa komentarz. Aby określić znak numeru literału w makrze, użyj daszek (^), podobnie jak w ^ #.

Określa znak dolara ($), wywołanie makra. Aby określić literał $, użyj $$.

Aby rozszerzyć definicji do nowego wiersza, zakończenia wiersza znakiem kreski ułamkowej odwróconej (\\). Po wywołaniu makra znak ukośnika odwrotnego oraz nowego wiersza jest zastępowany spację. Aby określić literału ukośnik odwrotny na końcu wiersza, należy poprzedzić znak daszka (^), lub należy postępować zgodnie ze specyfikatorem komentarza (#).

Aby określić znak literału nowego wiersza, zakończenia wiersza z daszkiem (^), jak w programie:

```
CMDS = cls^
dir
```

## <a name="see-also"></a>Zobacz też

[Definiowanie makro NMAKE](../build/defining-an-nmake-macro.md)