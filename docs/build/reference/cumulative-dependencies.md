---
title: Zależności zbiorcze
ms.date: 11/04/2016
helpviewer_keywords:
- dependencies, cumulative
- cumulative dependencies in NMAKE
- dependencies
ms.assetid: fa6dd777-80b8-437d-87a7-aec0ed818a49
ms.openlocfilehash: de0a9649be8f0dae58f45d8980d2df610ff2febe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294086"
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

## <a name="see-also"></a>Zobacz także

[Docelowe elementy](targets.md)
