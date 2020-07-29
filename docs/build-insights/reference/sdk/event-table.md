---
title: 'Zestaw SDK tworzenia usługi Insights dla języka C++: tabela zdarzeń'
description: Dokumentacja zdarzenia dla zestawu SDK usługi Visual Studio C++ build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Events
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6b1cf6871329fcce3166495e173360a88ac38ee0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224217"
---
# <a name="c-build-insights-sdk-event-table"></a>Zestaw SDK tworzenia usługi Insights dla języka C++: tabela zdarzeń

::: moniker range="<=vs-2015"

Zestaw SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora **wersji** programu Visual Studio dla tego artykułu na visual Studio 2017 lub visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

## <a name="compiler-events"></a>Zdarzenia kompilatora

[COMPILER](#compiler)\
[COMMAND_LINE](#command-line)\
[ENVIRONMENT_VARIABLE](#environment-variable)\
[FILE_INPUT](#file-input)\
[OBJ_OUTPUT](#obj-output)\
[FRONT_END_PASS](#front-end-pass)\
[BACK_END_PASS](#back-end-pass)

## <a name="compiler-front-end-events"></a>Zdarzenia frontonu kompilatora

[C1_DLL](#c1-dll)\
[FRONT_END_FILE](#front-end-file)\
[TEMPLATE_INSTANTIATION](#template-instantiation)\
[SYMBOL_NAME](#symbol-name)

## <a name="compiler-back-end-events"></a>Zdarzenia zaplecza kompilatora

[C2_DLL](#c2-dll)\
[WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis)\
[TOP_DOWN](#top-down)\
[BOTTOM_UP](#bottom-up)\
[CODE_GENERATION](#code-generation)\
[NICI](#thread)\
[FUNKCYJN](#function)\
[FORCE_INLINEE](#force-inlinee)

## <a name="linker-events"></a>Zdarzenia konsolidatora

[KONSOLIDATORA](#linker)\
[COMMAND_LINE](#command-line)\
[ENVIRONMENT_VARIABLE](#environment-variable)\
[FILE_INPUT](#file-input)\
[EXECUTABLE_IMAGE_OUTPUT](#executable-image-output)\
[EXP_OUTPUT](#exp-output)\
[IMP_LIB_OUTPUT](#imp-lib-output)\
[LIB_OUTPUT](#lib-output)\
[PASS1](#pass1)\
[PRE_LTCG_OPT_REF](#pre-ltcg-opt-ref)\
[LTCG](#ltcg)\
[OPT_REF](#opt-ref)\
[OPT_ICF](#opt-icf)\
[OPT_LBR](#opt-lbr)\
[PASS2](#pass2)

## <a name="event-table"></a>Tabela zdarzeń

| Wydarzenie | Właściwość | Opis |
|--|--|--|
| <a name="back-end-pass"></a>BACK_END_PASS | Typ | Działanie |
|  | Elementy nadrzędne | [COMPILER](#compiler) |
|  | Elementy podrzędne | [C2_DLL](#c2-dll) |
|  | Właściwości | -Absolutna ścieżka do wejściowego pliku źródłowego<br/>-Bezwzględna ścieżka do pliku obiektu wyjściowego |
|  | Klasy przechwytywania | [Działanie](cpp-event-data-types/activity.md)<br/>[CompilerPass](cpp-event-data-types/compiler-pass.md)<br/>[BackEndPass](cpp-event-data-types/back-end-pass.md) |
|  | Opis | Występuje po uruchomieniu i zatrzymaniu przejścia zaplecza kompilatora. Ten przebieg jest odpowiedzialny za optymalizację przeanalizowanego kodu źródłowego C/C++ i konwertowanie go na kod maszynowy. |
| <a name="bottom-up"></a>BOTTOM_UP | Typ | Działanie |
|  | Elementy nadrzędne | [WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Elementy podrzędne | Brak |
|  | Właściwości | Brak |
|  | Klasy przechwytywania | [Działanie](cpp-event-data-types/activity.md)<br/>[BottomUp](cpp-event-data-types/bottom-up.md) |
|  | Opis | Występuje po rozpoczęciu i zatrzymaniu całego przeprowadzenia analizy programu. |
| <a name="c1-dll"></a>C1_DLL | Typ | Działanie |
|  | Elementy nadrzędne | [FRONT_END_PASS](#front-end-pass) |
|  | Elementy podrzędne | [FRONT_END_FILE](#front-end-file)<br/>[SYMBOL_NAME](#symbol-name)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Właściwości | Brak |
|  | Klasy przechwytywania | [Działanie](cpp-event-data-types/activity.md)<br/>[C1DLL](cpp-event-data-types/c1-dll.md) |
|  | Opis | Występuje po uruchomieniu i zatrzymaniu *c1.dll* lub *c1xx.dll* wywołania. Te biblioteki DLL są frontonem C i C++ kompilatora. Są one wywoływane wyłącznie przez sterownik kompilatora (*cl.exe*). |
| <a name="c2-dll"></a>C2_DLL | Typ | Działanie |
|  | Elementy nadrzędne | [BACK_END_PASS](#back-end-pass)<br/>[LTCG](#ltcg) |
|  | Elementy podrzędne | [CODE_GENERATION](#code-generation)<br/>[WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Właściwości | Brak |
|  | Klasy przechwytywania | [Działanie](cpp-event-data-types/activity.md)<br/>[C2DLL](cpp-event-data-types/c2-dll.md) |
|  | Opis | Występuje po uruchomieniu i zatrzymaniu wywołania *c2.dll* . Ta biblioteka DLL jest zapleczem kompilatora. Jest on wywoływany przez sterownik kompilatora (*cl.exe*). Jest on także wywoływany przez konsolidator (*link.exe*), gdy jest używane generowanie kodu w czasie konsolidacji. |
| <a name="code-generation"></a>CODE_GENERATION | Typ | Działanie |
|  | Elementy nadrzędne | [C2_DLL](#c2-dll) |
|  | Elementy podrzędne | [FUNKCYJN](#function)<br/>[NICI](#thread) |
|  | Właściwości | Brak |
|  | Klasy przechwytywania | [Działanie](cpp-event-data-types/activity.md)<br/>[CodeGeneration](cpp-event-data-types/code-generation.md) |
|  | Opis | Występuje po uruchomieniu i zatrzymaniu fazy generowania kodu zaplecza. |
| <a name="command-line"></a>COMMAND_LINE | Typ | Zdarzenie proste |
|  | Elementy nadrzędne | [COMPILER](#compiler)<br/>[KONSOLIDATORA](#linker) |
|  | Elementy podrzędne | Brak |
|  | Właściwości | — Wiersz polecenia, który został użyty do wywołania *cl.exe* lub *link.exe* |
|  | Klasy przechwytywania | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[CommandLine](cpp-event-data-types/command-line.md) |
|  | Opis | Występuje, gdy kompilator i konsolidator są wykonywane podczas oceniania wiersza polecenia. Szacowany wiersz polecenia zawiera wszystkie *cl.exe* i *link.exe* parametry przekazane za pośrednictwem pliku odpowiedzi. Zawiera również parametry do *cl.exe* i *link.exe* przekazane za pomocą zmiennych środowiskowych, takich jak CL, \_ CL \_ , link i \_ link \_ . |
| <a name="compiler"></a>COMPILER | Typ | Działanie |
|  | Elementy nadrzędne | Brak |
|  | Elementy podrzędne | [BACK_END_PASS](#back-end-pass)<br/>[COMMAND_LINE](#command-line)<br/>[ENVIRONMENT_VARIABLE](#environment-variable)<br/>[FILE_INPUT](#file-input)<br/>[OBJ_OUTPUT](#obj-output)<br/>[FRONT_END_PASS](#front-end-pass) |
|  | Właściwości | -Wersja kompilatora<br/>— Katalog roboczy<br/>Ścieżka bezwzględna do wywołanego *cl.exe* |
|  | Klasy przechwytywania | [Działanie](cpp-event-data-types/activity.md)<br/>[Invocation](cpp-event-data-types/invocation.md)<br/>[Compiler](cpp-event-data-types/compiler.md) |
|  | Opis | Występuje po uruchomieniu i zatrzymaniu wywołania *cl.exe* . |
| <a name="environment-variable"></a>ENVIRONMENT_VARIABLE | Typ | Zdarzenie proste |
|  | Elementy nadrzędne | [COMPILER](#compiler)<br/>[KONSOLIDATORA](#linker) |
|  | Elementy podrzędne | Brak |
|  | Właściwości | -Nazwa zmiennej środowiskowej<br/>— Wartość zmiennej środowiskowej. |
|  | Klasy przechwytywania | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[EnvironmentVariable](cpp-event-data-types/environment-variable.md) |
|  | Opis | Występuje raz dla każdej istniejącej zmiennej środowiskowej w czasie *cl.exe* lub *link.exe* jest wywoływana. |
| <a name="executable-image-output"></a>EXECUTABLE_IMAGE_OUTPUT | Typ | Zdarzenie proste |
|  | Elementy nadrzędne | [KONSOLIDATORA](#linker) |
|  | Elementy podrzędne | Brak |
|  | Właściwości | — Ścieżka bezwzględna do pliku wyjściowego DLL lub wykonywalnego. |
|  | Klasy przechwytywania | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ExecutableImageOutput](cpp-event-data-types/executable-image-output.md) |
|  | Opis | Występuje, gdy jeden z danych wejściowych konsolidatora jest biblioteką DLL lub plikiem obrazu wykonywalnego. |
| <a name="exp-output"></a>EXP_OUTPUT | Typ | Zdarzenie proste |
|  | Elementy nadrzędne | [KONSOLIDATORA](#linker) |
|  | Elementy podrzędne | Brak |
|  | Właściwości | -Ścieżka bezwzględna do pliku wyjściowego *. EXP* . |
|  | Klasy przechwytywania | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ExpOutput](cpp-event-data-types/exp-output.md) |
|  | Opis | Występuje, gdy jeden z elementów wyjściowych konsolidatora jest plikiem *. EXP* . |
| <a name="file-input"></a>FILE_INPUT | Typ | Zdarzenie proste |
|  | Elementy nadrzędne | [COMPILER](#compiler)<br/>[KONSOLIDATORA](#linker) |
|  | Elementy podrzędne | Brak |
|  | Właściwości | -Bezwzględna ścieżka do pliku wejściowego<br/>— Typ pliku wejściowego |
|  | Klasy przechwytywania | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileInput](cpp-event-data-types/file-input.md) |
|  | Opis | Występuje, aby ogłosić *cl.exe* lub *link.exe* dane wejściowe. |
| <a name="force-inlinee"></a>FORCE_INLINEE | Typ | Zdarzenie proste |
|  | Elementy nadrzędne | [FUNKCYJN](#function) |
|  | Elementy podrzędne | Brak |
|  | Właściwości | -Nazwa funkcji wymuszonej.<br/>-Rozmiar funkcji bezwierszowej, reprezentowanej jako liczba instrukcji pośredniej. |
|  | Klasy przechwytywania | [Działanie](cpp-event-data-types/activity.md)<br/>[ForceInlinee](cpp-event-data-types/force-inlinee.md) |
|  | Opis | Występuje, gdy funkcja jest wymuszana — wbudowana w inną funkcję za pomocą **`__forceinline`** słowa kluczowego. |
| <a name="front-end-file"></a>FRONT_END_FILE | Typ | Działanie |
|  | Elementy nadrzędne | [C1_DLL](#c1-dll)<br/>[FRONT_END_FILE](#front-end-file) |
|  | Elementy podrzędne | [FRONT_END_FILE](#front-end-file)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Właściwości | Ścieżka bezwzględna do pliku. |
|  | Klasy przechwytywania | [Działanie](cpp-event-data-types/activity.md)<br/>[FrontEndFile](cpp-event-data-types/front-end-file.md) |
|  | Opis | Występuje, gdy fronton kompilatora zostanie uruchomiony i zatrzyma przetwarzanie pliku. To zdarzenie jest cykliczne. Rekursja występuje, gdy fronton analizuje dołączone pliki. |
| <a name="front-end-pass"></a>FRONT_END_PASS | Typ | Działanie |
|  | Elementy nadrzędne | [COMPILER](#compiler) |
|  | Elementy podrzędne | [C1_DLL](#c1-dll) |
|  | Właściwości | -Absolutna ścieżka do wejściowego pliku źródłowego<br/>-Bezwzględna ścieżka do pliku obiektu wyjściowego |
|  | Klasy przechwytywania | [Działanie](cpp-event-data-types/activity.md)<br/>[CompilerPass](cpp-event-data-types/compiler-pass.md)<br/>[FrontEndPass](cpp-event-data-types/front-end-pass.md) |
|  | Opis | Występuje na początku i zatrzymaniu frontonu kompilatora. Ten przebieg jest odpowiedzialny za analizowanie kodu źródłowego C/C++ i konwertowanie go do języka pośredniego. |
| <a name="function"></a>FUNKCYJN | Typ | Działanie |
|  | Elementy nadrzędne | [CODE_GENERATION](#code-generation)<br/>[NICI](#thread)<br/>[TOP_DOWN](#top-down) |
|  | Elementy podrzędne | [FORCE_INLINEE](#force-inlinee) |
|  | Właściwości | -Nazwa funkcji |
|  | Klasy przechwytywania | [Działanie](cpp-event-data-types/activity.md)<br/>[Funkcja](cpp-event-data-types/function.md) |
|  | Opis | Występuje po rozpoczęciu i zakończeniu generowania kodu dla funkcji. |
| <a name="imp-lib-output"></a>IMP_LIB_OUTPUT | Typ | Zdarzenie proste |
|  | Elementy nadrzędne | [KONSOLIDATORA](#linker) |
|  | Elementy podrzędne | Brak |
|  | Właściwości | -Ścieżka bezwzględna do pliku wyjściowego biblioteki importu. |
|  | Klasy przechwytywania | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ImpLibOutput](cpp-event-data-types/imp-lib-output.md) |
|  | Opis | Występuje, gdy jeden z elementów wyjściowych konsolidatora jest biblioteką importu. |
| <a name="lib-output"></a>LIB_OUTPUT | Typ | Zdarzenie proste |
|  | Elementy nadrzędne | [KONSOLIDATORA](#linker) |
|  | Elementy podrzędne | Brak |
|  | Właściwości | -Ścieżka bezwzględna do pliku wyjściowego biblioteki statycznej. |
|  | Klasy przechwytywania | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[LibOutput](cpp-event-data-types/lib-output.md) |
|  | Opis | Występuje, gdy jeden z elementów wyjściowych konsolidatora jest biblioteką statyczną. |
| <a name="linker"></a>KONSOLIDATORA | Typ | Działanie |
|  | Elementy nadrzędne | Brak |
|  | Elementy podrzędne | [COMMAND_LINE](#command-line)<br/>[ENVIRONMENT_VARIABLE](#environment-variable)<br/>[EXECUTABLE_IMAGE_OUTPUT](#executable-image-output)<br/>[EXP_OUTPUT](#exp-output)<br/>[FILE_INPUT](#file-input)<br/>[IMP_LIB_OUTPUT](#imp-lib-output)<br/>[LIB_OUTPUT](#lib-output)<br/>[PASS1](#pass1)<br/>[PASS2](#pass2) |
|  | Właściwości | -Wersja konsolidatora<br/>— Katalog roboczy<br/>Ścieżka bezwzględna do wywołanego *link.exe* |
|  | Klasy przechwytywania | [Działanie](cpp-event-data-types/activity.md)<br/>[Invocation](cpp-event-data-types/invocation.md)<br/>[Konsolidator](cpp-event-data-types/linker.md) |
|  | Opis | Występuje po uruchomieniu i zatrzymaniu wywołania *link.exe* . |
| <a name="ltcg"></a>LTCG | Typ | Działanie |
|  | Elementy nadrzędne | [PASS1](#pass1) |
|  | Elementy podrzędne | [C2_DLL](#c2-dll) |
|  | Właściwości | Brak |
|  | Klasy przechwytywania | [Działanie](cpp-event-data-types/activity.md)<br/>[LTCG](cpp-event-data-types/ltcg.md) |
|  | Opis | Występuje podczas uruchamiania i zatrzymywania generowania kodu w czasie konsolidacji. |
| <a name="obj-output"></a>OBJ_OUTPUT | Typ | Zdarzenie proste |
|  | Elementy nadrzędne | [COMPILER](#compiler) |
|  | Elementy podrzędne | Brak |
|  | Właściwości | -Ścieżka bezwzględna do pliku wyjściowego *. obj* |
|  | Klasy przechwytywania | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ObjOutput](cpp-event-data-types/obj-output.md) |
|  | Opis | Występuje raz dla każdego *. obj* dane wyjściowe generowane przez *cl.exe*. |
| <a name="opt-icf"></a>OPT_ICF | Typ | Działanie |
|  | Elementy nadrzędne | [PASS1](#pass1) |
|  | Elementy podrzędne | Brak |
|  | Właściwości | Brak |
|  | Klasy przechwytywania | [Działanie](cpp-event-data-types/activity.md)<br/>[OptICF](cpp-event-data-types/opt-icf.md) |
|  | Opis | Występuje po uruchomieniu i zatrzymaniu identycznej optymalizacji konsolidatora COMDAT (/OPT: ICF). |
| <a name="opt-lbr"></a>OPT_LBR | Typ | Działanie |
|  | Elementy nadrzędne | [PASS1](#pass1) |
|  | Elementy podrzędne | Brak |
|  | Właściwości | Brak |
|  | Klasy przechwytywania | [Działanie](cpp-event-data-types/activity.md)<br/>[OptLBR](cpp-event-data-types/opt-lbr.md) |
|  | Opis | Występuje po uruchomieniu i zatrzymaniu optymalizacji konsolidatora długiej gałęzi (/OPT: LBR). |
| <a name="opt-ref"></a>OPT_REF | Typ | Działanie |
|  | Elementy nadrzędne | [PASS1](#pass1) |
|  | Elementy podrzędne | Brak |
|  | Właściwości | Brak |
|  | Klasy przechwytywania | [Działanie](cpp-event-data-types/activity.md)<br/>[OptRef](cpp-event-data-types/opt-ref.md) |
|  | Opis | Występuje na początku i zatrzymywaniu funkcji niezwiązanych z odwołaniami i optymalizacji danych (/OPT: REF). |
| <a name="pass1"></a>PASS1 | Typ | Działanie |
|  | Elementy nadrzędne | [KONSOLIDATORA](#linker) |
|  | Elementy podrzędne | [LTCG](#ltcg)<br/>[OPT_ICF](#opt-icf)<br/>[OPT_LBR](#opt-lbr)<br/>[OPT_REF](#opt-ref) |
|  | Właściwości | Brak |
|  | Klasy przechwytywania | [Działanie](cpp-event-data-types/activity.md)<br/>[Pass1](cpp-event-data-types/pass1.md) |
|  | Opis | Występuje na początku i zatrzymywaniu przebiegu konsolidatora 1. |
| <a name="pass2"></a>PASS2 | Typ | Działanie |
|  | Elementy nadrzędne | [KONSOLIDATORA](#linker) |
|  | Elementy podrzędne | Brak |
|  | Właściwości | Brak |
|  | Klasy przechwytywania | [Działanie](cpp-event-data-types/activity.md)<br/>[Pass2](cpp-event-data-types/pass2.md) |
|  | Opis | Występuje na początku i zatrzymywaniu przebiegu konsolidatora 2. |
| <a name="pre-ltcg-opt-ref"></a>PRE_LTCG_OPT_REF | Typ | Działanie |
|  | Elementy nadrzędne | [PASS1](#pass1) |
|  | Elementy podrzędne | Brak |
|  | Właściwości | Brak |
|  | Klasy przechwytywania | [Działanie](cpp-event-data-types/activity.md)<br/>[PreLTCGOptRef](cpp-event-data-types/pre-ltcg-opt-ref.md) |
|  | Opis | Występuje na początku i po zatrzymaniu optymalizacji konsolidatora, która eliminuje nieużywane funkcje i dane (/OPT: REF). Jest ono wykonywane przed generowaniem kodu w czasie konsolidacji. |
| <a name="symbol-name"></a>SYMBOL_NAME | Typ | Zdarzenie proste |
|  | Elementy nadrzędne | [C1_DLL](#c1-dll) |
|  | Elementy podrzędne | Brak |
|  | Właściwości | -Klucz typu<br/> -Nazwa typu |
|  | Klasy przechwytywania | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[SymbolName](cpp-event-data-types/symbol-name.md) |
|  | Opis | Występuje na końcu przebiegu frontonu: jeden raz dla każdego typu związanego z tworzeniem wystąpień szablonu. Klucz jest identyfikatorem liczbowym dla typu, podczas gdy nazwa jest reprezentacją tekstu. Klucze typów są unikatowe w obrębie analizowanego śledzenia. Jednak różne klucze pochodzące z różnych passów frontonu kompilatora mogą wskazywać na ten sam typ. Porównywanie typów między różnymi passami frontonu kompilatora wymaga użycia ich nazw. Zdarzenia SYMBOL_NAME są emitowane na końcu przejścia frontonu kompilatora, po wykonaniu wszystkich wystąpień szablonu. |
| <a name="template-instantiation"></a>TEMPLATE_INSTANTIATION | Typ | Działanie |
|  | Elementy nadrzędne | [C1_DLL](#c1-dll)<br/>[FRONT_END_FILE](#front-end-file)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Elementy podrzędne | [TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Właściwości | -Klucz dla typu wyspecjalizowanego<br/>-Klucz dla typu szablonu podstawowego<br/>-Rodzaj szablonu, który został skonkretyzowany |
|  | Klasy przechwytywania | [Działanie](cpp-event-data-types/activity.md)<br/>[TemplateInstantiation](cpp-event-data-types/template-instantiation.md) |
|  | Opis | Występuje na początku i na końcu tworzenia wystąpienia szablonu. Typ szablonu podstawowego (na przykład `vector` ) jest skonkretyzowany jako typ wyspecjalizowany (na przykład `std::vector<int>` ). Dla obu typów podano klucz. Użyj zdarzenia [SYMBOL_NAME](#symbol-name) , aby przekonwertować klucz na nazwę typu. Klucze typów są unikatowe w obrębie analizowanego śledzenia. Jednak różne klucze pochodzące z różnych passów frontonu kompilatora mogą wskazywać na ten sam typ. Porównywanie typów między różnymi passami frontonu kompilatora wymaga użycia nazw symboli. To zdarzenie jest cykliczne. Rekursja występuje w niektórych przypadkach, gdy fronton tworzy wystąpienia szablonów zagnieżdżonych. |
| <a name="thread"></a>NICI | Typ | Działanie |
|  | Elementy nadrzędne | [CODE_GENERATION](#code-generation)<br/>[TOP_DOWN](#top-down) |
|  | Elementy podrzędne | [FUNKCYJN](#function) |
|  | Właściwości | Brak |
|  | Klasy przechwytywania | [Działanie](cpp-event-data-types/activity.md)<br/>[Nici](cpp-event-data-types/thread.md) |
|  | Opis | Występuje na początku i na końcu wykonywania wątku zaplecza kompilatora. Wstrzymany wątek jest uznawany za zakończony. Wybudzany wątku jest uznawany za uruchomiony. |
| <a name="top-down"></a>TOP_DOWN | Typ | Działanie |
|  | Elementy nadrzędne | [WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Elementy podrzędne | [FUNKCYJN](#function)<br/>[NICI](#thread) |
|  | Właściwości | Brak |
|  | Klasy przechwytywania | [Działanie](cpp-event-data-types/activity.md)<br/>[TopDown](cpp-event-data-types/top-down.md) |
|  | Opis | Występuje po uruchomieniu i zatrzymaniu przechodzenia do góry w dół analizy całego programu. |
| <a name="whole-program-analysis"></a>WHOLE_PROGRAM_ANALYSIS | Typ | Działanie |
|  | Elementy nadrzędne | [C2_DLL](#c2-dll) |
|  | Elementy podrzędne | [BOTTOM_UP](#bottom-up)<br/>[TOP_DOWN](#top-down) |
|  | Właściwości | Brak |
|  | Klasy przechwytywania | [Działanie](cpp-event-data-types/activity.md)<br/>[WholeProgramAnalysis](cpp-event-data-types/whole-program-analysis.md) |
|  | Opis | Występuje po uruchomieniu i zatrzymaniu fazy analizy całego programu dla generowania kodu w czasie konsolidacji. |

::: moniker-end
