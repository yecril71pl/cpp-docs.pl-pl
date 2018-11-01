---
title: _searchenv_s, _wsearchenv_s
ms.date: 11/04/2016
apiname:
- _wsearchenv_s
- _searchenv_s
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
- _searchenv_s
- _wsearchenv_s
- wsearchenv_s
- searchenv_s
helpviewer_keywords:
- tsearchenv_s function
- files [C++], finding
- buffers [C++], buffer overruns
- environment paths, searching for files
- wsearchenv_s function
- searchenv_s function
- _tsearchenv_s function
- buffer overruns
- buffers [C++], avoiding overruns
- _wsearchenv_s function
- _searchenv_s function
- environment paths
ms.assetid: 47f9fc29-250e-4c09-b52e-9e9f0ef395ca
ms.openlocfilehash: 40c2d0c42a3d61f84db78015388eba19742af06e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505680"
---
# <a name="searchenvs-wsearchenvs"></a>_searchenv_s, _wsearchenv_s

Wyszukiwanie plików przy użyciu ścieżki środowiska. Te wersje [_searchenv, _wsearchenv](searchenv-wsearchenv.md) mają wzmocnienia zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
errno_t _searchenv_s(
   const char *filename,
   const char *varname,
   char *pathname,
   size_t numberOfElements
);
errno_t _wsearchenv_s(
   const wchar_t *filename,
   const wchar_t *varname,
   wchar_t *pathname,
   size_t numberOfElements
);
template <size_t size>
errno_t _searchenv_s(
   const char *filename,
   const char *varname,
   char (&pathname)[size]
); // C++ only
template <size_t size>
errno_t _wsearchenv_s(
   const wchar_t *filename,
   const wchar_t *varname,
   wchar_t (&pathname)[size]
); // C++ only
```

### <a name="parameters"></a>Parametry

*Nazwa pliku*<br/>
Nazwa pliku do wyszukania.

*Nazwa zmiennej*<br/>
Środowisko do wyszukiwania.

*Nazwa ścieżki*<br/>
Bufor do przechowywania pełnej ścieżki.

*numberOfElements*<br/>
Rozmiar *pathname* buforu.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie; Kod błędu.

Jeśli *filename* jest pustym ciągiem, wartość zwracana jest **ENOENT**.

### <a name="error-conditions"></a>Warunki błędów

|*Nazwa pliku*|*Nazwa zmiennej*|*Nazwa ścieżki*|*numberOfElements*|Wartość zwracana|Zawartość *nazwy ścieżki*|
|----------------|---------------|----------------|------------------------|------------------|----------------------------|
|Wszystkie|Wszystkie|**NULL**|Wszystkie|**EINVAL**|n/d|
|**NULL**|Wszystkie|Wszystkie|Wszystkie|**EINVAL**|nie zmienione|
|Wszystkie|Wszystkie|Wszystkie|<= 0|**EINVAL**|nie zmienione|

Jeśli występuje którykolwiek z tych warunków błędu, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** do **EINVAL** i zwracają **EINVAL**.

## <a name="remarks"></a>Uwagi

**_Searchenv_s —** procedura wyszukiwania pliku docelowego w określonej domenie. *Nazwa_zmiennej* zmiennej może być dowolnym środowiskiem lub zmienną zdefiniowanych przez użytkownika, który określa listę ścieżek katalogów, takich jak **ścieżki**, **LIB**, i **DOŁĄCZANIA** . Ponieważ **_searchenv_s —** jest uwzględniana wielkość liter, *nazwa_zmiennej* powinien odpowiadać wielkości zmiennej środowiskowej. Jeśli *nazwa_zmiennej* nie pasuje nazwa zmiennej środowiskowej zdefiniowanej w środowisku procesu, funkcja zwraca zero i *pathname* zmiennej pozostaje niezmieniony.

Rutyna szuka najpierw pliku w bieżącym katalogu roboczym. Jeśli nie znajdzie pliku, szuka dalej przez katalogi określone przez zmienną środowiskową. Jeśli plik docelowy znajduje się w jednym z tych katalogów, nowo utworzona ścieżka jest kopiowana do *pathname*. Jeśli *filename* nie znaleziono pliku *pathname* zawiera pusty ciąg zakończony znakiem null.

*Pathname* buforu powinien wynosić co najmniej **_MAX_PATH** znaków, aby było pomieścić taką pełną nazwę ścieżki konstruowanej. W przeciwnym razie **_searchenv_s —** może przepełnienie *pathname* buforu spowodować nieoczekiwane zachowanie.

**_wsearchenv_s —** to wersja znaku dwubajtowego **_searchenv_s —**; argumenty **_wsearchenv_s —** są ciągami znaków dwubajtowych. **_wsearchenv_s —** i **_searchenv_s —** zachowują się identycznie.

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążania szablonu; przeciążenia mogą automatycznie wywnioskować długość buforu (eliminując potrzebę określenia argumentu rozmiaru) oraz ich mogą automatycznie zastąpić starsze, niezabezpieczone funkcje ich nowsze, bezpieczne odpowiedniki. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsearchenv_s —**|**_searchenv_s**|**_searchenv_s**|**_wsearchenv_s**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_searchenv_s**|\<stdlib.h>|
|**_wsearchenv_s**|\<stdlib.h > lub \<wchar.h >|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_searchenv_s.c
/* This program searches for a file in
* a directory specified by an environment variable.
*/

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char pathbuffer[_MAX_PATH];
   char searchfile[] = "CL.EXE";
   char envvar[] = "PATH";
   errno_t err;

   /* Search for file in PATH environment variable: */
   err = _searchenv_s( searchfile, envvar, pathbuffer, _MAX_PATH );
   if (err != 0)
   {
      printf("Error searching the path. Error code: %d\n", err);
   }
   if( *pathbuffer != '\0' )
      printf( "Path for %s:\n%s\n", searchfile, pathbuffer );
   else
      printf( "%s not found\n", searchfile );
}
```

```Output
Path for CL.EXE:
C:\Program Files\Microsoft Visual Studio 2010\VC\BIN\CL.EXE
```

## <a name="see-also"></a>Zobacz także

[Kontrola katalogu](../../c-runtime-library/directory-control.md)<br/>
[_searchenv, _wsearchenv](searchenv-wsearchenv.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_putenv, _wputenv](putenv-wputenv.md)<br/>
