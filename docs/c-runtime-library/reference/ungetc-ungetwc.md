---
title: ungetc, ungetwc
ms.date: 4/2/2020
api_name:
- ungetwc
- ungetc
- _o_ungetc
- _o_ungetwc
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
ms.openlocfilehash: 484af7b72f860a8a9d12cf0b62444871caad4675
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361294"
---
# <a name="ungetc-ungetwc"></a>ungetc, ungetwc

Wypycha znak z powrotem do strumienia.

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

*C*<br/>
Postać do pchania.

*Strumienia*<br/>
Wskaźnik do struktury **PLIK.**

## <a name="return-value"></a>Wartość zwracana

Jeśli powiedzie się, każda z tych funkcji zwraca argument znaku *c*. Jeśli *c* nie może zostać odepchnięty lub jeśli nie odczytano żadnego znaku, strumień wejściowy pozostaje niezmieniony, a **ungetc** zwraca **EOF;** **ungetwc** zwraca **WEOF**. Jeśli *strumień* ma **wartość NULL**, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [yd.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, **EOF** lub **WEOF** jest zwracany i **errno** jest ustawiona na **EINVAL**.

Aby uzyskać informacje na temat tych i innych kodów błędów, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **ungetc** wypycha znak *c* z powrotem do *strumienia* i czyści wskaźnik końca pliku. Strumień musi być otwarty do odczytu. Kolejna operacja odczytu na *strumieniu* rozpoczyna się *od c*. Próba wypchnięcia **EOF** do strumienia przy użyciu **ungetc** jest ignorowana.

Znaki umieszczone w strumieniu przez **ungetc** mogą zostać usunięte, jeśli **fflush**, [fseek](fseek-fseeki64.md), **fsetpos**, lub [przewinąć](rewind.md) do tyłu jest wywoływana przed odczytywaniem znaku ze strumienia. Wskaźnik położenia pliku będzie miał wartość, którą miał przed przesunięciu znaków. Zewnętrzna pamięć odpowiadająca strumieniu pozostaje niezmieniona. W przypadku pomyślnego wywołania **ungetc** względem strumienia tekstu wskaźnik położenia pliku jest nieokreślony, dopóki wszystkie odepchnięte znaki nie zostaną odczytane lub odrzucone. Na każdym pomyślnym wywołaniu **ungetc** względem strumienia binarnego wskaźnik położenia pliku jest zmniejszany; jeśli jego wartość wynosiła 0 przed wywołaniem, wartość jest niezdefiniowana po wywołaniu.

Wyniki są nieprzewidywalne, jeśli **ungetc** jest wywoływana dwa razy bez operacji odczytu lub pozycjonowania plików między dwoma wywołaniami. Po wywołaniu **fscanf**wywołanie **ungetc** może zakończyć się niepowodzeniem, chyba że została wykonana inna operacja odczytu (na przykład **getc).** To **dlatego, że fscanf** się nazywa **ungetc**.

**ungetwc** jest szerokoznakową wersją **ungetc**. Jednak w każdym pomyślnym **wywołaniu ungetwc** względem strumienia tekstowego lub binarnego wartość wskaźnika położenia pliku jest nieokreślona, dopóki wszystkie odepchnięte znaki nie zostaną odczytane lub odrzucone.

Funkcje te są bezpieczne dla wątków i zablokować poufne dane podczas wykonywania. Aby uzyskać wersję niezablokującą, zobacz [_ungetc_nolock _ungetwc_nolock](ungetc-nolock-ungetwc-nolock.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ungettc**|**ungetc (ungetc)**|**ungetc (ungetc)**|**ungetwc (ungetwc)**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**ungetc (ungetc)**|\<stdio.h>|
|**ungetwc (ungetwc)**|\<stdio.h> lub \<wchar.h>|

Konsola nie jest obsługiwana w aplikacjach platformy uniwersalnej systemu Windows (UWP). Standardowe uchwyty strumienia, które są skojarzone z konsolą, **stdin**, **stdout**i **stderr**, muszą zostać przekierowane, zanim funkcje c w czasie wykonywania mogą z nich korzystać w aplikacjach platformy uniwersalnej systemu Windows. Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
