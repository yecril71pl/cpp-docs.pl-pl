---
title: Znaki specjalne w makrach | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- special characters, in NMAKE macros
ms.assetid: c0a06cfc-7103-4ee2-a585-e8f6e85dccd7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 55a94001e2f912049518120911c25ae64afa24da
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45721431"
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