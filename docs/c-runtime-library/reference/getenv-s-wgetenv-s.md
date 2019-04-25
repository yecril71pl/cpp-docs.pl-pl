---
title: getenv_s, _wgetenv_s
ms.date: 11/04/2016
apiname:
- getenv_s
- _wgetenv_s
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
ms.openlocfilehash: eac3c036e2f4f271c7bc2d77c8ae82bec28d3617
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331743"
---
# <a name="getenvs-wgetenvs"></a>getenv_s, _wgetenv_s

Pobiera wartość z bieżącego środowiska. Te wersje [getenv, _wgetenv —](getenv-wgetenv.md) mają wzmocnienia zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Rozmiar buforu, który jest wymagany, lub 0, jeśli zmienna nie zostanie znaleziona.

*buffer*<br/>
Bufor do przechowywania wartości zmiennej środowiskowej.

*numberOfElements*<br/>
Rozmiar *buforu*.

*Nazwa zmiennej*<br/>
Nazwa zmiennej środowiskowej.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie; w przeciwnym razie, kod błędu: w przypadku niepowodzenia.

### <a name="error-conditions"></a>Warunki błędów

|*pReturnValue*|*buffer*|*numberOfElements*|*Nazwa zmiennej*|Wartość zwracana|
|--------------------|--------------|------------------------|---------------|------------------|
|**NULL**|Wszystkie|Wszystkie|Wszystkie|**EINVAL**|
|Wszystkie|**NULL**|>0|Wszystkie|**EINVAL**|
|Wszystkie|Wszystkie|Wszystkie|**NULL**|**EINVAL**|

Którykolwiek z tych warunków błędu wywołuje program obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcje ustawiają **errno** do **EINVAL** i zwracają **EINVAL**.

Ponadto, jeśli bufor jest zbyt mały, te funkcje zwracają **ERANGE**. Nie wywołują procedurę obsługi nieprawidłowego parametru. Wymagany rozmiar buforu w nich zapisać *pReturnValue*, a tym samym Włącz programy do wywołania funkcji ponownie, używając bufor większe.

## <a name="remarks"></a>Uwagi

**Getenv_s —** Funkcja przeszukuje listę zmiennych środowiskowych dla *nazwa_zmiennej*. **getenv_s —** nie uwzględnia wielkości liter w systemie operacyjnym Windows. **getenv_s —** i [_putenv_s](putenv-s-wputenv-s.md) użyj kopii środowiska, która jest wskazywana przez zmienną globalną **_environ** można uzyskiwać dostęp do środowiska. **getenv_s —** działa tylko na struktur danych, które są dostępne dla biblioteki wykonawczej a nie na środowisko "segmentu", który jest tworzony dla procesu przez system operacyjny. W związku z tym, programy używające *envp* argument [głównego](../../cpp/main-program-startup.md) lub [wmain](../../cpp/main-program-startup.md) może pobrać nieprawidłowe informacje.

**_wgetenv_s —** to wersja znaku dwubajtowego **getenv_s —**; argument i wartość zwracana przez **_wgetenv_s —** są ciągami znaków dwubajtowych. **_Wenviron** zmienna globalna jest wersją znaków dwubajtowych **_environ**.

W programie MBCS (na przykład w programie SBCS ASCII) **_wenviron** jest początkowo **NULL** ponieważ środowisko składa się z ciągami znaków wielobajtowych. Następnie w pierwszym wywołaniu [_wputenv —](putenv-wputenv.md), lub na pierwszym wywołaniu **_wgetenv_s —**, jeśli istnieje już środowisko (znaków MBCS), odpowiednie środowisko ciąg znaków dwubajtowych jest tworzony i następnie jest wskazywany przez **_wenviron**.

Podobnie w formacie Unicode (**_wmain**) program, **_environ** jest początkowo **NULL** ponieważ środowisko składa się z ciągami znaków dwubajtowych. Następnie w pierwszym wywołaniu [_putenv](putenv-wputenv.md), lub na pierwszym wywołaniu **getenv_s —** Jeśli środowiska (Unicode) już istnieje, odpowiednie środowisko MBCS jest tworzony i następnie jest wskazywany przez **_ Environ —**.

Gdy dwie kopie środowiska (MBCS i Unicode) jednocześnie istnieje w programie, systemu w czasie wykonywania, musisz utrzymywać obu kopiach i powoduje wolniejszego czasu wykonania. Na przykład gdy wywołujesz **_putenv**, wywołanie **_wputenv —** również jest wykonywane automatycznie, tak, aby odpowiadać zmiennych środowiskowych dwa.

> [!CAUTION]
> W rzadkich przypadkach po system środowiska wykonawczego jest obsługa wersji standardu Unicode i wielobajtowych wersję środowiska, wersje dwa środowiska mogą nie odpowiadać dokładnie. Dzieje się tak, ponieważ, mimo że dowolny unikatowy ciąg znaków wielobajtowych jest mapowany na ciąg Unicode unikatowy, mapowanie unikatowy ciąg Unicode na ciąg znaków wielobajtowych nie muszą być unikatowe. Aby uzyskać więcej informacji, zobacz [_environ, _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> **_Putenv_s** i **_getenv_s** rodziny funkcji nie są wątkowo. **_getenv_s** może zwracać wskaźnik ciągu podczas **_putenv_s** modyfikuje ciąg, a także spowodować błędy losowe. Upewnij się, że wywołania tych funkcji są synchronizowane.

W języku C++ korzystania z tych funkcji jest uproszczone przez przeciążania szablonu; przeciążenia mogą automatycznie wywnioskować długość buforu i tym samym wyeliminować konieczność określenia argumentu rozmiaru. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tgetenv_s**|**getenv_s**|**getenv_s**|**_wgetenv_s**|

Aby sprawdzić lub zmienić wartość **TZ** użycie zmiennej, środowisko **getenv_s —**, **_putenv**, i **_tzset —**, co jest wymagane. Aby uzyskać więcej informacji na temat **TZ**, zobacz [_tzset —](tzset.md) i [_daylight, _dstbias, _timezone i _tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**getenv_s**|\<stdlib.h>|
|**_wgetenv_s**|\<stdlib.h> or \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[Stałe środowiska](../../c-runtime-library/environmental-constants.md)<br/>
[_putenv, _wputenv](putenv-wputenv.md)<br/>
[_dupenv_s, _wdupenv_s](dupenv-s-wdupenv-s.md)<br/>
