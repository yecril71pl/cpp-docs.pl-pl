---
title: _clear87, _clearfp
ms.date: 04/05/2018
api_name:
- _clearfp
- _clear87
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- clearfp
- _clearfp
- _clear87
- clear87
helpviewer_keywords:
- clearing floating point status word
- clearfp function
- _clear87 function
- _clearfp function
- clear87 function
ms.assetid: 72d24a70-7688-4793-ae09-c96d33fcca52
ms.openlocfilehash: 4ca49895b881d9e307c1116681bc36f86b167c25
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942954"
---
# <a name="_clear87-_clearfp"></a>_clear87, _clearfp

Pobiera i czyści słowo stanu zmiennoprzecinkowego.

## <a name="syntax"></a>Składnia

```C
unsigned int _clear87( void );
unsigned int _clearfp( void );
```

## <a name="return-value"></a>Wartość zwracana

Bity w zwracanej wartości wskazują stan zmiennoprzecinkowy przed wywołaniem metody **_clear87** lub **_clearfp**. Aby uzyskać pełną definicję bitów zwracanych przez **_clear87**, zobacz float. h. Wiele funkcji biblioteki matematycznej modyfikuje wyraz o stanie 8087/80287 z nieprzewidywalnymi wynikami. Wartości zwracane z **_clear87** i **_status87** stają się bardziej niezawodne, ponieważ mniej operacji zmiennoprzecinkowych jest wykonywanych między znanymi Stanami wyrazu stanu zmiennoprzecinkowego.

## <a name="remarks"></a>Uwagi

Funkcja **_clear87** czyści flagi wyjątku w słowie stanu zmiennoprzecinkowego, ustawia bit zajęty na 0 i zwraca słowo stanu. Słowo stanu zmiennoprzecinkowego jest kombinacją słowa stanu 8087/80287 i innych warunków wykrytych przez program obsługi wyjątków 8087/80287, takich jak przepływy stosu zmiennoprzecinkowe i niedopełnienie.

**_clearfp** to niezależna od platformy, Przenośna wersja procedury **_clear87** . Jest on identyczny z **_clear87** na platformach firmy Intel (x86) i jest również obsługiwany przez platformy x64 i ARM. Aby upewnić się, że kod zmiennoprzecinkowy jest przenośny z architekturą x64 i ARM, użyj **_clearfp**. Jeśli masz tylko platformy x86, możesz użyć opcji **_clear87** lub **_clearfp**.

Te funkcje są przestarzałe podczas kompilowania z [/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](../../build/reference/clr-common-language-runtime-compilation.md) , ponieważ środowisko uruchomieniowe języka wspólnego obsługuje tylko domyślną precyzję zmiennoprzecinkową.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_clear87**|\<float.h>|
|**_clearfp**|\<float.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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
