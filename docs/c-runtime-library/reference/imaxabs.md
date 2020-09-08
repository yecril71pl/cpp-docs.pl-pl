---
title: imaxabs
description: Dokumentacja interfejsu API dla imaxabs, która oblicza wartość bezwzględną liczby całkowitej o dowolnym rozmiarze.
ms.date: 04/05/2018
api_name:
- imaxabs
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- imaxabs
helpviewer_keywords:
- imaxabs function
ms.assetid: de2566a3-1415-4e9a-91b5-7ac3a49ebf5e
ms.openlocfilehash: 599e8a0cb20f24bda24201be40fa1acc0ade993c
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555504"
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

*Azotan*<br/>
Wartość całkowita.

## <a name="return-value"></a>Wartość zwracana

Funkcja **imaxabs** zwraca wartość bezwzględną argumentu. Nie ma żadnego powrotu błędu.

> [!NOTE]
> Ponieważ zakres ujemnych liczb całkowitych, które mogą być reprezentowane za pomocą **intmax_t** , jest większy niż zakres dodatnich liczb całkowitych, które mogą być reprezentowane, możliwe jest podanie argumentu **imaxabs** , którego nie można przekonwertować. Jeśli wartość bezwzględna argumentu nie może być reprezentowana przez zwracany typ, zachowanie **imaxabs** jest niezdefiniowane.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**imaxabs**|\<inttypes.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek uruchomieniowych języka C](../../c-runtime-library/crt-library-features.md).

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

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md)<br/>
[abs, labs, llabs, _abs64](abs-labs-llabs-abs64.md)<br/>
[_cabs](cabs.md)<br/>
[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)<br/>
