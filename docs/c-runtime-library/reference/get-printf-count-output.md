---
title: _get_printf_count_output | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- '%n format'
- get_printf_count_output function
- _get_printf_count_output function
ms.assetid: 850f9f33-8319-433e-98d8-6a694200d994
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 216df8d973f391db2b6114d9bbcb50dcf509c5b5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32398373"
---
# <a name="getprintfcountoutput"></a>_get_printf_count_output

Wskazuje, czy [printf, _printf_l —, wprintf, _wprintf_l —](printf-printf-l-wprintf-wprintf-l.md)-rodziny funkcji obsługi **%n** format.

## <a name="syntax"></a>Składnia

```C
int _get_printf_count_output();
```

## <a name="return-value"></a>Wartość zwracana

Jeśli niezerowa **%n** jest obsługiwana, 0 Jeśli **%n** nie jest obsługiwane.

## <a name="remarks"></a>Uwagi

Jeśli **%n** jest nieobsługiwane (domyślna), napotkania **%n** w ciągu formatu któregokolwiek z **printf** funkcje wywoła program obsługi nieprawidłowych parametrów, zgodnie z opisem w temacie [Sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli **%n** włączona jest obsługa (zobacz [_set_printf_count_output —](set-printf-count-output.md)) następnie **%n** będzie działać zgodnie z opisem w temacie [składnia specyfikacji formatu: printf i wprintf Funkcje](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_get_printf_count_output**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [_set_printf_count_output —](set-printf-count-output.md).

## <a name="see-also"></a>Zobacz także

[_set_printf_count_output](set-printf-count-output.md)<br/>
