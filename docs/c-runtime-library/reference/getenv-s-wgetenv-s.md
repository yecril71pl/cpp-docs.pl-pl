---
title: getenv_s, _wgetenv_s
description: Zawiera opis biblioteki getenv_s środowiska _wgetenv_s wykonawczego i funkcji środowiska wykonawczego firmy Microsoft C.
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 17c4e001f7f4637f6f66f218c94378368976901f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344281"
---
# <a name="getenv_s-_wgetenv_s"></a>getenv_s, _wgetenv_s

Pobiera wartość z bieżącego środowiska. Te wersje [getenv, _wgetenv](getenv-wgetenv.md) mają ulepszenia zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*pZawąkaWartość*<br/>
Rozmiar buforu, który jest wymagany lub 0, jeśli zmienna nie zostanie znaleziona.

*Buforu*<br/>
Bufor do przechowywania wartości zmiennej środowiskowej.

*liczbaOfElements*<br/>
Rozmiar *bufora*.

*Varname*<br/>
Nazwa zmiennej środowiskowej.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli się powiedzie; w przeciwnym razie kod błędu w przypadku awarii.

### <a name="error-conditions"></a>Warunki błędu

|*pZawąkaWartość*|*Buforu*|*liczbaOfElements*|*Varname*|Wartość zwracana|
|--------------------|--------------|------------------------|---------------|------------------|
|**Null**|Wszelki|Wszelki|Wszelki|**Einval**|
|Wszelki|**Null**|>0|Wszelki|**Einval**|
|Wszelki|Wszelki|Wszelki|**Null**|**Einval**|

Każdy z tych warunków błędu wywołuje nieprawidłowy program obsługi parametrów, zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, funkcje ustawić **errno** do **EINVAL** i **zwracać EINVAL**.

Ponadto, jeśli bufor jest zbyt mały, te funkcje zwracają **ERANGE**. Nie wywołują one nieprawidłowego programu obsługi parametrów. Zapisują wymagany rozmiar buforu w *pReturnValue*, a tym samym umożliwiają programom ponowne wywołanie funkcji z większym buforem.

## <a name="remarks"></a>Uwagi

Funkcja **getenv_s** przeszukuje listę zmiennych środowiskowych dla *warname*. **getenv_s** nie jest rozróżniana wielkość liter w systemie operacyjnym Windows. **getenv_s** i [_putenv_s](putenv-s-wputenv-s.md) używać kopii środowiska, na które wskazuje zmienna globalna **_environ** dostępu do środowiska. **getenv_s** działa tylko na strukturach danych, które są dostępne dla biblioteki w czasie wykonywania, a nie w środowisku "segment", który jest tworzony dla procesu przez system operacyjny. W związku z tym programy, które używają *envp* argument do [main](../../cpp/main-function-command-line-args.md) lub [wmain](../../cpp/main-function-command-line-args.md) może pobrać nieprawidłowe informacje.

**_wgetenv_s** jest szerokoznakową wersją **getenv_s**; argument i zwraca wartość **_wgetenv_s** są ciągami znaków o szerokich znakach. **Zmienna globalna _wenviron** jest szerokoznakową wersją **_environ**.

W programie MBCS (na przykład w programie SBCS ASCII) **_wenviron** jest początkowo **null,** ponieważ środowisko składa się z ciągów znaków wielobajtowych. Następnie przy pierwszym wywołaniu [_wputenv](putenv-wputenv.md)lub przy pierwszym wywołaniu **_wgetenv_s**, jeśli środowisko (MBCS) już istnieje, tworzone jest odpowiednie środowisko ciągów szerokoznakowych, a następnie wskazywowy przez **_wenviron**.

Podobnie w programie Unicode (**_wmain**) **_environ** jest początkowo **NULL,** ponieważ środowisko składa się z ciągów znaków o szerokich znakach. Następnie przy pierwszym wywołaniu [_putenv](putenv-wputenv.md)lub przy pierwszym wywołaniu **getenv_s** jeśli środowisko (Unicode) już istnieje, tworzone jest odpowiednie środowisko MBCS, a następnie wskazywowane przez **_environ**.

Gdy dwie kopie środowiska (MBCS i Unicode) istnieją jednocześnie w programie, system czasu wykonywania musi obsługiwać obie kopie, co powoduje wolniejszy czas wykonywania. Na przykład podczas wywoływania **_putenv**, wywołanie **_wputenv** jest również wykonywane automatycznie, tak aby dwa parametry środowiska odpowiadają.

> [!CAUTION]
> W rzadkich przypadkach, gdy system czasu wykonywania jest utrzymanie zarówno wersji Unicode i wielobajtowej wersji środowiska, dwie wersje środowiska może nie odpowiadać dokładnie. Dzieje się tak, ponieważ chociaż dowolny unikatowy ciąg znaków wielobajtowych jest mapowany na unikatowy ciąg Unicode, mapowanie z unikatowego ciągu Unicode do ciągu znaków wielobajtowych niekoniecznie jest unikatowe. Aby uzyskać więcej informacji, zobacz [_environ _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> **_putenv_s** i **_getenv_s** rodzin funkcji nie są bezpieczne dla wątków. **_getenv_s** może zwrócić wskaźnik ciągu, podczas gdy **_putenv_s** modyfikuje ciąg i tym samym powodować losowe błędy. Upewnij się, że wywołania tych funkcji są synchronizowane.

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążenia szablonu; przeciążenia można wywnioskować długość buforu automatycznie, a tym samym wyeliminować konieczność określenia argumentu rozmiaru. Aby uzyskać więcej informacji, zobacz [Bezpieczne przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tgetenv_s**|**getenv_s**|**getenv_s**|**_wgetenv_s**|

Aby sprawdzić lub zmienić wartość zmiennej środowiskowej **TZ,** należy w razie potrzeby użyć **getenv_s**, **_putenv**i **_tzset.** Aby uzyskać więcej informacji o **TZ**, zobacz [_tzset](tzset.md) i [_daylight, _dstbias, _timezone i _tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**getenv_s**|\<>|
|**_wgetenv_s**|\<> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

[Kontrola procesu i środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[Stałe środowiska](../../c-runtime-library/environmental-constants.md)<br/>
[_putenv, _wputenv](putenv-wputenv.md)<br/>
[_dupenv_s, _wdupenv_s](dupenv-s-wdupenv-s.md)<br/>
