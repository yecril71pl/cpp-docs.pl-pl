---
title: Stream operacji We/Wy | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 9ab13141c573ad302528a09b74cb3a5e2aaa0382
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035231"
---
# <a name="stream-io"></a>We/Wy strumienia

Te funkcje, przetwarzanie danych w różnych rozmiarów i formatów, pojedyncze znaki do struktur dużych ilości danych. Zapewniają także buforowania, co może zwiększyć wydajność. Domyślny rozmiar buforu strumienia jest 4K. Te procedury wpływa na tylko buforów utworzonych przez procedury biblioteki wykonawczej i nie mają wpływu na buforów utworzonych przez system operacyjny.

## <a name="stream-io-routines"></a>Procedury Stream operacji We/Wy

|Procedura|Zastosowanie|
|-------------|---------|
|[clearerr —](../c-runtime-library/reference/clearerr.md), [clearerr_s —](../c-runtime-library/reference/clearerr-s.md)|Wskaźnik wyczyść błędu dla strumienia|
|[fclose —](../c-runtime-library/reference/fclose-fcloseall.md)|Zamknij strumień|
|[_fcloseall](../c-runtime-library/reference/fclose-fcloseall.md)|Zamknij wszystkie otwarte strumieni z wyjątkiem **stdin**, **stdout**, i **strumienia wyjściowego stderr**|
|[_fdopen —, wfdopen —](../c-runtime-library/reference/fdopen-wfdopen.md)|Kojarzenie strumienia z deskryptorem pliku otwartego pliku|
|[feof](../c-runtime-library/reference/feof.md)|Test na koniec pliku w usłudze stream|
|[ferror](../c-runtime-library/reference/ferror.md)|Test błędu dla strumienia|
|[fflush](../c-runtime-library/reference/fflush.md)|Zapisywanie strumienia do buforu lub urządzenie pamięci masowej|
|[fgetc, fgetwc](../c-runtime-library/reference/fgetc-fgetwc.md)|Odczyt znaku ze strumienia (wersje funkcji **getc —** i **getwc —**)|
|[_fgetchar, _fgetwchar](../c-runtime-library/reference/fgetc-fgetwc.md)|Odczyt znaku z **stdin** (wersje funkcji **getchar** i **getwchar —**)|
|[fgetpos](../c-runtime-library/reference/fgetpos.md)|Pobierz wskaźnik położenia strumienia|
|[fgets, fgetws](../c-runtime-library/reference/fgets-fgetws.md)|Ciąg Odczyt ze strumienia|
|[_fileno](../c-runtime-library/reference/fileno.md)|Pobieranie deskryptora pliku skojarzone z usługą stream|
|[_flushall](../c-runtime-library/reference/flushall.md)|Opróżnij wszystkie strumienie do buforu lub urządzenie pamięci masowej|
|[fopen —, _wfopen —](../c-runtime-library/reference/fopen-wfopen.md), [fopen_s —, _wfopen_s —](../c-runtime-library/reference/fopen-s-wfopen-s.md)|Otwieranie strumienia|
|[fprintf, _fprintf_l —, fwprintf —, _fwprintf_l —](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md), [fprintf_s —, _fprintf_s_l —, fwprintf_s —, _fwprintf_s_l —](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|Wpisz sformatowane dane do usługi stream|
|[fputc, fputwc](../c-runtime-library/reference/fputc-fputwc.md)|Wpisz znak w strumieniu (wersje funkcji **putc** i **putwc**)|
|[_fputchar, _fputwchar](../c-runtime-library/reference/fputc-fputwc.md)|Znak do zapisu **stdout** (wersje funkcji **putchar** i **putwchar**)|
|[fputs, fputws](../c-runtime-library/reference/fputs-fputws.md)|Zapisz ciąg do strumienia|
|[fread](../c-runtime-library/reference/fread.md)|Przeczytaj niesformatowanych danych ze strumienia|
|[freopen —, _wfreopen —](../c-runtime-library/reference/freopen-wfreopen.md), [freopen_s —, _wfreopen_s —](../c-runtime-library/reference/freopen-s-wfreopen-s.md)|Ponowne przypisywanie **pliku** wskaźnik strumienia do nowego pliku lub urządzenia|
|[fscanf —, fwscanf —](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md), [fscanf_s —, _fscanf_s_l —, fwscanf_s —, _fwscanf_s_l —](../c-runtime-library/reference/fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)|Odczyt sformatowanych danych ze strumienia|
|[fseek, _fseeki64](../c-runtime-library/reference/fseek-fseeki64.md)|Położenie pliku przenoszenia do podanej lokalizacji|
|[fsetpos](../c-runtime-library/reference/fsetpos.md)|Wskaźnik położenia zestaw strumienia|
|[_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)|Otwieranie strumienia z funkcją Udostępnianie plików|
|[ftell, _ftelli64](../c-runtime-library/reference/ftell-ftelli64.md)|Pobieranie bieżącej pozycji w pliku|
|[fwrite](../c-runtime-library/reference/fwrite.md)|Zapisuj elementy niesformatowanych danych do przesyłania strumieniowego|
|[getc, getwc](../c-runtime-library/reference/getc-getwc.md)|Odczyt znaku ze strumienia (wersje — makro **fgetc —** i **fgetwc —**)|
|[getchar, getwchar](../c-runtime-library/reference/getc-getwc.md)|Odczyt znaku z **stdin** (wersje — makro **fgetchar —** i **fgetwchar —**)|
|[_getmaxstdio](../c-runtime-library/reference/getmaxstdio.md)|Zwraca liczbę jednocześnie otwartych plików, w poziomie operacje We/Wy strumienia.|
|[gets_s, _getws_s](../c-runtime-library/reference/gets-s-getws-s.md)|Odczytaj wiersz z **stdin**|
|[_getw](../c-runtime-library/reference/getw.md)|Odczytaj plik binarny **int** ze strumienia|
|[printf, _printf_l —, wprintf, _wprintf_l —](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md),[printf_s, _printf_s_l —, wprintf_s —, _wprintf_s_l —](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|Wpisz sformatowane dane do **stdout**|
|[putc, putwc](../c-runtime-library/reference/putc-putwc.md)|Wpisz znak w strumieniu (wersje — makro **fputc** i **fputwc —**)|
|[putchar, putwchar](../c-runtime-library/reference/putc-putwc.md)|Znak do zapisu **stdout** (wersje — makro **fputchar —** i **fputwchar —**)|
|[puts, _putws](../c-runtime-library/reference/puts-putws.md)|Zapisać wiersza do strumienia|
|[_putw](../c-runtime-library/reference/putw.md)|Zapisywania danych binarnych **int** do strumienia|
|[rewind](../c-runtime-library/reference/rewind.md)|Przenieś położenie pliku do początku strumienia|
|[_rmtmp](../c-runtime-library/reference/rmtmp.md)|Usuwanie plików tymczasowych utworzonych przez **tmpfile —**|
|[scanf, _scanf_l —, wscanf, _wscanf_l —](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md),[scanf_s, _scanf_s_l —, wscanf_s —, _wscanf_s_l —](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)|Odczyt sformatowanych danych z **stdin**|
|[setbuf](../c-runtime-library/reference/setbuf.md)|Buforowanie strumienia kontroli|
|[_setmaxstdio](../c-runtime-library/reference/setmaxstdio.md)|Ustaw maksymalną liczbę plików jednocześnie otwarty na we/wy strumienia poziomu.|
|[setvbuf](../c-runtime-library/reference/setvbuf.md)|Buforowanie strumienia kontroli i rozmiar buforu|
|[_snprintf, _snwprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md), [_snprintf_s, _snprintf_s_l, _snwprintf_s, _snwprintf_s_l](../c-runtime-library/reference/snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md)|Wpisz sformatowane dane o określonej długości do ciągu|
|[_snscanf —, _snwscanf —](../c-runtime-library/reference/snscanf-snscanf-l-snwscanf-snwscanf-l.md), [_snscanf_s —, _snscanf_s_l —, _snwscanf_s —, _snwscanf_s_l —](../c-runtime-library/reference/snscanf-s-snscanf-s-l-snwscanf-s-snwscanf-s-l.md)|Odczyt sformatowanych danych o określonej długości ze standardowego strumienia wejściowego.|
|[sprintf, swprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md), [sprintf_s —, _sprintf_s_l —, swprintf_s —, _swprintf_s_l —](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|Wpisz sformatowane dane do ciągu|
|[sscanf —, swscanf —](../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md), [sscanf_s —, _sscanf_s_l —, swscanf_s —, _swscanf_s_l —](../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)|Odczyt sformatowanych danych z ciągu|
|[_tempnam —, _wtempnam —](../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)|Wygenerować tymczasowej nazwy pliku w danym katalogu|
|[tmpfile —](../c-runtime-library/reference/tmpfile.md), [tmpfile_s —](../c-runtime-library/reference/tmpfile-s.md)|Utworzyć pliku tymczasowego|
|[tmpnam —, _wtmpnam —](../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md), [tmpnam_s —, _wtmpnam_s —](../c-runtime-library/reference/tmpnam-s-wtmpnam-s.md)|Wygenerować tymczasowej nazwy pliku|
|[ungetc, ungetwc](../c-runtime-library/reference/ungetc-ungetwc.md)|Wypchnięcia znaków z powrotem do strumienia|
|[_vcprintf —, _vcwprintf —](../c-runtime-library/reference/vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md), [_vcprintf_s —, _vcprintf_s_l —, _vcwprintf_s —, _vcwprintf_s_l —](../c-runtime-library/reference/vcprintf-s-vcprintf-s-l-vcwprintf-s-vcwprintf-s-l.md)|Wpisz sformatowane dane do konsoli.|
|[vfprintf —, vfwprintf —](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md), [vfprintf_s —, _vfprintf_s_l —, vfwprintf_s —, _vfwprintf_s_l —](../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)|Wpisz sformatowane dane do usługi stream|
|[vprintf —, vwprintf —](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md), [vprintf_s —, _vprintf_s_l —, vwprintf_s —, _vwprintf_s_l —](../c-runtime-library/reference/vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md)|Wpisz sformatowane dane do **stdout**|
|[_vsnprintf —, _vsnwprintf —](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md), [vsnprintf_s —, _vsnprintf_s —, _vsnprintf_s_l —, _vsnwprintf_s —, _vsnwprintf_s_l —](../c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md)|Wpisz sformatowane dane o określonej długości do buforu|
|[vsprintf —, vswprintf —](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md), [vsprintf_s —, _vsprintf_s_l —, vswprintf_s —, _vswprintf_s_l —](../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)|Wpisz sformatowane dane do usługi buffer|

Po rozpoczęciu wykonywania programu kod uruchamiający automatycznie otwiera kilka strumienie: standardowe dane wejściowe (wskazywany przez **stdin**), wyjścia standardowego (wskazywany przez **stdout**) i błąd standardowy (wskazywany przez **stderr**). Te strumienie nastąpi przekierowanie do konsoli (klawiatury i ekran) domyślnie. Użyj **freopen —** przekierowywanie **stdin**, **stdout**, lub **stderr** pliku na dysku lub na urządzeniu.

Pliki otwierane przy użyciu procedury strumienia są buforowane domyślnie. **Stdout** i **stderr** funkcje zostały przesłane, ilekroć są one pełne, lub jeśli piszesz z urządzeniem znaku po każdym wywołaniu biblioteki. Jeśli program zakończy się nieprawidłowo, buforów danych wyjściowych może nie można opróżnić, co spowoduje utratę danych. Użyj **fflush —** lub **_flushall —** zapewnienie buforu skojarzone z określonym plikiem lub wszystkie otwarte bufory zostały przesłane do systemu operacyjnego, który może buforować dane przed zapisem go na dysku. Funkcja commit-to-disk gwarantuje, że zawartość buforu opróżnionych nie zostaną utracone w przypadku awarii systemu.

Istnieją dwa sposoby, aby zatwierdzić zawartości buforu na dysku:

- Połącz się z plikiem COMMODE. OBJ, aby ustawić globalną flagę zatwierdzania. Domyślne ustawienie flagi globalne to **n**, aby uzyskać "no-commit".

- Ustaw flagę trybu **c** z **fopen —** lub **_fdopen —**.

Każdy plik jest otwarty specjalnie z oboma **c** lub **n** flagi zachowuje się zgodnie z flagą, bez względu na stan globalnej flagi zatwierdzania/nie-commit.

Jeśli program nie zamykaj jawnie strumienia, strumień zostanie zamknięty automatycznie, gdy program kończy. Jednak należy zamknąć strumień po zakończeniu program, dzięki niemu jako liczbę strumieni, które mogą być otwarte w tym samym czasie jest ograniczona. Zobacz [_setmaxstdio —](../c-runtime-library/reference/setmaxstdio.md) uzyskać informacji na temat tego limitu.

Dane wejściowe można wykonać w danych wyjściowych bezpośrednio tylko interwencyjnego wywołania **fflush —** lub funkcji położenia pliku (**fseek**, **fsetpos**, lub **rewind**). Dane wyjściowe można wykonać dane wejściowe bez interwencyjnego wywołania funkcji położenia pliku, jeśli operacja wprowadzania napotka koniec pliku.

## <a name="see-also"></a>Zobacz też

[Dane wejściowe i wyjściowe](../c-runtime-library/input-and-output.md)<br/>
[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
