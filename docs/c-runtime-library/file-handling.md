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
ms.openlocfilehash: e5e43fe2cfcdfe067833d02bda511e8c9cb944ad
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500108"
---
# <a name="file-handling"></a>Obsługa plików

Te procedury służą do tworzenia, usuwania i manipulowania plikami oraz do ustawiania i sprawdzania uprawnień dostępu do plików.

Biblioteki uruchomieniowe C mają limit 512 dla liczby plików, które można otworzyć w dowolnym momencie. Próba otwarcia więcej niż maksymalnej liczby deskryptorów plików lub strumieni plików powoduje awarię programu. Użyj [_setmaxstdio](../c-runtime-library/reference/setmaxstdio.md) , aby zmienić tę liczbę.

## <a name="file-handling-routines-file-descriptor"></a>Procedury obsługi plików (deskryptor pliku)

Procedury te działają na plikach wydzielonych przez deskryptor pliku.

|Procedura|Zastosowanie|
|-------------|---------|
|[_chsize](../c-runtime-library/reference/chsize.md),[_chsize_s](../c-runtime-library/reference/chsize-s.md)|Zmień rozmiar pliku|
|[_filelength, _filelengthi64](../c-runtime-library/reference/filelength-filelengthi64.md)|Pobierz długość pliku|
|[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)|Pobierz informacje o stanie pliku dla deskryptora|
|[_get_osfhandle](../c-runtime-library/reference/get-osfhandle.md)|Zwróć dojście do pliku systemu operacyjnego powiązane z istniejącym deskryptorem pliku w czasie wykonywania C|
|[_isatty](../c-runtime-library/reference/isatty.md)|Sprawdź obecność urządzenia znakowego|
|[_locking](../c-runtime-library/reference/locking.md)|Zablokuj obszary pliku|
|[_open_osfhandle](../c-runtime-library/reference/open-osfhandle.md)|Skojarz deskryptor pliku C w czasie wykonywania z istniejącym dojściem do pliku systemu operacyjnego|
|[_setmode](../c-runtime-library/reference/setmode.md)|Ustawianie trybu tłumaczenia plików|

## <a name="file-handling-routines-path-or-filename"></a>Procedury obsługi plików (ścieżka lub nazwa pliku)

Procedury te działają na plikach określonych przez ścieżkę lub nazwę pliku.

|Procedura|Zastosowanie|
|-------------|---------|
|[_access, _waccess](../c-runtime-library/reference/access-waccess.md), [_access_s, _waccess_s](../c-runtime-library/reference/access-s-waccess-s.md)|Sprawdź ustawienie uprawnienia do pliku|
|[_chmod, _wchmod](../c-runtime-library/reference/chmod-wchmod.md)|Zmień ustawienie uprawnienia do pliku|
|[_fullpath, _wfullpath](../c-runtime-library/reference/fullpath-wfullpath.md)|Rozwiń ścieżkę względną do nazwy ścieżki bezwzględnej|
|[_makepath, _wmakepath](../c-runtime-library/reference/makepath-wmakepath.md), [_makepath_s, _wmakepath_s](../c-runtime-library/reference/makepath-s-wmakepath-s.md)|Scalanie składników ścieżki w jedną, pełną ścieżkę|
|[_mktemp, _wmktemp](../c-runtime-library/reference/mktemp-wmktemp.md), [_mktemp_s, _wmktemp_s](../c-runtime-library/reference/mktemp-s-wmktemp-s.md)|Utwórz unikatową nazwę pliku|
|[remove, _wremove](../c-runtime-library/reference/remove-wremove.md)|Usuń plik|
|[rename, _wrename](../c-runtime-library/reference/rename-wrename.md)|Zmień nazwę pliku|
|[_splitpath, _wsplitpath](../c-runtime-library/reference/splitpath-wsplitpath.md), [_splitpath_s, _wsplitpath_s](../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)|Analizowanie ścieżki do składników|
|[_stat, _stat64, _stati64, _wstat, _wstat64, _wstati64](../c-runtime-library/reference/stat-functions.md)|Pobierz informacje o stanie pliku dla nazwanego pliku|
|[_umask](../c-runtime-library/reference/umask.md), [_umask_s](../c-runtime-library/reference/umask-s.md)|Ustaw domyślną maskę uprawnień dla nowych plików utworzonych przez program|
|[_unlink, _wunlink](../c-runtime-library/reference/unlink-wunlink.md)|Usuń plik|

## <a name="file-handling-routines-open-file"></a>Procedury obsługi plików (otwarty plik)

Te procedury otwierają pliki.

|Procedura|Zastosowanie|
|-------------|---------|
|[fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md), [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)|Otwiera plik i zwraca wskaźnik do otwartego pliku.|
|[_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)|Otwórz strumień z funkcją udostępniania plików i zwraca wskaźnik do otwartego pliku.|
|[_open, _wopen](../c-runtime-library/reference/open-wopen.md)|Otwiera plik i zwraca deskryptor pliku do otwartego pliku.|
|[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md), [_sopen_s, _wsopen_s](../c-runtime-library/reference/sopen-s-wsopen-s.md)|Otwórz plik z funkcją udostępniania plików i zwraca deskryptor pliku do otwartego pliku.|
|[_pipe](../c-runtime-library/reference/pipe.md)|Tworzy potok do odczytu i zapisu.|
|[freopen, _wfreopen](../c-runtime-library/reference/freopen-wfreopen.md), [freopen_s, _wfreopen_s](../c-runtime-library/reference/freopen-s-wfreopen-s.md)|Ponownie Przypisz wskaźnik do pliku.|

Te procedury umożliwiają zmianę reprezentacji pliku między `FILE` strukturą, deskryptorem pliku i dojściem do pliku Win32.

|Procedura|Zastosowanie|
|-------------|---------|
|[_fdopen, _wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)|Kojarzy strumień z plikiem, który został wcześniej otwarty dla operacji we/wy niskiego poziomu i zwraca wskaźnik do otwartego strumienia.|
|[_fileno](../c-runtime-library/reference/fileno.md)|Pobiera deskryptor pliku skojarzony ze strumieniem.|
|[_get_osfhandle](../c-runtime-library/reference/get-osfhandle.md)|Zwróć dojście do pliku systemu operacyjnego powiązane z istniejącym deskryptorem pliku w czasie wykonywania C|
|[_open_osfhandle](../c-runtime-library/reference/open-osfhandle.md)|Kojarzy deskryptor pliku w czasie wykonywania C z istniejącym dojściem do pliku systemu operacyjnego.|

Następujące funkcje Win32 również otwierają pliki i potoki:

- [CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew)

- [Potok](/windows/win32/api/namedpipeapi/nf-namedpipeapi-createpipe)

- [CreateNamedPipe](/windows/win32/api/winbase/nf-winbase-createnamedpipew)

## <a name="see-also"></a>Zobacz także

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Kontrola katalogu](../c-runtime-library/directory-control.md)<br/>
[Wywołania systemowe](../c-runtime-library/system-calls.md)<br/>
