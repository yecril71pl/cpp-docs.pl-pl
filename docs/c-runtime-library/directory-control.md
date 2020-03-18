---
title: Kontrola katalogu
ms.date: 11/04/2016
helpviewer_keywords:
- controls [C++], directory
- directory control routines
ms.assetid: a72dcf6f-f366-4d20-8850-0e19cc53ca18
ms.openlocfilehash: 640ce8a8665936b604c6e8e6270e358a200c880a
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438534"
---
# <a name="directory-control"></a>Kontrola katalogu

Te procedury służą do uzyskiwania dostępu do informacji o strukturze katalogów oraz ich modyfikowania.

## <a name="directory-control-routines"></a>Procedury kontroli katalogu

|Procedura|Użycie|
|-------------|---------|
|[_chdir, _wchdir](../c-runtime-library/reference/chdir-wchdir.md)|Zmień bieżący katalog roboczy|
|[_chdrive](../c-runtime-library/reference/chdrive.md)|Zmień bieżący dysk|
|[_getcwd, _wgetcwd](../c-runtime-library/reference/getcwd-wgetcwd.md)|Pobierz bieżący katalog roboczy dla dysku domyślnego|
|[_getdcwd, _wgetdcwd](../c-runtime-library/reference/getdcwd-wgetdcwd.md)|Pobierz bieżący katalog roboczy dla określonego dysku|
|[_getdiskfree](../c-runtime-library/reference/getdiskfree.md)|Wypełnia strukturę **_diskfree_t** informacjami o stacji dysków.|
|[_getdrive](../c-runtime-library/reference/getdrive.md)|Pobieranie bieżącego (domyślnego) dysku|
|[_getdrives](../c-runtime-library/reference/getdrives.md)|Zwraca maskę bitów reprezentującą aktualnie dostępne stacje dysków.|
|[_mkdir, _wmkdir](../c-runtime-library/reference/mkdir-wmkdir.md)|Utwórz nowy katalog|
|[_rmdir, _wrmdir](../c-runtime-library/reference/rmdir-wrmdir.md)|Usuń katalog|
|[_searchenv, _wsearchenv](../c-runtime-library/reference/searchenv-wsearchenv.md), [_searchenv_s _wsearchenv_s](../c-runtime-library/reference/searchenv-s-wsearchenv-s.md)|Wyszukaj podany plik w określonych ścieżkach|

## <a name="see-also"></a>Zobacz też

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Obsługa plików](../c-runtime-library/file-handling.md)<br/>
[Wywołania systemowe](../c-runtime-library/system-calls.md)<br/>
