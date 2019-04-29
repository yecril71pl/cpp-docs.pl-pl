---
title: _status87, _statusfp, _statusfp2
ms.date: 04/05/2018
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
ms.openlocfilehash: 271c28dd4e267e5b3b702858cc398689e3e35d6f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62354434"
---
# <a name="status87-statusfp-statusfp2"></a>_status87, _statusfp, _statusfp2

Pobiera wyrazy stanu zmiennoprzecinkowe.

## <a name="syntax"></a>Składnia

```C
unsigned int _status87( void );
unsigned int _statusfp( void );
void _statusfp2(unsigned int *px86, unsigned int *pSSE2)
```

### <a name="parameters"></a>Parametry

*px86*<br/>
Ten adres jest wypełniony wyrazami stanu dla x87 jednostki zmiennoprzecinkowej.

*pSSE2*<br/>
Ten adres jest wypełniony wyrazami stanu dla jednostki zmiennoprzecinkowej SSE2.

## <a name="return-value"></a>Wartość zwracana

Aby uzyskać **_status87 —** i **_statusfp —**, bity w wartości zwracanej wskazują status sterowania zmiennoprzecinkowego. Zobacz wartość ZMIENNOPRZECINKOWA. H dołączyć plik, aby uzyskać pełną definicję bitów, które są zwracane przez **_statusfp —**. Wiele funkcji bibliotek matematycznych zmodyfikować słowa stanu zmiennoprzecinkowego, za pomocą nieprzewidywalne rezultaty. Optymalizacja można zmienić kolejność, łączenie i wyeliminować operacji zmiennoprzecinkowych wokół wywołania **_status87 —**, **_statusfp —** i pokrewnych funkcji. Użyj [/Od (Wyłącz (Debuguj))](../../build/reference/od-disable-debug.md) — opcja kompilatora lub [fenv_access](../../preprocessor/fenv-access.md) dyrektywa pragmy, aby zapobiec optymalizacje, które zmieniać kolejność operacji zmiennoprzecinkowych. Zwracane wartości **_clearfp —** i **_statusfp —** i również zwracany parametry **_statusfp2 —**, są bardziej wiarygodne, gdy mniej operacji zmiennoprzecinkowych jest wykonywane między znanymi stanami statusu słowa zmiennoprzecinkowego.

## <a name="remarks"></a>Uwagi

**_Statusfp —** funkcja pobiera zmiennoprzecinkowe wyrazy stanu. Wyrazy stanu jest kombinacją stanu zmiennoprzecinkowego procesora i innych warunków wykrytych przez program obsługi wyjątków zmiennoprzecinkowych — na przykład przepełnienie stosu zmiennoprzecinkowego i niedomiaru. Zaznaczona wyjątki są sprawdzane zanim zawartości wyrazów stanu są zwracane. Oznacza to, że obiekt wywołujący jest informowany o oczekujących wyjątkach. Na x86 platformach **_statusfp —** zwraca połączenie x87 i stan zmiennoprzecinkowego SSE2. Na x64 platform, stan, który jest zwracany jest oparty na stanie SSE MXCSR. Na platformach ARM **_statusfp —** zwraca stan z rejestru fpscr.

**_statusfp —** jest niezależny od platformy, przenośną wersją **_status87 —**. Jest on identyczny **_status87 —** na platformach firmy Intel (x86) i jest również obsługiwana przez platformy ARM i x64. Aby upewnić się, że kod zmiennoprzecinkowy jest przenośny do wszystkich architektur, należy użyć **_statusfp —**. Jeśli są przeznaczone tylko dla x86 platform, można użyć dowolnego **_status87 —** lub **_statusfp —**.

Firma Microsoft zaleca **_statusfp2 —** na czipy (na przykład Pentium IV), które mają zarówno x87, jak i procesora zmiennoprzecinkowego SSE2. Aby uzyskać **_statusfp2 —**, adresy są wypełnione przy użyciu słowa stanu zmiennoprzecinkowego dla obu x87 lub procesora zmiennoprzecinkowego SSE2. Przypadku chipa, który obsługuje x87 i procesory zmiennoprzecinkowe SSE2, obiekt EM_AMBIGUOUS jest ustawiony na 1, gdy **_statusfp —** lub **_controlfp** jest używany i czynność była niejednoznaczna, ponieważ mogła się odwołać do x87 lub SSE2 słowa stanu zmiennoprzecinkowego. **_Statusfp2 —** funkcja jest obsługiwana tylko na x86 platform.

Te funkcje nie są przydatne w przypadku [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md) ponieważ środowisko uruchomieniowe języka wspólnego (CLR) obsługuje tylko domyślną precyzję zmiennoprzecinkową.

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
