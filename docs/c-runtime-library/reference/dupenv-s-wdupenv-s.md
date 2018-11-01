---
title: _dupenv_s, _wdupenv_s
ms.date: 11/04/2016
apiname:
- _dupenv_s
- _wdupenv_s
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
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: bc8af3282b57c9fa411aac97f5fa4d414bc3305b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646511"
---
# <a name="dupenvs-wdupenvs"></a>_dupenv_s, _wdupenv_s

Pobiera wartość z bieżącego środowiska.

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Nazwa zmiennej*<br/>
Nazwa zmiennej środowiskowej.

## <a name="return-value"></a>Wartość zwracana

Zero, w przypadku powodzenia, kod błędu.

Te funkcje sprawdzają poprawność parametrów; Jeśli *buforu* lub *nazwa_zmiennej* jest **NULL**, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcje ustawiają **errno** do **EINVAL** i zwracają **EINVAL**.

Jeśli te funkcje nie może przydzielić wystarczającej ilości pamięci, ustawiają *buforu* do **NULL** i *numberOfElements* do 0 i zwracają **ENOMEM**.

## <a name="remarks"></a>Uwagi

**_Dupenv_s —** Funkcja przeszukuje listę zmiennych środowiskowych dla *nazwa_zmiennej*. Jeśli zmienna zostanie znaleziona, **_dupenv_s —** przydziela bufor i kopiuje wartość zmiennej do bufora. Adres i długość buforu są zwracane w *buforu* i *numberOfElements*. Przydzielając sam bufor, **_dupenv_s —** zapewnia wygodniejszą alternatywę [getenv_s —, _wgetenv_s —](getenv-s-wgetenv-s.md).

> [!NOTE]
> Odpowiada za program wywołujący zwolnienie pamięci przez wywołanie metody [bezpłatne](free.md).

Jeśli zmienna nie zostanie znaleziony, następnie *buforu* ustawiono **NULL**, *numberOfElements* jest równa 0, i wartość zwracana to 0, ponieważ ta sytuacja nie jest uważany za błąd warunek.

Jeśli nie jesteś zainteresowany rozmiarem buforu można przekazać **NULL** dla *numberOfElements*.

**_dupenv_s —** nie uwzględnia wielkości liter w systemie operacyjnym Windows. **_dupenv_s —** używa kopii środowiska wskazywanego przez zmienną globalną **_environ** można uzyskiwać dostęp do środowiska. Zobacz uwagi w [getenv_s —, _wgetenv_s —](getenv-s-wgetenv-s.md) dyskusję na temat **_environ**.

Wartość w *buforu* jest kopią wartość zmiennej środowiskowej; modyfikowanie nie ma wpływu na środowisko. Użyj [_putenv_s, _wputenv_s —](putenv-s-wputenv-s.md) funkcji, aby zmodyfikować wartość zmiennej środowiskowej.

**_wdupenv_s —** to wersja znaku dwubajtowego **_dupenv_s —**; argumenty **_wdupenv_s —** są ciągami znaków dwubajtowych. **_Wenviron** zmienna globalna jest wersją znaków dwubajtowych **_environ**. Zobacz uwagi w [getenv_s —, _wgetenv_s —](getenv-s-wgetenv-s.md) Aby uzyskać więcej informacji na temat **_wenviron**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tdupenv_s —**|**_dupenv_s**|**_dupenv_s**|**_wdupenv_s**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_dupenv_s**|\<stdlib.h>|
|**_wdupenv_s**|\<stdlib.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
