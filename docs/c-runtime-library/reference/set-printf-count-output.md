---
title: _set_printf_count_output
ms.date: 11/04/2016
api_name:
- _set_printf_count_output
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_printf_count_output
- _set_printf_count_output
helpviewer_keywords:
- '%n format'
- set_printf_count_output function
- _set_printf_count_output function
ms.assetid: d8259ec5-764e-42d0-9169-72172e95163b
ms.openlocfilehash: 0d53b4e4c56a69582a4eb517fa1a5c9e10cd7d2f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948421"
---
# <a name="_set_printf_count_output"></a>_set_printf_count_output

Włącz lub Wyłącz obsługę formatu **% n** w [printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)-Family Functions.

## <a name="syntax"></a>Składnia

```C
int _set_printf_count_output(
   int enable
);
```

### <a name="parameters"></a>Parametry

*mogły*<br/>
Wartość niezerowa, aby włączyć obsługę elementu **% n** , 0, aby wyłączyć obsługę **% n** .

## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość

Stan **% n** obsługi przed wywołaniem tej funkcji: wartość niezerowa, jeśli włączono obsługę **% n** , 0, jeśli została wyłączona.

## <a name="remarks"></a>Uwagi

Ze względów bezpieczeństwa Pomoc techniczna dla specyfikatora formatu **% n** jest domyślnie wyłączona w **printf** i wszystkich jego wariantów. Jeśli element **% n** zostanie napotkany w specyfikacji formatu **printf** , domyślnym zachowaniem jest Wywołaj procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Wywołanie **_set_printf_count_output** z niezerowym argumentem spowoduje, że funkcje rodziny **printf**będą interpretować element **% n** zgodnie z opisem w [składni specyfikacji formatu: printf i wprintf Functions](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_set_printf_count_output**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_set_printf_count_output.c
#include <stdio.h>

int main()
{
   int e;
   int i;
   e = _set_printf_count_output( 1 );
   printf( "%%n support was %sabled.\n",
        e ? "en" : "dis" );
   printf( "%%n support is now %sabled.\n",
        _get_printf_count_output() ? "en" : "dis" );
   printf( "12345%n6789\n", &i ); // %n format should set i to 5
   printf( "i = %d\n", i );
}
```

```Output
%n support was disabled.
%n support is now enabled.
123456789
i = 5
```

## <a name="see-also"></a>Zobacz także

[_get_printf_count_output](get-printf-count-output.md)<br/>
