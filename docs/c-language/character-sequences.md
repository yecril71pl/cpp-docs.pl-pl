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

**ANSI 3.8.2** mapowanie sekwencje znaków pliku źródłowego

Instrukcje preprocesora używają ten sam znak, ustaw jak instrukcje pliku źródłowego z powodu wyjątku, sekwencje unikowe, które nie są obsługiwane.

W związku z tym aby określić ścieżkę dla pliku dołączanego, należy użyć tylko jednej kreski ułamkowej odwróconej:

```
#include "path1\path2\myfile"
```

W kodzie źródłowym niezbędne są dwa ukośniki odwrotne:

```
fil = fopen( "path1\\path2\\myfile", "rt" );
```

## <a name="see-also"></a>Zobacz także

[Dyrektywy przetwarzania wstępnego](../c-language/preprocessing-directives.md)
