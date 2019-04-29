---
title: _searchenv, _wsearchenv
ms.date: 11/04/2016
apiname:
- _searchenv
- _wsearchenv
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
- _wsearchenv
- _tsearchenv
- wsearchenv
- _searchenv
- searchenv
helpviewer_keywords:
- _wsearchenv function
- files [C++], finding
- _searchenv function
- tsearchenv function
- environment paths, searching for files
- _tsearchenv function
- wsearchenv function
- searchenv function
- environment paths
ms.assetid: 9c944a27-d326-409b-aee6-410e8762d9d3
ms.openlocfilehash: c1d2361fceec448c98fd9e5a368653aac38c83e2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356774"
---
# <a name="searchenv-wsearchenv"></a>_searchenv, _wsearchenv

Używa ścieżki środowiska, aby wyszukać plik. Bardziej bezpieczne wersje tych funkcji są dostępne; zobacz [_searchenv_s —, _wsearchenv_s —](searchenv-s-wsearchenv-s.md).

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
void _searchenv(
   const char *filename,
   const char *varname,
   char *pathname
);
void _wsearchenv(
   const wchar_t *filename,
   const wchar_t *varname,
   wchar_t *pathname
);
template <size_t size>
void _searchenv(
   const char *filename,
   const char *varname,
   char (&pathname)[size]
); // C++ only
template <size_t size>
void _wsearchenv(
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

## <a name="remarks"></a>Uwagi

**_Searchenv** procedura wyszukiwania pliku docelowego w określonej domenie. *Nazwa_zmiennej* zmiennej może być dowolnym środowiskiem lub zmienną zdefiniowaną przez użytkownika — na przykład **ścieżki**, **LIB**, lub **INCLUDE**— Określa, że Lista ścieżek katalogów. Ponieważ **_searchenv** jest uwzględniana wielkość liter, *nazwa_zmiennej* powinien odpowiadać wielkości zmiennej środowiskowej.

Rutyna szuka najpierw pliku w bieżącym katalogu roboczym. Jeśli nie znajdzie pliku, szuka przez katalogi, które są określone przez zmienną środowiskową. Jeśli plik docelowy znajduje się w jednym z tych katalogów, nowo utworzona ścieżka jest kopiowana do *pathname*. Jeśli *filename* nie znaleziono pliku *pathname* zawiera pusty ciąg zakończony znakiem null.

*Pathname* buforu powinien wynosić co najmniej **_MAX_PATH** znaków, aby było pomieścić taką pełną nazwę ścieżki konstruowanej. W przeciwnym razie **_searchenv** może przepełnienie *pathname* buffer i spowodować nieoczekiwane zachowanie.

**_wsearchenv** to wersja znaku dwubajtowego **_searchenv**i argumenty do **_wsearchenv** są ciągami znaków dwubajtowych. **_wsearchenv** i **_searchenv** zachowują się identycznie.

Jeśli *filename* jest pustym ciągiem, funkcje te zwracają **ENOENT**.

Jeśli *filename* lub *pathname* jest **NULL** wskaźnika, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają wartość -1 i ustaw **errno** do **EINVAL**.

Aby uzyskać więcej informacji na temat **errno** i kodach błędów, zobacz [errno — stałe](../../c-runtime-library/errno-constants.md).

W języku C++ funkcje te mają przeciążenia szablonu, które wywołują nowsze, bezpieczniejsze odpowiedniki tych funkcji. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsearchenv —**|**_searchenv**|**_searchenv**|**_wsearchenv**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_searchenv**|\<stdlib.h>|
|**_wsearchenv**|\<stdlib.h> or \<wchar.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_searchenv.c
// compile with: /W3
// This program searches for a file in
// a directory that's specified by an environment variable.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char pathbuffer[_MAX_PATH];
   char searchfile[] = "CL.EXE";
   char envvar[] = "PATH";

   // Search for file in PATH environment variable:
   _searchenv( searchfile, envvar, pathbuffer ); // C4996
   // Note: _searchenv is deprecated; consider using _searchenv_s
   if( *pathbuffer != '\0' )
      printf( "Path for %s:\n%s\n", searchfile, pathbuffer );
   else
      printf( "%s not found\n", searchfile );
}
```

```Output
Path for CL.EXE:
C:\Program Files\Microsoft Visual Studio 8\VC\BIN\CL.EXE
```

## <a name="see-also"></a>Zobacz także

[Kontrola katalogu](../../c-runtime-library/directory-control.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_putenv, _wputenv](putenv-wputenv.md)<br/>
[_searchenv_s, _wsearchenv_s](searchenv-s-wsearchenv-s.md)<br/>
