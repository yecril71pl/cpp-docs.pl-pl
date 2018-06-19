---
title: _clear87 —, _clearfp — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _clearfp
- _clear87
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- clearfp
- _clearfp
- _clear87
- clear87
dev_langs:
- C++
helpviewer_keywords:
- clearing floating point status word
- clearfp function
- _clear87 function
- _clearfp function
- clear87 function
ms.assetid: 72d24a70-7688-4793-ae09-c96d33fcca52
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 195bd9f78ed9edfa47ec9ebbd2babbee676e5644
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32395620"
---
# <a name="clear87-clearfp"></a>_clear87, _clearfp

Pobiera i czyści słowa stanu zmiennoprzecinkowych.

## <a name="syntax"></a>Składnia

```C
unsigned int _clear87( void );
unsigned int _clearfp( void );
```

## <a name="return-value"></a>Wartość zwracana

Usługa bits w wartości zwracanej wskazują stan zmiennoprzecinkowe przed wywołaniem do **_clear87 —** lub **_clearfp —**. Dla pełnej definicji bitów zwrócony przez **_clear87 —**, zobacz float.h —. Wiele funkcji biblioteki matematyczne zmodyfikować programu word 8087/80287 stan może mieć nieprzewidywalne skutki. Wartości zwracanych z **_clear87 —** i **_status87 —** staną się bardziej niezawodny mniejszej liczby zmiennoprzecinkowe operacje są wykonywane między Stanami znane Word stan zmiennoprzecinkowy.

## <a name="remarks"></a>Uwagi

**_Clear87 —** funkcja czyści flagi wyjątek w programie word zmiennoprzecinkowy stan, ustawia bit zajęty 0 i zwraca słowa stanu. Słowa stanu zmiennoprzecinkowej jest kombinacją słowa stanu 8087/80287 i innych warunków wykrytych przez program obsługi wyjątku 8087/80287, takie jak przepełnienie stosu zmiennoprzecinkowych i niedopełnienie.

**_clearfp —** jest niezależne od platformy, przenośne wersja **_clear87 —** procedury. Jest on identyczny **_clear87 —** na platformach firmy Intel (x86) i jest również obsługiwana przez platformy ARM i x64. Zapewnienie zmiennoprzecinkowe kodu przenośnego x64 i ARM, użyj **_clearfp —**. Jeśli przeznaczonych tylko x86 platform, możesz użyć dowolnej **_clear87 —** lub **_clearfp —**.

Te funkcje są przestarzałe podczas kompilowania za pomocą [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md) ponieważ środowisko uruchomieniowe języka wspólnego obsługuje tylko domyślna dokładność zmiennoprzecinkowych.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_clear87**|\<float.h>|
|**_clearfp —**|\<float.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_clear87.c
// compile with: /Od

// This program creates various floating-point
// problems, then uses _clear87 to report on these problems.
// Compile this program with Optimizations disabled (/Od).
// Otherwise the optimizer will remove the code associated with
// the unused floating-point values.
//

#include <stdio.h>
#include <float.h>

int main( void )
{
   double a = 1e-40, b;
   float x, y;

   printf( "Status: %.4x - clear\n", _clear87()  );

   // Store into y is inexact and underflows:
   y = a;
   printf( "Status: %.4x - inexact, underflow\n", _clear87() );

   // y is denormal:
   b = y;
   printf( "Status: %.4x - denormal\n", _clear87() );
}
```

```Output
Status: 0000 - clear
Status: 0003 - inexact, underflow
Status: 80000 - denormal
```

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[_control87, _controlfp, \__control87_2](control87-controlfp-control87-2.md)<br/>
[_status87, _statusfp, _statusfp2](status87-statusfp-statusfp2.md)<br/>
