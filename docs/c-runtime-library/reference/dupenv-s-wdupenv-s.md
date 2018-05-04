---
title: _dupenv_s —, _wdupenv_s — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _dupenv_s function
- _tdupenv_s function
- _wdupenv_s function
- environment variables
- wdupenv_s function
- dupenv_s function
- tdupenv_s function
ms.assetid: b729ecc2-a31d-4ccf-92a7-5accedb8f8c8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5a918b866b0b43fb0e6b31e2deb5d9861dabe9a2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="dupenvs-wdupenvs"></a>_dupenv_s, _wdupenv_s

Pobiera wartość po bieżącym środowisku.

> [!IMPORTANT]
> Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Bufor do przechowywania wartość zmiennej.

*numberOfElements*<br/>
Rozmiar *buforu*.

*nazwa_zmiennej*<br/>
Nazwa zmiennej środowiskowej.

## <a name="return-value"></a>Wartość zwracana

Zero w przypadku powodzenia, kod błędu w przypadku awarii.

Te funkcje walidację ich parametrów; Jeśli *buforu* lub *nazwa_zmiennej* jest **NULL**, zgodnie z opisem w wywołaniu program obsługi nieprawidłowych parametrów [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, Ustaw funkcje **errno** do **einval —** i zwracać **einval —**.

Jeśli te funkcje nie może przydzielić wystarczającej ilości pamięci, sami ustawiają *buforu* do **NULL** i *numberOfElements* 0 i powrotu **enomem —**.

## <a name="remarks"></a>Uwagi

**_Dupenv_s —** funkcja wyszukuje listę zmiennych środowiskowych dla *nazwa_zmiennej*. Jeśli zmienna zostanie znaleziony, **_dupenv_s —** przydziela buforu i kopiuje wartość zmiennej w buforze. Adres buforu i długość są zwracane w *buforu* i *numberOfElements*. Przydzielając buforu, **_dupenv_s —** wygodniejsze alternatywą dla [getenv_s —, _wgetenv_s —](getenv-s-wgetenv-s.md).

> [!NOTE]
> Jest odpowiedzialny za program wywołujący, aby zwolnić pamięć, wywołując [wolnego](free.md).

Jeśli zmienna nie zostanie znaleziony, następnie *buforu* ustawiono **NULL**, *numberOfElements* jest ustawiona na 0, i zwracana wartość wynosi 0, ponieważ taka sytuacja nie jest traktowana jako błąd warunek.

Jeśli nie jesteś zainteresowany rozmiar buforu można przekazać **NULL** dla *numberOfElements*.

**_dupenv_s —** nie jest uwzględniana wielkość liter w systemie operacyjnym Windows. **_dupenv_s —** używa kopii środowiska wskazywanej przez zmienną globalne **_environ —** można uzyskiwać dostęp do środowiska. Zobacz uwagi w [getenv_s —, _wgetenv_s —](getenv-s-wgetenv-s.md) omówienie **_environ —**.

Wartość w *buforu* jest kopią wartości zmiennej środowiskowej; modyfikowania jej nie ma wpływu na środowisko. Użyj [_putenv_s —, _wputenv_s —](putenv-s-wputenv-s.md) funkcji, aby zmodyfikować wartość zmiennej środowiskowej.

**_wdupenv_s —** jest wersja znaków dwubajtowych **_dupenv_s —**; argumentów **_wdupenv_s —** są ciągami znaków dwubajtowych. **_Wenviron —** — zmienna globalna jest wersja znaków dwubajtowych **_environ —**. Zobacz uwagi w [getenv_s —, _wgetenv_s —](getenv-s-wgetenv-s.md) Aby uzyskać więcej informacji na temat **_wenviron —**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
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
