---
title: _searchenv_s, _wsearchenv_s
ms.date: 4/2/2020
api_name:
- _wsearchenv_s
- _searchenv_s
- _o__searchenv_s
- _o__wsearchenv_s
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
ms.openlocfilehash: 3d526c546e1496b3b13b14a12c9025cbd0347cd2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332398"
---
# <a name="_searchenv_s-_wsearchenv_s"></a>_searchenv_s, _wsearchenv_s

Wyszukuje plik przy użyciu ścieżek środowiska. Te wersje [_searchenv, _wsearchenv](searchenv-wsearchenv.md) mają ulepszenia zabezpieczeń, zgodnie z opisem w [funkcji zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Pod nazwą*<br/>
Nazwa pliku do wyszukania.

*Varname*<br/>
Środowisko do wyszukiwania.

*Nazwa_ścieżki*<br/>
Bufor do przechowywania pełnej ścieżki.

*liczbaOfElements*<br/>
Rozmiar buforu *nazwy ścieżki.*

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli się powiedzie; kod błędu w przypadku awarii.

Jeśli *nazwa pliku* jest pustym ciągiem, zwracaną wartością jest **ENOENT**.

### <a name="error-conditions"></a>Warunki błędu

|*Pod nazwą*|*Varname*|*Nazwa_ścieżki*|*liczbaOfElements*|Wartość zwracana|Zawartość *nazwy ścieżki*|
|----------------|---------------|----------------|------------------------|------------------|----------------------------|
|Wszelki|Wszelki|**Null**|Wszelki|**Einval**|Nie dotyczy|
|**Null**|Wszelki|Wszelki|Wszelki|**Einval**|nie zmieniono|
|Wszelki|Wszelki|Wszelki|<= 0|**Einval**|nie zmieniono|

Jeśli wystąpi którykolwiek z tych warunków błędu, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [obszarze Sprawdzanie poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, te funkcje **ustawiają errno** na **EINVAL** i zwracają **EINVAL**.

## <a name="remarks"></a>Uwagi

**_searchenv_s** rutynowe wyszukiwanie pliku docelowego w określonej domenie. Zmienną *warname* może być dowolna zmienna środowiska lub zdefiniowana przez użytkownika, która określa listę ścieżek katalogowych, takich jak **PATH,** **LIB**i **INCLUDE**. Ponieważ **_searchenv_s** jest rozróżniana wielkość liter, *varname* powinien odpowiadać wielkości przypadku zmiennej środowiskowej. Jeśli *nazwa warname* nie jest zgodna z nazwą zmiennej środowiskowej zdefiniowanej w środowisku procesu, funkcja zwraca zero, a *zmienna pathname* pozostaje niezmieniona.

Procedura najpierw wyszukuje plik w bieżącym katalogu roboczym. Jeśli nie znajdzie pliku, szuka dalej za pośrednictwem katalogów określonych przez zmienną środowiskową. Jeśli plik docelowy znajduje się w jednym z tych katalogów, nowo utworzona ścieżka jest kopiowana do *nazwy ścieżki*. Jeśli nie znaleziono pliku *nazwy pliku,* *nazwa ścieżki* zawiera pusty ciąg zakończony z wartością null.

Bufor *nazwy ścieżki* powinien mieć co najmniej **_MAX_PATH** znaków, aby pomieścić pełną długość nazwy ścieżki skonstruowanej. W przeciwnym razie **_searchenv_s** może przekroczyć *bufornazy,* co spowoduje nieoczekiwane zachowanie.

**_wsearchenv_s** jest szerokoznakową wersją **_searchenv_s**; argumenty, które **mają _wsearchenv_s,** to ciągi znaków o szerokich znakach. **_wsearchenv_s** i **_searchenv_s** zachowują się identycznie w przeciwnym razie.

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążenia szablonu; przeciążenia można wywnioskować długość buforu automatycznie (eliminując konieczność określenia argumentu rozmiaru) i mogą automatycznie zastąpić starsze, niezabezpieczone funkcje z ich nowszych, bezpiecznych odpowiedników. Aby uzyskać więcej informacji, zobacz [Bezpieczne przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsearchenv_s**|**_searchenv_s**|**_searchenv_s**|**_wsearchenv_s**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_searchenv_s**|\<>|
|**_wsearchenv_s**|\<> lub \<wchar.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Kontrola katalogu](../../c-runtime-library/directory-control.md)<br/>
[_searchenv, _wsearchenv](searchenv-wsearchenv.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_putenv, _wputenv](putenv-wputenv.md)<br/>
