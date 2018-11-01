---
title: Sekwencje znaków
ms.date: 11/04/2016
ms.assetid: 1e6961a9-150e-4c13-b427-9af4b6a1fb7a
ms.openlocfilehash: dea24a2ae5887ea8c0111d8251ba4d9d03ccba0f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50489664"
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

## <a name="see-also"></a>Zobacz też

[Dyrektywy przetwarzania wstępnego](../c-language/preprocessing-directives.md)