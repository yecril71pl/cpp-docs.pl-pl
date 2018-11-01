---
title: Wiele obiektów docelowych
ms.date: 11/04/2016
helpviewer_keywords:
- makefiles, targets
- multiple targets in NMAKE
- targets, multiple in NMAKE
- NMAKE program, targets
ms.assetid: b609a179-0b9f-4b08-9930-998047588ae0
ms.openlocfilehash: 2762e458781e3a95f478ea3477fc8ef02f9196fb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50645067"
---
# <a name="multiple-targets"></a>Wiele obiektów docelowych

NMAKE ocenia wiele obiektów docelowych w jednym zależności, tak, jakby każdy zostały określone w bloku oddzielne opis.

Na przykład to...

```Output
bounce.exe leap.exe : jump.obj
   echo Building...
```

.. jest standardem ocenione ponieważ:

```Output
bounce.exe : jump.obj
   echo Building...
leap.exe : jump.obj
   echo Building...
```

## <a name="see-also"></a>Zobacz też

[Docelowe elementy](../build/targets.md)