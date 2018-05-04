---
title: Procedury debugowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/10/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- c.debug
dev_langs:
- C++
helpviewer_keywords:
- debugging [CRT], using macros
- macros, debugging with
- debug routines
- debug macros
- debugging [CRT], runtime routines
ms.assetid: cb4d2664-10f3-42f7-a516-595558075471
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4efef4c7dfb907120778390874a5e56222889350
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="debug-routines"></a>Procedury debugowania

Wersja do debugowania biblioteki C runtime udostępnia wiele usługi diagnostyczne ułatwić debugowania programów, które umożliwiają deweloperom:

- Krok bezpośrednio w czasie wykonywania funkcji podczas debugowania

- Usuń potwierdzeń, błędy i wyjątki

- Alokacje sterty śledzenia i zapobiec przecieki pamięci

- Komunikaty debugowania raportu do użytkownika

## <a name="debug-versions-of-the-c-runtime-library-routines"></a>Wersja procedury biblioteki języka C środowiska uruchomieniowego debugowania

Aby użyć tych procedur [_DEBUG](../c-runtime-library/debug.md) flagi musi być zdefiniowany. Wszystkie te procedury nie rób w sprzedaży detalicznej kompilacji aplikacji. Aby uzyskać więcej informacji na temat sposobu użycia nowego procedur debugowania, zobacz [techniki testowania CRT](/visualstudio/debugger/crt-debugging-techniques).

|Procedura|Zastosowanie|
|-------------|---------|
|[_ASSERT](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)|Oszacować wyrażenia i generuje raport debugowania, jeśli wynik to FAŁSZ|
|[_ASSERTE —](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)|Podobnie jak **_ASSERT**, ale zawiera wyrażenie, które nie powiodło się w generowanym raporcie|
|[_CrtCheckMemory](../c-runtime-library/reference/crtcheckmemory.md)|Potwierdzenia integralności bloki pamięci przydzielony na stosie debugowania|
|[_CrtDbgBreak](../c-runtime-library/reference/crtdbgbreak.md)|Ustawia punkt przerwania.|
|[_CrtDbgReport, _CrtDbgReportW](../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)|Generowanie raportu debugowania z następującym komunikatem użytkownika i wysłać raport do trzech miejsc docelowych możliwe|
|[_CrtDoForAllClientObjects](../c-runtime-library/reference/crtdoforallclientobjects.md)|Wywołanie funkcji aplikacji dla wszystkich **_client_block —** typy na stosie|
|[_CrtDumpMemoryLeaks](../c-runtime-library/reference/crtdumpmemoryleaks.md)|Wszystkie bloki pamięci w stosie debugowania zrzutu, gdy wystąpił wyciek pamięci znaczących|
|[_CrtIsMemoryBlock](../c-runtime-library/reference/crtismemoryblock.md)|Sprawdź, czy blok pamięci określony znajduje się w lokalnej sterty i ma identyfikator typu bloku sterty debugowania prawidłowy|
|[_CrtIsValidHeapPointer](../c-runtime-library/reference/crtisvalidheappointer.md)|Sprawdza, czy określony wskaźnika w lokalnej sterty|
|[_CrtIsValidPointer](../c-runtime-library/reference/crtisvalidpointer.md)|Sprawdź poprawność do odczytywania i zapisywania zakresu określonego pamięci|
|[_CrtMemCheckpoint](../c-runtime-library/reference/crtmemcheckpoint.md)|Uzyskaj bieżącego stanu sterty debugowania i zapisz go w aplikacji dostarczone przez **_crtmemstate —** — struktura|
|[_CrtMemDifference](../c-runtime-library/reference/crtmemdifference.md)|Porównać dwa stany pamięci w przypadku istotnych różnic, a następnie zwracają wyniki|
|[_CrtMemDumpAllObjectsSince](../c-runtime-library/reference/crtmemdumpallobjectssince.md)|Informacje dotyczące obiektów na stercie, ponieważ został przełączony do określonego punktu kontrolnego lub od początku wykonywania programu zrzutu|
|[_CrtMemDumpStatistics](../c-runtime-library/reference/crtmemdumpstatistics.md)|Informacje o nagłówku debugowania pamięci określonego stanu użytkownika i przechowywane w formie zrzutu|
|[_CrtReportBlockType](../c-runtime-library/reference/crtreportblocktype.md)|Zwraca blok typ/podtyp skojarzone ze wskaźnikiem bloku sterty debugowania danego.|
|[_CrtSetAllocHook](../c-runtime-library/reference/crtsetallochook.md)|Zainstalować funkcję alokacji zdefiniowanymi przez klienta przez Przechwytywanie go do procesu alokacji pamięci środowiska wykonawczego debugowania C|
|[_CrtSetBreakAlloc](../c-runtime-library/reference/crtsetbreakalloc.md)|Ustaw punkt przerwania na numer zamówienia alokacji określonego obiektu|
|[_CrtSetDbgFlag](../c-runtime-library/reference/crtsetdbgflag.md)|Pobieranie lub zmodyfikuj stan **_crtdbgflag —** flagę, aby kontrolować sposób przydzielania menedżera sterty debugowania|
|[_CrtSetDumpClient](../c-runtime-library/reference/crtsetdumpclient.md)|Zainstaluj funkcję zdefiniowanym przez aplikację, która jest wywoływana za każdym razem, gdy wywoływana jest funkcja zrzutu debugowania zrzutu **_client_block —** wpisz bloki pamięci|
|[_CrtSetReportFile](../c-runtime-library/reference/crtsetreportfile.md)|Określenie pliku lub strumienia do użycia jako miejsce docelowe dla typu określonego raportu przez **_crtdbgreport —**|
|[_CrtSetReportHook](../c-runtime-library/reference/crtsetreporthook.md)|Zainstalować funkcję raportowania zdefiniowane przez klienta przez Przechwytywanie go do debugowania wykonawcze języka C raportowania procesu|
|[_CrtSetReportHook2, _CrtSetReportHookW2](../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md)|Instaluje lub odinstalowuje zdefiniowane przez klienta funkcji raportowania przez Przechwytywanie go do debugowania wykonawcze języka C raportowania procesu.|
|[_CrtSetReportMode](../c-runtime-library/reference/crtsetreportmode.md)|Określ ogólne przeznaczenie dla typu określonego raportu generowane przez **_crtdbgreport —**|
|[_RPT&AMP;#91;0,1,2,3,4&AMP;#93;](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md)|Śledzenie postępu aplikacji przez Generowanie raportu debugowania przez wywołanie metody **_crtdbgreport —** z ciągu formatu i zmienną liczbę argumentów. Udostępnia plików i wierszy numer informacji źródłowych.|
|[_RPTF&AMP;#91;0,1,2,3,4&AMP;#93;](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md)|Podobnie jak **_rptn —** makra, ale zapewnia numeru nazwy i wiersza pliku źródłowego którego pochodzi żądanie raportu|
|[_calloc_dbg](../c-runtime-library/reference/calloc-dbg.md)|Przydziel określoną liczbę bloków pamięci na stercie z dodatkowym miejscem dla nagłówka debugowania i zastąpić buforów|
|[_expand_dbg](../c-runtime-library/reference/expand-dbg.md)|Zmień rozmiar określony blok pamięci na stercie przez rozszerzanie lub zawierania bloku|
|[_free_dbg](../c-runtime-library/reference/free-dbg.md)|Zwolnij bloku pamięci na stercie|
|[_fullpath_dbg, _wfullpath_dbg](../c-runtime-library/reference/fullpath-dbg-wfullpath-dbg.md)|Utwórz nazwę określoną ścieżką względną ścieżką bezwzględną ani Pełna nazwa, za pomocą [_malloc_dbg —](../c-runtime-library/reference/malloc-dbg.md) można przydzielić pamięci.|[System::IO::File:: Utwórz](https://msdn.microsoft.com/en-us/library/system.io.file.create.aspx)|
|[_getcwd_dbg, _wgetcwd_dbg](../c-runtime-library/reference/getcwd-dbg-wgetcwd-dbg.md)|Pobierz bieżący katalog roboczy za pomocą [_malloc_dbg —](../c-runtime-library/reference/malloc-dbg.md) można przydzielić pamięci.|
|[_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md)|Przydzielić bloku pamięci sterty z dodatkowym miejscem dla nagłówka debugowania i zastąpić buforów|
|[_msize_dbg](../c-runtime-library/reference/msize-dbg.md)|Oblicz rozmiar bloku pamięci na stercie|
|[_realloc_dbg](../c-runtime-library/reference/realloc-dbg.md)|Ponowne przydzielenie określony blok pamięci na stercie przez przeniesienie lub zmiana rozmiaru bloku|
|[_strdup_dbg, _wcsdup_dbg](../c-runtime-library/reference/strdup-dbg-wcsdup-dbg.md)|Duplikaty ciągu, przy użyciu [_malloc_dbg —](../c-runtime-library/reference/malloc-dbg.md) można przydzielić pamięci.|
|[_tempnam_dbg, _wtempnam_dbg](../c-runtime-library/reference/tempnam-dbg-wtempnam-dbg.md)|Generuj służy do tworzenia plików tymczasowych, przy użyciu nazwy [_malloc_dbg —](../c-runtime-library/reference/malloc-dbg.md) można przydzielić pamięci.|

## <a name="c-runtime-routines-that-are-not-available-in-source-code-form"></a>Procedury języka C środowiska uruchomieniowego, które nie są dostępne w źródła w postaci kodu

Debuger może służyć do kroków kodu źródłowego dla większości procedury środowiska wykonawczego języka C, podczas gdy proces debugowania. Jednak firma Microsoft uzna innej technologii być zastrzeżonych i, w związku z tym nie ma kodu źródłowego dla podzestawów tych procedur. Większość tych procedur należy do obsługi wyjątków lub grup przetwarzania liczb zmiennoprzecinkowych, ale kilku innych są uwzględniane również. W poniższej tabeli wymieniono te procedury.

||||
|-|-|-|
|[ACOS](../c-runtime-library/reference/acos-acosf-acosl.md)|[ACOSH](../c-runtime-library/reference/acosh-acoshf-acoshl.md)|[ASIN](../c-runtime-library/reference/asin-asinf-asinl.md)|
|[ASINH](../c-runtime-library/reference/asinh-asinhf-asinhl.md)|[ATAN, funkcja atan2](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[atanh](../c-runtime-library/reference/atanh-atanhf-atanhl.md)|
|[Funkcje Bessela](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|[_cabs](../c-runtime-library/reference/cabs.md)|[ceil](../c-runtime-library/reference/ceil-ceilf-ceill.md)|
|[_chgsign](../c-runtime-library/reference/chgsign-chgsignf-chgsignl.md)|[_clear87, _clearfp](../c-runtime-library/reference/clear87-clearfp.md)|[_control87 —, _controlfp —](../c-runtime-library/reference/control87-controlfp-control87-2.md)|
|[copysign —](../c-runtime-library/reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)|[COS](../c-runtime-library/reference/cos-cosf-cosl.md)|[COSH](../c-runtime-library/reference/cosh-coshf-coshl.md)|
|[EXP](../c-runtime-library/reference/exp-expf.md)|[fabs —](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|[_finite](../c-runtime-library/reference/finite-finitef.md)|
|[FLOOR](../c-runtime-library/reference/floor-floorf-floorl.md)|[fmod —](../c-runtime-library/reference/fmod-fmodf.md)|[_fpclass](../c-runtime-library/reference/fpclass-fpclassf.md)|
|[_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md)|[_fpreset](../c-runtime-library/reference/fpreset.md)|[frexp](../c-runtime-library/reference/frexp.md)|
|[_hypot](../c-runtime-library/reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md)|[_isnan —](../c-runtime-library/reference/isnan-isnan-isnanf.md)|[ldexp](../c-runtime-library/reference/ldexp.md)|
|[log](../c-runtime-library/reference/log-logf-log10-log10f.md)|[_logb —](../c-runtime-library/reference/logb-logbf-logbl-logb-logbf.md)|[log10](../c-runtime-library/reference/log-logf-log10-log10f.md)|
|[longjmp](../c-runtime-library/reference/longjmp.md)|[_matherr](../c-runtime-library/reference/matherr.md)|[modf](../c-runtime-library/reference/modf-modff-modfl.md)|
|[_nextafter](../c-runtime-library/reference/nextafter-functions.md)|[Pow](../c-runtime-library/reference/pow-powf-powl.md)|[printf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|
|[printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|[_scalb](../c-runtime-library/reference/scalb.md)|[scanf_s](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)|
|[scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)|[setjmp](../c-runtime-library/reference/setjmp.md)|[SIN](../c-runtime-library/reference/sin-sinf-sinl.md)|
|[SINH](../c-runtime-library/reference/sinh-sinhf-sinhl.md)|[sqrt](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|[_status87 —, _statusfp —](../c-runtime-library/reference/status87-statusfp-statusfp2.md)|
|[tan](../c-runtime-library/reference/tan-tanf-tanl.md)|[TANH](../c-runtime-library/reference/tanh-tanhf-tanhl.md)||

Mimo że kod źródłowy jest dostępny dla większości **printf** i **scanf** procedury, należy wywoływana wewnętrznie do innej procedury, które źródła nie podano kodu.

## <a name="routines-that-behave-differently-in-a-debug-build-of-an-application"></a>Tworzenie procedury, które zachowują się inaczej w przypadku debugowania aplikacji

Niektóre funkcje wykonawcze języka C i C++ operatory zachowywać się inaczej, gdy wywoływana z kompilacji debugowania aplikacji. (Należy pamiętać, że kompilację debugowania aplikacji może odbywać się albo definiując `_DEBUG` flaga lub przez łączenie z wersja biblioteki wykonawczej języka C do debugowania.) Różnice funkcjonalne zwykle składają się z dodatkowych funkcji lub informacji dostarczonych przez procedury do obsługi debugowania procesu. W poniższej tabeli wymieniono te procedury.

|||
|-|-|
|C [przerwać](../c-runtime-library/reference/abort.md) procedury|C++ [usunąć](../cpp/delete-operator-cpp.md) — operator|
|C [assert](../c-runtime-library/reference/assert-macro-assert-wassert.md) procedury|C++ [nowe](../cpp/new-operator-cpp.md) — operator|

## <a name="see-also"></a>Zobacz także

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Sprawdzanie błędów czasu wykonywania](../c-runtime-library/run-time-error-checking.md)<br/>
