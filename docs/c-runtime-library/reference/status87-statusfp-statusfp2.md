---
title: _status87 —, _statusfp —, _statusfp2 — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _statusfp2
- _statusfp
- _status87
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
- _statusfp2
- _statusfp
- statusfp2
- _status87
- status87
- statusfp
dev_langs:
- C++
helpviewer_keywords:
- floating-point functions, getting status word
- floating-point numbers, status word
- status87 function
- status word, getting floating point
- statusfp function
- _statusfp function
- _statusfp2 function
- statusfp2 function
- _status87 function
- floating-point functions
- status word
ms.assetid: 7ef963fa-b1fb-429d-94d6-fbf282ab7432
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 69297d7ff1e3ec40cfe4fc22dec86c356d1697d4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="status87-statusfp-statusfp2"></a>_status87, _statusfp, _statusfp2

Pobiera słowa stanu zmiennoprzecinkowych.

## <a name="syntax"></a>Składnia

```C
unsigned int _status87( void );
unsigned int _statusfp( void );
void _statusfp2(unsigned int *px86, unsigned int *pSSE2)
```

### <a name="parameters"></a>Parametry

*px86*<br/>
Ten adres jest wypełniony słowa stanu dla x87 zmiennoprzecinkowe jednostki.

*pSSE2*<br/>
Ten adres jest wypełniony słowa stanu jednostki zmiennoprzecinkowe SSE2.

## <a name="return-value"></a>Wartość zwracana

Aby uzyskać **_status87 —** i **_statusfp —**, bity wartość, która jest zwracana wskazują stan zmiennoprzecinkowy. Zobacz FLOAT. H Uwzględnij plik dla definicji usługi bits, które są zwracane przez **_statusfp —**. Wiele funkcji biblioteki matematyczne zmodyfikować programu word zmiennoprzecinkowy stan może mieć nieprzewidywalne skutki. Optymalizacja można zmienić kolejność, łączenie i wyeliminować operacji zmiennoprzecinkowych wokół wywołań **_status87 —**, **_statusfp —**i powiązane funkcje. Użyj [/Od (Wyłącz (Debuguj))](../../build/reference/od-disable-debug.md) — opcja kompilatora lub [fenv_access](../../preprocessor/fenv-access.md) dyrektywa pragma, aby zapobiec funkcje optymalizacji, które zmienić kolejność operacji zmiennoprzecinkowych. Wartości zwracanych z **_clearfp —** i **_statusfp —**, a także parametrów zwracanych z **_statusfp2 —**, są bardziej niezawodne, jeśli wykonywane są operacje mniejszej liczby zmiennoprzecinkowe między znane stanami słowa stanu zmiennoprzecinkowych.

## <a name="remarks"></a>Uwagi

**_Statusfp —** funkcja pobiera słowa stanu zmiennoprzecinkowych. Pobieranie słowa stanu jest kombinacją stanu procesora zmiennoprzecinkowych i innych warunków wykrytych przez program obsługi wyjątku zmiennoprzecinkowe — na przykład przepełnienie stosu zmiennoprzecinkowych i niedopełnienie. Zamaskowana wyjątki są sprawdzane pod kątem przed zawartość słowa stanu są zwracane. Oznacza to, wywołujący informowanie o oczekujących wyjątków. Na x86 platform, **_statusfp —** zwraca kombinację x87 i stan zmiennoprzecinkowy SSE2. Na x64 platform, stan, który jest zwracany jest na podstawie SSE MXCSR stanu. Na platformach ARM **_statusfp —** zwraca stan z rejestru FPSCR.

**_statusfp —** jest niezależne od platformy, przenośne wersja **_status87 —**. Jest on identyczny **_status87 —** na platformach firmy Intel (x86) i jest również obsługiwana przez platformy ARM i x64. W celu zapewnienia przenośne do wszystkich architektury zmiennoprzecinkowe kodu, użyj **_statusfp —**. Jeśli przeznaczonych tylko x86 platform, możesz użyć dowolnej **_status87 —** lub **_statusfp —**.

Firma Microsoft zaleca **_statusfp2 —** dla mikroukłady (na przykład Pentium IV), które x87 i SSE2 procesora zmiennoprzecinkowych. Aby uzyskać **_statusfp2 —**, adresy są wypełniane przy użyciu słowa stanu zmiennoprzecinkowe x87 lub procesor zmiennoprzecinkowe SSE2. Mikroukładu obsługującego x87 i procesorów zmiennoprzecinkowe SSE2, EM_AMBIGUOUS jest ustawiona na 1, gdy **_statusfp —** lub **_controlfp —** jest używany i akcji jest niejednoznaczne, ponieważ on można odwoływać się do x87 lub SSE2 Pobieranie słowa stanu zmiennoprzecinkowych. **_Statusfp2 —** funkcja jest obsługiwana tylko na x86 platform.

Te funkcje nie są przydatne w przypadku [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md) ponieważ środowisko uruchomieniowe języka wspólnego (CLR) obsługuje tylko domyślna dokładność zmiennoprzecinkowych.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_status87 —**, **_statusfp —**, **_statusfp2 —**|\<float.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_statusfp.c
// Build by using: cl /W4 /Ox /nologo crt_statusfp.c
// This program creates various floating-point errors and
// then uses _statusfp to display messages that indicate these problems.

#include <stdio.h>
#include <float.h>
#pragma fenv_access(on)

double test( void )
{
   double a = 1e-40;
   float b;
   double c;

   printf("Status = 0x%.8x - clear\n", _statusfp());

   // Assignment into b is inexact & underflows:
   b = (float)(a + 1e-40);
   printf("Status = 0x%.8x - inexact, underflow\n", _statusfp());

   // c is denormal:
   c = b / 2.0;
   printf("Status = 0x%.8x - inexact, underflow, denormal\n",
            _statusfp());

   // Clear floating point status:
   _clearfp();
   return c;
}

int main(void)
{
   return (int)test();
}
```

```Output
Status = 0x00000000 - clear
Status = 0x00000003 - inexact, underflow
Status = 0x00080003 - inexact, underflow, denormal
```

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87, _clearfp](clear87-clearfp.md)<br/>
[_control87, _controlfp, \__control87_2](control87-controlfp-control87-2.md)<br/>
