---
title: _searchenv —, _wsearchenv — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 62e0fea9154801f850640234355af53dc1154160
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32408918"
---
# <a name="searchenv-wsearchenv"></a>_searchenv, _wsearchenv

Używa środowiska ścieżek, aby wyszukać plik. Bezpieczniejsza wersje te funkcje są dostępne; zobacz [_searchenv_s —, _wsearchenv_s —](searchenv-s-wsearchenv-s.md).

> [!IMPORTANT]
> Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Nazwa pliku* nazwę pliku do wyszukania.

*nazwa_zmiennej* środowiska do wyszukiwania.

*Nazwa ścieżki* buforu do przechowywania pełną ścieżkę.

## <a name="remarks"></a>Uwagi

**_Searchenv —** procedura wyszukiwania dla pliku docelowego w określonej domenie. *Nazwa_zmiennej* zmiennej może być dowolną środowiska lub zmiennej zdefiniowanej przez użytkownika — na przykład **ścieżki**, **LIB**, lub **INCLUDE**— Określa, że Lista ścieżek katalogów. Ponieważ **_searchenv —** jest rozróżniana wielkość liter, *nazwa_zmiennej* powinno być zgodne w przypadku ustawienia zmiennej środowiskowej.

Procedura najpierw szuka pliku w bieżącym katalogu roboczym. Jeśli plik nie zostanie znaleziona, przeszukiwanie katalogi, które są określone przez zmienną środowiskową. Jeśli plik docelowy znajduje się w jednym z tych katalogów, nowo utworzona ścieżka jest kopiowana do *pathname*. Jeśli *filename* nie znaleziono pliku *pathname* zawiera pusty ciąg zerem.

*Pathname* buforu powinien być co najmniej **_max_path —** znaków, aby pomieścić długie nazwy ścieżki skonstruowane. W przeciwnym razie **_searchenv —** może przepełnienie *pathname* buforu i spowodować nieoczekiwane zachowanie.

**_wsearchenv —** jest wersja znaków dwubajtowych **_searchenv —** i argumenty **_wsearchenv —** są ciągami znaków dwubajtowych. **_wsearchenv —** i **_searchenv —** zachowują się tak samo w przeciwnym razie wartość.

Jeśli *filename* jest pustym ciągiem, te funkcje zwracają **enoent —**.

Jeśli *filename* lub *pathname* jest **NULL** wskaźnika, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Zwróć -1, jeśli wykonanie może kontynuować, następujące funkcje i ustaw **errno** do **einval —**.

Aby uzyskać więcej informacji na temat **errno** i kody błędów, zobacz [errno — stałe](../../c-runtime-library/errno-constants.md).

W języku C++ tych funkcji mają przeciążenia szablonu, które wywołują odpowiedników nowsze, bezpieczniejsze tych funkcji. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsearchenv —**|**_searchenv**|**_searchenv**|**_wsearchenv —**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_searchenv**|\<stdlib.h>|
|**_wsearchenv —**|\<stdlib.h > lub \<wchar.h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
