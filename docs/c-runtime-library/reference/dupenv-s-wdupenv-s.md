---
title: _dupenv_s, _wdupenv_s
ms.date: 11/04/2016
api_name:
- _dupenv_s
- _wdupenv_s
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
- api-ms-win-crt-environment-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- tdupenv_s
- _dupenv_s
- wdupenv_s
- dupenv_s
- _tdupenv_s
- _wdupenv_s
helpviewer_keywords:
- _dupenv_s function
- _tdupenv_s function
- _wdupenv_s function
- environment variables
- wdupenv_s function
- dupenv_s function
- tdupenv_s function
ms.assetid: b729ecc2-a31d-4ccf-92a7-5accedb8f8c8
ms.openlocfilehash: f66828e0941c2324d75797cbb1fa77bdfa184205
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942024"
---
# <a name="_dupenv_s-_wdupenv_s"></a>_dupenv_s, _wdupenv_s

Pobiera wartość z bieżącego środowiska.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
errno_t _dupenv_s(
   char **buffer,
   size_t *numberOfElements,
   const char *varname
);
errno_t _wdupenv_s(
   wchar_t **buffer,
   size_t *numberOfElements,
   const wchar_t *varname
);
```

### <a name="parameters"></a>Parametry

*buffer*<br/>
Bufor do przechowywania wartości zmiennej.

*numberOfElements*<br/>
Rozmiar *buforu*.

*nazwa_zmiennej*<br/>
Nazwa zmiennej środowiskowej.

## <a name="return-value"></a>Wartość zwracana

Zero po powodzeniu, kod błędu w przypadku niepowodzenia.

Te funkcje sprawdzają poprawność swoich parametrów; Jeśli *buffer* lub *Nazwa_zmiennej* ma **wartość null**, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcje ustawiają **errno** na **EINVAL** i zwracają **EINVAL**.

Jeśli te funkcje nie mogą przydzielić wystarczającej ilości pamięci, ustawia *bufor* na **null** i *NumberOfElements* na 0, a następnie zwraca **ENOMEM**.

## <a name="remarks"></a>Uwagi

Funkcja **_dupenv_s** przeszukuje listę zmiennych środowiskowych dla elementu *nazwa_zmiennej*. Jeśli zmienna zostanie znaleziona, **_dupenv_s** przydziela bufor i kopiuje wartość zmiennej do buforu. Adres i długość buforu są zwracane w *buforze* i *NumberOfElements*. Przydzielając sam bufor, **_dupenv_s** zapewnia bardziej wygodną alternatywę dla [getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md).

> [!NOTE]
> Program wywołujący jest odpowiedzialny za zwolnienie pamięci przez wywołanie [bezpłatnej](free.md).

Jeśli zmienna nie zostanie znaleziona, *bufor* ma wartość **null**, *NumberOfElements* jest ustawiona na 0, a wartość zwracana to 0, ponieważ ta sytuacja nie jest uważana za warunek błędu.

Jeśli nie interesują Cię wielkości bufora, można przekazać **wartość null** dla *NumberOfElements*.

w systemie operacyjnym Windows w **_dupenv_s** nie jest rozróżniana wielkość liter. **_dupenv_s** używa kopii środowiska wskazanej przez zmienną globalną **_environ** w celu uzyskania dostępu do środowiska. Zobacz uwagi w [getenv_s, _wgetenv_s,](getenv-s-wgetenv-s.md) aby zapoznać się z omówieniem **_environ**.

Wartość w *buforze* jest kopią wartości zmiennej środowiskowej; Modyfikowanie go nie ma wpływu na środowisko. Użyj funkcji [_putenv_s, _wputenv_s,](putenv-s-wputenv-s.md) aby zmodyfikować wartość zmiennej środowiskowej.

**_wdupenv_s** to dwubajtowa wersja **_dupenv_s**; argumenty **_wdupenv_s** są ciągami znaków dwubajtowych. **_Wenviron** Global Variable to dwubajtowa wersja **_environ**. Zobacz uwagi w [getenv_s, _wgetenv_s,](getenv-s-wgetenv-s.md) Aby uzyskać więcej informacji na temat **_wenviron**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _UNICODE & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tdupenv_s**|**_dupenv_s**|**_dupenv_s**|**_wdupenv_s**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_dupenv_s**|\<stdlib.h>|
|**_wdupenv_s**|\<STDLIB. h > lub \<WCHAR. h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_dupenv_s.c
#include  <stdlib.h>

int main( void )
{
   char *pValue;
   size_t len;
   errno_t err = _dupenv_s( &pValue, &len, "pathext" );
   if ( err ) return -1;
   printf( "pathext = %s\n", pValue );
   free( pValue );
   err = _dupenv_s( &pValue, &len, "nonexistentvariable" );
   if ( err ) return -1;
   printf( "nonexistentvariable = %s\n", pValue );
   free( pValue ); // It's OK to call free with NULL
}
```

```Output
pathext = .COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.pl
nonexistentvariable = (null)
```

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[Stałe środowiska](../../c-runtime-library/environmental-constants.md)<br/>
[_dupenv_s_dbg, _wdupenv_s_dbg](dupenv-s-dbg-wdupenv-s-dbg.md)<br/>
[getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md)<br/>
[_putenv_s, _wputenv_s](putenv-s-wputenv-s.md)<br/>
