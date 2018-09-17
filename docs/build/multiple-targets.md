---
title: Wiele elementów docelowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- makefiles, targets
- multiple targets in NMAKE
- targets, multiple in NMAKE
- NMAKE program, targets
ms.assetid: b609a179-0b9f-4b08-9930-998047588ae0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 66849bdbe28ac2bd965714de56f962df98ced133
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703667"
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