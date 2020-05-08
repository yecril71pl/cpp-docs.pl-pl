---
title: fputc, fputwc
ms.date: 4/2/2020
api_name:
- fputc
- fputwc
- _o_fputc
- _o_fputwc
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 90091bff6a8ee3ced050c359ed540f45afe74f6b
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910208"
---
# <a name="fputc-fputwc"></a>fputc, fputwc

Zapisuje znak w strumieniu.

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

*s*<br/>
Znak do zapisania.

*produkcyjne*<br/>
Wskaźnik do struktury **pliku** .

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca znak zapisany. Dla **fputc**wartość zwracana przez **EOF** wskazuje na błąd. Dla **fputwc**wartość zwracana przez **WEOF** wskazuje na błąd. Jeśli *strumień* ma **wartość null**, te funkcje wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, zwracają **eof** i ustawiają **errno** na **EINVAL**.

Aby uzyskać więcej informacji na temat tych i innych kodów błędów, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

## <a name="remarks"></a>Uwagi

Każda z tych funkcji zapisuje pojedynczy znak *c* do pliku w pozycji wskazywanej przez wskaźnik położenia skojarzonego pliku (jeśli jest zdefiniowany) i przesuwa wskaźnik odpowiednio do potrzeb. W przypadku **fputc** i **fputwc**plik jest skojarzony ze *strumieniem*. Jeśli plik nie może obsługiwać żądań pozycjonowania lub został otwarty w trybie dołączania, znak jest dołączany na końcu strumienia.

Dwie funkcje zachowują się identycznie, jeśli strumień jest otwarty w trybie ANSI. **fputc** obecnie nie obsługuje danych wyjściowych w strumieniu Unicode.

Wersje z sufiksem **_nolock** są identyczne, z tą różnicą, że nie są chronione przed ingerencją przez inne wątki. Aby uzyskać więcej informacji, zobacz[_fputc_nolock, _fputwc_nolock](fputc-nolock-fputwc-nolock.md).

Uwagi dotyczące rutynowych czynności.

|Procedura|Uwagi|
|-------------|-------------|
|**fputc**|Równoważne **putc**, ale zaimplementowane tylko jako funkcja, a nie jako funkcja i makro.|
|**fputwc**|Dwubajtowa wersja **fputc**. Zapisuje *c* jako znak wielobajtowy lub szeroki znak w zależności od tego, czy *strumień* jest otwarty w trybie tekstowym czy w trybie binarnym.|

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _MBCS _UNICODE &|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fputtc**|**fputc**|**fputc**|**fputwc**|

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fputc**|\<stdio. h>|
|**fputwc**|\<stdio. h> lub \<WCHAR. h>|

Konsola nie jest obsługiwana w aplikacjach platforma uniwersalna systemu Windows (platformy UWP). Standardowe uchwyty strumienia, które są skojarzone z konsolą —**stdin**, **stdout**i **stderr**— muszą zostać przekierowane przed użyciem funkcji języka C w aplikacjach platformy UWP. Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fgetc, fgetwc](fgetc-fgetwc.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
