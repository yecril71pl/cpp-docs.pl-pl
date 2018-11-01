---
title: _CrtGetReportHook
ms.date: 11/04/2016
apiname:
- _CrtGetReportHook
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
apitype: DLLExport
f1_keywords:
- CrtGetReportHook
- _CrtGetReportHook
helpviewer_keywords:
- CrtGetReportHook function
- _CrtGetReportHook function
ms.assetid: 922758ed-7edd-4359-9c92-0535192dc11a
ms.openlocfilehash: 0b8b666093807c95312d4328ca9b3043ad1e09df
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536763"
---
# <a name="crtgetreporthook"></a>_CrtGetReportHook

Pobiera zdefiniowaną przez klienta funkcji raportowania dla podłączenie jej do C wykonawczego do debugowania procesu (tylko wersja debugowania) raportowania.

## <a name="syntax"></a>Składnia

```C
_CRT_REPORT_HOOK _CrtGetReportHook( void );
```

## <a name="return-value"></a>Wartość zwracana

Zwraca bieżącą funkcję raportowania zdefiniowaną przez klienta.

## <a name="remarks"></a>Uwagi

**_Crtgetreporthook —** umożliwia aplikacji można pobrać bieżącą funkcję raportowania dla bibliotek debugowania w czasie wykonywania C procesu raportowania.

Aby uzyskać więcej informacji na temat korzystania innych funkcją podłączania funkcji wykonawczej i pisanie własnych zdefiniowaną przez klienta funkcje punktów zaczepienia, zobacz [debugowania pisania funkcji punktów zaczepienia](/visualstudio/debugger/debug-hook-function-writing).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtGetReportHook**|\<crtdbg.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="example"></a>Przykład

Przykład sposobu użycia **_CrtSetReportHook**, zobacz [raportu](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/report).

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetReportHook](crtsetreporthook.md)<br/>
