---
title: _status87, _statusfp, _statusfp2
ms.date: 04/05/2018
api_name:
- _statusfp2
- _statusfp
- _status87
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
ms.openlocfilehash: 54faf70296ef41f2682f88a8edaa82ee0d2071d4
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958089"
---
# <a name="_status87-_statusfp-_statusfp2"></a>_status87, _statusfp, _statusfp2

Pobiera słowo stanu zmiennoprzecinkowego.

## <a name="syntax"></a>Składnia

```C
unsigned int _status87( void );
unsigned int _statusfp( void );
void _statusfp2(unsigned int *px86, unsigned int *pSSE2)
```

### <a name="parameters"></a>Parametry

*px86*<br/>
Ten adres jest wypełniony wyrazem stanu dla jednostki zmiennoprzecinkowej x87.

*pSSE2*<br/>
Ten adres jest wypełniony wyrazem stanu dla jednostki zmiennoprzecinkowej SSE2.

## <a name="return-value"></a>Wartość zwracana

W przypadku **_status87** i **_statusfp**bity w zwracanej wartości wskazują stan zmiennoprzecinkowy. Zobacz ZMIENNOPRZECINKOWe. H Dołącz plik dla definicji bitów, które są zwracane przez **_statusfp**. Wiele funkcji biblioteki matematycznej modyfikuje wyraz o stanie zmiennoprzecinkowe z nieprzewidywalnymi wynikami. Optymalizacja może zmienić kolejność, łączenie i eliminowanie operacji zmiennoprzecinkowych wokół wywołań **_status87**, **_statusfp**i powiązanych funkcji. Użyj opcji kompilatora [/od (Wyłącz (Debuguj))](../../build/reference/od-disable-debug.md) lub dyrektywy pragma [fenv_access](../../preprocessor/fenv-access.md) , aby zapobiec optymalizacji, która zmienia kolejność operacji zmiennoprzecinkowych. Zwracaj wartości z **_clearfp** i **_statusfp**, a także parametry powrotu **_statusfp2**, są bardziej niezawodne, jeśli przeprowadzono mniejszą liczbę operacji zmiennoprzecinkowych między znanymi Stanami wyrazu stanu zmiennoprzecinkowego.

## <a name="remarks"></a>Uwagi

Funkcja **_statusfp** pobiera słowo stanu zmiennoprzecinkowego. Słowo stanu jest kombinacją stanu procesora zmiennoprzecinkowego i innych warunków wykrytych przez program obsługi wyjątków zmiennoprzecinkowych — na przykład przepełnienie stosu zmiennoprzecinkowego i niedomiar. Wyjątki niemaskowane są sprawdzane przed zwróceniem zawartości słowa stanu. Oznacza to, że obiekt wywołujący jest informowany o oczekujących wyjątkach. Na platformach x86 **_statusfp** zwraca kombinację stanu zmiennoprzecinkowego X87 i SSE2. Na platformach x64 zwrócony stan jest określany na podstawie stanu MXCSR instrukcji SSE. Na platformach ARM **_statusfp** zwraca status z rejestru rejestru FPSCR.

**_statusfp** to niezależna od platformy, Przenośna wersja **_status87**. Jest on identyczny z **_status87** na platformach firmy Intel (x86) i jest również obsługiwany przez platformy x64 i ARM. Aby upewnić się, że kod zmiennoprzecinkowy jest przenośny ze wszystkimi architekturami, użyj **_statusfp**. Jeśli masz tylko platformy x86, możesz użyć opcji **_status87** lub **_statusfp**.

Zalecamy **_statusfp2** dla mikroukładów (takich jak Pentium IV), które mają zarówno x87, jak i SSE2 procesora zmiennoprzecinkowego. W przypadku **_statusfp2**adresy są wypełniane przy użyciu wyrazu stanu zmiennoprzecinkowego zarówno dla x87, jak i SSE2 procesora zmiennoprzecinkowego. Dla mikroukładu, który obsługuje procesory zmiennoprzecinkowe x87 i SSE2, EM_AMBIGUOUS jest ustawione na 1, jeśli użyto **_statusfp** lub **_controlfp** i akcja była niejednoznaczna, ponieważ może odwoływać się do x87 lub SSE2 stanu zmiennoprzecinkowego. Funkcja **_statusfp2** jest obsługiwana tylko na platformach x86.

Te funkcje nie są przydatne w przypadku opcji [/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](../../build/reference/clr-common-language-runtime-compilation.md) , ponieważ środowisko uruchomieniowe języka wspólnego (CLR) obsługuje tylko domyślną precyzję zmiennoprzecinkową.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_status87**, **_statusfp**, **_statusfp2**|\<float.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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
