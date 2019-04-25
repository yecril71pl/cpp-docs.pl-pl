---
title: Skutki uboczne zależności
ms.date: 11/04/2016
helpviewer_keywords:
- dependencies, side effects
- NMAKE program, dependents
ms.assetid: d4e8db25-fdc0-4d73-81ec-1538f2e1b3e8
ms.openlocfilehash: b89306b6e4d85e0e08729fb1d35fb041d69647e7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272116"
---
# <a name="dependency-side-effects"></a>Skutki uboczne zależności

Jeśli obiekt docelowy jest określony za pomocą dwukropka (:) w dwóch wierszach zależności w różnych lokalizacjach i polecenia pojawiają się po tylko jeden z wierszy, NMAKE interpretuje zależności, tak, jakby sąsiadujące lub połączone. Nie jest wywoływany reguły wnioskowania dla zależności, która nie ma żadnych poleceń, ale zamiast tego założono, że zależności należą do bloku jeden opis i wykonuje polecenia określone w przypadku innych zależności. Na przykład ten zestaw reguł:

```Output
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
```

jest oceniane jako to:

```Output
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

W tym celu nie występuje w przypadku podwójny dwukropek (`::`) jest używany. Na przykład ten zestaw reguł:

```Output
bounce.exe :: jump.obj
   echo Building bounce.exe...

bounce.exe :: up.obj
```

jest oceniane jako to:

```Output
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
# invokes an inference rule
```

## <a name="see-also"></a>Zobacz także

[Docelowe elementy](targets.md)
