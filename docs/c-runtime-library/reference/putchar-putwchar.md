---
title: putchar, putwchar
ms.date: 4/2/2020
api_name:
- putchar
- putwchar
- _o_putchar
- _o_putwchar
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 09ad53a7f4e953da05d7eafd6662bf250731b5d6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333129"
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

*C*<br/>
Znak do zapisania.

## <a name="return-value"></a>Wartość zwracana

Zwraca zapisany znak. Aby wskazać błąd lub warunek końca pliku, **putc** i **putchar** zwracają **EOF**; **putwc** i **putwchar** powrót **WEOF**. W przypadku wszystkich czterech procedur użyj [ferror](ferror.md) lub [feof,](feof.md) aby sprawdzić, czy nie ma błędu lub końca pliku. Jeśli przeszedł wskaźnik null dla *strumienia,* te funkcje generują nieprawidłowy wyjątek parametru, zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, zwracają **EOF** lub **WEOF** i ustawić **errno** do **EINVAL**.

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr aby](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) uzyskać więcej informacji na temat tych i innych kodów błędów.

## <a name="remarks"></a>Uwagi

Procedura **putc** zapisuje pojedynczy znak *c* do *strumienia* wyjściowego w bieżącej pozycji. Każda liczba całkowita może być przekazywana do **putc**, ale zapisywane są tylko niższe 8 bitów. Procedura **putchar** jest `putc( c, stdout )`identyczna z . Dla każdej procedury, jeśli wystąpi błąd odczytu, wskaźnik błędu dla strumienia jest ustawiony. **putc** i **putchar** są podobne do **fputc** i **_fputchar,** odpowiednio, ale są implementowane zarówno jako funkcje, jak i jako makra (patrz [Wybieranie między funkcjami i makrami](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)). **putwc** i **putwchar** są szerokoznakowymi wersjami **putc** i **putchar**, odpowiednio.

Wersje z sufiksem **_nolock** są identyczne, z tą różnicą, że nie są chronione przed zakłóceniami przez inne wątki. Mogą one być szybsze, ponieważ nie ponoszą narzutu blokowania innych wątków. Użyj tych funkcji tylko w kontekstach bezpiecznych dla wątków, takich jak aplikacje jednowątkowe lub gdzie zakres wywołujący obsługuje już izolację wątku.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_puttchar**|**putchar ( putchar )**|**putchar ( putchar )**|**putwchar ( putwchar )**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**putchar ( putchar )**|\<stdio.h>|
|**putwchar ( putwchar )**|\<stdio.h> lub \<wchar.h>|

Konsola nie jest obsługiwana w aplikacjach platformy uniwersalnej systemu Windows (UWP). Standardowe uchwyty strumienia, które są skojarzone z konsolą, **stdin**, **stdout**i **stderr**, muszą zostać przekierowane, zanim funkcje c w czasie wykonywania mogą z nich korzystać w aplikacjach platformy uniwersalnej systemu Windows. Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek wyładowywowych języka C](../../c-runtime-library/crt-library-features.md).

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

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fputc, fputwc](fputc-fputwc.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
