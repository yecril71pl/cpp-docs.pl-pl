---
title: ungetc, ungetwc
ms.date: 11/04/2016
api_name:
- ungetwc
- ungetc
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
ms.openlocfilehash: f3b6c6ed3fe8ff5976afa1da2ed437e25c923b99
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957419"
---
# <a name="ungetc-ungetwc"></a>ungetc, ungetwc

Wypchnięcie znaku z powrotem do strumienia.

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

*stream*<br/>
Wskaźnik do struktury **pliku** .

## <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, każda z tych funkcji zwraca argument znaku *c*. Jeśli nie można wypchnąć *dysku c* lub nie odczytano żadnego znaku, strumień wejściowy jest niezmieniony i **ungetc —** zwraca **EOF**; **ungetwc** zwraca **WEOF**. Jeśli *strumień* ma **wartość null**, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, zwracany jest **znacznik EOF** lub **WEOF** , a **errno** jest ustawiony na **EINVAL**.

Aby uzyskać informacje o tych i innych kodach błędów, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **ungetc —** wypchnięcie znaku *c* z powrotem do *strumienia* i czyści wskaźnik końca pliku. Strumień musi być otwarty do odczytu. Kolejna operacja odczytu *strumienia* zaczyna się od *c*. Próba wypychania **eof** do strumienia przy użyciu **ungetc —** jest ignorowana.

Znaki umieszczone w strumieniu przez **ungetc —** mogą zostać wymazane, jeśli **fflush**, [fseek](fseek-fseeki64.md), **fsetpos**lub [przewijania do tyłu](rewind.md) jest wywoływana przed odczytaniem znaku ze strumienia. Wskaźnik położenia pliku będzie miał wartość, która miała przed wypchnięciem znaków. Zewnętrzne magazyny odpowiadające strumieniu nie są zmieniane. W przypadku pomyślnego wywołania **ungetc —** na strumień tekstowy wskaźnik położenia pliku jest nieokreślony do momentu odczytania wszystkich znaków push lub odrzuconych. Dla każdego pomyślnego wywołania **ungetc —** względem strumienia binarnego wskaźnik położenia pliku jest zmniejszany; Jeśli wartość była równa 0 przed wywołaniem, wartość jest niezdefiniowana po wywołaniu.

Wyniki są nieprzewidywalne, jeśli **ungetc —** jest wywoływana dwukrotnie bez operacji odczytu lub położenia pliku między dwoma wywołaniami. Po wywołaniu **fscanf**wywołanie **ungetc —** może zakończyć się niepowodzeniem, chyba że została wykonana inna operacja odczytu (na przykład **getc —** ). Wynika to z faktu, że **fscanf** same wywołuje **ungetc —** .

**ungetwc** to dwubajtowa wersja **ungetc —** . Jednak dla każdego pomyślnego wywołania **ungetwc** na strumień tekstowy lub binarny wartość wskaźnika położenia pliku jest nieokreślona do momentu odczytania lub odrzucenia wszystkich znaków wypchnięcia.

Te funkcje są bezpieczne dla wątków i blokują dane poufne podczas wykonywania. W przypadku wersji, która nie jest blokowana, zobacz [_ungetc_nolock, _ungetwc_nolock](ungetc-nolock-ungetwc-nolock.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _UNICODE & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ungettc**|**ungetc**|**ungetc**|**ungetwc**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**ungetc**|\<stdio.h>|
|**ungetwc**|\<stdio. h > lub \<WCHAR. h >|

Konsola nie jest obsługiwana w aplikacjach platforma uniwersalna systemu Windows (platformy UWP). Standardowe uchwyty strumienia, które są skojarzone z konsolą, **stdin**, **stdout**i **stderr**, muszą zostać przekierowane przed użyciem funkcji języka C w aplikacjach platformy UWP. Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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

[We/wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
