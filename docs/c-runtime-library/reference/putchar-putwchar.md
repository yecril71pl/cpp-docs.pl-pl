---
title: putchar, putwchar
ms.date: 11/04/2016
apiname:
- putchar
- putwchar
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
ms.openlocfilehash: becee3d79f58ac018d1161c1af36e9a4646640bf
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51327060"
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

Zwraca znak napisany. Aby wskazać błąd lub warunek końca pliku **putc** i **putchar** zwracają **EOF**; **putwc** i **putwchar** zwracają **WEOF**. W przypadku wszystkich czterech procedur, użyj [ferror](ferror.md) lub [feof](feof.md) pod kątem błąd lub koniec pliku. Jeśli przekazywany jest pusty wskaźnik *strumienia*, te funkcje tworzą wyjątek nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, zwracają one **EOF** lub **WEOF** i ustaw **errno** do **EINVAL**.

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Aby uzyskać więcej informacji na temat tych i innych kodów błędu,.

## <a name="remarks"></a>Uwagi

**Putc** rutynowo pisze pojedynczy znak *c* w danych wyjściowych *strumienia* w bieżącym położeniu. Dowolna liczba całkowita może być przekazywany do **putc**, ale tylko niższe 8 bitów jest zapisywane. **Putchar** rutyna jest identyczna z `putc( c, stdout )`. Dla każdej procedury Jeśli wystąpi błąd odczytu, wskaźnik błędu dla strumienia jest ustawiony. **putc** i **putchar** są podobne do **fputc** i **_fputchar**, odpowiednio, ale są implementowane zarówno funkcje, jak makra (zobacz [ Wybierania pomiędzy funkcjami i makrami](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)). **putwc** i **putwchar** są wersjami znaków dwubajtowych **putc** i **putchar**, odpowiednio.

Wersje **_nolock** sufiksem są identyczne, z tą różnicą, że nie są chronione przed ingerencją przez inne wątki. Mogą one być szybsze, ponieważ nie wiążą się z obciążeniem związanym z blokowaniem innych wątków. Za pomocą tych funkcji tylko w kontekstach wątków, takich jak aplikacje jednowątkowe lub gdzie zakres wywołujący już obsługuje izolację wątków.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_puttchar —**|**putchar**|**putchar**|**putwchar**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**putchar**|\<stdio.h>|
|**putwchar**|\<stdio.h > lub \<wchar.h >|

Konsola nie jest obsługiwana w aplikacjach platformy uniwersalnej Windows (UWP). Standardowe uchwyty strumienia, które są powiązane z konsolą, **stdin**, **stdout**, i **stderr**, muszą zostać przekierowane zanim funkcje środowiska wykonawczego języka C można ich używać w aplikacjach platformy UWP . Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

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

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[fputc, fputwc](fputc-fputwc.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
