---
title: putc, putwc | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- putwc
- putc
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
- _puttc
- putwc
- putc
dev_langs:
- C++
helpviewer_keywords:
- streams, writing characters to
- characters, writing
- putwc function
- putc function
- _puttc function
- puttc function
ms.assetid: a37b2e82-9d88-4565-8190-ff8d04c0ddb9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af5c6987f88238398a00e9da7f0d769f246ffc54
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211072"
---
# <a name="putc-putwc"></a>putc, putwc

Zapisuje znak do strumienia.

## <a name="syntax"></a>Składnia

```C
int putc(
   int c,
   FILE *stream
);
wint_t putwc(
   wchar_t c,
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Znak do zapisania.

*Stream*<br/>
Wskaźnik do **pliku** struktury.

## <a name="return-value"></a>Wartość zwracana

Zwraca znak napisany. Aby wskazać błąd lub warunek końca pliku **putc** i **putchar** zwracają ** EOF`; **putwc` i **putwchar** zwracają **WEOF**. W przypadku wszystkich czterech procedur, użyj [ferror](ferror.md) lub [feof](feof.md) pod kątem błąd lub koniec pliku. Jeśli przekazywany jest pusty wskaźnik *strumienia*, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają **EOF** lub **WEOF** i ustaw **errno** do **EINVAL**.

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Aby uzyskać więcej informacji na temat tych i innych kodów błędu,.

## <a name="remarks"></a>Uwagi

**Putc** rutynowo pisze pojedynczy znak *c* w danych wyjściowych *strumienia* w bieżącym położeniu. Dowolna liczba całkowita może być przekazywany do **putc**, ale tylko niższe 8 bitów jest zapisywane. **Putchar** rutyna jest identyczna z `putc( c, stdout )`. Dla każdej procedury Jeśli wystąpi błąd odczytu, wskaźnik błędu dla strumienia jest ustawiony. **putc** i **putchar** są podobne do **fputc** i **_fputchar**, odpowiednio, ale są implementowane zarówno funkcje, jak makra (zobacz [ Wybierania pomiędzy funkcjami i makrami](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)). **putwc** i **putwchar** są wersjami znaków dwubajtowych **putc** i **putchar**, odpowiednio. **putwc** i **putc** zachowują się identycznie, jeżeli strumień jest otwarty w trybie ANSI. **putc** aktualnie nie obsługuje danych wyjściowych w strumieniu UNICODE.

Wersje **_nolock** sufiksem są identyczne, z tą różnicą, że nie są chronione przed ingerencją przez inne wątki. Aby uzyskać więcej informacji, zobacz **_putc_nolock, _putwc_nolock**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_puttc —**|**putc**|**putc**|**putwc**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**putc**|\<stdio.h>|
|**putwc**|\<stdio.h > lub \<wchar.h >|

Konsola nie jest obsługiwana w aplikacjach platformy uniwersalnej Windows (UWP). Standardowe uchwyty strumienia, które są powiązane z konsolą, **stdin**, **stdout**, i **stderr**, muszą zostać przekierowane zanim funkcje środowiska wykonawczego języka C można ich używać w aplikacjach platformy UWP . Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

```C
// crt_putc.c
/* This program uses putc to write buffer
* to a stream. If an error occurs, the program
* stops before writing the entire buffer.
*/

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char *p, buffer[] = "This is the line of output\n";
   int  ch;

   ch = 0;
   /* Make standard out the stream and write to it. */
   stream = stdout;
   for( p = buffer; (ch != EOF) && (*p != '\0'); p++ )
      ch = putc( *p, stream );
}
```

### <a name="output"></a>Dane wyjściowe

```Output
This is the line of output
```

## <a name="see-also"></a>Zobacz także

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[fputc, fputwc](fputc-fputwc.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
