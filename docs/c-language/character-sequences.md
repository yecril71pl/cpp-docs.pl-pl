---
title: Sekwencje znaków
ms.date: 11/04/2016
ms.assetid: 1e6961a9-150e-4c13-b427-9af4b6a1fb7a
ms.openlocfilehash: 42fb6b61771feb3eaedfb4ce1e674003df91b263
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149939"
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
