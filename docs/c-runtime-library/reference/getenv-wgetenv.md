---
title: getenv, _wgetenv
description: Zawiera opis biblioteki getenv środowiska _wgetenv wykonawczego i funkcji środowiska wykonawczego firmy Microsoft C.
ms.date: 4/2/2020
api_name:
- getenv
- _wgetenv
- _o__wgetenv
- _o_getenv
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
no-loc:
- getenv
- _wgetenv
- getenv_s
- _wgetenv_s
- _putenv_s
- main
- wmain
- errno
- EINVAL
- ERANGE
- _environ
- _wenviron
- _putenv
- _wputenv
- _tgetenv_s
- _tzset
- _dupenv_s
- _wdupenv_s
ms.openlocfilehash: c9d7f7e1a2c5d6b15aee2f7f972a30cc0c90115c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344253"
---
# <a name="getenv-_wgetenv"></a>getenv, _wgetenv

Pobiera wartość z bieżącego środowiska. Dostępne są bezpieczniejsze wersje tych funkcji; patrz [getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md).

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Varname*<br/>
Nazwa zmiennej środowiskowej.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do wpisu tabeli środowiska zawierającego *varname*. Nie jest bezpieczne, aby zmodyfikować wartość zmiennej środowiskowej przy użyciu zwracanego wskaźnika. Funkcja [_putenv](putenv-wputenv.md) służy do modyfikowania wartości zmiennej środowiskowej. Zwracana wartość jest **NULL,** jeśli nie znaleziono *warname* w tabeli środowiska.

## <a name="remarks"></a>Uwagi

Funkcja **getenv** przeszukuje listę zmiennych środowiskowych dla *varname*. **getenv** nie jest rozróżniana wielkość liter w systemie operacyjnym Windows. **getenv** i **_putenv** korzystają z kopii środowiska wskazanej przez zmienną globalną **_environ** dostępu do środowiska. **getenv** działa tylko na strukturach danych dostępnych dla biblioteki czasu wykonywania, a nie na "segmencie" środowiska utworzonym dla procesu przez system operacyjny. W związku z tym programy, które używają *envp* argument do [main](../../cpp/main-function-command-line-args.md) lub [wmain](../../cpp/main-function-command-line-args.md) może pobrać nieprawidłowe informacje.

Jeśli *nazwa warname* ma **wartość NULL**, ta funkcja wywołuje nieprawidłowy program obsługi parametrów, zgodnie z opisem w [zatwierdzeniu parametru.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, ta funkcja ustawia **errno** na **Wartość EINVAL** i zwraca **wartość NULL**.

**_wgetenv** jest szerokoznakowa wersja **getenv**; argument i zwraca wartość **_wgetenv** są ciągami znaków o szerokich znakach. **Zmienna globalna _wenviron** jest szerokoznakową wersją **_environ**.

W programie MBCS (na przykład w programie SBCS ASCII) **_wenviron** jest początkowo **null,** ponieważ środowisko składa się z ciągów znaków wielobajtowych. Następnie przy pierwszym wywołaniu [_wputenv](putenv-wputenv.md)lub przy pierwszym wywołaniu **_wgetenv** jeśli środowisko (MBCS) już istnieje, tworzone jest odpowiednie środowisko ciągów szerokoznakowych, a następnie wskazywowy przez **_wenviron**.

Podobnie w programie Unicode (**_wmain**) **_environ** jest początkowo **NULL,** ponieważ środowisko składa się z ciągów znaków o szerokich znakach. Następnie przy pierwszym wywołaniu **_putenv**lub przy pierwszym wywołaniu **getenv,** jeśli środowisko (Unicode) już istnieje, tworzone jest odpowiednie środowisko MBCS, a następnie wskazywalne przez **_environ**.

Gdy dwie kopie środowiska (MBCS i Unicode) istnieją jednocześnie w programie, system czasu wykonywania musi obsługiwać obie kopie, co powoduje wolniejszy czas wykonywania. Na przykład za każdym razem, gdy wywołasz **_putenv**, wywołanie **_wputenv** jest również wykonywane automatycznie, tak aby dwa parametry środowiska odpowiadały.

> [!CAUTION]
> W rzadkich przypadkach, gdy system czasu wykonywania jest utrzymanie zarówno wersji Unicode i wielobajtowej wersji środowiska, te dwie wersje środowiska może nie odpowiadać dokładnie. Dzieje się tak, ponieważ chociaż dowolny unikatowy ciąg znaków wielobajtowych jest mapowany na unikatowy ciąg Unicode, mapowanie z unikatowego ciągu Unicode do ciągu znaków wielobajtowych niekoniecznie jest unikatowe. Aby uzyskać więcej informacji, zobacz [_environ _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> **_putenv** i **_getenv** rodzin funkcji nie są bezpieczne dla wątków. **_getenv** może zwrócić wskaźnik ciągu, podczas gdy **_putenv** modyfikuje ciąg, powodując losowe błędy. Upewnij się, że wywołania tych funkcji są synchronizowane.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tgetenv**|**getenv ( getenv )**|**getenv ( getenv )**|**_wgetenv**|

Aby sprawdzić lub zmienić wartość zmiennej środowiskowej **TZ,** w razie potrzeby użyj **getenv**, **_putenv** i **_tzset.** Aby uzyskać więcej informacji o **TZ**, zobacz [_tzset](tzset.md) i [_daylight, strefa czasowa i _tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**getenv**|\<>|
|**_wgetenv**|\<> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[_putenv, _wputenv](putenv-wputenv.md)<br/>
[Stałe środowiskowe](../../c-runtime-library/environmental-constants.md)<br/>
