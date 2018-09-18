---
title: stdin, stdout, stderr | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- stdin
- stderr
- stdout
dev_langs:
- C++
helpviewer_keywords:
- stdout function
- standard output stream
- standard error stream
- stdin function
- standard input stream
- stderr function
ms.assetid: badd4735-596d-4498-857c-ec8b7e670e4c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a36d5fd60a19222e6f802e5a14037fb01ff865f5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071981"
---
# <a name="stdin-stdout-stderr"></a>stdin, stdout, stderr

## <a name="syntax"></a>Składnia

```

      FILE *stdin; 
FILE *stdout; 
FILE *stderr; 
#include <stdio.h>
```

## <a name="remarks"></a>Uwagi

Są to standardowych strumieni danych wejściowych, danych wyjściowych i dane wyjściowe błędu.

Domyślnie standardowe dane wejściowe są odczytywane z klawiatury, podczas gdy wyjście standardowe i błąd standardowy są drukowane na ekranie.

Następujące wskaźniki strumienia są dostępne dla dostępu do standardowych strumieni:

|Wskaźnik|Strumień|
|-------------|------------|
|`stdin`|Standardowe dane wejściowe|
|**STDOUT**|Standardowe dane wyjściowe|
|`stderr`|Standardowy błąd|

Te wskaźniki może służyć jako argumenty funkcji. Niektóre funkcje, takie jak **getchar** i `putchar`, użyj `stdin` i **stdout** automatycznie.

Te wskaźniki są stałe i nie można przypisać nowe wartości. `freopen` Funkcja może służyć do przekierowania strumieni plików na dysku lub innych urządzeń. System operacyjny umożliwia przekierowywanie standardowe dane wejściowe i dane wyjściowe na poziomie polecenia programu.

## <a name="see-also"></a>Zobacz też

[Stream operacji We/Wy](../c-runtime-library/stream-i-o.md)<br/>
[Stałe globalne](../c-runtime-library/global-constants.md)