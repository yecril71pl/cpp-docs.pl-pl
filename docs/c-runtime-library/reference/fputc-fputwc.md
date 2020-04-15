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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 289e1114a936bdaa41fc59a0526db006536461f7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346269"
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

*C*<br/>
Znak do zapisania.

*Strumienia*<br/>
Wskaźnik do struktury **PLIK.**

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca zapisany znak. Dla **fputc**, zwracana wartość **EOF** wskazuje błąd. Dla **fputwc**, zwracana wartość **WEOF** wskazuje błąd. Jeśli *strumień* ma **wartość NULL**, te funkcje wywołują nieprawidłowy program obsługi parametrów, zgodnie z opisem w [zatwierdzeniu parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, zwracają **EOF** i ustawić **errno** do **EINVAL**.

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr aby](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) uzyskać więcej informacji na temat tych i innych kodów błędów.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji zapisuje pojedynczy znak *c* do pliku w pozycji wskazanej przez powiązany wskaźnik położenia pliku (jeśli jest zdefiniowany) i przesuwa wskaźnik, stosownie do przypadku. W przypadku **fputc** i **fputwc**plik jest skojarzony ze *strumieniem*. Jeśli plik nie obsługuje żądań pozycjonowania lub został otwarty w trybie dołączania, znak jest dołączany na końcu strumienia.

Te dwie funkcje zachowują się identycznie, jeśli strumień jest otwarty w trybie ANSI. **fputc** obecnie nie obsługuje danych wyjściowych do strumienia UNICODE.

Wersje z sufiksem **_nolock** są identyczne, z tą różnicą, że nie są chronione przed zakłóceniami przez inne wątki. Aby uzyskać więcej informacji, zobacz[_fputc_nolock _fputwc_nolock](fputc-nolock-fputwc-nolock.md).

Rutynowe uwagi następują.

|Procedura|Uwagi|
|-------------|-------------|
|**fputc ( fputc )**|Odpowiednik **putc**, ale realizowane tylko jako funkcja, a nie jako funkcja i makro.|
|**fputwc ( fputwc )**|Szerokoznakowa wersja **fputc**. Zapisuje *c* jako znak wielobajtowy lub szeroki znak w zależności od tego, czy *strumień* jest otwarty w trybie tekstowym, czy w trybie binarnym.|

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fputtc**|**fputc ( fputc )**|**fputc ( fputc )**|**fputwc ( fputwc )**|

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fputc ( fputc )**|\<stdio.h>|
|**fputwc ( fputwc )**|\<stdio.h> lub \<wchar.h>|

Konsola nie jest obsługiwana w aplikacjach platformy uniwersalnej systemu Windows (UWP). Standardowe uchwyty strumienia, które są skojarzone z konsolą—**stdin,** **stdout**i **stderr**— muszą zostać przekierowane, zanim funkcje c w czasie wykonywania będą mogły z nich korzystać w aplikacjach platformy uniwersalnej systemu Windows. Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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
