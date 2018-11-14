---
title: ungetc, ungetwc
ms.date: 11/04/2016
apiname:
- ungetwc
- ungetc
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
- _ungettc
- ungetwc
- ungetc
helpviewer_keywords:
- ungetwc function
- ungettc function
- characters, pushing back onto stream
- _ungettc function
- ungetc function
ms.assetid: e0754f3a-b4c6-408f-90c7-e6387b830d84
ms.openlocfilehash: c504540f8fbbe14961fa051bb93ebef350c2c1da
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51332390"
---
# <a name="ungetc-ungetwc"></a>ungetc, ungetwc

Przesuwa znak do strumienia.

## <a name="syntax"></a>Składnia

```C
int ungetc(
   int c,
   FILE *stream
);
wint_t ungetwc(
   wint_t c,
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Znak do wypchnięcia.

*Stream*<br/>
Wskaźnik do **pliku** struktury.

## <a name="return-value"></a>Wartość zwracana

Jeśli operacja się powiedzie, każda z tych funkcji zwraca znak argumentu *c*. Jeśli *c* nie może zostać przesunięty lub jeśli został odczytany żaden znak, strumień wejściowy pozostaje niezmieniony i **ungetc —** zwraca **EOF**; **ungetwc —** zwraca **WEOF**. Jeśli *strumienia* jest **NULL**, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **EOF** lub **WEOF** zwróceniem i **errno** ustawiono **EINVAL**.

Aby uzyskać informacje na temat tych i innych kodów błędu, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**Ungetc —** funkcja umieszcza znak *c* na *strumienia* i czyści wskaźnik końca pliku. Strumień musi być otwarty do odczytu. Kolejna operacja odczytu na *strumienia* rozpoczyna się od *c*. Próba popchnięcia **EOF** do strumienia z wykorzystaniem **ungetc —** jest ignorowana.

Znaki umieszczone w strumieniu przez **ungetc —** mogą zostać wymazane, jeśli **fflush —**, [fseek](fseek-fseeki64.md), **fsetpos**, lub [rewind](rewind.md) jest wywoływana przed odczytem znaku ze strumienia. Wskaźnik położenia pliku będzie miał wartość, jaką miała zanim znaki były odsunięte. Magazynu zewnętrznego, odpowiadające strumieniowi jest bez zmian. Po pomyślnym **ungetc —** wywołaniu strumienia tekstu, wskaźnik pozycji pliku jest nieokreślony, aż wszystkie znaki przesunięta wstecz zostaną odczytywane lub odrzucone. Na każdym pomyślnym **ungetc —** wywołaniu strumienia binarnego, wskaźnik pozycji pliku zostanie zmniejszony; jeśli jego wartość wynosiła 0 przed wywołaniem, wartość jest niezdefiniowana po wywołaniu.

Wyniki są nieprzewidywalne Jeśli **ungetc —** jest wywoływana dwa razy bez odczytu lub operacji położenia pliku między dwoma połączeniami. Po wywołaniu **fscanf —**, wywołanie **ungetc —** może zakończyć się niepowodzeniem, chyba że inna operacja odczytu (takie jak **getc —**) została wykonana. Jest to spowodowane **fscanf —** nazywa **ungetc —**.

**ungetwc —** to wersja znaku dwubajtowego **ungetc —**. Jednak na każdym pomyślnym **ungetwc —** wywołaniu strumienia tekstu lub pliku binarnego, wartość wskaźnika pozycji pliku jest nieokreślony, aż wszystkie znaki przesunięta wstecz zostaną odczytywane lub odrzucone.

Te funkcje są odporne na wątki i blokują dane poufne podczas wykonywania. Dla wersji bez blokady, zobacz [_ungetc_nolock —, _ungetwc_nolock —](ungetc-nolock-ungetwc-nolock.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ungettc —**|**ungetc**|**ungetc**|**ungetwc**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**ungetc**|\<stdio.h>|
|**ungetwc**|\<stdio.h > lub \<wchar.h >|

Konsola nie jest obsługiwana w aplikacjach platformy uniwersalnej Windows (UWP). Standardowe uchwyty strumienia, które są powiązane z konsolą, **stdin**, **stdout**, i **stderr**, muszą zostać przekierowane zanim funkcje środowiska wykonawczego języka C można ich używać w aplikacjach platformy UWP . Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_ungetc.c
// This program first converts a character
// representation of an unsigned integer to an integer. If
// the program encounters a character that is not a digit,
// the program uses ungetc to replace it in the  stream.
//

#include <stdio.h>
#include <ctype.h>

int main( void )
{
   int ch;
   int result = 0;

   // Read in and convert number:
   while( ((ch = getchar()) != EOF) && isdigit( ch ) )
      result = result * 10 + ch - '0';    // Use digit.
   if( ch != EOF )
      ungetc( ch, stdin );                // Put nondigit back.
   printf( "Number = %d\nNext character in stream = '%c'",
            result, getchar() );
}
```

```Output

      521aNumber = 521
Next character in stream = 'a'
```

## <a name="see-also"></a>Zobacz także

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
