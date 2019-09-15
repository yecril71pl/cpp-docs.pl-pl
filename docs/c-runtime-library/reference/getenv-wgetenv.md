---
title: getenv, _wgetenv
ms.date: 11/04/2016
api_name:
- getenv
- _wgetenv
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
- _wgetenv
- getenv
- _tgetenv
helpviewer_keywords:
- getenv function
- tgetenv function
- wgetenv function
- environment values
- environment variables
- _tgetenv function
- _wgetenv function
ms.assetid: 3b9cb9ab-a126-4e0e-a44f-6c5a7134daf4
ms.openlocfilehash: 7cacd8588bcc74c6d064da370ce6254aada56c12
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955063"
---
# <a name="getenv-_wgetenv"></a>getenv, _wgetenv

Pobiera wartość z bieżącego środowiska. Bardziej bezpieczne wersje tych funkcji są dostępne; Zobacz [getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md).

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
char *getenv(
   const char *varname
);
wchar_t *_wgetenv(
   const wchar_t *varname
);
```

### <a name="parameters"></a>Parametry

*nazwa_zmiennej*<br/>
Nazwa zmiennej środowiskowej.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do wpisu tabeli środowiska zawierającego element *nazwa_zmiennej*. Nie można bezpiecznie modyfikować wartości zmiennej środowiskowej przy użyciu zwróconego wskaźnika. Użyj funkcji [_putenv](putenv-wputenv.md) , aby zmodyfikować wartość zmiennej środowiskowej. Wartość zwracana ma wartość **null** , jeśli nie można odnaleźć parametru *nazwa_zmiennej* w tabeli środowiskowej.

## <a name="remarks"></a>Uwagi

Funkcja **getenv** przeszukuje listę zmiennych środowiskowych dla elementu *nazwa_zmiennej*. w systemie operacyjnym Windows w **getenv** nie jest rozróżniana wielkość liter. **getenv** i **_putenv** używają kopii środowiska wskazanej przez zmienną globalną **_environ** w celu uzyskania dostępu do środowiska. **getenv** działa tylko na strukturach danych dostępnych dla biblioteki wykonawczej, a nie w środowisku "segment" utworzonym dla procesu przez system operacyjny. W związku z tym programy korzystające z argumentu *envp* do [Main](../../cpp/main-program-startup.md) lub [wmain](../../cpp/main-program-startup.md) mogą pobrać nieprawidłowe informacje.

Jeśli *nazwa_zmiennej* ma **wartość null**, ta funkcja wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, ta funkcja ustawia **errno** na **EINVAL** i zwraca **wartość null**.

**_wgetenv** to dwubajtowa wersja **getenv**; argument i wartość zwracana przez **_wgetenv** są ciągami znaków dwubajtowych. **_Wenviron** Global Variable to dwubajtowa wersja **_environ**.

W programie MBCS (na przykład w programie SBCS ASCII) **_wenviron** jest początkowo **wartością null** , ponieważ środowisko składa się z ciągów znaków wielobajtowych. Następnie podczas pierwszego wywołania [_wputenv](putenv-wputenv.md)lub pierwszego wywołania **_wgetenv** , jeśli istnieje już środowisko (MBCS), jest tworzone odpowiednie środowisko ciągu znaków dwubajtowych, a następnie wskazywane przez **_wenviron**.

Podobnie w programie Unicode ( **_wmain**), **_Environ** jest początkowo **wartością null** , ponieważ środowisko składa się z ciągów znaków dwubajtowych. Następnie podczas pierwszego wywołania **_putenv**lub pierwszego wywołania **getenv** , jeśli istnieje już środowisko (Unicode), odpowiednie środowisko MBCS jest tworzone i jest wskazywane przez **_environ**.

Gdy dwie kopie środowiska (MBCS i Unicode) istnieją jednocześnie w programie, system czasu wykonywania musi zachować obie kopie, co powoduje wolniejszy czas wykonywania. Na przykład za każdym razem, gdy wywołasz **_putenv**, wywołanie **_wputenv** jest również wykonywane automatycznie, dzięki czemu dwa ciągi środowiska odpowiadają.

> [!CAUTION]
> W rzadkich przypadkach, gdy system czasu wykonywania zachowuje zarówno wersję standardu Unicode, jak i wielobajtowe wersje środowiska, te systemy mogą nie odpowiadać dokładnie. Wynika to z faktu, że wszystkie unikatowe ciągi znaków wielobajtowych są mapowane na unikatowy ciąg Unicode, mapowanie z unikatowego ciągu Unicode na ciąg znaków wielobajtowych nie musi być unikatowe. Aby uzyskać więcej informacji, zobacz [_environ, _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> Rodziny **_putenv** i **_getenv** funkcji nie są bezpieczne wątkowo. **_getenv** może zwrócić wskaźnik ciągu, podczas gdy **_putenv** modyfikuje ciąg, powodując błędy losowe. Upewnij się, że wywołania tych funkcji są zsynchronizowane.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _UNICODE & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tgetenv**|**getenv**|**getenv**|**_wgetenv**|

Aby sprawdzić lub zmienić wartość **zmiennej środowiskowej** $, w razie potrzeby użyj **getenv**, **_putenv** i **_tzset** . Aby uzyskać więcej informacji o **programie, zobacz** [_tzset](tzset.md) and [_daylight, timezone i _tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**getenv**|\<stdlib.h>|
|**_wgetenv**|\<STDLIB. h > lub \<WCHAR. h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_getenv.c
// compile with: /W3
// This program uses getenv to retrieve
// the LIB environment variable and then uses
// _putenv to change it to a new value.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char *libvar;

   // Get the value of the LIB environment variable.
   libvar = getenv( "LIB" ); // C4996
   // Note: getenv is deprecated; consider using getenv_s instead

   if( libvar != NULL )
      printf( "Original LIB variable is: %s\n", libvar );

   // Attempt to change path. Note that this only affects the environment
   // variable of the current process. The command processor's
   // environment is not changed.
   _putenv( "LIB=c:\\mylib;c:\\yourlib" ); // C4996
   // Note: _putenv is deprecated; consider using putenv_s instead

   // Get new value.
   libvar = getenv( "LIB" ); // C4996

   if( libvar != NULL )
      printf( "New LIB variable is: %s\n", libvar );
}
```

```Output
Original LIB variable is: C:\progra~1\devstu~1\vc\lib
New LIB variable is: c:\mylib;c:\yourlib
```

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[_putenv, _wputenv](putenv-wputenv.md)<br/>
[Stałe środowiska](../../c-runtime-library/environmental-constants.md)<br/>
