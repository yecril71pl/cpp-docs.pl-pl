---
title: fputc, fputwc
ms.date: 11/04/2016
apiname:
- fputc
- fputwc
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
- fputc
- fputwc
- _fputtc
helpviewer_keywords:
- streams, writing characters to
- fputtc function
- _fputtc function
- fputwc function
- fputc function
ms.assetid: 5a0a593d-43f4-4fa2-a401-ec4e23de4d2f
ms.openlocfilehash: fc06c9f2060baae63071339768cef11fc5f34023
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62288022"
---
# <a name="fputc-fputwc"></a>fputc, fputwc

Zapisuje znak do strumienia.

## <a name="syntax"></a>Składnia

```C
int fputc(
   int c,
   FILE *stream
);
wint_t fputwc(
   wchar_t c,
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Znak do zapisania.

*stream*<br/>
Wskaźnik do **pliku** struktury.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca znak napisany. Aby uzyskać **fputc**, zwracana wartość wynosząca **EOF** wskazuje na błąd. Aby uzyskać **fputwc —**, zwracana wartość wynosząca **WEOF** wskazuje na błąd. Jeśli *strumienia* jest **NULL**, funkcje te wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, zwracają one **EOF** i ustaw **errno** do **EINVAL**.

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Aby uzyskać więcej informacji na temat tych i innych kodów błędu,.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji pisze pojedynczy znak *c* do pliku w miejscu wskazywanym przez wskaźnik położenia skojarzonego pliku (Jeżeli zdefiniowano) i przesuwa wskaźnik zgodnie z potrzebami. W przypadku właściwości **fputc** i **fputwc —**, plik jest skojarzony z *strumienia*. Jeśli plik nie może obsłużyć żądania pozycjonowania lub został otwarty w trybie dołączania, znak jest dołączany na końcu strumienia.

Te dwie funkcje zachowują się identycznie, jeżeli strumień jest otwarty w trybie ANSI. **fputc** aktualnie nie obsługuje danych wyjściowych w strumieniu UNICODE.

Wersje **_nolock** sufiksem są identyczne, z tą różnicą, że nie są chronione przed ingerencją przez inne wątki. Aby uzyskać więcej informacji, zobacz[_fputc_nolock, _fputwc_nolock —](fputc-nolock-fputwc-nolock.md).

Wykonaj rutynowe specyficzne uwagi.

|Procedura|Uwagi|
|-------------|-------------|
|**fputc**|Odpowiednikiem **putc**, ale realizowane tylko jako funkcja, a nie jako funkcja i makra.|
|**fputwc —**|Wersja znaków dwubajtowych **fputc**. Zapisuje *c* jako znak wielobajtowy lub znak dwubajtowy ze czy *strumienia* jest otwarty w trybie tekstu lub w trybie binarnym.|

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fputtc —**|**fputc**|**fputc**|**fputwc —**|

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fputc**|\<stdio.h>|
|**fputwc —**|\<stdio.h > lub \<wchar.h >|

Konsola nie jest obsługiwana w aplikacjach platformy uniwersalnej Windows (UWP). Standardowe uchwyty strumienia, które są powiązane z konsolą —**stdin**, **stdout**, i **stderr**— muszą zostać przekierowane zanim funkcje środowiska wykonawczego języka C można ich używać w aplikacjach platformy UWP . Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_fputc.c
// This program uses fputc
// to send a character array to stdout.

#include <stdio.h>

int main( void )
{
   char strptr1[] = "This is a test of fputc!!\n";
   char *p;

   // Print line to stream using fputc.
   p = strptr1;
   while( (*p != '\0') && fputc( *(p++), stdout ) != EOF ) ;

}
```

```Output
This is a test of fputc!!
```

## <a name="see-also"></a>Zobacz także

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[fgetc, fgetwc](fgetc-fgetwc.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
