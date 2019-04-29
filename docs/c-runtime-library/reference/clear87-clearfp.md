---
title: _clear87, _clearfp
ms.date: 04/05/2018
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
helpviewer_keywords:
- clearing floating point status word
- clearfp function
- _clear87 function
- _clearfp function
- clear87 function
ms.assetid: 72d24a70-7688-4793-ae09-c96d33fcca52
ms.openlocfilehash: 4148f85d82a4210033686455c73046081832e3c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62340556"
---
# <a name="clear87-clearfp"></a>_clear87, _clearfp

Pobiera i czyści słowa stanu zmiennoprzecinkowego.

## <a name="syntax"></a>Składnia

```C
unsigned int _clear87( void );
unsigned int _clearfp( void );
```

## <a name="return-value"></a>Wartość zwracana

Bity w wartości zwracanej wskazują status sterowania zmiennoprzecinkowego przed wywołaniem do **_clear87 —** lub **_clearfp —**. Aby uzyskać pełną definicję bitów, zwracany przez **_clear87 —**, zobacz Float.h. Wiele funkcji bibliotek matematycznych zmodyfikować 8087/80287 stanu wyrazu jednostki za pomocą nieprzewidywalne rezultaty. Zwracane wartości **_clear87 —** i **_status87 —** stają się bardziej niezawodne, mniej operacji zmiennoprzecinkowych jest wykonywane między znanymi stanami statusu słowa zmiennoprzecinkowego.

## <a name="remarks"></a>Uwagi

**_Clear87 —** funkcja czyści flagi wyjątek w słowa stanu zmiennoprzecinkowego, ustawia bit zajęty 0 i zwraca wyrazy stanu. Zmiennoprzecinkowe wyrazy stanu jest kombinacją wyrazy stanu 8087/80287 i innych warunków wykrytych przez program obsługi wyjątków 8087/80287, takie jak przepełnienie stosu zmiennoprzecinkowego i niedomiaru.

**_clearfp —** jest niezależny od platformy, przenośną wersją **_clear87 —** procedury. Jest on identyczny **_clear87 —** na platformach firmy Intel (x86) i jest również obsługiwana przez platformy ARM i x64. Aby upewnić się, że kod zmiennoprzecinkowy jest przenośny do x64 i ARM, należy użyć **_clearfp —**. Jeśli są przeznaczone tylko dla x86 platform, można użyć dowolnego **_clear87 —** lub **_clearfp —**.

Funkcje te są używane podczas kompilowania za pomocą [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md) ponieważ środowisko uruchomieniowe języka wspólnego obsługuje tylko domyślną precyzję zmiennoprzecinkową.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_clear87**|\<float.h>|
|**_clearfp —**|\<float.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
