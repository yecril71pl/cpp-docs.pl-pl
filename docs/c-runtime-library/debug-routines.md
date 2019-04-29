---
title: Procedury debugowania
ms.date: 04/10/2018
f1_keywords:
- c.debug
helpviewer_keywords:
- debugging [CRT], using macros
- macros, debugging with
- debug routines
- debug macros
- debugging [CRT], runtime routines
ms.assetid: cb4d2664-10f3-42f7-a516-595558075471
ms.openlocfilehash: e1281b578435086dc7de04c7962145c2b265277a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62344450"
---
# <a name="debug-routines"></a>Procedury debugowania

Wersja do debugowania biblioteki środowiska uruchomieniowego C dostarcza wiele usługi diagnostyczne, łatwiejsze debugowanie programów, które umożliwiają deweloperom:

- Krok po kroku bezpośrednio do funkcji wykonawczej podczas debugowania

- Rozwiąż potwierdzeń, błędy i wyjątki

- Śledzenie Alokacje sterty i zapobiec przeciekom pamięci

- Raport debugowania wiadomości do użytkownika

## <a name="debug-versions-of-the-c-runtime-library-routines"></a>Debuguj wersje procedury biblioteki środowiska uruchomieniowego języka C

Aby użyć tych procedur [_DEBUG](../c-runtime-library/debug.md) flagi musi być zdefiniowany. Wszystkie z tych procedur nie, nic robić, w przypadku kompilacji detalicznej aplikacji. Aby uzyskać więcej informacji na temat korzystania z nowej procedury debugowania, zobacz [techniki testowania CRT](/visualstudio/debugger/crt-debugging-techniques).

|Procedura|Zastosowanie|
|-------------|---------|
|[_ASSERT](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)|Ocena wyrażenia i generuje raport debugowania, jeśli wynik to FALSE|
|[_ASSERTE](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)|Podobnie jak **_ASSERT**, ale zawiera wyrażenie zakończonych niepowodzeniem w wygenerowanym raporcie|
|[_CrtCheckMemory](../c-runtime-library/reference/crtcheckmemory.md)|Potwierdzenia integralności bloki pamięci przydzielane w stercie debugowania|
|[_CrtDbgBreak](../c-runtime-library/reference/crtdbgbreak.md)|Ustawia punkt przerwania.|
|[_CrtDbgReport, _CrtDbgReportW](../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)|Generowanie raportu debugowania z komunikatem o użytkownika i wysłać raport do trzech możliwych miejsc docelowych|
|[_CrtDoForAllClientObjects](../c-runtime-library/reference/crtdoforallclientobjects.md)|Wywołania funkcji dostarczonych przez aplikację dla wszystkich **_CLIENT_BLOCK** typy na stosie|
|[_CrtDumpMemoryLeaks](../c-runtime-library/reference/crtdumpmemoryleaks.md)|Wszystkie bloki pamięci w stercie debugowania zrzutu, gdy wystąpił przeciek pamięci znaczące|
|[_CrtIsMemoryBlock](../c-runtime-library/reference/crtismemoryblock.md)|Sprawdź, czy blok pamięci określonej znajduje się w obrębie lokalnej sterty i ma identyfikator typu bloku sterty debugowania prawidłowe|
|[_CrtIsValidHeapPointer](../c-runtime-library/reference/crtisvalidheappointer.md)|Sprawdza, czy określony wskaźnik myszy znajduje się w lokalnej sterty|
|[_CrtIsValidPointer](../c-runtime-library/reference/crtisvalidpointer.md)|Sprawdź, czy zakres określony pamięci jest prawidłowy dla odczytu i zapisu|
|[_CrtMemCheckpoint](../c-runtime-library/reference/crtmemcheckpoint.md)|Uzyskaj bieżący stan sterty debugowania i zapisz go w dostarczonej przez aplikację **_CrtMemState** struktury|
|[_CrtMemDifference](../c-runtime-library/reference/crtmemdifference.md)|Porównaj dwa stany pamięci między nimi istotne różnice i zwracają wyniki|
|[_CrtMemDumpAllObjectsSince](../c-runtime-library/reference/crtmemdumpallobjectssince.md)|Zrzuć informacje o obiektach sterty, ponieważ został przełączony do określonego punktu kontrolnego lub od początku wykonywania programu|
|[_CrtMemDumpStatistics](../c-runtime-library/reference/crtmemdumpstatistics.md)|Zrzutu informacji nagłówka debugowania stanu pamięci określonej w formie czytelny dla użytkownika|
|[_CrtReportBlockType](../c-runtime-library/reference/crtreportblocktype.md)|Zwraca typ bloku/podtyp skojarzone ze wskaźnikiem bloku sterty debugowania danego.|
|[_CrtSetAllocHook](../c-runtime-library/reference/crtsetallochook.md)|Zainstaluj funkcję alokacji zdefiniowaną przez klienta przez podłączenie jej do procesu alokacji pamięci debugowania w czasie wykonywania języka C|
|[_CrtSetBreakAlloc](../c-runtime-library/reference/crtsetbreakalloc.md)|Ustaw punkt przerwania na określony obiekt wielu zlecenia alokacji|
|[_CrtSetDbgFlag](../c-runtime-library/reference/crtsetdbgflag.md)|Pobierania lub modyfikowanie stanu **_crtDbgFlag** flagi sterujące zachowaniem alokacji podczas menedżera stosu debugowania|
|[_CrtSetDumpClient](../c-runtime-library/reference/crtsetdumpclient.md)|Instalowanie funkcji zdefiniowanych przez aplikację, która jest wywoływana za każdym razem, gdy jest wywoływana funkcja zrzutu debugowania, aby zrzutu **_CLIENT_BLOCK** wpisz bloków pamięci|
|[_CrtSetReportFile](../c-runtime-library/reference/crtsetreportfile.md)|Identyfikowanie pliku lub strumienia mającego służyć jako miejsce docelowe dla określonego typu raportu przez **_CrtDbgReport**|
|[_CrtSetReportHook](../c-runtime-library/reference/crtsetreporthook.md)|Zainstalować funkcję raportowania zdefiniowaną przez klienta przez podłączenie jej do raportowania procesu debugowania środowiska wykonawczego języka C|
|[_CrtSetReportHook2, _CrtSetReportHookW2](../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md)|Instaluje lub odinstalowuje zdefiniowaną przez klienta funkcji raportowania przez podłączenie jej do raportowania procesu debugowania środowiska wykonawczego języka C.|
|[_CrtSetReportMode](../c-runtime-library/reference/crtsetreportmode.md)|Określ ogólne przeznaczenie dla określonego typu raportu generowanego przez **_CrtDbgReport**|
|[_RPT&AMP;#91;0,1,2,3,4&AMP;#93;](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md)|Śledzenie postępu aplikacji przez wygenerowanie raportu debugowania, wywołując **_CrtDbgReport** za pomocą ciągu formatu i zmienną liczbę argumentów. Udostępnia Brak pliku i wierszu numer informacji o źródle.|
|[_RPTF&#91;0,1,2,3,4&#93;](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md)|Podobnie jak **_RPTn** makra, ale zapewnia źródła pliku nazwa i numer wiersza skąd pochodzi żądanie raportu|
|[_calloc_dbg](../c-runtime-library/reference/calloc-dbg.md)|Przydziel określoną liczbę bloków pamięci na stosie przy użyciu dodatkowego miejsca dla nagłówka debugowania i zastąpienia buforów|
|[_expand_dbg](../c-runtime-library/reference/expand-dbg.md)|Zmień rozmiar określony blok pamięci na stosie przez rozszerzanie lub zawierania bloku|
|[_free_dbg](../c-runtime-library/reference/free-dbg.md)|Wolny blok pamięci na stosie|
|[_fullpath_dbg, _wfullpath_dbg](../c-runtime-library/reference/fullpath-dbg-wfullpath-dbg.md)|Utwórz nazwę określoną ścieżką względną ścieżkę bezwzględną, lub pełną nazwę, za pomocą [_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md) można przydzielić pamięci.|
|[_getcwd_dbg, _wgetcwd_dbg](../c-runtime-library/reference/getcwd-dbg-wgetcwd-dbg.md)|Pobieranie bieżącego katalogu roboczego przy użyciu [_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md) można przydzielić pamięci.|
|[_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md)|Przydzielają blok pamięci na stosie przy użyciu dodatkowego miejsca dla nagłówka debugowania i zastąpienia buforów|
|[_msize_dbg](../c-runtime-library/reference/msize-dbg.md)|Oblicz rozmiar bloku pamięci na stosie|
|[_realloc_dbg](../c-runtime-library/reference/realloc-dbg.md)|Ponowne przydzielenie określony blok pamięci na stosie, przenoszenie i/lub zmiany rozmiaru bloku|
|[_strdup_dbg, _wcsdup_dbg](../c-runtime-library/reference/strdup-dbg-wcsdup-dbg.md)|Duplikuje ciąg przy użyciu [_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md) można przydzielić pamięci.|
|[_tempnam_dbg, _wtempnam_dbg](../c-runtime-library/reference/tempnam-dbg-wtempnam-dbg.md)|Generuj służy do tworzenia tymczasowych plików przy użyciu nazwy [_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md) można przydzielić pamięci.|

## <a name="c-runtime-routines-that-are-not-available-in-source-code-form"></a>Procedury czasu wykonywania języka C, które nie są dostępne w źródła w postaci kodu

Debuger może służyć do kroku za pomocą kodu źródłowego dla większości procedury środowiska uruchomieniowego języka C w procesie debugowania. Jednak firma Microsoft uwzględnia on technologie za zastrzeżone i, w związku z tym, nie dostarcza kod źródłowy dla podzbiór tych procedur. Większość z tych procedur należy do obsługi wyjątków lub grup przetwarzania zmiennoprzecinkowego, ale kilka innych zostały uwzględnione w także. Poniższa tabela zawiera listę tych procedur.

||||
|-|-|-|
|[ACOS](../c-runtime-library/reference/acos-acosf-acosl.md)|[acosh](../c-runtime-library/reference/acosh-acoshf-acoshl.md)|[ASIN](../c-runtime-library/reference/asin-asinf-asinl.md)|
|[ASINH —](../c-runtime-library/reference/asinh-asinhf-asinhl.md)|[ATAN, atan2](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[atanh](../c-runtime-library/reference/atanh-atanhf-atanhl.md)|
|[Funkcje Bessela](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|[_cabs](../c-runtime-library/reference/cabs.md)|[Ceil —](../c-runtime-library/reference/ceil-ceilf-ceill.md)|
|[_chgsign](../c-runtime-library/reference/chgsign-chgsignf-chgsignl.md)|[_clear87, _clearfp](../c-runtime-library/reference/clear87-clearfp.md)|[_control87, _controlfp](../c-runtime-library/reference/control87-controlfp-control87-2.md)|
|[copysign —](../c-runtime-library/reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)|[cos](../c-runtime-library/reference/cos-cosf-cosl.md)|[cosh](../c-runtime-library/reference/cosh-coshf-coshl.md)|
|[EXP](../c-runtime-library/reference/exp-expf.md)|[fabs —](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|[_finite](../c-runtime-library/reference/finite-finitef.md)|
|[floor](../c-runtime-library/reference/floor-floorf-floorl.md)|[Fmod —](../c-runtime-library/reference/fmod-fmodf.md)|[_fpclass](../c-runtime-library/reference/fpclass-fpclassf.md)|
|[_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md)|[_fpreset](../c-runtime-library/reference/fpreset.md)|[frexp](../c-runtime-library/reference/frexp.md)|
|[_hypot](../c-runtime-library/reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md)|[_isnan —](../c-runtime-library/reference/isnan-isnan-isnanf.md)|[ldexp](../c-runtime-library/reference/ldexp.md)|
|[log](../c-runtime-library/reference/log-logf-log10-log10f.md)|[_logb —](../c-runtime-library/reference/logb-logbf-logbl-logb-logbf.md)|[log10](../c-runtime-library/reference/log-logf-log10-log10f.md)|
|[longjmp](../c-runtime-library/reference/longjmp.md)|[_matherr](../c-runtime-library/reference/matherr.md)|[modf](../c-runtime-library/reference/modf-modff-modfl.md)|
|[_nextafter](../c-runtime-library/reference/nextafter-functions.md)|[Pow](../c-runtime-library/reference/pow-powf-powl.md)|[printf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|
|[printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|[_scalb](../c-runtime-library/reference/scalb.md)|[scanf_s](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)|
|[scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)|[setjmp](../c-runtime-library/reference/setjmp.md)|[sin](../c-runtime-library/reference/sin-sinf-sinl.md)|
|[SINH](../c-runtime-library/reference/sinh-sinhf-sinhl.md)|[sqrt](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|[_status87 —, _statusfp —](../c-runtime-library/reference/status87-statusfp-statusfp2.md)|
|[tan](../c-runtime-library/reference/tan-tanf-tanl.md)|[tanh](../c-runtime-library/reference/tanh-tanhf-tanhl.md)||

Mimo że kod źródłowy jest dostępny dla większości **printf** i **scanf** procedur, ich wywoływania wewnętrznego innej procedury, dla którego źródło nie zostanie podany kod.

## <a name="routines-that-behave-differently-in-a-debug-build-of-an-application"></a>Tworzenie procedury, które zachowują się odmiennie w debugowania w aplikacji

Niektóre funkcje środowiska wykonawczego języka C i C++ operatorów zachowywać się inaczej, gdy zostanie wywołana z kompilacji debugowania aplikacji. (Należy pamiętać, że do kompilacji debugowanej aplikacji może odbywać się przez definiowanie albo `_DEBUG` flaga lub przez połączenie z wersją debugera biblioteki wykonawczej C.) Różnice w zachowaniu składają się zazwyczaj z dodatkowych funkcji lub otrzymane od procedury obsługi procesu debugowania. Poniższa tabela zawiera listę tych procedur.

|||
|-|-|
|C [przerwać](../c-runtime-library/reference/abort.md) procedury|C++ [Usuń](../cpp/delete-operator-cpp.md) — operator|
|C [asercja](../c-runtime-library/reference/assert-macro-assert-wassert.md) procedury|C++ [nowe](../cpp/new-operator-cpp.md) — operator|

## <a name="see-also"></a>Zobacz także

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Sprawdzanie błędów czasu wykonywania](../c-runtime-library/run-time-error-checking.md)<br/>
