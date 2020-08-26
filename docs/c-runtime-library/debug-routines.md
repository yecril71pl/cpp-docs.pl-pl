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
ms.openlocfilehash: 59e705947856ba9fe9477e88328b1fb2344abb7c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842497"
---
# <a name="debug-routines"></a>Procedury debugowania

Wersja do debugowania biblioteki środowiska uruchomieniowego języka C oferuje wiele usług diagnostycznych, które ułatwiają programowanie programów do debugowania i umożliwiają deweloperom:

- Wkrocz bezpośrednio do funkcji w czasie wykonywania podczas debugowania

- Rozwiązywanie potwierdzeń, błędów i wyjątków

- Śledzenie alokacji sterty i zapobieganie wyciekom pamięci

- Zgłoś komunikaty debugowania użytkownikowi

## <a name="debug-versions-of-the-c-runtime-library-routines"></a>Debuguj wersje procedur biblioteki środowiska uruchomieniowego języka C

Aby użyć tych procedur, należy zdefiniować flagę [_DEBUG](../c-runtime-library/debug.md) . Wszystkie te procedury nie wykonują żadnych operacji w kompilacji detalicznej aplikacji. Aby uzyskać więcej informacji na temat korzystania z nowych procedur debugowania, zobacz [techniki debugowania CRT](/visualstudio/debugger/crt-debugging-techniques).

| Procedura | Zastosowanie |
|--|--|
| [`_ASSERT`](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) | Oceń wyrażenie i Wygeneruj raport debugowania, gdy wynik jest FAŁSZYWy |
| [`_ASSERTE`](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) | Podobnie jak **`_ASSERT`** w przypadku, ale zawiera wyrażenie zakończone niepowodzeniem w wygenerowanym raporcie |
| [`_CrtCheckMemory`](../c-runtime-library/reference/crtcheckmemory.md) | Potwierdź integralność bloków pamięci przydzieloną na stercie debugowania |
| [`_CrtDbgBreak`](../c-runtime-library/reference/crtdbgbreak.md) | Ustawia punkt przerwania. |
| [`_CrtDbgReport`, `_CrtDbgReportW`](../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) | Generowanie raportu debugowania z komunikatem użytkownika i wysyłanie raportu do trzech możliwych miejsc docelowych |
| [`_CrtDoForAllClientObjects`](../c-runtime-library/reference/crtdoforallclientobjects.md) | Wywoływanie funkcji dostarczonej przez aplikację dla wszystkich `_CLIENT_BLOCK` typów na stercie |
| [`_CrtDumpMemoryLeaks`](../c-runtime-library/reference/crtdumpmemoryleaks.md) | Zrzuć wszystkie bloki pamięci na stercie debugowania, gdy wystąpi znaczący wyciek pamięci |
| [`_CrtIsMemoryBlock`](../c-runtime-library/reference/crtismemoryblock.md) | Sprawdź, czy określony blok pamięci znajduje się w stercie lokalnym i czy ma prawidłowy identyfikator typu bloku sterty debugowania |
| [`_CrtIsValidHeapPointer`](../c-runtime-library/reference/crtisvalidheappointer.md) | Sprawdza, czy określony wskaźnik znajduje się na stercie lokalnej |
| [`_CrtIsValidPointer`](../c-runtime-library/reference/crtisvalidpointer.md) | Sprawdź, czy określony zakres pamięci jest prawidłowy do odczytu i zapisu |
| [`_CrtMemCheckpoint`](../c-runtime-library/reference/crtmemcheckpoint.md) | Uzyskaj bieżący stan sterty debugowania i Zapisz go w strukturze dostarczonej przez aplikację `_CrtMemState` |
| [`_CrtMemDifference`](../c-runtime-library/reference/crtmemdifference.md) | Porównanie dwóch stanów pamięci w celu uzyskania znaczących różnic i zwrócenie wyników |
| [`_CrtMemDumpAllObjectsSince`](../c-runtime-library/reference/crtmemdumpallobjectssince.md) | Zrzuć informacje o obiektach na stercie od momentu wykonania określonego punktu kontrolnego lub od początku wykonywania programu |
| [`_CrtMemDumpStatistics`](../c-runtime-library/reference/crtmemdumpstatistics.md) | Zrzuć informacje z nagłówka debugowania dla określonego stanu pamięci w formie możliwej do odczytu przez użytkownika |
| [`_CrtReportBlockType`](../c-runtime-library/reference/crtreportblocktype.md) | Zwraca typ bloku/podtyp skojarzony z danym wskaźnikiem bloku sterty debugowania. |
| [`_CrtSetAllocHook`](../c-runtime-library/reference/crtsetallochook.md) | Zainstaluj funkcję alokacji zdefiniowaną przez klienta, przełączając ją do procesu alokacji pamięci debugowania w czasie wykonywania C |
| [`_CrtSetBreakAlloc`](../c-runtime-library/reference/crtsetbreakalloc.md) | Ustaw punkt przerwania dla określonego numeru zamówienia alokacji obiektu |
| [`_CrtSetDbgFlag`](../c-runtime-library/reference/crtsetdbgflag.md) | Pobieranie lub modyfikowanie stanu `_crtDbgFlag` flagi w celu sterowania zachowaniem alokacji menedżera sterty debugowania |
| [`_CrtSetDumpClient`](../c-runtime-library/reference/crtsetdumpclient.md) | Instalowanie funkcji zdefiniowanej przez aplikację, która jest wywoływana za każdym razem, gdy wywoływana jest funkcja zrzutu debugowania w celu zrzutu `_CLIENT_BLOCK` bloków pamięci typu |
| [`_CrtSetReportFile`](../c-runtime-library/reference/crtsetreportfile.md) | Zidentyfikuj plik lub strumień, który ma być używany jako miejsce docelowe dla określonego typu raportu, `_CrtDbgReport` |
| [`_CrtSetReportHook`](../c-runtime-library/reference/crtsetreporthook.md) | Zainstaluj funkcję raportowania zdefiniowaną przez klienta, przełączając ją do procesu raportowania debugowania w czasie wykonywania C |
| [`_CrtSetReportHook2`, `_CrtSetReportHookW2`](../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) | Instaluje lub Odinstalowuje funkcję raportowania zdefiniowaną przez klienta, przełączając ją do procesu raportowania debugowania w czasie wykonywania języka C. |
| [`_CrtSetReportMode`](../c-runtime-library/reference/crtsetreportmode.md) | Określ ogólne elementy docelowe dla określonego typu raportu generowanego przez `_CrtDbgReport` |
| [_RPT&#91;0, 1, 2, 3, 4&#93;](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md) | Śledź postęp aplikacji, generując raport debugowania, wywołując `_CrtDbgReport` Ciąg formatujący i zmienną liczbę argumentów. Nie zawiera informacji o pliku źródłowym i numerze wiersza. |
| [_RPTF&#91;0, 1, 2, 3, 4&#93;](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md) | Podobnie jak w przypadku `_RPTn` makr, ale zawiera nazwę pliku źródłowego i numer wiersza, z którego pochodzi żądanie raportu |
| [`_calloc_dbg`](../c-runtime-library/reference/calloc-dbg.md) | Przydziel określoną liczbę bloków pamięci na stercie z dodatkowym miejscem dla nagłówka debugowania i buforów zastąpień |
| [`_expand_dbg`](../c-runtime-library/reference/expand-dbg.md) | Zmiana rozmiaru określonego bloku pamięci na stercie przez rozwijanie lub zablokowanie bloku |
| [`_free_dbg`](../c-runtime-library/reference/free-dbg.md) | Zwolnij blok pamięci na stercie |
| [`_fullpath_dbg`, `_wfullpath_dbg`](../c-runtime-library/reference/fullpath-dbg-wfullpath-dbg.md) | Utwórz bezwzględną lub pełną nazwę ścieżki dla określonej nazwy ścieżki względnej, używając [`_malloc_dbg`](../c-runtime-library/reference/malloc-dbg.md) do przydzielenia pamięci. |
| [`_getcwd_dbg`, `_wgetcwd_dbg`](../c-runtime-library/reference/getcwd-dbg-wgetcwd-dbg.md) | Pobierz bieżący katalog roboczy przy użyciu [`_malloc_dbg`](../c-runtime-library/reference/malloc-dbg.md) programu w celu przydzielenia pamięci. |
| [`_malloc_dbg`](../c-runtime-library/reference/malloc-dbg.md) | Przydzielanie bloku pamięci na stercie z dodatkowym miejscem dla nagłówka debugowania i buforów zastąpień |
| [`_msize_dbg`](../c-runtime-library/reference/msize-dbg.md) | Obliczanie rozmiaru bloku pamięci na stercie |
| [`_realloc_dbg`](../c-runtime-library/reference/realloc-dbg.md) | Przydziel ponownie określony blok pamięci na stercie, przenosząc i/lub zmieniając rozmiar bloku |
| [`_strdup_dbg`, `_wcsdup_dbg`](../c-runtime-library/reference/strdup-dbg-wcsdup-dbg.md) | Duplikuje ciąg, używając [`_malloc_dbg`](../c-runtime-library/reference/malloc-dbg.md) do przydzielenia pamięci. |
| [`_tempnam_dbg`, `_wtempnam_dbg`](../c-runtime-library/reference/tempnam-dbg-wtempnam-dbg.md) | Generuj nazwy, których można użyć do tworzenia plików tymczasowych przy użyciu [`_malloc_dbg`](../c-runtime-library/reference/malloc-dbg.md) programu w celu przydzielenia pamięci. |

## <a name="c-runtime-routines-that-are-not-available-in-source-code-form"></a>Procedury środowiska uruchomieniowego języka C, które nie są dostępne w formularzu kodu źródłowego

Debuger może służyć do przechodzenia przez kod źródłowy większości procedur środowiska uruchomieniowego języka C podczas procesu debugowania. Jednak firma Microsoft uważa, że niektóre technologie są zastrzeżone i w związku z tym nie udostępniają kodu źródłowego podzbioru tych procedur. Większość z tych procedur należy do obsługi wyjątków lub grup przetwarzania zmiennoprzecinkowego, ale również kilka innych. W poniższej tabeli wymieniono te procedury.

:::row:::
   :::column span="":::
      [`acos`](../c-runtime-library/reference/acos-acosf-acosl.md)\
      [`acosh`](../c-runtime-library/reference/acosh-acoshf-acoshl.md)\
      [`asin`](../c-runtime-library/reference/asin-asinf-asinl.md)\
      [`asinh`](../c-runtime-library/reference/asinh-asinhf-asinhl.md)\
      [`atan`, `atan2`](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)\
      [`atanh`](../c-runtime-library/reference/atanh-atanhf-atanhl.md)\
      [`Bessel functions`](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)\
      [`_cabs`](../c-runtime-library/reference/cabs.md)\
      [`ceil`](../c-runtime-library/reference/ceil-ceilf-ceill.md)\
      [`_chgsign`](../c-runtime-library/reference/chgsign-chgsignf-chgsignl.md)\
      [`_clear87`, `_clearfp`](../c-runtime-library/reference/clear87-clearfp.md)\
      [`_control87`, `_controlfp`](../c-runtime-library/reference/control87-controlfp-control87-2.md)
   :::column-end:::
   :::column span="":::
      [`copysign`](../c-runtime-library/reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)\
      [`cos`](../c-runtime-library/reference/cos-cosf-cosl.md)\
      [`cosh`](../c-runtime-library/reference/cosh-coshf-coshl.md)\
      [`Exp`](../c-runtime-library/reference/exp-expf.md)\
      [`fabs`](../c-runtime-library/reference/fabs-fabsf-fabsl.md)\
      [`_finite`](../c-runtime-library/reference/finite-finitef.md)\
      [`floor`](../c-runtime-library/reference/floor-floorf-floorl.md)\
      [`fmod`](../c-runtime-library/reference/fmod-fmodf.md)\
      [`_fpclass`](../c-runtime-library/reference/fpclass-fpclassf.md)\
      [`_fpieee_flt`](../c-runtime-library/reference/fpieee-flt.md)\
      [`_fpreset`](../c-runtime-library/reference/fpreset.md)\
      [`frexp`](../c-runtime-library/reference/frexp.md)
   :::column-end:::
   :::column span="":::
      [`_hypot`](../c-runtime-library/reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md)\
      [`_isnan`](../c-runtime-library/reference/isnan-isnan-isnanf.md)\
      [`ldexp`](../c-runtime-library/reference/ldexp.md)\
      [`log`](../c-runtime-library/reference/log-logf-log10-log10f.md)\
      [`_logb`](../c-runtime-library/reference/logb-logbf-logbl-logb-logbf.md)\
      [`log10`](../c-runtime-library/reference/log-logf-log10-log10f.md)\
      [`longjmp`](../c-runtime-library/reference/longjmp.md)\
      [`_matherr`](../c-runtime-library/reference/matherr.md)\
      [`modf`](../c-runtime-library/reference/modf-modff-modfl.md)\
      [`_nextafter`](../c-runtime-library/reference/nextafter-functions.md)\
      [`pow`](../c-runtime-library/reference/pow-powf-powl.md)\
      [`printf_s`](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)
   :::column-end:::
   :::column span="":::
      [`printf`](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)\
      [`_scalb`](../c-runtime-library/reference/scalb.md)\
      [`scanf_s`](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)\
      [`scanf`](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)\
      [`setjmp`](../c-runtime-library/reference/setjmp.md)\
      [`sin`](../c-runtime-library/reference/sin-sinf-sinl.md)\
      [`sinh`](../c-runtime-library/reference/sinh-sinhf-sinhl.md)\
      [`sqrt`](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)\
      [`_status87`, `_statusfp`](../c-runtime-library/reference/status87-statusfp-statusfp2.md)\
      [`tan`](../c-runtime-library/reference/tan-tanf-tanl.md)\
      [`tanh`](../c-runtime-library/reference/tanh-tanhf-tanhl.md)
   :::column-end:::
:::row-end:::

Chociaż kod źródłowy jest dostępny dla większości procedur **printf** i **scanf** , tworzą one wewnętrzne wywołanie do innej procedury, dla której kod źródłowy nie został podany.

## <a name="routines-that-behave-differently-in-a-debug-build-of-an-application"></a>Procedury, które zachowują się inaczej w kompilacji debugowania aplikacji

Niektóre funkcje środowiska uruchomieniowego C i operatory języka C++ działają inaczej, gdy są wywoływane z kompilacji aplikacji. (Należy zauważyć, że kompilacja do debugowania aplikacji może być wykonywana przez zdefiniowanie `_DEBUG` flagi lub przez połączenie z wersją debugową biblioteki wykonawczej C). Różnice zachowania zwykle składają się z dodatkowych funkcji lub informacji dostarczonych przez procedurę do obsługi procesu debugowania. W poniższej tabeli wymieniono te procedury.

:::row:::
   :::column span="":::
      Procedura języka C [`abort`](../c-runtime-library/reference/abort.md)
   :::column-end:::
   :::column span="":::
      Procedura języka C [`assert`](../c-runtime-library/reference/assert-macro-assert-wassert.md)
   :::column-end:::
   :::column span="":::
      Operator języka C++ [`delete`](../cpp/delete-operator-cpp.md)
   :::column-end:::
   :::column span="":::
      Operator języka C++ [`new`](../cpp/new-operator-cpp.md)
   :::column-end:::
:::row-end:::

## <a name="see-also"></a>Zobacz też

[Procedury środowiska uruchomieniowego języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Sprawdzanie błędów czasu wykonywania](../c-runtime-library/run-time-error-checking.md)<br/>
