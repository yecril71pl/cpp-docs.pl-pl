---
title: getenv_s, _wgetenv_s
description: Zawiera opis biblioteki getenv_s i _wgetenv_s funkcji środowiska uruchomieniowego Microsoft C.
ms.date: 4/2/2020
api_name:
- getenv_s
- _wgetenv_s
- _o__wgetenv_s
- _o_getenv_s
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- getenv_s
- _tgetenv_s
- _wgetenv_s
helpviewer_keywords:
- _tgetenv_s function
- wgetenv_s function
- _wgetenv_s function
- getenv_s function
- environment variables
- tgetenv_s function
ms.assetid: c3ae1ffe-d4cd-4bae-bcb1-3afa754c613a
no-loc:
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
ms.openlocfilehash: 0713ed5735916c31edaab1a178a5e9b1b7cf5377
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913683"
---
# <a name="getenv_s-_wgetenv_s"></a>getenv_s, _wgetenv_s

Pobiera wartość z bieżącego środowiska. Te wersje programu [getenv _wgetenv](getenv-wgetenv.md) mają ulepszenia zabezpieczeń, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
errno_t getenv_s(
   size_t *pReturnValue,
   char* buffer,
   size_t numberOfElements,
   const char *varname
);
errno_t _wgetenv_s(
   size_t *pReturnValue,
   wchar_t *buffer,
   size_t numberOfElements,
   const wchar_t *varname
);
template <size_t size>
errno_t getenv_s(
   size_t *pReturnValue,
   char (&buffer)[size],
   const char *varname
); // C++ only
template <size_t size>
errno_t _wgetenv_s(
   size_t *pReturnValue,
   wchar_t (&buffer)[size],
   const wchar_t *varname
); // C++ only
```

### <a name="parameters"></a>Parametry

*pReturnValue*<br/>
Wymagany rozmiar buforu lub 0, jeśli zmienna nie zostanie znaleziona.

*buforu*<br/>
Bufor do przechowywania wartości zmiennej środowiskowej.

*numberOfElements*<br/>
Rozmiar *buforu*.

*nazwa_zmiennej*<br/>
Nazwa zmiennej środowiskowej.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli pomyślne; w przeciwnym razie kod błędu w przypadku niepowodzenia.

### <a name="error-conditions"></a>Warunki błędów

|*pReturnValue*|*buforu*|*numberOfElements*|*nazwa_zmiennej*|Wartość zwracana|
|--------------------|--------------|------------------------|---------------|------------------|
|**NULL**|ile|ile|ile|**EINVAL**|
|ile|**NULL**|>0|ile|**EINVAL**|
|ile|ile|ile|**NULL**|**EINVAL**|

Każdy z tych warunków błędu wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcje ustawiają **errno** na **EINVAL** i zwracają **EINVAL**.

Ponadto, jeśli bufor jest za mały, te funkcje zwracają **ERANGE**. Nie wywołują procedury obsługi nieprawidłowego parametru. Zapisują wymagany rozmiar buforu w *pReturnValue*, a tym samym umożliwiają programom ponowne wywoływanie funkcji z większym buforem.

## <a name="remarks"></a>Uwagi

Funkcja **getenv_s** przeszukuje listę zmiennych środowiskowych dla elementu *nazwa_zmiennej*. w systemie operacyjnym Windows w **getenv_s** nie jest rozróżniana wielkość liter. **getenv_s** i [_putenv_s](putenv-s-wputenv-s.md) użyć kopii środowiska, która jest wskazywana przez zmienną globalną **_environ** w celu uzyskania dostępu do środowiska. **getenv_s** działa tylko na strukturach danych, które są dostępne dla biblioteki wykonawczej, a nie w środowisku "segment", który jest tworzony dla procesu przez system operacyjny. W związku z tym programy korzystające z argumentu *envp* do [Main](../../cpp/main-function-command-line-args.md) lub [wmain](../../cpp/main-function-command-line-args.md) mogą pobrać nieprawidłowe informacje.

**_wgetenv_s** to dwubajtowa wersja **getenv_s**; argument i zwracana wartość **_wgetenv_s** są ciągami znaków dwubajtowych. **_Wenviron** zmienna globalna to dwubajtowa wersja **_environ**.

W programie MBCS (na przykład w programie SBCS ASCII) **_wenviron** jest początkowo **wartością null** , ponieważ środowisko składa się z ciągów znaków wielobajtowych. Następnie podczas pierwszego wywołania [_wputenv](putenv-wputenv.md)lub pierwszego wywołania **_wgetenv_s**, jeśli istnieje już środowisko (MBCS), zostanie utworzone odpowiednie środowisko ciągu znaków dwubajtowych, a następnie wskazywane przez **_wenviron**.

Podobnie w programie Unicode (**_wmain**) **_Environ** jest początkowo **wartością null** , ponieważ środowisko składa się z ciągów znaków dwubajtowych. Następnie podczas pierwszego wywołania [_putenv](putenv-wputenv.md)lub pierwszego wywołania **getenv_s** , jeśli istnieje już środowisko (Unicode), odpowiednie środowisko MBCS jest tworzone, a następnie wskazywane przez **_environ**.

Gdy dwie kopie środowiska (MBCS i Unicode) istnieją jednocześnie w programie, system czasu wykonywania musi obsługiwać obie kopie i powoduje wolniejszy czas wykonywania. Na przykład podczas wywoływania **_putenv**, wywołanie **_wputenv** jest również wykonywane automatycznie, tak aby oba ciągi środowiska odpowiadały.

> [!CAUTION]
> W rzadkich przypadkach, gdy system czasu wykonywania zachowuje zarówno wersję standardu Unicode, jak i wielobajtowe wersje środowiska, te systemy mogą nie odpowiadać dokładnie. Dzieje się tak, ponieważ chociaż każdy unikatowy ciąg znaków wielobajtowych jest mapowany na unikatowy ciąg Unicode, mapowanie z unikatowego ciągu Unicode na ciąg znaków wielobajtowych nie musi być unikatowe. Aby uzyskać więcej informacji, zobacz [_environ, _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> **_Putenv_s** i **_getenv_s** rodziny funkcji nie są bezpieczne wątkowo. **_getenv_s** może zwrócić wskaźnik ciągu, podczas gdy **_putenv_s** modyfikuje ciąg i w związku z tym powoduje losowe błędy. Upewnij się, że wywołania tych funkcji są zsynchronizowane.

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążenia szablonów; przeciążenia mogą automatycznie wywnioskować długość buforu, a tym samym wyeliminować konieczność określenia argumentu rozmiaru. Aby uzyskać więcej informacji, zobacz [bezpieczne przeciążenia szablonów](../../c-runtime-library/secure-template-overloads.md).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _MBCS _UNICODE &|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tgetenv_s**|**getenv_s**|**getenv_s**|**_wgetenv_s**|

Aby sprawdzić lub zmienić wartość **zmiennej środowiskowej** $, w razie potrzeby użyj **getenv_s**, **_putenv**i **_tzset**. Aby uzyskać więcej informacji o **programie, zobacz** [_tzset](tzset.md) i [_daylight, _dstbias, _timezone i _tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**getenv_s**|\<STDLIB. h>|
|**_wgetenv_s**|\<STDLIB. h> lub \<WCHAR. h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_getenv_s.c
// This program uses getenv_s to retrieve
// the LIB environment variable and then uses
// _putenv to change it to a new value.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char* libvar;
   size_t requiredSize;

   getenv_s( &requiredSize, NULL, 0, "LIB");
   if (requiredSize == 0)
   {
      printf("LIB doesn't exist!\n");
      exit(1);
   }

   libvar = (char*) malloc(requiredSize * sizeof(char));
   if (!libvar)
   {
      printf("Failed to allocate memory!\n");
      exit(1);
   }

   // Get the value of the LIB environment variable.
   getenv_s( &requiredSize, libvar, requiredSize, "LIB" );

   printf( "Original LIB variable is: %s\n", libvar );

   // Attempt to change path. Note that this only affects
   // the environment variable of the current process. The command
   // processor's environment is not changed.
   _putenv_s( "LIB", "c:\\mylib;c:\\yourlib" );

   getenv_s( &requiredSize, NULL, 0, "LIB");

   libvar = (char*) realloc(libvar, requiredSize * sizeof(char));
   if (!libvar)
   {
      printf("Failed to allocate memory!\n");
      exit(1);
   }

   // Get the new value of the LIB environment variable.
   getenv_s( &requiredSize, libvar, requiredSize, "LIB" );

   printf( "New LIB variable is: %s\n", libvar );

   free(libvar);
}
```

```Output
Original LIB variable is: c:\vctools\lib;c:\vctools\atlmfc\lib;c:\vctools\PlatformSDK\lib;c:\vctools\Visual Studio SDKs\DIA Sdk\lib;c:\vctools\Visual Studio SDKs\BSC Sdk\lib
New LIB variable is: c:\mylib;c:\yourlib
```

## <a name="see-also"></a>Zobacz też

[Proces i kontrola środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[Stałe środowiska](../../c-runtime-library/environmental-constants.md)<br/>
[_putenv, _wputenv](putenv-wputenv.md)<br/>
[_dupenv_s, _wdupenv_s](dupenv-s-wdupenv-s.md)<br/>
