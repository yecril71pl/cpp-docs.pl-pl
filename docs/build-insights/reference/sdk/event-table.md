---
title: 'C++ Build Insights SDK: tabela zdarzeń'
description: Odwołanie do zdarzenia dla sdk aplikacji Visual Studio C++ Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Events
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 932b78347e05d313e7962da2fdff8c3454dec963
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324136"
---
# <a name="c-build-insights-sdk-event-table"></a>C++ Build Insights SDK: tabela zdarzeń

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

## <a name="compiler-events"></a>Zdarzenia kompilatora

[Kompilator](#compiler)\
[COMMAND_LINE](#command-line)\
[ENVIRONMENT_VARIABLE](#environment-variable)\
[FILE_INPUT](#file-input)\
[OBJ_OUTPUT](#obj-output)\
[FRONT_END_PASS](#front-end-pass)\
[BACK_END_PASS](#back-end-pass)

## <a name="compiler-front-end-events"></a>Kompilator zdarzenia front-end

[C1_DLL](#c1-dll)\
[FRONT_END_FILE](#front-end-file)\
[TEMPLATE_INSTANTIATION](#template-instantiation)\
[SYMBOL_NAME](#symbol-name)

## <a name="compiler-back-end-events"></a>Kompilator zdarzenia zaplecza

[C2_DLL](#c2-dll)\
[WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis)\
[TOP_DOWN](#top-down)\
[BOTTOM_UP](#bottom-up)\
[CODE_GENERATION](#code-generation)\
[Wątku](#thread)\
[Funkcja](#function)\
[FORCE_INLINEE](#force-inlinee)

## <a name="linker-events"></a>Zdarzenia konsolidatora

[Linker](#linker)\
[COMMAND_LINE](#command-line)\
[ENVIRONMENT_VARIABLE](#environment-variable)\
[FILE_INPUT](#file-input)\
[EXECUTABLE_IMAGE_OUTPUT](#executable-image-output)\
[EXP_OUTPUT](#exp-output)\
[IMP_LIB_OUTPUT](#imp-lib-output)\
[LIB_OUTPUT](#lib-output)\
[PRZEPUSTKA1](#pass1)\
[PRE_LTCG_OPT_REF](#pre-ltcg-opt-ref)\
[Ltcg](#ltcg)\
[OPT_REF](#opt-ref)\
[OPT_ICF](#opt-icf)\
[OPT_LBR](#opt-lbr)\
[PRZEPUSTKA 2](#pass2)

## <a name="event-table"></a>Tabela zdarzeń

| Wydarzenie | Właściwość | Opis |
|--|--|--|
| <a name="back-end-pass"></a>BACK_END_PASS | Typ | Działanie |
|  | Elementy nadrzędne | [Kompilator](#compiler) |
|  | Elementy podrzędne | [C2_DLL](#c2-dll) |
|  | Właściwości | - Bezwzględna ścieżka do pliku źródłowego wejściowego<br/>- Bezwzględna ścieżka do pliku obiektu wyjściowego |
|  | Przechwytywanie klas | [Działanie](cpp-event-data-types/activity.md)<br/>[KompilatorPrzechajnik](cpp-event-data-types/compiler-pass.md)<br/>[BackEndPass (BackEndPass)](cpp-event-data-types/back-end-pass.md) |
|  | Opis | Występuje na początku i zatrzymaniu kompilatora zaplecza przebiegu. Ten przebieg jest odpowiedzialny za optymalizację analizowanego kodu źródłowego C/C++ i przekonwertowanie go na kod maszynowy. |
| <a name="bottom-up"></a>BOTTOM_UP | Typ | Działanie |
|  | Elementy nadrzędne | [WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Elementy podrzędne | Brak |
|  | Właściwości | Brak |
|  | Przechwytywanie klas | [Działanie](cpp-event-data-types/activity.md)<br/>[Dół](cpp-event-data-types/bottom-up.md) |
|  | Opis | Występuje na początku i na przystanku całej analizy programu oddolnego przejścia. |
| <a name="c1-dll"></a>C1_DLL | Typ | Działanie |
|  | Elementy nadrzędne | [FRONT_END_PASS](#front-end-pass) |
|  | Elementy podrzędne | [FRONT_END_FILE](#front-end-file)<br/>[SYMBOL_NAME](#symbol-name)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Właściwości | Brak |
|  | Przechwytywanie klas | [Działanie](cpp-event-data-types/activity.md)<br/>[Biblioteka C1DLL](cpp-event-data-types/c1-dll.md) |
|  | Opis | Występuje na początku i zatrzymaniu wywołania *c1.dll* lub *c1xx.dll.* Te biblioteki DLL są c i C++ front end kompilatora. Są one wywoływane wyłącznie przez sterownik kompilatora (*cl.exe*). |
| <a name="c2-dll"></a>C2_DLL | Typ | Działanie |
|  | Elementy nadrzędne | [BACK_END_PASS](#back-end-pass)<br/>[Ltcg](#ltcg) |
|  | Elementy podrzędne | [CODE_GENERATION](#code-generation)<br/>[WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Właściwości | Brak |
|  | Przechwytywanie klas | [Działanie](cpp-event-data-types/activity.md)<br/>[Biblioteka C2DLL](cpp-event-data-types/c2-dll.md) |
|  | Opis | Występuje na początku i zatrzymaniu wywołania *c2.dll.* Ta biblioteka DLL jest zaplecza kompilatora. Jest wywoływana przez sterownik kompilatora (*cl.exe*). Jest również wywoływana przez konsolidator (*link.exe*), gdy używane jest generowanie kodu w czasie łącza. |
| <a name="code-generation"></a>CODE_GENERATION | Typ | Działanie |
|  | Elementy nadrzędne | [C2_DLL](#c2-dll) |
|  | Elementy podrzędne | [Funkcja](#function)<br/>[Wątku](#thread) |
|  | Właściwości | Brak |
|  | Przechwytywanie klas | [Działanie](cpp-event-data-types/activity.md)<br/>[CodeGeneration (Pojęć kodowe)](cpp-event-data-types/code-generation.md) |
|  | Opis | Występuje na początku i na przystanku fazy generowania kodu zaplecza. |
| <a name="command-line"></a>COMMAND_LINE | Typ | Proste zdarzenie |
|  | Elementy nadrzędne | [Kompilator](#compiler)<br/>[Linker](#linker) |
|  | Elementy podrzędne | Brak |
|  | Właściwości | - Wiersz polecenia, który został użyty do wywołania *cl.exe* lub *link.exe* |
|  | Przechwytywanie klas | [ProsteVent](cpp-event-data-types/simple-event.md)<br/>[Commandline](cpp-event-data-types/command-line.md) |
|  | Opis | Występuje, gdy kompilator i konsolidator są wykonywane oceny wiersza polecenia. Oceniany wiersz polecenia zawiera wszystkie parametry *cl.exe* i *link.exe* przekazywane za pośrednictwem pliku odpowiedzi. Zawiera również parametry *cl.exe* i *link.exe* przekazywane za pośrednictwem \_\_zmiennych środowiskowych, takich jak CL, CL, LINK i \_LINK\_. |
| <a name="compiler"></a>Kompilator | Typ | Działanie |
|  | Elementy nadrzędne | Brak |
|  | Elementy podrzędne | [BACK_END_PASS](#back-end-pass)<br/>[COMMAND_LINE](#command-line)<br/>[ENVIRONMENT_VARIABLE](#environment-variable)<br/>[FILE_INPUT](#file-input)<br/>[OBJ_OUTPUT](#obj-output)<br/>[FRONT_END_PASS](#front-end-pass) |
|  | Właściwości | - Wersja kompilatora<br/>- Katalog roboczy<br/>- Bezwzględna ścieżka do wywoływanych *cl.exe* |
|  | Przechwytywanie klas | [Działanie](cpp-event-data-types/activity.md)<br/>[Wywołania](cpp-event-data-types/invocation.md)<br/>[Kompilator](cpp-event-data-types/compiler.md) |
|  | Opis | Występuje na początku i zatrzymaniu *wywołania cl.exe.* |
| <a name="environment-variable"></a>ENVIRONMENT_VARIABLE | Typ | Proste zdarzenie |
|  | Elementy nadrzędne | [Kompilator](#compiler)<br/>[Linker](#linker) |
|  | Elementy podrzędne | Brak |
|  | Właściwości | - Nazwa zmiennej środowiskowej<br/>- Wartość zmiennej środowiskowej. |
|  | Przechwytywanie klas | [ProsteVent](cpp-event-data-types/simple-event.md)<br/>[ŚrodowiskoWaralne](cpp-event-data-types/environment-variable.md) |
|  | Opis | Występuje raz dla każdej istniejącej zmiennej środowiskowej w czasie *cl.exe* lub *link.exe* jest wywoływana. |
| <a name="executable-image-output"></a>EXECUTABLE_IMAGE_OUTPUT | Typ | Proste zdarzenie |
|  | Elementy nadrzędne | [Linker](#linker) |
|  | Elementy podrzędne | Brak |
|  | Właściwości | - Bezwzględna ścieżka do biblioteki DLL lub pliku wyjściowego wykonywalnego. |
|  | Przechwytywanie klas | [ProsteVent](cpp-event-data-types/simple-event.md)<br/>[FileOutput (FileOutput)](cpp-event-data-types/file-output.md)<br/>[Plik wykonywalnyImageOutput](cpp-event-data-types/executable-image-output.md) |
|  | Opis | Występuje, gdy jednym z danych wejściowych konsolidatora jest biblioteka DLL lub plik obrazu wykonywalnego. |
| <a name="exp-output"></a>EXP_OUTPUT | Typ | Proste zdarzenie |
|  | Elementy nadrzędne | [Linker](#linker) |
|  | Elementy podrzędne | Brak |
|  | Właściwości | - Bezwzględna ścieżka do pliku wyjściowego *.exp.* |
|  | Przechwytywanie klas | [ProsteVent](cpp-event-data-types/simple-event.md)<br/>[FileOutput (FileOutput)](cpp-event-data-types/file-output.md)<br/>[ExpOutput (ExpOutput)](cpp-event-data-types/exp-output.md) |
|  | Opis | Występuje, gdy jednym z wyjść konsolidatora jest plik *.exp.* |
| <a name="file-input"></a>FILE_INPUT | Typ | Proste zdarzenie |
|  | Elementy nadrzędne | [Kompilator](#compiler)<br/>[Linker](#linker) |
|  | Elementy podrzędne | Brak |
|  | Właściwości | - Bezwzględna ścieżka do pliku wejściowego<br/>- Typ pliku wejściowego |
|  | Przechwytywanie klas | [ProsteVent](cpp-event-data-types/simple-event.md)<br/>[FileInput (Plucie pliku)](cpp-event-data-types/file-input.md) |
|  | Opis | Występuje, aby ogłosić *cl.exe* lub *link.exe* wejście. |
| <a name="force-inlinee"></a>FORCE_INLINEE | Typ | Proste zdarzenie |
|  | Elementy nadrzędne | [Funkcja](#function) |
|  | Elementy podrzędne | Brak |
|  | Właściwości | - Nazwa funkcji force-inlined.<br/>- Rozmiar funkcji force-inlined, reprezentowanej jako pośrednia liczba instrukcji. |
|  | Przechwytywanie klas | [Działanie](cpp-event-data-types/activity.md)<br/>[ForceInlinee (Linia siłowa)](cpp-event-data-types/force-inlinee.md) |
|  | Opis | Występuje, gdy funkcja jest force-inlined do innej `__forceinline` funkcji za pomocą słowa kluczowego. |
| <a name="front-end-file"></a>FRONT_END_FILE | Typ | Działanie |
|  | Elementy nadrzędne | [C1_DLL](#c1-dll)<br/>[FRONT_END_FILE](#front-end-file) |
|  | Elementy podrzędne | [FRONT_END_FILE](#front-end-file)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Właściwości | - Bezwzględna ścieżka do pliku. |
|  | Przechwytywanie klas | [Działanie](cpp-event-data-types/activity.md)<br/>[Plik frontu](cpp-event-data-types/front-end-file.md) |
|  | Opis | Występuje, gdy przód kompilatora rozpoczyna się i zatrzymuje przetwarzanie pliku. To zdarzenie jest cykliczne. Rekursja ma miejsce, gdy fronton jest analizowanie dołączonych plików. |
| <a name="front-end-pass"></a>FRONT_END_PASS | Typ | Działanie |
|  | Elementy nadrzędne | [Kompilator](#compiler) |
|  | Elementy podrzędne | [C1_DLL](#c1-dll) |
|  | Właściwości | - Bezwzględna ścieżka do pliku źródłowego wejściowego<br/>- Bezwzględna ścieżka do pliku obiektu wyjściowego |
|  | Przechwytywanie klas | [Działanie](cpp-event-data-types/activity.md)<br/>[KompilatorPrzechajnik](cpp-event-data-types/compiler-pass.md)<br/>[FrontEndPass (Karnet frontu)](cpp-event-data-types/front-end-pass.md) |
|  | Opis | Występuje na początku i zatrzymaniu kompilatora front-end pass. Ten przebieg jest odpowiedzialny za analizowanie kodu źródłowego języka C/C++ i konwertowanie go na język pośredni. |
| <a name="function"></a>Funkcja | Typ | Działanie |
|  | Elementy nadrzędne | [CODE_GENERATION](#code-generation)<br/>[Wątku](#thread)<br/>[TOP_DOWN](#top-down) |
|  | Elementy podrzędne | [FORCE_INLINEE](#force-inlinee) |
|  | Właściwości | - Nazwa funkcji |
|  | Przechwytywanie klas | [Działanie](cpp-event-data-types/activity.md)<br/>[Funkcja](cpp-event-data-types/function.md) |
|  | Opis | Występuje podczas uruchamiania i kończenia generowania kodu dla funkcji. |
| <a name="imp-lib-output"></a>IMP_LIB_OUTPUT | Typ | Proste zdarzenie |
|  | Elementy nadrzędne | [Linker](#linker) |
|  | Elementy podrzędne | Brak |
|  | Właściwości | - Bezwzględna ścieżka do pliku wyjściowego biblioteki importu. |
|  | Przechwytywanie klas | [ProsteVent](cpp-event-data-types/simple-event.md)<br/>[FileOutput (FileOutput)](cpp-event-data-types/file-output.md)<br/>[ImpLibOutput (ImpLibOutput)](cpp-event-data-types/imp-lib-output.md) |
|  | Opis | Występuje, gdy jednym z danych wyjściowych konsolidatora jest biblioteka importu. |
| <a name="lib-output"></a>LIB_OUTPUT | Typ | Proste zdarzenie |
|  | Elementy nadrzędne | [Linker](#linker) |
|  | Elementy podrzędne | Brak |
|  | Właściwości | - Bezwzględna ścieżka do statycznego pliku wyjściowego biblioteki. |
|  | Przechwytywanie klas | [ProsteVent](cpp-event-data-types/simple-event.md)<br/>[FileOutput (FileOutput)](cpp-event-data-types/file-output.md)<br/>[LibOutput (LibOutput)](cpp-event-data-types/lib-output.md) |
|  | Opis | Występuje, gdy jeden z wyjść konsolidatora jest biblioteka statyczna. |
| <a name="linker"></a>Linker | Typ | Działanie |
|  | Elementy nadrzędne | Brak |
|  | Elementy podrzędne | [COMMAND_LINE](#command-line)<br/>[ENVIRONMENT_VARIABLE](#environment-variable)<br/>[EXECUTABLE_IMAGE_OUTPUT](#executable-image-output)<br/>[EXP_OUTPUT](#exp-output)<br/>[FILE_INPUT](#file-input)<br/>[IMP_LIB_OUTPUT](#imp-lib-output)<br/>[LIB_OUTPUT](#lib-output)<br/>[PRZEPUSTKA1](#pass1)<br/>[PRZEPUSTKA 2](#pass2) |
|  | Właściwości | - Wersja linker<br/>- Katalog roboczy<br/>- Bezwzględna ścieżka do *wywoływanelink.exe* |
|  | Przechwytywanie klas | [Działanie](cpp-event-data-types/activity.md)<br/>[Wywołania](cpp-event-data-types/invocation.md)<br/>[Konsolidator](cpp-event-data-types/linker.md) |
|  | Opis | Występuje na początku i zatrzymaniu wywołania *pliku link.exe.* |
| <a name="ltcg"></a>Ltcg | Typ | Działanie |
|  | Elementy nadrzędne | [PRZEPUSTKA1](#pass1) |
|  | Elementy podrzędne | [C2_DLL](#c2-dll) |
|  | Właściwości | Brak |
|  | Przechwytywanie klas | [Działanie](cpp-event-data-types/activity.md)<br/>[Ltcg](cpp-event-data-types/ltcg.md) |
|  | Opis | Występuje na początku i na zatrzymaniu generowania kodu w czasie łącza. |
| <a name="obj-output"></a>OBJ_OUTPUT | Typ | Proste zdarzenie |
|  | Elementy nadrzędne | [Kompilator](#compiler) |
|  | Elementy podrzędne | Brak |
|  | Właściwości | - Bezwzględna ścieżka do pliku wyjściowego *.obj* |
|  | Przechwytywanie klas | [ProsteVent](cpp-event-data-types/simple-event.md)<br/>[FileOutput (FileOutput)](cpp-event-data-types/file-output.md)<br/>[ObjOutput (ObjOutput)](cpp-event-data-types/obj-output.md) |
|  | Opis | Występuje raz na każde wyjście *.obj* wytwarzane przez *cl.exe*. |
| <a name="opt-icf"></a>OPT_ICF | Typ | Działanie |
|  | Elementy nadrzędne | [PRZEPUSTKA1](#pass1) |
|  | Elementy podrzędne | Brak |
|  | Właściwości | Brak |
|  | Przechwytywanie klas | [Działanie](cpp-event-data-types/activity.md)<br/>[OpticF ( OptICF )](cpp-event-data-types/opt-icf.md) |
|  | Opis | Występuje na początku i zatrzymaniu identycznej optymalizacji konsolidatora składającego COMDAT (/OPT:ICF). |
| <a name="opt-lbr"></a>OPT_LBR | Typ | Działanie |
|  | Elementy nadrzędne | [PRZEPUSTKA1](#pass1) |
|  | Elementy podrzędne | Brak |
|  | Właściwości | Brak |
|  | Przechwytywanie klas | [Działanie](cpp-event-data-types/activity.md)<br/>[OptLBR (właso)](cpp-event-data-types/opt-lbr.md) |
|  | Opis | Występuje na początku i zatrzymaniu długiej gałęzi (/OPT:LBR) optymalizacji konsolidatora. |
| <a name="opt-ref"></a>OPT_REF | Typ | Działanie |
|  | Elementy nadrzędne | [PRZEPUSTKA1](#pass1) |
|  | Elementy podrzędne | Brak |
|  | Właściwości | Brak |
|  | Przechwytywanie klas | [Działanie](cpp-event-data-types/activity.md)<br/>[OptRef (Odz.](cpp-event-data-types/opt-ref.md) |
|  | Opis | Występuje na początku i zatrzymaniu funkcji nieodniesione i eliminacji danych (/OPT:REF) optymalizacji konsolidatora. |
| <a name="pass1"></a>PRZEPUSTKA1 | Typ | Działanie |
|  | Elementy nadrzędne | [Linker](#linker) |
|  | Elementy podrzędne | [Ltcg](#ltcg)<br/>[OPT_ICF](#opt-icf)<br/>[OPT_LBR](#opt-lbr)<br/>[OPT_REF](#opt-ref) |
|  | Właściwości | Brak |
|  | Przechwytywanie klas | [Działanie](cpp-event-data-types/activity.md)<br/>[Przepustka 1](cpp-event-data-types/pass1.md) |
|  | Opis | Występuje na początku i na przystanku przejścia konsolidatora 1. |
| <a name="pass2"></a>PRZEPUSTKA 2 | Typ | Działanie |
|  | Elementy nadrzędne | [Linker](#linker) |
|  | Elementy podrzędne | Brak |
|  | Właściwości | Brak |
|  | Przechwytywanie klas | [Działanie](cpp-event-data-types/activity.md)<br/>[Przepustka 2](cpp-event-data-types/pass2.md) |
|  | Opis | Występuje na początku i na przystanku przejścia konsolidatora 2. |
| <a name="pre-ltcg-opt-ref"></a>PRE_LTCG_OPT_REF | Typ | Działanie |
|  | Elementy nadrzędne | [PRZEPUSTKA1](#pass1) |
|  | Elementy podrzędne | Brak |
|  | Właściwości | Brak |
|  | Przechwytywanie klas | [Działanie](cpp-event-data-types/activity.md)<br/>[PreLTCGOptRef](cpp-event-data-types/pre-ltcg-opt-ref.md) |
|  | Opis | Występuje na początku i zatrzymaniu przebiegu optymalizacji konsolidatora, który eliminuje nieodłączonych funkcji i danych (/OPT:REF). Odbywa się to przed generowaniem kodu w czasie łącza. |
| <a name="symbol-name"></a>SYMBOL_NAME | Typ | Proste zdarzenie |
|  | Elementy nadrzędne | [C1_DLL](#c1-dll) |
|  | Elementy podrzędne | Brak |
|  | Właściwości | - Klucz typu<br/> - Nazwa typu |
|  | Przechwytywanie klas | [ProsteVent](cpp-event-data-types/simple-event.md)<br/>[Nazwa symbolu](cpp-event-data-types/symbol-name.md) |
|  | Opis | Występuje na końcu przebiegu front-end: raz dla każdego typu zaangażowanych w wystąpienia szablonu. Klucz jest identyfikatorem numerycznym dla typu, podczas gdy nazwa jest jego reprezentacją tekstową. Klucze typu są unikatowe w analizowanym śledzenia. Jednak różne klucze pochodzące z różnych kompilatorów przepustek front-end może wskazywać na ten sam typ. Porównywanie typów między różnymi przebiegami frontu kompilatora wymaga użycia ich nazw. SYMBOL_NAME zdarzenia są emitowane na końcu przebiegu front-end kompilatora, po wszystkie wystąpienia szablonu miały miejsce. |
| <a name="template-instantiation"></a>TEMPLATE_INSTANTIATION | Typ | Działanie |
|  | Elementy nadrzędne | [C1_DLL](#c1-dll)<br/>[FRONT_END_FILE](#front-end-file)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Elementy podrzędne | [TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Właściwości | - Klucz do typu specjalistycznego<br/>- Klucz dla typu szablonu podstawowego<br/>- Rodzaj szablonu, który został s wystąpieniu |
|  | Przechwytywanie klas | [Działanie](cpp-event-data-types/activity.md)<br/>[SzablonInstantiation](cpp-event-data-types/template-instantiation.md) |
|  | Opis | Występuje na początku i na końcu wystąpienia szablonu. Główny typ szablonu `vector`(na przykład) jest tworzone, co powoduje, `std::vector<int>`że typ specjalistyczny (na przykład ). Klucz jest podany dla obu typów. Użyj [zdarzenia SYMBOL_NAME,](#symbol-name) aby przekonwertować klucz na nazwę typu. Klucze typu są unikatowe w analizowanym śledzenia. Jednak różne klucze pochodzące z różnych kompilatorów przepustek front-end może wskazywać na ten sam typ. Porównywanie typów między różnymi przebiegami frontu kompilatora wymaga użycia nazw symboli. To zdarzenie jest cykliczne. Rekursja ma miejsce w niektórych przypadkach, gdy fronton jest tworzenie wystąpienia szablonów zagnieżdżonych. |
| <a name="thread"></a>Wątku | Typ | Działanie |
|  | Elementy nadrzędne | [CODE_GENERATION](#code-generation)<br/>[TOP_DOWN](#top-down) |
|  | Elementy podrzędne | [Funkcja](#function) |
|  | Właściwości | Brak |
|  | Przechwytywanie klas | [Działanie](cpp-event-data-types/activity.md)<br/>[Wątku](cpp-event-data-types/thread.md) |
|  | Opis | Występuje na początku i na końcu wykonania wątku zaplecza kompilatora. Zawieszony wątek jest uważany za zakończony. Wątek budzi się jest uważany za rozpoczęty. |
| <a name="top-down"></a>TOP_DOWN | Typ | Działanie |
|  | Elementy nadrzędne | [WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Elementy podrzędne | [Funkcja](#function)<br/>[Wątku](#thread) |
|  | Właściwości | Brak |
|  | Przechwytywanie klas | [Działanie](cpp-event-data-types/activity.md)<br/>[Doliczanie do góry](cpp-event-data-types/top-down.md) |
|  | Opis | Występuje na początku i na przystanku całej analizy programu z góry na dół. |
| <a name="whole-program-analysis"></a>WHOLE_PROGRAM_ANALYSIS | Typ | Działanie |
|  | Elementy nadrzędne | [C2_DLL](#c2-dll) |
|  | Elementy podrzędne | [BOTTOM_UP](#bottom-up)<br/>[TOP_DOWN](#top-down) |
|  | Właściwości | Brak |
|  | Przechwytywanie klas | [Działanie](cpp-event-data-types/activity.md)<br/>[WholeProgramAnalysis](cpp-event-data-types/whole-program-analysis.md) |
|  | Opis | Występuje na początku i na przystanku fazy analizy całego programu generowania kodu w czasie łącza. |

::: moniker-end
