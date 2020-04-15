---
title: _dupenv_s, _wdupenv_s
ms.date: 4/2/2020
api_name:
- _dupenv_s
- _wdupenv_s
- _o__dupenv_s
- _o__wdupenv_s
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: f65f1da3e8cef077df04d0bdb7eb2aaf75afd9fa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348056"
---
# <a name="_dupenv_s-_wdupenv_s"></a>_dupenv_s, _wdupenv_s

Pobiera wartość z bieżącego środowiska.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Buforu*<br/>
Bufor do przechowywania wartości zmiennej.

*liczbaOfElements*<br/>
Rozmiar *bufora*.

*Varname*<br/>
Nazwa zmiennej środowiskowej.

## <a name="return-value"></a>Wartość zwracana

Zero na sukces, kod błędu na niepowodzenie.

Te funkcje sprawdzają ich parametry; jeśli *bufor* lub *nazwa warzna* ma **wartość NULL**, nieprawidłowy program obsługi parametrów jest wywoływany zgodnie z opisem w [zatwierdzeniu parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, funkcje ustawić **errno** do **EINVAL** i **zwracać EINVAL**.

Jeśli te funkcje nie mogą przydzielić wystarczającej ilości pamięci, ustawiają *bufor* na **NULL** i *numberOfElements* na 0 i zwracają **ENOMEM**.

## <a name="remarks"></a>Uwagi

Funkcja **_dupenv_s** przeszukuje listę zmiennych środowiskowych dla *warname*. Jeśli zmienna zostanie znaleziona, **_dupenv_s** przydziela bufor i kopiuje wartość zmiennej do buforu. Adres i długość buforu są zwracane w *buforze* i *numberOfElements*. Przydzielając sam bufor, **_dupenv_s** stanowi wygodniejszą alternatywę dla [getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md).

> [!NOTE]
> Jest to odpowiedzialność programu wywołującego, aby zwolnić pamięć, dzwoniąc [za darmo](free.md).

Jeśli zmienna nie zostanie znaleziona, *bufor* jest ustawiony na **NULL**, *numberOfElements* jest ustawiona na 0, a zwracana wartość wynosi 0, ponieważ ta sytuacja nie jest uważana za warunek błędu.

Jeśli nie jesteś zainteresowany rozmiarem buforu, możesz przekazać **wartość NULL** dla *numberOfElements*.

**_dupenv_s** nie jest rozróżniana wielkość liter w systemie operacyjnym Windows. **_dupenv_s** używa kopii środowiska wskazanej przez zmienną globalną **_environ** dostępu do środowiska. Zobacz uwagi w [getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md) do dyskusji na temat **_environ**.

Wartość w *buforze* jest kopią wartości zmiennej środowiskowej; jego modyfikacja nie ma wpływu na środowisko. Użyj [funkcji _putenv_s, _wputenv_s,](putenv-s-wputenv-s.md) aby zmodyfikować wartość zmiennej środowiskowej.

**_wdupenv_s** jest szerokoznakową wersją **_dupenv_s**; argumenty **_wdupenv_s** są ciągami znaków o szerokich znakach. **Zmienna globalna _wenviron** jest szerokoznakową wersją **_environ**. Więcej informacji na temat **_wenviron**można _wgetenv_s znaleźć w [getenv_s.](getenv-s-wgetenv-s.md)

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tdupenv_s**|**_dupenv_s**|**_dupenv_s**|**_wdupenv_s**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_dupenv_s**|\<>|
|**_wdupenv_s**|\<> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Kontrola procesu i środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[Stałe środowiska](../../c-runtime-library/environmental-constants.md)<br/>
[_dupenv_s_dbg, _wdupenv_s_dbg](dupenv-s-dbg-wdupenv-s-dbg.md)<br/>
[getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md)<br/>
[_putenv_s, _wputenv_s](putenv-s-wputenv-s.md)<br/>
