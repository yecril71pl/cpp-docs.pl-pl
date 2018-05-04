---
title: Obsługa plików | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.files
dev_langs:
- C++
helpviewer_keywords:
- files [C++], handling
- files [C++], opening
- files [C++], manipulating
ms.assetid: 48119e2e-e94f-4602-b08b-b72440f731d8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 95971cceab5673755b33bd99c3365bee62610bf5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="file-handling"></a>Obsługa plików

Za pomocą tych procedur tworzenia, usuwania i manipulowanie plikami i ustawianie i sprawdzanie uprawnień dostępu do plików.

Biblioteki wykonawcze języka C mają 512 limit liczby plików, które można otworzyć w dowolnym momencie. Próba otwarcia więcej niż maksymalna liczba deskryptorów plików lub plików strumieni powoduje awarii programu. Użyj [_setmaxstdio —](../c-runtime-library/reference/setmaxstdio.md) Aby zmienić tę liczbę.

## <a name="file-handling-routines-file-descriptor"></a>Procedury obsługi plików (deskryptorów plików)

Procedury te działają na pliki wskazywany przez deskryptorów plików.

|Procedura|Zastosowanie|
|-------------|---------|
|[_chsize —](../c-runtime-library/reference/chsize.md),[_chsize_s —](../c-runtime-library/reference/chsize-s.md)|Zmienić rozmiar pliku|
|[_filelength, _filelengthi64](../c-runtime-library/reference/filelength-filelengthi64.md)|Pobieranie długości pliku|
|[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)|Pobierz stan pliku informacji o deskryptora|
|[_get_osfhandle](../c-runtime-library/reference/get-osfhandle.md)|Dojście do powrotu pliku systemu operacyjnego skojarzonego z istniejącego deskryptora czasu wykonywania pliku C|
|[_isatty](../c-runtime-library/reference/isatty.md)|Sprawdzanie urządzenia znakowego|
|[_locking](../c-runtime-library/reference/locking.md)|Obszary blokady pliku|
|[_open_osfhandle](../c-runtime-library/reference/open-osfhandle.md)|Skojarz deskryptorów plików wykonawcze języka C z istniejących dojście do pliku systemu operacyjnego|
|[_setmode](../c-runtime-library/reference/setmode.md)|Ustaw tryb tłumaczenia pliku|

## <a name="file-handling-routines-path-or-filename"></a>Procedury obsługi plików (ścieżka lub nazwa pliku)

Procedury te działają na pliki w ścieżce lub nazwie pliku.

|Procedura|Zastosowanie|
|-------------|---------|
|[_access —, _waccess —](../c-runtime-library/reference/access-waccess.md), [_access_s —, _waccess_s —](../c-runtime-library/reference/access-s-waccess-s.md)|Sprawdź ustawienie uprawnień do pliku|
|[_chmod, _wchmod](../c-runtime-library/reference/chmod-wchmod.md)|Zmień ustawienie uprawnień do pliku|
|[_fullpath, _wfullpath](../c-runtime-library/reference/fullpath-wfullpath.md)|Rozwiń węzeł ścieżki względnej do jego nazwy ścieżki bezwzględne|
|[_makepath —, _wmakepath —](../c-runtime-library/reference/makepath-wmakepath.md), [_makepath_s —, _wmakepath_s —](../c-runtime-library/reference/makepath-s-wmakepath-s.md)|Scal składników ścieżki, w jednej, pełna ścieżka|
|[_mktemp —, _wmktemp —](../c-runtime-library/reference/mktemp-wmktemp.md), [_mktemp_s —, _wmktemp_s —](../c-runtime-library/reference/mktemp-s-wmktemp-s.md)|Utworzyć unikatową nazwę pliku|
|[remove, _wremove](../c-runtime-library/reference/remove-wremove.md)|Usuń plik|
|[rename, _wrename](../c-runtime-library/reference/rename-wrename.md)|Zmień nazwę pliku|
|[_splitpath —, _wsplitpath —](../c-runtime-library/reference/splitpath-wsplitpath.md), [_splitpath_s —, _wsplitpath_s —](../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)|Przeanalizować ścieżkę do składników|
|[_stat, _stat64 —, _stati64 —, _wstat — _wstat64 —, _wstati64 —](../c-runtime-library/reference/stat-functions.md)|Pobierz stan pliku informacji w pliku o nazwie|
|[_umask —](../c-runtime-library/reference/umask.md), [_umask_s —](../c-runtime-library/reference/umask-s.md)|Ustaw domyślną maskę uprawnień dla nowych plików utworzonych przez program|
|[_unlink, _wunlink](../c-runtime-library/reference/unlink-wunlink.md)|Usuń plik|

## <a name="file-handling-routines-open-file"></a>Procedury obsługi plików (Otwórz plik)

Te procedury otwierać plików.

|Procedura|Zastosowanie|
|-------------|---------|
|[fopen —, _wfopen —](../c-runtime-library/reference/fopen-wfopen.md), [fopen_s —, _wfopen_s —](../c-runtime-library/reference/fopen-s-wfopen-s.md)|Otwiera plik i zwraca wskaźnik do otwartego pliku.|
|[_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)|Otwórz strumienia z udostępnianiem plików i zwraca wskaźnik do otwartego pliku.|
|[_open, _wopen](../c-runtime-library/reference/open-wopen.md)|Otwiera plik i zwraca deskryptorów plików do otwartego pliku.|
|[_sopen —, _wsopen —](../c-runtime-library/reference/sopen-wsopen.md), [_sopen_s —, _wsopen_s —](../c-runtime-library/reference/sopen-s-wsopen-s.md)|Otwórz plik z udostępnianiem plików i zwraca deskryptorów plików do otwartego pliku.|
|[_pipe](../c-runtime-library/reference/pipe.md)|Tworzy potoku do odczytu i zapisu.|
|[freopen —, _wfreopen —](../c-runtime-library/reference/freopen-wfreopen.md), [freopen_s —, _wfreopen_s —](../c-runtime-library/reference/freopen-s-wfreopen-s.md)|Ponowne przypisanie wskaźnika pliku.|

Te procedury umożliwiają zmienić reprezentację plików między `FILE` strukturę, deskryptorów plików i dojście do pliku Win32.

|Procedura|Zastosowanie|
|-------------|---------|
|[_fdopen, _wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)|Kojarzy strumienia z pliku, który został poprzednio otwarty dla niskiego poziomu we/wy i zwraca wskaźnik można otworzyć strumienia.|
|[_fileno](../c-runtime-library/reference/fileno.md)|Pobiera deskryptor pliku skojarzone z strumienia.|
|[_get_osfhandle](../c-runtime-library/reference/get-osfhandle.md)|Dojście do powrotu pliku systemu operacyjnego skojarzonego z istniejącego deskryptora czasu wykonywania pliku C|
|[_open_osfhandle](../c-runtime-library/reference/open-osfhandle.md)|Kojarzy deskryptorów plików wykonawcze języka C z istniejących dojście do pliku systemu operacyjnego.|

 Następujące funkcje Win32 również otworzyć pliki i potoków:

- [CreateFile](http://msdn.microsoft.com/library/windows/desktop/aa363858.aspx)

- [CreatePipe](http://msdn.microsoft.com/library/windows/desktop/aa365152.aspx)

- [CreateNamedPipe](http://msdn.microsoft.com/library/windows/desktop/aa365150.aspx)

## <a name="see-also"></a>Zobacz też

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Kontrola katalogu](../c-runtime-library/directory-control.md)<br/>
[Wywołania systemowe](../c-runtime-library/system-calls.md)<br/>
