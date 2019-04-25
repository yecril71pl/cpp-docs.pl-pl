---
title: imaxabs
ms.date: 04/05/2018
apiname:
- imaxabs
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- imaxabs
helpviewer_keywords:
- imaxabs function
ms.assetid: de2566a3-1415-4e9a-91b5-7ac3a49ebf5e
ms.openlocfilehash: a7492e08c3a078698292923ce395524ab5327ecf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157503"
---
# <a name="imaxabs"></a>imaxabs

Oblicza wartość bezwzględną liczby całkowitej o dowolnym rozmiarze.

## <a name="syntax"></a>Składnia

```C
intmax_t imaxabs(
   intmax_t n
);
```

### <a name="parameters"></a>Parametry

*n*<br/>
Wartość liczby całkowitej.

## <a name="return-value"></a>Wartość zwracana

**Imaxabs —** funkcja zwraca wartość bezwzględną argumentu. Nie będzie zwrotu błędu.

> [!NOTE]
> Ponieważ zakres ujemnych liczb całkowitych, które mogą być reprezentowane za pomocą **intmax_t** jest większy niż zakres dodatnich liczb całkowitych, które mogą być reprezentowane, jest możliwe, aby podać argument do **imaxabs —** który nie może zostać przekonwertowany. Jeśli wartość bezwzględna argumentu nie może być przedstawiona przez zwracany typ, zachowanie **imaxabs —** jest niezdefiniowana.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**imaxabs**|\<inttypes.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

```C
// crt_imaxabs.c
// Build using: cl /W3 /Tc crt_imaxabs.c
// This example calls imaxabs to compute an
// absolute value, then displays the results.

#include <stdio.h>
#include <stdlib.h>
#include <inttypes.h>

int main(int argc, char *argv[])
{
   intmax_t x = LLONG_MIN + 2;

   printf("The absolute value of %lld is %lld\n", x, imaxabs(x));
}
```

```Output
The absolute value of -9223372036854775806 is 9223372036854775806
```

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[abs, labs, llabs, _abs64](abs-labs-llabs-abs64.md)<br/>
[_cabs](cabs.md)<br/>
[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)<br/>
