---
title: _fputchar —, _fputwchar — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _fputchar
- _fputwchar
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
- fputtchar
- _fputwchar
- fputwchar
- _fputtchar
- fputchar
- _fputchar
dev_langs:
- C++
helpviewer_keywords:
- fputchar function
- standard output, writing to
- _fputtchar function
- fputwchar function
- _fputwchar function
- fputtchar function
- _fputchar function
ms.assetid: b92ff600-a924-4f2b-b0e7-3097ee31bdff
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3fd5a1d60c61fdde5864f3447b5f721f409bc3a4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32399595"
---
# <a name="fputchar-fputwchar"></a>_fputchar, _fputwchar

Zapisuje znaku **stdout**.

## <a name="syntax"></a>Składnia

```C
int _fputchar(
   int c
);
wint_t _fputwchar(
   wchar_t c
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Znak do zapisania.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca znak zapisywane. Aby uzyskać **_fputchar —**, zwracana wartość **EOF** wskazuje błąd. Aby uzyskać **_fputwchar —**, zwracana wartość **weof —** wskazuje błąd. Jeśli jest c **NULL**, te funkcje wygeneruje wyjątek nieprawidłowy parametr, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, zwracają **EOF** (lub **weof —**) i ustawić **errno** do **einval —**.

Aby uzyskać więcej informacji na temat tych i innych kodów błędów, zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Obie te funkcje zapisuje pojedynczy znak *c* do **stdout** i przesuwa wskaźnik zależnie od potrzeb. **_fputchar —** jest odpowiednikiem `fputc( stdout )`. Również jest odpowiednikiem **putchar —**, ale zaimplementowany tylko jako funkcję, a nie jako funkcję i makra. W odróżnieniu od **fputc —** i **putchar —**, te funkcje nie są zgodne ze standardem ANSI.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_fputtchar —**|**_fputchar —**|**_fputchar —**|**_fputwchar —**|

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_fputchar —**|\<stdio.h>|
|**_fputwchar —**|\<stdio.h > lub \<wchar.h >|

Konsoli nie jest obsługiwane w aplikacjach systemu Windows platformy Uniwersalnej. Uchwyty Standardowy strumień, które są skojarzone z konsoli programu —**stdin**, **stdout**, i **stderr**— muszą być przekierowywane przed funkcje wykonawcze języka C można używać ich w aplikacji platformy uniwersalnej systemu Windows . Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_fputchar.c
// This program uses _fputchar
// to send a character array to stdout.

#include <stdio.h>

int main( void )
{
    char strptr[] = "This is a test of _fputchar!!\n";
    char *p = NULL;

    // Print line to stream using _fputchar.
    p = strptr;
    while( (*p != '\0') && _fputchar( *(p++) ) != EOF )
      ;
}
```

```Output
This is a test of _fputchar!!
```

## <a name="see-also"></a>Zobacz także

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fgetc, fgetwc](fgetc-fgetwc.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
