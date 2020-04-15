---
title: _searchenv, _wsearchenv
ms.date: 4/2/2020
api_name:
- _searchenv
- _wsearchenv
- _o__searchenv
- _o__wsearchenv
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
ms.openlocfilehash: 22a8ca8fa7e56a84289d7e90ffb519073f006b5c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332382"
---
# <a name="_searchenv-_wsearchenv"></a>_searchenv, _wsearchenv

Używa ścieżek środowiska do wyszukiwania pliku. Dostępne są bezpieczniejsze wersje tych funkcji; patrz [_searchenv_s, _wsearchenv_s](searchenv-s-wsearchenv-s.md).

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Pod nazwą*<br/>
Nazwa pliku do wyszukania.

*Varname*<br/>
Środowisko do wyszukiwania.

*Nazwa_ścieżki*<br/>
Bufor do przechowywania pełnej ścieżki.

## <a name="remarks"></a>Uwagi

**_searchenv** rutynowe wyszukiwanie pliku docelowego w określonej domenie. Zmienną *warname* może być dowolna zmienna środowiska lub zmienna zdefiniowana przez użytkownika — na przykład **PATH,** **LIB**lub **INCLUDE**— określająca listę ścieżek katalogowych. Ponieważ **_searchenv** jest rozróżniana wielkość liter, *varname* powinien odpowiadać wielkości przypadku zmiennej środowiskowej.

Procedura najpierw wyszukuje plik w bieżącym katalogu roboczym. Jeśli nie znajdzie pliku, przeszukuje katalogi, które są określone przez zmienną środowiskową. Jeśli plik docelowy znajduje się w jednym z tych katalogów, nowo utworzona ścieżka jest kopiowana do *nazwy ścieżki*. Jeśli nie znaleziono pliku *nazwy pliku,* *nazwa ścieżki* zawiera pusty ciąg zakończony z wartością null.

Bufor *nazwy ścieżki* powinien mieć co najmniej **_MAX_PATH** znaków, aby pomieścić pełną długość nazwy ścieżki skonstruowanej. W przeciwnym razie **_searchenv** może przekroczyć *bufornazy i* spowodować nieoczekiwane zachowanie.

**_wsearchenv** jest szerokoznakową wersją **_searchenv**, a argumentami, które **należy _wsearchenv,** są ciągi znaków o szerokich znakach. **_wsearchenv** i **_searchenv** zachowują się identycznie w przeciwnym razie.

Jeśli *nazwa pliku* jest pustym ciągiem, te funkcje zwracają **ENOENT**.

Jeśli *nazwa pliku* lub nazwa *ścieżki* jest wskaźnikiem **NULL,** wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w polu [Sprawdzanie poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, te funkcje zwracają -1 i ustawić **errno** na **EINVAL**.

Aby uzyskać więcej informacji na temat **kodów błędów** i błędów, zobacz [errno Constants](../../c-runtime-library/errno-constants.md).

W języku C++ te funkcje mają przeciążenia szablonu, które wywołują nowsze, bezpieczniejsze odpowiedniki tych funkcji. Aby uzyskać więcej informacji, zobacz [Bezpieczne przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsearchenv**|**_searchenv**|**_searchenv**|**_wsearchenv**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_searchenv**|\<>|
|**_wsearchenv**|\<> lub \<wchar.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Kontrola katalogu](../../c-runtime-library/directory-control.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_putenv, _wputenv](putenv-wputenv.md)<br/>
[_searchenv_s, _wsearchenv_s](searchenv-s-wsearchenv-s.md)<br/>
