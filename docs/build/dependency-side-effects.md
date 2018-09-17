---
title: Skutki uboczne zależności | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dependencies, side effects
- NMAKE program, dependents
ms.assetid: d4e8db25-fdc0-4d73-81ec-1538f2e1b3e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9a70df679434b187bc2eee4eb4aad5881db0da1c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716541"
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

## <a name="see-also"></a>Zobacz też

[Docelowe elementy](../build/targets.md)