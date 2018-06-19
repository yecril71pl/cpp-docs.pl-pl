---
title: _searchenv_s —, _wsearchenv_s — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b14dee908cdf1cc0d564047035a72f501df130b4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32410918"
---
# <a name="searchenvs-wsearchenvs"></a>_searchenv_s, _wsearchenv_s

Wyszukiwanie plików przy użyciu ścieżki środowiska. Te wersje programu [_searchenv —, _wsearchenv —](searchenv-wsearchenv.md) zostały ulepszone zabezpieczenia, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*nazwa_zmiennej*<br/>
Środowisko wyszukiwania.

*Nazwa ścieżki*<br/>
Bufor do przechowywania pełną ścieżkę.

*numberOfElements*<br/>
Rozmiar *pathname* buforu.

## <a name="return-value"></a>Wartość zwracana

Zero w przypadku powodzenia; błąd o kodzie błędu.

Jeśli *filename* to ciąg pusty jest zwracana wartość **enoent —**.

### <a name="error-conditions"></a>Warunki błędów

|*Nazwa pliku*|*nazwa_zmiennej*|*Nazwa ścieżki*|*numberOfElements*|Wartość zwracana|Zawartość *nazwy ścieżki*|
|----------------|---------------|----------------|------------------------|------------------|----------------------------|
|wszystkie|wszystkie|**NULL**|wszystkie|**EINVAL —**|n/d|
|**NULL**|wszystkie|wszystkie|wszystkie|**EINVAL —**|nie został zmieniony|
|wszystkie|wszystkie|wszystkie|<= 0|**EINVAL —**|nie został zmieniony|

Jeśli dowolny z tych warunków błąd wystąpi, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli dozwolone jest wykonywanie aby kontynuować, ustawianie tych funkcji **errno** do **einval —** i zwracać **einval —**.

## <a name="remarks"></a>Uwagi

**_Searchenv_s —** procedura wyszukiwania dla pliku docelowego w określonej domenie. *Nazwa_zmiennej* zmiennej może być dowolną środowiska lub zmiennej zdefiniowanej przez użytkownika określa listę ścieżki katalogu, takie jak **ścieżki**, **LIB**, i **DOŁĄCZANIA** . Ponieważ **_searchenv_s —** jest rozróżniana wielkość liter, *nazwa_zmiennej* powinno być zgodne w przypadku ustawienia zmiennej środowiskowej. Jeśli *nazwa_zmiennej* nie odpowiada nazwa zmiennej środowiskowej zdefiniowana w środowisku procesu, funkcja zwraca wartość zero i *pathname* zmienna jest bez zmian.

Procedura najpierw szuka pliku w bieżącym katalogu roboczym. Jeśli plik nie zostanie znaleziona, wygląda dalej za pośrednictwem katalogów, określonej przez zmienną środowiskową. Jeśli plik docelowy znajduje się w jednym z tych katalogów, nowo utworzona ścieżka jest kopiowana do *pathname*. Jeśli *filename* nie znaleziono pliku *pathname* zawiera pusty ciąg zerem.

*Pathname* buforu powinien być co najmniej **_max_path —** znaków, aby pomieścić długie nazwy ścieżki skonstruowane. W przeciwnym razie **_searchenv_s —** może przepełnienie *pathname* buforu spowodować nieoczekiwane zachowanie.

**_wsearchenv_s —** jest wersja znaków dwubajtowych **_searchenv_s —**; argumenty **_wsearchenv_s —** są ciągami znaków dwubajtowych. **_wsearchenv_s —** i **_searchenv_s —** zachowują się tak samo w przeciwnym razie wartość.

W języku C++ za pomocą tych funkcji zostało uproszczone dzięki przeciążenia szablonu; przeciążeń można automatycznie rozpoznać długość buforu (wyeliminowanie konieczności określania argumentem rozmiaru) i automatycznie można zastąpić starszą, które nie są bezpieczne funkcje z ich odpowiedniki nowsza, bezpieczne. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsearchenv_s —**|**_searchenv_s**|**_searchenv_s**|**_wsearchenv_s**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_searchenv_s**|\<stdlib.h>|
|**_wsearchenv_s**|\<stdlib.h > lub \<wchar.h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
