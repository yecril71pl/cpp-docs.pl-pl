---
title: Zależności zbiorcze | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dependencies, cumulative
- cumulative dependencies in NMAKE
- dependencies
ms.assetid: fa6dd777-80b8-437d-87a7-aec0ed818a49
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5a66b153a52da06cca14845b9a58fcef0f42676d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725715"
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