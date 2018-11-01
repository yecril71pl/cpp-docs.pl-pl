---
title: stdin, stdout, stderr
ms.date: 10/23/2018
f1_keywords:
- stdin
- stderr
- stdout
helpviewer_keywords:
- stdout function
- standard output stream
- standard error stream
- stdin function
- standard input stream
- stderr function
ms.assetid: badd4735-596d-4498-857c-ec8b7e670e4c
ms.openlocfilehash: 0ecb7c51f6c38ffcb6637a093ec06a6f248839d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452198"
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
|`stdout`|Standardowe dane wyjściowe|
|`stderr`|Standardowy błąd|

Te wskaźniki może służyć jako argumenty funkcji. Niektóre funkcje, takie jak [getchar](../c-runtime-library/reference/getchar-getwchar.md) i [putchar](../c-runtime-library/reference/putchar-putwchar.md), użyj `stdin` i `stdout` automatycznie.

Te wskaźniki są stałe i nie można przypisać nowe wartości. [Freopen —](../c-runtime-library/reference/freopen-wfreopen.md) funkcja może służyć do przekierowania strumieni plików na dysku lub innych urządzeń. System operacyjny umożliwia przekierowywanie standardowe dane wejściowe i dane wyjściowe na poziomie polecenia programu.

## <a name="see-also"></a>Zobacz też

[Stream operacji We/Wy](../c-runtime-library/stream-i-o.md)<br/>
[Stałe globalne](../c-runtime-library/global-constants.md)
