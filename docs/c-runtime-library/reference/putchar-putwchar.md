---
title: putchar, putwchar
ms.date: 11/04/2016
api_name:
- putchar
- putwchar
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- putchar
- putwchar
- _puttchar
helpviewer_keywords:
- putchar function
- _puttchar function
- characters, writing
- standard output, writing to
- putwchar function
ms.assetid: 93657c7f-cca1-4032-8e3a-cd6ab6193748
ms.openlocfilehash: 88d1181fc2718d49533f3179c8fd0bfd818d589a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949916"
---
# <a name="putchar-putwchar"></a>putchar, putwchar

Zapisuje znak do **stdout**.

## <a name="syntax"></a>Składnia

```C
int putchar(
   int c
);
wint_t putwchar(
   wchar_t c
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Znak do zapisania.

## <a name="return-value"></a>Wartość zwracana

Zwraca znak zapisany. Aby wskazać błąd lub koniec pliku, **putc** i **putchar** Return **EOF**; **putwc** i **putwchar** zwracają **WEOF**. Dla wszystkich czterech procedur Użyj obiektu [powołującego](ferror.md) lub [feof](feof.md) , aby sprawdzić, czy wystąpił błąd lub koniec pliku. Jeśli przeszedł wskaźnik o wartości null dla *strumienia*, te funkcje generują wyjątek nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, zwracają **EOF** lub **WEOF** i ustawiają **errno** na **EINVAL**.

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) , aby uzyskać więcej informacji na temat tych i innych kodów błędów.

## <a name="remarks"></a>Uwagi

Procedura **putc** zapisuje pojedynczy znak *c* do *strumienia* wyjściowego w bieżącym położeniu. Dowolną liczbę całkowitą można przesłać do **putc**, ale zapisywane są tylko dolne 8 bitów. Procedura **putchar** jest taka sama jak `putc( c, stdout )`. Dla każdej procedury, jeśli wystąpi błąd odczytu, zostanie ustawiony wskaźnik błędu dla strumienia. **putc** i **putchar** są podobne do **fputc** i **_fputchar**odpowiednio, ale są implementowane zarówno jako funkcje, jak i jako makra (zobacz [wybór między funkcjami i makrami](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)). **putwc** i **putwchar** są odpowiednio wersjami **putc** i **putchar**.

Wersje z sufiksem **_nolock** są identyczne, z tą różnicą, że nie są chronione przed ingerencją przez inne wątki. Mogą one być szybsze, ponieważ nie wiążą się z zablokowaniem innych wątków. Tych funkcji należy używać tylko w kontekstach bezpiecznych dla wątków, takich jak aplikacje jednowątkowe lub gdzie zakres wywoływania już obsługuje izolację wątku.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _UNICODE & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_puttchar**|**putchar**|**putchar**|**putwchar**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**putchar**|\<stdio.h>|
|**putwchar**|\<stdio. h > lub \<WCHAR. h >|

Konsola nie jest obsługiwana w aplikacjach platforma uniwersalna systemu Windows (platformy UWP). Standardowe uchwyty strumienia, które są skojarzone z konsolą, **stdin**, **stdout**i **stderr**, muszą zostać przekierowane przed użyciem funkcji języka C w aplikacjach platformy UWP. Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek uruchomieniowych języka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

```C
// crt_putchar.c
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

   for( p = buffer; (ch != EOF) && (*p != '\0'); p++ )
      ch = putchar( *p );
}
```

### <a name="output"></a>Dane wyjściowe

```Output
This is the line of output
```

## <a name="see-also"></a>Zobacz także

[We/wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fputc, fputwc](fputc-fputwc.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
