---
title: Strumień we/wy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.io
dev_langs:
- C++
helpviewer_keywords:
- I/O routines, stream I/O
- I/O [CRT], stream
- stream I/O
ms.assetid: dc7874d3-a91b-456a-9015-4748bb358217
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a3fba53f16fad9321701e641020ed01349b13a5c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418108"
---
# <a name="stream-io"></a>We/Wy strumienia

Te funkcje przetwarzania danych w różnych rozmiarach i formaty pojedynczy znaki do struktur dużej ilości danych. Zapewniają także buforowania, które może poprawić wydajność. Domyślny rozmiar buforu strumienia jest 4K. Te procedury wpływają na tylko buforów utworzone przez procedury biblioteki wykonawczej i nie mają wpływu na buforów utworzony przez system operacyjny.

## <a name="stream-io-routines"></a>Procedury we/wy strumienia

|Procedura|Zastosowanie|
|-------------|---------|
|[clearerr —](../c-runtime-library/reference/clearerr.md), [clearerr_s —](../c-runtime-library/reference/clearerr-s.md)|Wskaźnik błędów wyczyść dla strumienia|
|[fclose —](../c-runtime-library/reference/fclose-fcloseall.md)|Zamknij strumienia|
|[_fcloseall —](../c-runtime-library/reference/fclose-fcloseall.md)|Zamknij wszystkie otwarte strumieni z wyjątkiem **stdin**, **stdout**, i **stderr**|
|[_fdopen —, wfdopen —](../c-runtime-library/reference/fdopen-wfdopen.md)|Skojarz strumienia z deskryptorów plików Otwieranie pliku|
|[feof](../c-runtime-library/reference/feof.md)|Test na koniec pliku w strumieniu|
|[ferror](../c-runtime-library/reference/ferror.md)|Test na błąd w strumieniu|
|[fflush](../c-runtime-library/reference/fflush.md)|Zapisywanie strumienia buforu lub urządzenie pamięci masowej|
|[fgetc, fgetwc](../c-runtime-library/reference/fgetc-fgetwc.md)|Znak do odczytu strumienia (funkcji wersji **getc —** i **getwc —**)|
|[_fgetchar, _fgetwchar](../c-runtime-library/reference/fgetc-fgetwc.md)|Przeczytaj znak z **stdin** (funkcji wersji **getchar** i **getwchar —**)|
|[fgetpos](../c-runtime-library/reference/fgetpos.md)|Pobierz wskaźnik położenia strumienia|
|[fgets, fgetws](../c-runtime-library/reference/fgets-fgetws.md)|Parametry odczytu ze strumienia|
|[_fileno](../c-runtime-library/reference/fileno.md)|Pobierz deskryptorów plików skojarzonych z strumienia|
|[_flushall](../c-runtime-library/reference/flushall.md)|Zapisywanie wszystkich strumieni buforu lub urządzenie pamięci masowej|
|[fopen —, _wfopen —](../c-runtime-library/reference/fopen-wfopen.md), [fopen_s —, _wfopen_s —](../c-runtime-library/reference/fopen-s-wfopen-s.md)|Otwórz strumienia|
|[fprintf —, _fprintf_l —, fwprintf —, _fwprintf_l —](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md), [fprintf_s —, _fprintf_s_l —, fwprintf_s —, _fwprintf_s_l —](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|Zapisać sformatowanych danych do strumienia|
|[fputc, fputwc](../c-runtime-library/reference/fputc-fputwc.md)|Wpisz znak w strumieniu (funkcji wersji **putc —** i **putwc —**)|
|[_fputchar, _fputwchar](../c-runtime-library/reference/fputc-fputwc.md)|Wpisz znak do **stdout** (funkcji wersji **putchar —** i **putwchar —**)|
|[fputs, fputws](../c-runtime-library/reference/fputs-fputws.md)|Zapisz ciąg do strumienia|
|[fread](../c-runtime-library/reference/fread.md)|Przeczytaj niesformatowanych danych ze strumienia|
|[freopen —, _wfreopen —](../c-runtime-library/reference/freopen-wfreopen.md), [freopen_s —, _wfreopen_s —](../c-runtime-library/reference/freopen-s-wfreopen-s.md)|Ponownie przypisać **pliku** strumienia wskaźnika do nowego pliku lub urządzenia|
|[fscanf —, fwscanf —](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md), [fscanf_s —, _fscanf_s_l —, fwscanf_s —, _fwscanf_s_l —](../c-runtime-library/reference/fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)|Odczyt sformatowanych danych ze strumienia|
|[fseek, _fseeki64](../c-runtime-library/reference/fseek-fseeki64.md)|Położenie pliku Przenieś do podanej lokalizacji|
|[fsetpos](../c-runtime-library/reference/fsetpos.md)|Wskaźnik położenia zestaw strumienia|
|[_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)|Otwórz strumienia z udostępnianiem plików|
|[ftell, _ftelli64](../c-runtime-library/reference/ftell-ftelli64.md)|Pobierz bieżące położenie pliku|
|[fwrite](../c-runtime-library/reference/fwrite.md)|Zapisz elementy niesformatowanych danych do strumienia|
|[getc, getwc](../c-runtime-library/reference/getc-getwc.md)|Znak do odczytu strumienia (wersje makro **fgetc —** i **fgetwc —**)|
|[getchar, getwchar](../c-runtime-library/reference/getc-getwc.md)|Przeczytaj znak z **stdin** (wersje makro **fgetchar —** i **fgetwchar —**)|
|[_getmaxstdio](../c-runtime-library/reference/getmaxstdio.md)|Zwraca liczbę równocześnie otwarte pliki w poziomie we/wy strumienia.|
|[gets_s, _getws_s](../c-runtime-library/reference/gets-s-getws-s.md)|Odczytaj wiersz z **stdin**|
|[_getw](../c-runtime-library/reference/getw.md)|Odczyt danych binarnych **int** ze strumienia|
|[printf, _printf_l —, wprintf, _wprintf_l —](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md),[printf_s —, _printf_s_l —, wprintf_s —, _wprintf_s_l —](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|Zapis sformatowanych danych do **stdout**|
|[putc, putwc](../c-runtime-library/reference/putc-putwc.md)|Wpisz znak w strumieniu (wersje makro **fputc —** i **fputwc —**)|
|[putchar, putwchar](../c-runtime-library/reference/putc-putwc.md)|Wpisz znak do **stdout** (wersje makro **fputchar —** i **fputwchar —**)|
|[puts, _putws](../c-runtime-library/reference/puts-putws.md)|Zapisz wiersz do strumienia|
|[_putw](../c-runtime-library/reference/putw.md)|Zapisywania danych binarnych **int** do strumienia|
|[rewind](../c-runtime-library/reference/rewind.md)|Przenieś na początek strumienia położenie pliku|
|[_rmtmp](../c-runtime-library/reference/rmtmp.md)|Usuwanie plików tymczasowych utworzonych przez **tmpfile —**|
|[scanf, _scanf_l —, wscanf —, _wscanf_l —](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md),[scanf_s —, _scanf_s_l —, wscanf_s —, _wscanf_s_l —](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)|Odczyt sformatowanych danych z **stdin**|
|[setbuf](../c-runtime-library/reference/setbuf.md)|Buforowanie strumienia formantu|
|[_setmaxstdio](../c-runtime-library/reference/setmaxstdio.md)|Ustaw poziom maksymalna liczba równocześnie otwartych plików na we/wy strumienia.|
|[setvbuf](../c-runtime-library/reference/setvbuf.md)|Buforowanie strumienia kontroli i rozmiar buforu|
|[_snprintf —, _snwprintf —](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md), [_snprintf_s —, _snprintf_s_l —, _snwprintf_s —, _snwprintf_s_l —](../c-runtime-library/reference/snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md)|Zapisać sformatowanych danych o określonej długości ciągu|
|[_snscanf —, _snwscanf —](../c-runtime-library/reference/snscanf-snscanf-l-snwscanf-snwscanf-l.md), [_snscanf_s —, _snscanf_s_l —, _snwscanf_s —, _snwscanf_s_l —](../c-runtime-library/reference/snscanf-s-snscanf-s-l-snwscanf-s-snwscanf-s-l.md)|Odczyt sformatowanych danych o określonej długości ze strumienia wejściowego standardowa.|
|[sprintf, swprintf —](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md), [sprintf_s —, _sprintf_s_l —, swprintf_s —, _swprintf_s_l —](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|Zapis sformatowane dane do ciągu|
|[sscanf —, swscanf —](../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md), [sscanf_s —, _sscanf_s_l —, swscanf_s —, _swscanf_s_l —](../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)|Odczyt sformatowane dane z ciągu|
|[_tempnam —, _wtempnam —](../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)|Wygenerować tymczasowej nazwy pliku w podanej katalogu|
|[tmpfile —](../c-runtime-library/reference/tmpfile.md), [tmpfile_s —](../c-runtime-library/reference/tmpfile-s.md)|Utworzyć pliku tymczasowego|
|[tmpnam —, _wtmpnam —](../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md), [tmpnam_s —, _wtmpnam_s —](../c-runtime-library/reference/tmpnam-s-wtmpnam-s.md)|Wygenerować tymczasowej nazwy pliku|
|[ungetc, ungetwc](../c-runtime-library/reference/ungetc-ungetwc.md)|Znak wypychaną powrót do strumienia|
|[_vcprintf —, _vcwprintf —](../c-runtime-library/reference/vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md), [_vcprintf_s —, _vcprintf_s_l —, _vcwprintf_s —, _vcwprintf_s_l —](../c-runtime-library/reference/vcprintf-s-vcprintf-s-l-vcwprintf-s-vcwprintf-s-l.md)|Zapis sformatowanych danych do konsoli.|
|[vfprintf —, vfwprintf —](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md), [vfprintf_s —, _vfprintf_s_l —, vfwprintf_s —, _vfwprintf_s_l —](../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)|Zapisać sformatowanych danych do strumienia|
|[vprintf —, vwprintf —](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md), [vprintf_s —, _vprintf_s_l —, vwprintf_s —, _vwprintf_s_l —](../c-runtime-library/reference/vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md)|Zapis sformatowanych danych do **stdout**|
|[_vsnprintf —, _vsnwprintf —](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md), [vsnprintf_s —, _vsnprintf_s —, _vsnprintf_s_l —, _vsnwprintf_s —, _vsnwprintf_s_l —](../c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md)|Bufor zapisu sformatowanych danych o określonej długości|
|[vsprintf —, vswprintf —](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md), [vsprintf_s —, _vsprintf_s_l —, vswprintf_s —, _vswprintf_s_l —](../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)|Zapis sformatowanych danych do buforu|

 Po rozpoczęciu wykonywania programu kod uruchomienia automatycznie otwiera wiele strumieni: standardowe dane wejściowe (wskazywanego przez **stdin**), wyjścia standardowego (wskazywanego przez **stdout**) i błąd standardowy (wskazywanego przez **stderr**). Tych strumieni są przekierowywane do konsoli (klawiatury i ekranu), domyślnie. Użyj **freopen —** przekierować **stdin**, **stdout**, lub **stderr** pliku na dysku lub urządzeniu.

 Pliki otwierane przy użyciu procedury strumienia są buforowane domyślnie. **Stdout** i **stderr** funkcje są opróżniane zawsze, gdy są pełne, lub jeśli piszesz na urządzeniu znak po każdym wywołaniu biblioteki. Jeśli program nieprawidłowo kończy buforów danych wyjściowych może nie można opróżnić, co grozi utratą danych. Użyj **fflush —** lub **_flushall —** aby upewnić się, że buforu skojarzonych z określonym plikiem lub wszystkie otwarte buforów są opróżniane system operacyjny, który może buforować dane przed zapisaniem go na dysku. Funkcja commit-to-disk gwarantuje, że zawartości buforu opróżnionych nie zostaną utracone w przypadku awarii systemu.

 Istnieją dwa sposoby można przekazać zawartości buforu na dysku:

-   Połącz się z plikiem COMMODE. OBJ można ustawić flagi globalne zatwierdzania. Domyślne ustawienie flagi globalne to **n**, dla "nie-commit".

-   Ustaw wartość flagi trybu **c** z **fopen —** lub **_fdopen —**.

 Każdy plik w szczególności otwarty przy użyciu jednej **c** lub **n** flagi działa zgodnie z flagi, bez względu na stan flagi globalne commit/nie zatwierdzania.

 Jeśli program nie jawnie zamknąć strumienia, strumień jest zamknięty automatycznie, gdy program zakończenie. Jednak należy zamknąć strumienia po zakończeniu programu, jak liczba strumieni, które można otworzyć w tym samym czasie jest ograniczona. Zobacz [_setmaxstdio —](../c-runtime-library/reference/setmaxstdio.md) informacji na ten limit.

 Dane wejściowe można wykonać w danych wyjściowych bezpośrednio tylko za pomocą pośredniczące wywołania do **fflush —** lub do rozmieszczania plików funkcji (**fseek**, **fsetpos —**, lub **rewind**). Dane wyjściowe można wykonać dane wejściowe bez pośredniczące wywołania funkcji pozycjonowanie plik, jeśli operacja wejścia napotkał koniec pliku.

## <a name="see-also"></a>Zobacz też

[Dane wejściowe i wyjściowe](../c-runtime-library/input-and-output.md)<br/>
 [Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
