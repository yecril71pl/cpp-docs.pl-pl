---
title: _searchenv, _wsearchenv
ms.date: 11/04/2016
api_name:
- _searchenv
- _wsearchenv
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
ms.openlocfilehash: a3139ab87335ba581ef65707602c5da1819ce4a1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948773"
---
# <a name="_searchenv-_wsearchenv"></a>_searchenv, _wsearchenv

Wyszukuje plik za pomocą ścieżek środowiskowych. Bardziej bezpieczne wersje tych funkcji są dostępne; Zobacz [_searchenv_s, _wsearchenv_s](searchenv-s-wsearchenv-s.md).

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*nazwa_zmiennej*<br/>
Środowisko do wyszukania.

*ścieżki*<br/>
Bufor do przechowywania pełnej ścieżki.

## <a name="remarks"></a>Uwagi

Procedura **_searchenv** wyszukuje plik docelowy w określonej domenie. Zmienna *nazwa_zmiennej* może być dowolnego środowiska lub zmiennej zdefiniowanej przez użytkownika, na przykład **Path**, **lib**lub **include**, która określa listę ścieżek katalogów. Ponieważ **_searchenv** jest uwzględniana wielkość liter, wartość *nazwa_zmiennej* powinna być zgodna z wielkością liter zmiennej środowiskowej.

Procedura najpierw przeszukuje plik w bieżącym katalogu roboczym. Jeśli plik nie zostanie znaleziony, przeszukiwane są katalogi, które są określone przez zmienną środowiskową. Jeśli plik docelowy znajduje się w jednym z tych katalogów, nowo utworzona ścieżka jest kopiowana do *nazwy ścieżki*. Jeśli plik *filename* nie zostanie znaleziony, *Nazwa ścieżki* zawiera pusty ciąg zakończony znakiem null.

Bufor nazw powinien zawierać co najmniej **_MAX_PATH** *znaków, aby* pomieścić pełną długość ścieżki skonstruowanej. W przeciwnym razie **_searchenv** może przekroczyć bufor *nazwy ścieżki* i spowodować nieoczekiwane zachowanie.

**_wsearchenv** to dwubajtowa wersja **_searchenv**, a argumenty dla **_wsearchenv** są ciągami znaków dwubajtowych. **_wsearchenv** i **_searchenv** zachowują się identycznie w inny sposób.

Jeśli *Nazwa pliku* jest pustym ciągiem, funkcje te zwracają **ENOENT**.

Jeśli *Nazwa pliku* lub *Nazwa ścieżki* jest **pustym** wskaźnikiem, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają wartość-1 i ustawiają **errno** na **EINVAL**.

Aby uzyskać więcej informacji o **errno** i kodach błędów, zobacz [errno stałe](../../c-runtime-library/errno-constants.md).

W C++programie te funkcje mają przeciążenia szablonu, które wywołują nowsze, bardziej bezpieczne odpowiedniki tych funkcji. Aby uzyskać więcej informacji, zobacz [bezpieczne przeciążenia szablonów](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsearchenv**|**_searchenv**|**_searchenv**|**_wsearchenv**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_searchenv**|\<stdlib.h>|
|**_wsearchenv**|\<STDLIB. h > lub \<WCHAR. h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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
