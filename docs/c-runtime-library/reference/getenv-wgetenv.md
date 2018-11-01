---
title: getenv, _wgetenv
ms.date: 11/04/2016
apiname:
- getenv
- _wgetenv
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
ms.openlocfilehash: 79c685fef8d6a4b966c53bb7d94b423d16971976
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50568178"
---
# <a name="getenv-wgetenv"></a>getenv, _wgetenv

Pobiera wartość z bieżącego środowiska. Bardziej bezpieczne wersje tych funkcji są dostępne; zobacz [getenv_s —, _wgetenv_s —](getenv-s-wgetenv-s.md).

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Nazwa zmiennej*<br/>
Nazwa zmiennej środowiskowej.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do środowiska tabeli wpisu zawierający *nazwa_zmiennej*. Nie jest bezpieczne zmodyfikować wartość zmiennej środowiskowej, za pomocą zwrócony wskaźnik. Użyj [_putenv](putenv-wputenv.md) funkcji, aby zmodyfikować wartość zmiennej środowiskowej. Wartość zwracana jest **NULL** Jeśli *nazwa_zmiennej* nie znajduje się w tabeli środowiska.

## <a name="remarks"></a>Uwagi

**Getenv** Funkcja przeszukuje listę zmiennych środowiskowych dla *nazwa_zmiennej*. **getenv** nie uwzględnia wielkości liter w systemie operacyjnym Windows. **getenv** i **_putenv** użyj kopii środowiska wskazywanego przez zmienną globalną **_environ** można uzyskiwać dostęp do środowiska. **getenv** działa tylko na dostęp do biblioteki wykonawczej struktury danych i nie w środowisku "segmentu" dla procesu utworzonych przez system operacyjny. W związku z tym, programy używające *envp* argument [głównego](../../cpp/main-program-startup.md) lub [wmain](../../cpp/main-program-startup.md) może pobrać nieprawidłowe informacje.

Jeśli *nazwa_zmiennej* jest **NULL**, funkcja wywoła procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja ta ustawia **errno** do **EINVAL** i zwraca **NULL**.

**_wgetenv —** to wersja znaku dwubajtowego **getenv**; argument i wartość zwracana przez **_wgetenv —** są ciągami znaków dwubajtowych. **_Wenviron** zmienna globalna jest wersją znaków dwubajtowych **_environ**.

W programie MBCS (na przykład w programie SBCS ASCII) **_wenviron** jest początkowo **NULL** ponieważ środowisko składa się z ciągami znaków wielobajtowych. Następnie w pierwszym wywołaniu [_wputenv —](putenv-wputenv.md), lub na pierwszym wywołaniu **_wgetenv —** Jeśli istnieje już środowisko (znaków MBCS), odpowiednie środowisko ciąg znaków dwubajtowych jest tworzony i następnie jest wskazywany przez **_wenviron**.

Podobnie w formacie Unicode (**_wmain**) program, **_environ** jest początkowo **NULL** ponieważ środowisko składa się z ciągami znaków dwubajtowych. Następnie w pierwszym wywołaniu **_putenv**, lub na pierwszym wywołaniu **getenv** Jeśli środowiska (Unicode) już istnieje, odpowiednie środowisko MBCS jest tworzony i następnie jest wskazywany przez **_ Environ —**.

Jeśli dwie kopie środowiska (MBCS i Unicode), jednocześnie istnieją w programie, system środowiska wykonawczego, musisz utrzymywać obu kopiach skutkuje wolniejszego czasu wykonania. Na przykład gdy wywołujesz **_putenv**, wywołanie **_wputenv —** również jest wykonywane automatycznie, tak, aby odpowiadać zmiennych środowiskowych dwa.

> [!CAUTION]
> W rzadkich przypadkach po system środowiska wykonawczego jest obsługa wersji standardu Unicode i wielobajtowych wersję środowiska, te wersje dwa środowiska mogą nie odpowiadać dokładnie. To dlatego, chociaż dowolny unikatowy ciąg znaków wielobajtowych jest mapowany na ciąg Unicode unikatowy, mapowanie unikatowy ciąg Unicode na ciąg znaków wielobajtowych nie jest muszą być unikatowe. Aby uzyskać więcej informacji, zobacz [_environ, _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> **_Putenv** i **_getenv** rodziny funkcji nie są wątkowo. **_getenv** może zwracać wskaźnik ciągu podczas **_putenv** modyfikuje ciąg, powodując błędy losowe. Upewnij się, że wywołania tych funkcji są synchronizowane.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tgetenv —**|**getenv**|**getenv**|**_wgetenv**|

Aby sprawdzić lub zmienić wartość **TZ** użycie zmiennej, środowisko **getenv**, **_putenv** i **_tzset —** zgodnie z potrzebami. Aby uzyskać więcej informacji na temat **TZ**, zobacz [_tzset —](tzset.md) i [_daylight, strefa czasowa i _tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**getenv**|\<stdlib.h>|
|**_wgetenv**|\<stdlib.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
