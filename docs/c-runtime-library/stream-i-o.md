---
title: We/Wy strumienia
ms.date: 11/04/2016
helpviewer_keywords:
- I/O routines, stream I/O
- I/O [CRT], stream
- stream I/O
ms.assetid: dc7874d3-a91b-456a-9015-4748bb358217
ms.openlocfilehash: 8bff3cd74dfe4b1e3aa749ec28a361dd4a09c2f7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231250"
---
# <a name="stream-io"></a>We/Wy strumienia

Te funkcje przetwarzają dane w różnych rozmiarach i formatach, od pojedynczych znaków do dużych struktur danych. Zapewniają również buforowanie, które może poprawić wydajność. Domyślny rozmiar buforu strumienia to 4K. Procedury te mają wpływ tylko na bufory utworzone przez procedury biblioteki wykonawczej i nie mają wpływu na bufory utworzone przez system operacyjny.

## <a name="stream-io-routines"></a>Procedury we/wy strumienia

|Procedura|Zastosowanie|
|-------------|---------|
|[clearerr](../c-runtime-library/reference/clearerr.md), [clearerr_s](../c-runtime-library/reference/clearerr-s.md)|Wyczyść wskaźnik błędu dla usługi Stream|
|[fclose](../c-runtime-library/reference/fclose-fcloseall.md)|Zamknij strumień|
|[_fcloseall](../c-runtime-library/reference/fclose-fcloseall.md)|Zamknij wszystkie otwarte strumienie z wyjątkiem **stdin**, **stdout**i **stderr**|
|[_fdopen, wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)|Skojarz strumień z deskryptorem pliku otwartego pliku|
|[feof](../c-runtime-library/reference/feof.md)|Testuj pod kątem końca pliku w strumieniu|
|[ferror](../c-runtime-library/reference/ferror.md)|Testuj pod kątem błędu w strumieniu|
|[fflush](../c-runtime-library/reference/fflush.md)|Opróżnianie strumienia do buforu lub urządzenia magazynującego|
|[fgetc, fgetwc](../c-runtime-library/reference/fgetc-fgetwc.md)|Odczyt znaku ze strumienia (wersje funkcji **getc —** i **getwc**)|
|[_fgetchar, _fgetwchar](../c-runtime-library/reference/fgetc-fgetwc.md)|Odczytaj znak z **stdin** (wersje funkcji **GetChar** i **getwchar**)|
|[fgetpos](../c-runtime-library/reference/fgetpos.md)|Pobierz wskaźnik pozycji strumienia|
|[fgets, fgetws](../c-runtime-library/reference/fgets-fgetws.md)|Odczytaj ciąg ze strumienia|
|[_fileno](../c-runtime-library/reference/fileno.md)|Pobierz deskryptor pliku skojarzony ze strumieniem|
|[_flushall](../c-runtime-library/reference/flushall.md)|Opróżnianie wszystkich strumieni do bufora lub urządzenia magazynującego|
|[fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md), [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)|Otwórz strumień|
|[fprintf —, _fprintf_l, fwprintf, _fwprintf_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md), [fprintf_s, _fprintf_s_l, fwprintf_s, _fwprintf_s_l](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|Zapisz sformatowane dane do strumienia|
|[fputc, fputwc](../c-runtime-library/reference/fputc-fputwc.md)|Napisz znak do strumienia (wersje funkcji **putc** i **putwc**)|
|[_fputchar, _fputwchar](../c-runtime-library/reference/fputc-fputwc.md)|Napisz znak do **stdout** (wersje funkcji **putchar** i **putwchar**)|
|[fputs, fputws](../c-runtime-library/reference/fputs-fputws.md)|Napisz ciąg do strumienia|
|[fread](../c-runtime-library/reference/fread.md)|Odczytaj niesformatowane dane ze strumienia|
|[freopen, _wfreopen](../c-runtime-library/reference/freopen-wfreopen.md), [freopen_s, _wfreopen_s](../c-runtime-library/reference/freopen-s-wfreopen-s.md)|Ponownie Przypisz wskaźnik strumienia **pliku** do nowego pliku lub urządzenia|
|[fscanf, fwscanf](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md), [fscanf_s, _fscanf_s_l, fwscanf_s _fwscanf_s_l](../c-runtime-library/reference/fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)|Odczytaj sformatowane dane ze strumienia|
|[fseek, _fseeki64](../c-runtime-library/reference/fseek-fseeki64.md)|Przenieś położenie pliku do danej lokalizacji|
|[fsetpos](../c-runtime-library/reference/fsetpos.md)|Ustaw wskaźnik położenia strumienia|
|[_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)|Otwieranie strumienia przy użyciu udostępniania plików|
|[ftell, _ftelli64](../c-runtime-library/reference/ftell-ftelli64.md)|Pobierz bieżące położenie pliku|
|[fwrite](../c-runtime-library/reference/fwrite.md)|Zapisuj niesformatowane elementy danych do strumienia|
|[getc, getwc](../c-runtime-library/reference/getc-getwc.md)|Odczytaj znak ze strumienia (wersje makr **fgetc** i **fgetwc**)|
|[getchar, getwchar](../c-runtime-library/reference/getc-getwc.md)|Odczytaj znak z **stdin** (wersje makr **fgetchar** i **fgetwchar**)|
|[_getmaxstdio](../c-runtime-library/reference/getmaxstdio.md)|Zwraca liczbę jednocześnie otwartych plików dozwolonych na poziomie strumienia we/wy.|
|[gets_s, _getws_s](../c-runtime-library/reference/gets-s-getws-s.md)|Odczytaj wiersz od **stdin**|
|[_getw](../c-runtime-library/reference/getw.md)|Odczytaj **`int`** dane binarne ze strumienia|
|[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md),[printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|Zapisz sformatowane dane do **stdout**|
|[putc, putwc](../c-runtime-library/reference/putc-putwc.md)|Pisanie znaku w strumieniu (wersje makr **fputc** i **fputwc**)|
|[putchar, putwchar](../c-runtime-library/reference/putc-putwc.md)|Napisz znak do **stdout** (wersje makr **fputchar** i **fputwchar**)|
|[puts, _putws](../c-runtime-library/reference/puts-putws.md)|Zapisz wiersz do strumienia|
|[_putw](../c-runtime-library/reference/putw.md)|Zapisz dane binarne **`int`** do strumienia|
|[przewijanie](../c-runtime-library/reference/rewind.md)|Przenieś położenie pliku do początku strumienia|
|[_rmtmp](../c-runtime-library/reference/rmtmp.md)|Usuń pliki tymczasowe utworzone przez **tmpfile**|
|[scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md),[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)|Odczytywanie sformatowanych danych z **stdin**|
|[setbuf](../c-runtime-library/reference/setbuf.md)|Buforowanie strumienia kontroli|
|[_setmaxstdio](../c-runtime-library/reference/setmaxstdio.md)|Ustaw maksymalną liczbę jednocześnie otwartych plików na poziomie strumienia we/wy.|
|[setvbuf](../c-runtime-library/reference/setvbuf.md)|Buforowanie strumienia kontroli i rozmiar buforu|
|[_snprintf, _snwprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md), [_snprintf_s, _snprintf_s_l, _snwprintf_s](../c-runtime-library/reference/snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md) _snwprintf_s_l|Zapisz sformatowane dane o określonej długości do ciągu|
|[_snscanf, _snwscanf](../c-runtime-library/reference/snscanf-snscanf-l-snwscanf-snwscanf-l.md), [_snscanf_s, _snscanf_s_l, _snwscanf_s](../c-runtime-library/reference/snscanf-s-snscanf-s-l-snwscanf-s-snwscanf-s-l.md) _snwscanf_s_l|Odczytaj sformatowane dane o określonej długości ze standardowego strumienia wejściowego.|
|[sprintf —, swprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md), [sprintf_s, _sprintf_s_l, swprintf_s _swprintf_s_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|Zapisz sformatowane dane do ciągu|
|[sscanf, swscanf](../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md), [sscanf_s, _sscanf_s_l, swscanf_s _swscanf_s_l](../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)|Odczytaj sformatowane dane z ciągu|
|[_tempnam, _wtempnam](../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)|Generuj tymczasową nazwę pliku w podanym katalogu|
|[tmpfile](../c-runtime-library/reference/tmpfile.md), [tmpfile_s](../c-runtime-library/reference/tmpfile-s.md)|Utwórz plik tymczasowy|
|[tmpnam, _wtmpnam](../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md), [tmpnam_s, _wtmpnam_s](../c-runtime-library/reference/tmpnam-s-wtmpnam-s.md)|Generuj tymczasową nazwę pliku|
|[ungetc, ungetwc](../c-runtime-library/reference/ungetc-ungetwc.md)|Wypchnij znak z powrotem do strumienia|
|[_vcprintf, _vcwprintf](../c-runtime-library/reference/vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md), [_vcprintf_s, _vcprintf_s_l, _vcwprintf_s](../c-runtime-library/reference/vcprintf-s-vcprintf-s-l-vcwprintf-s-vcwprintf-s-l.md) _vcwprintf_s_l|Zapisz sformatowane dane w konsoli programu.|
|[vfprintf, vfwprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md), [vfprintf_s, _vfprintf_s_l, vfwprintf_s _vfwprintf_s_l](../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)|Zapisz sformatowane dane do strumienia|
|[vprintf —, vwprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md), [vprintf_s, _vprintf_s_l, vwprintf_s _vwprintf_s_l](../c-runtime-library/reference/vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md)|Zapisz sformatowane dane do **stdout**|
|[_vsnprintf, _vsnwprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md), [vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l](../c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md)|Zapisz sformatowane dane o określonej długości w buforze|
|[vsprintf, vswprintf](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md), [vsprintf_s, _vsprintf_s_l, vswprintf_s _vswprintf_s_l](../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)|Zapisz sformatowane dane w buforze|

Gdy program rozpoczyna wykonywanie, kod uruchamiania automatycznie otwiera kilka strumieni: standardowe dane wejściowe (wskazywane przez **stdin**), standardowe wyjście (wskazywane przez **stdout**) i błąd standardowy (wskazywany przez **stderr**). Te strumienie są domyślnie kierowane do konsoli (klawiatury i ekranu). Użyj **freopen** , aby przekierować **stdin**, **stdout**lub **stderr** do pliku dysku lub urządzenia.

Pliki otwierane przy użyciu procedur przesyłania strumieniowego są domyślnie buforowane. Funkcje **stdout** i **stderr** są opróżniane za każdym razem, gdy są pełne lub, jeśli piszesz na znakowe urządzenie, po każdym wywołaniu biblioteki. Jeśli program kończy się nieprawidłowo, bufory wyjściowe nie mogą być opróżniane, co spowodowało utratę danych. Użyj **fflush** lub **_flushall** , aby upewnić się, że bufor skojarzony z określonym plikiem lub wszystkie otwarte bufory są opróżniane do systemu operacyjnego, który może buforować dane przed zapisaniem go na dysku. Funkcja Zatwierdź do dysku gwarantuje, że opróżniona zawartość buforu nie zostanie utracona w przypadku awarii systemu.

Istnieją dwa sposoby zatwierdzania zawartości buforu na dysk:

- Połącz z plikiem. OBJ, aby ustawić globalną flagę zatwierdzania. Domyślnym ustawieniem flagi globalnej jest **n**dla opcji "No-Commit".

- Ustaw flagę Mode na **c** z **fopen** lub **_fdopen**.

Każdy plik otwarty z flagą **c** lub **n** zachowuje się zgodnie z flagą, niezależnie od stanu flagi globalnego zatwierdzenia/bez zatwierdzania.

Jeśli w programie nie zamknięto jawnie strumienia, strumień jest automatycznie zamykany po zakończeniu działania programu. Należy jednak zamknąć strumień, gdy program go zakończy, ponieważ liczba strumieni, które mogą być otwarte w tym samym czasie, jest ograniczona. Aby uzyskać informacje dotyczące tego limitu, zobacz [_setmaxstdio](../c-runtime-library/reference/setmaxstdio.md) .

Dane wejściowe mogą być bezpośrednio zgodne z wywołaniem wywołującym **fflush** lub funkcją pozycjonowania plików (**fseek**, **fsetpos**lub **przewijania do tyłu**). Dane wyjściowe mogą podążać za danymi wejściowymi bez wywołującego wywołania funkcji umieszczania plików, jeśli operacja wejściowa napotka koniec pliku.

## <a name="see-also"></a>Zobacz także

[Wejście i wyjście](../c-runtime-library/input-and-output.md)<br/>
[Procedury środowiska uruchomieniowego języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
