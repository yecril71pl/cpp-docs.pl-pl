---
title: Sekwencje znaków
ms.date: 11/04/2016
ms.assetid: 1e6961a9-150e-4c13-b427-9af4b6a1fb7a
ms.openlocfilehash: 42fb6b61771feb3eaedfb4ce1e674003df91b263
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62312690"
---
# <a name="character-sequences"></a>Sekwencje znaków

**3.8.2 ANSI** Mapowanie sekwencji znaków pliku źródłowego

Instrukcje preprocesora używają tego samego zestawu znaków jako instrukcji pliku źródłowego z wyjątkiem tego, że sekwencje ucieczki nie są obsługiwane.

Aby określić ścieżkę do pliku dołączanego, należy użyć tylko jednego ukośnika odwrotnego:

```
#include "path1\path2\myfile"
```

W ramach kodu źródłowego wymagane są dwa ukośniki odwrotne:

```
fil = fopen( "path1\\path2\\myfile", "rt" );
```

## <a name="see-also"></a>Zobacz też

[Dyrektywy przetwarzania wstępnego](../c-language/preprocessing-directives.md)
