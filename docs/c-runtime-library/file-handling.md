---
title: Obsługa plików
ms.date: 11/04/2016
f1_keywords:
- c.files
helpviewer_keywords:
- files [C++], handling
- files [C++], opening
- files [C++], manipulating
ms.assetid: 48119e2e-e94f-4602-b08b-b72440f731d8
ms.openlocfilehash: 9bbd64b27a760969635d70ae7689d09afed2d729
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62343826"
---
# <a name="file-handling"></a>Obsługa plików

Umożliwia tych procedur do tworzenia, usuwania i operowania plikami oraz Ustawianie i sprawdzanie uprawnień dostępu do plików.

Biblioteki wykonawczej C ma 512 limitu liczby plików, które można otworzyć w dowolnym momencie. Podjęto próbę otwarcia przekracza maksymalną liczbę deskryptorów plików i strumieni plików powoduje awarię programu. Użyj [_setmaxstdio —](../c-runtime-library/reference/setmaxstdio.md) zmieniać tej wartości.

## <a name="file-handling-routines-file-descriptor"></a>Procedury obsługi plików (deskryptorów plików)

Procedury te działają na pliki wyznaczonym przez deskryptor pliku.

|Procedura|Zastosowanie|
|-------------|---------|
|[_chsize —](../c-runtime-library/reference/chsize.md),[_chsize_s —](../c-runtime-library/reference/chsize-s.md)|Zmienić rozmiar pliku|
|[_filelength, _filelengthi64](../c-runtime-library/reference/filelength-filelengthi64.md)|Pobierz plik długość|
|[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)|Uzyskaj informacje o stanie pliku dla deskryptora|
|[_get_osfhandle](../c-runtime-library/reference/get-osfhandle.md)|Uchwyt zwracany plików systemu operacyjnego skojarzony z istniejącego deskryptora pliku środowiska wykonawczego języka C|
|[_isatty](../c-runtime-library/reference/isatty.md)|Sprawdzanie urządzenia znakowego|
|[_locking](../c-runtime-library/reference/locking.md)|Obszary blokowanie pliku|
|[_open_osfhandle](../c-runtime-library/reference/open-osfhandle.md)|Kojarzenie deskryptor pliku środowiska wykonawczego języka C z istniejących dojście do pliku systemu operacyjnego|
|[_setmode](../c-runtime-library/reference/setmode.md)|Ustaw tryb tłumaczenia pliku|

## <a name="file-handling-routines-path-or-filename"></a>Procedury obsługi plików (ścieżka lub nazwa pliku)

Procedury te działają na plików określone przez ścieżkę lub nazwę pliku.

|Procedura|Zastosowanie|
|-------------|---------|
|[_access, _waccess —](../c-runtime-library/reference/access-waccess.md), [_access_s —, _waccess_s —](../c-runtime-library/reference/access-s-waccess-s.md)|Sprawdź ustawienie uprawnień pliku|
|[_chmod, _wchmod](../c-runtime-library/reference/chmod-wchmod.md)|Zmień ustawienie uprawnień pliku|
|[_fullpath, _wfullpath](../c-runtime-library/reference/fullpath-wfullpath.md)|Rozwiń ścieżkę względną nazwę ścieżki bezwzględnej|
|[_makepath —, _wmakepath —](../c-runtime-library/reference/makepath-wmakepath.md), [_makepath_s —, _wmakepath_s —](../c-runtime-library/reference/makepath-s-wmakepath-s.md)|Scal składników ścieżki w pojedynczą, pełną ścieżkę|
|[_mktemp —, _wmktemp —](../c-runtime-library/reference/mktemp-wmktemp.md), [_mktemp_s —, _wmktemp_s —](../c-runtime-library/reference/mktemp-s-wmktemp-s.md)|Utwórz unikatową nazwę pliku|
|[remove, _wremove](../c-runtime-library/reference/remove-wremove.md)|Usuń plik|
|[rename, _wrename](../c-runtime-library/reference/rename-wrename.md)|Zmień nazwę pliku|
|[_splitpath —, _wsplitpath —](../c-runtime-library/reference/splitpath-wsplitpath.md), [_splitpath_s —, _wsplitpath_s —](../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)|Przeanalizować ścieżki do składników|
|[_stat, _stat64, _stati64, _wstat — _wstat64, _wstati64](../c-runtime-library/reference/stat-functions.md)|Uzyskaj informacje o stanie pliku dla pliku o nazwie|
|[_umask —](../c-runtime-library/reference/umask.md), [_umask_s —](../c-runtime-library/reference/umask-s.md)|Ustaw domyślną maskę uprawnień dla nowych plików utworzonych przez program|
|[_unlink, _wunlink](../c-runtime-library/reference/unlink-wunlink.md)|Usuń plik|

## <a name="file-handling-routines-open-file"></a>Procedury obsługi plików (Otwórz plik)

Te procedury otwierać plików.

|Procedura|Zastosowanie|
|-------------|---------|
|[fopen —, _wfopen —](../c-runtime-library/reference/fopen-wfopen.md), [fopen_s —, _wfopen_s —](../c-runtime-library/reference/fopen-s-wfopen-s.md)|Otwiera plik, a następnie zwraca wskaźnik do otwartego pliku.|
|[_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)|Otwórz strumienia z funkcją Udostępnianie plików i zwraca wskaźnik do otwartego pliku.|
|[_open, _wopen](../c-runtime-library/reference/open-wopen.md)|Otwiera plik i zwraca deskryptor pliku do otwartego pliku.|
|[_sopen, _wsopen —](../c-runtime-library/reference/sopen-wsopen.md), [_sopen_s —, _wsopen_s —](../c-runtime-library/reference/sopen-s-wsopen-s.md)|Otwórz plik z funkcją Udostępnianie plików i zwraca deskryptor pliku do otwartego pliku.|
|[_pipe](../c-runtime-library/reference/pipe.md)|Tworzy potok do odczytu i zapisu.|
|[freopen —, _wfreopen —](../c-runtime-library/reference/freopen-wfreopen.md), [freopen_s —, _wfreopen_s —](../c-runtime-library/reference/freopen-s-wfreopen-s.md)|Ponowne przypisywanie wskaźnika pliku.|

Te procedury umożliwiają zmienić reprezentację pliku między `FILE` struktury, deskryptor pliku i dojście do pliku systemu Win32.

|Procedura|Zastosowanie|
|-------------|---------|
|[_fdopen, _wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)|Kojarzy strumienia z pliku, który był wcześniej otwarty dla niskiego poziomu we/wy i zwraca wskaźnik do otwartego strumienia.|
|[_fileno](../c-runtime-library/reference/fileno.md)|Pobiera deskryptor pliku skojarzone ze strumieniem.|
|[_get_osfhandle](../c-runtime-library/reference/get-osfhandle.md)|Uchwyt zwracany plików systemu operacyjnego skojarzony z istniejącego deskryptora pliku środowiska wykonawczego języka C|
|[_open_osfhandle](../c-runtime-library/reference/open-osfhandle.md)|Powoduje skojarzenie deskryptora pliku środowiska wykonawczego języka C z istniejący uchwyt pliku systemu operacyjnego.|

Następujące funkcje systemu Win32 jest również otworzyć pliki i potoki:

- [CreateFile](/windows/desktop/api/fileapi/nf-fileapi-createfilea)

- [CreatePipe](https://msdn.microsoft.com/library/windows/desktop/aa365152.aspx)

- [CreateNamedPipe](/windows/desktop/api/winbase/nf-winbase-createnamedpipea)

## <a name="see-also"></a>Zobacz także

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Kontrola katalogu](../c-runtime-library/directory-control.md)<br/>
[Wywołania systemowe](../c-runtime-library/system-calls.md)<br/>
