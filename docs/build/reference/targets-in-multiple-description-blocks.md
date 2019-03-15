---
title: Obiekty docelowe w Blokach opisów
ms.date: 11/04/2016
helpviewer_keywords:
- description blocks
- blocks, multiple description
- multiple description blocks
ms.assetid: 8618dcd9-c11d-4562-91a7-0c904ed438a8
ms.openlocfilehash: 03a6e1d0be44e12bb76767b7334ab647a6054b6e
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823816"
---
# <a name="targets-in-multiple-description-blocks"></a>Obiekty docelowe w Blokach opisów

Aby zaktualizować element docelowy w więcej niż jednego bloku opis przy użyciu różnych poleceń, określ dwóch następujących po sobie dwukropek (:) między elementy docelowe i zależności.

```
target.lib :: one.asm two.asm three.asm
    ml one.asm two.asm three.asm
    lib target one.obj two.obj three.obj
target.lib :: four.c five.c
    cl /c four.c five.c
    lib target four.obj five.obj
```

## <a name="see-also"></a>Zobacz także

[Docelowe elementy](targets.md)
