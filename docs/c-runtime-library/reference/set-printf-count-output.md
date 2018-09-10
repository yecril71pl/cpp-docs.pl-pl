---
title: _set_printf_count_output | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _set_printf_count_output
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- set_printf_count_output
- _set_printf_count_output
dev_langs:
- C++
helpviewer_keywords:
- '%n format'
- set_printf_count_output function
- _set_printf_count_output function
ms.assetid: d8259ec5-764e-42d0-9169-72172e95163b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 783225412b01430d1043dafd4761cb7432eaa1d7
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44108322"
---
# <a name="setprintfcountoutput"></a>_set_printf_count_output

Włącza lub wyłącza obsługę **%n** formatowania w [printf, _printf_l —, wprintf, _wprintf_l —](printf-printf-l-wprintf-wprintf-l.md)-rodziny funkcji.

## <a name="syntax"></a>Składnia

```C
int _set_printf_count_output(
   int enable
);
```

### <a name="parameters"></a>Parametry

*Włącz*<br/>
Wartość niezerową, aby umożliwić **%n** pomocy technicznej, 0 — wyłączenie **%n** pomocy technicznej.

## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość

Stan **%n** obsługuje przed wywołaniem tej funkcji: różna od zera, jeśli **%n** włączona była obsługa, 0, jeśli została ona wyłączona.

## <a name="remarks"></a>Uwagi

Ze względu na bezpieczeństwo, obsługa **%n** specyfikator formatu jest domyślnie wyłączona w systemie **printf** i jej wariantów. Jeśli **%n** zostanie napotkany w **printf** specyfikacji formatu, zachowanie domyślne jest wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Wywoływanie **_set_printf_count_output —** z argumentem równa zero spowoduje, że **printf**-rodziny funkcji do interpretacji **%n** zgodnie z opisem w [formatu Składnia specyfikacji: funkcje printf i wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_set_printf_count_output**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
