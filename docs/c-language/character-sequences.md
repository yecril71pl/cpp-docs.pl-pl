---
title: Znak sekwencji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 1e6961a9-150e-4c13-b427-9af4b6a1fb7a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5cf3b52b8a4e76062d06b0b9ca3d4535b79595c5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061516"
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