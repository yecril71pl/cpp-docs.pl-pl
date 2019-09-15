---
title: _CrtGetReportHook
ms.date: 11/04/2016
api_name:
- _CrtGetReportHook
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- CrtGetReportHook
- _CrtGetReportHook
helpviewer_keywords:
- CrtGetReportHook function
- _CrtGetReportHook function
ms.assetid: 922758ed-7edd-4359-9c92-0535192dc11a
ms.openlocfilehash: bc005dda435b5e11d6c3c886de180ed85b9c2a04
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942403"
---
# <a name="_crtgetreporthook"></a>_CrtGetReportHook

Pobiera funkcję raportowania zdefiniowaną przez klienta służącą do podłączania jej do czasu uruchomienia języka C dla procesu raportowania debugowania (tylko wersja do debugowania).

## <a name="syntax"></a>Składnia

```C
_CRT_REPORT_HOOK _CrtGetReportHook( void );
```

## <a name="return-value"></a>Wartość zwracana

Zwraca bieżącą funkcję raportowania zdefiniowaną przez klienta.

## <a name="remarks"></a>Uwagi

**_CrtGetReportHook** umożliwia aplikacji pobranie bieżącej funkcji raportowania dla procesu raportowania biblioteki debugowania w czasie wykonywania C.

Aby uzyskać więcej informacji na temat korzystania z innych funkcji w czasie wykonywania z możliwością podłączania i pisania własnych zdefiniowanych przez klienta funkcji Hook, zobacz [Zapisywanie funkcji punktu zaczepienia debugowania](/visualstudio/debugger/debug-hook-function-writing).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtGetReportHook**|\<crtdbg.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje wyłącznie [bibliotek uruchomieniowych C](../../c-runtime-library/crt-library-features.md) .

## <a name="example"></a>Przykład

Aby zapoznać się z przykładem sposobu korzystania z **_CrtSetReportHook**, zobacz [raport](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/report).

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetReportHook](crtsetreporthook.md)<br/>
