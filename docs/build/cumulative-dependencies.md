---
title: Zależności zbiorcze
ms.date: 11/04/2016
helpviewer_keywords:
- dependencies, cumulative
- cumulative dependencies in NMAKE
- dependencies
ms.assetid: fa6dd777-80b8-437d-87a7-aec0ed818a49
ms.openlocfilehash: c31740b830993c91568aea6d167fd3113b04fc57
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460284"
---
# <a name="cumulative-dependencies"></a>Zależności zbiorcze

Zależności kumulują się w bloku opisu, jeśli obiekt docelowy jest powtarzany.

Na przykład ten zestaw reguł

```Output
bounce.exe : jump.obj
bounce.exe : up.obj
   echo Building bounce.exe...
```

jest oceniane jako to:

```Output
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

Wiele elementów docelowych w wielu wierszach zależności w bloku jeden opis są oceniane tak, jakby każdy zostały określone w bloku oddzielne opis, ale obiektów docelowych, które nie znajdują się w ostatnim wierszu zależności nie należy używać blok poleceń. NMAKE próbuje użyć reguły wnioskowania dla tych celów.

Na przykład ten zestaw reguł

```Output
leap.exe bounce.exe : jump.obj
bounce.exe climb.exe : up.obj
   echo Building bounce.exe...
```

jest oceniane jako to:

```Output

leap.exe : jump.obj
# invokes an inference rule
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
climb.exe : up.obj
   echo Building bounce.exe...
```

## <a name="see-also"></a>Zobacz też

[Docelowe elementy](../build/targets.md)