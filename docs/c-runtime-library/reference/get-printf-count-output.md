---
title: _get_printf_count_output
ms.date: 11/04/2016
apiname:
- _get_printf_count_output
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
- get_printf_count_output
- _get_printf_count_output
helpviewer_keywords:
- '%n format'
- get_printf_count_output function
- _get_printf_count_output function
ms.assetid: 850f9f33-8319-433e-98d8-6a694200d994
ms.openlocfilehash: 477e4a9e987f27bd70b9707e91b9ea9d84b69993
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50610642"
---
# <a name="getprintfcountoutput"></a>_get_printf_count_output

Wskazuje, czy [printf, _printf_l —, wprintf, _wprintf_l —](printf-printf-l-wprintf-wprintf-l.md)-rodziny funkcji obsługi **%n** formatu.

## <a name="syntax"></a>Składnia

```C
int _get_printf_count_output();
```

## <a name="return-value"></a>Wartość zwracana

Jeśli niezerowa Koniunkcja **%n** jest obsługiwany, 0, jeśli **%n** nie jest obsługiwane.

## <a name="remarks"></a>Uwagi

Jeśli **%n** jest nieobsługiwane (domyślna), napotkania **%n** w ciągu formatu któregokolwiek z **printf** funkcje wywoła procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w temacie [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli **%n** jest włączona obsługa (zobacz [_set_printf_count_output —](set-printf-count-output.md)) następnie **%n** będzie działać zgodnie z opisem w [składnia specyfikacji formatu: printf i wprintf Funkcje](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_get_printf_count_output**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [_set_printf_count_output —](set-printf-count-output.md).

## <a name="see-also"></a>Zobacz także

[_set_printf_count_output](set-printf-count-output.md)<br/>
