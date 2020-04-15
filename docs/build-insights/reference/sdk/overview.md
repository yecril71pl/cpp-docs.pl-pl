---
title: SDK kompilacji języka C++
description: Omówienie visual studio C++ Kompilacja sdk aplikacji.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Analyzing
- Relogging
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 126abb0d039227eb269500966d46ef0a729763ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323260"
---
# <a name="c-build-insights-sdk"></a>SDK kompilacji języka C++

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Zestaw SDK kompilacji języka C++ to zbiór interfejsów API, które umożliwiają tworzenie spersonalizowanych narzędzi na platformie Konsuwowanie języka C++. Ta strona zawiera omówienie wysokiego poziomu, które ułatwia rozpoczęcie pracy.

## <a name="obtaining-the-sdk"></a>Uzyskanie sdk

Można pobrać C++ Build Insights SDK jako pakiet NuGet, wykonując następujące kroki:

1. W programie Visual Studio 2017 i nowszych utwórz nowy projekt języka C++.
1. W okienku **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt.
1. Z menu kontekstowego **wybierz polecenie Zarządzaj pakietami NuGet.**
1. W prawym górnym rogu wybierz **źródło nuget.org** pakietu.
1. Wyszukaj najnowszą wersję pakietu Microsoft.Cpp.BuildInsights.
1. Wybierz **pozycję Zainstaluj**.
1. Zaakceptuj licencję.

Czytaj dalej, aby uzyskać informacje na temat ogólnych pojęć otaczających SDK. Można również uzyskać dostęp do oficjalnych [przykładów aplikacji GitHub w usłudze C++ Build Insights,](https://github.com/microsoft/cpp-build-insights-samples) aby wyświetlić przykłady prawdziwych aplikacji języka C++, które używają zestawu SDK.

## <a name="collecting-a-trace"></a>Zbieranie śladu

Za pomocą zestawu SDK analizy kompilacji języka C++ do analizowania zdarzeń wychodzących z pęku narzędzi MSVC wymaga, aby najpierw zebrać śledzenia. SDK korzysta z śledzenia zdarzeń dla systemu Windows (ETW) jako podstawowej technologii śledzenia. Zbieranie śladu można wykonać na dwa sposoby:

### <a name="method-1-using-vcperf-in-visual-studio-2019-and-above"></a>Metoda 1: używanie vcperf w programie Visual Studio 2019 i powyżej

1. Otwórz wiersz polecenia narzędzia natywne narzędzia x64 z podwyższonym poziomem uprawnień x64 dla programu VS 2019.
1. Uruchom następujące polecenie:`vcperf /start MySessionName`
1. Skompilowanie projektu.
1. Uruchom następujące polecenie:`vcperf /stopnoanalyze MySessionName outputTraceFile.etl`

   > [!IMPORTANT]
   > Użyj `/stopnoanalyze` polecenia podczas zatrzymywania śledzenia z vcperf. Nie można użyć C++ Build Insights SDK do analizowania `/stop` śladów zatrzymanych przez zwykłe polecenie.

### <a name="method-2-programmatically"></a>Metoda 2: programowo

Użyj dowolnego z tych funkcji kolekcji śledzenia SDK kompilacji języka C++, aby programowo uruchamiać i zatrzymywać ślady. **Program, który wykonuje te wywołania funkcji musi mieć uprawnienia administracyjne.** Tylko funkcje śledzenia uruchamiania i zatrzymywania wymagają uprawnień administracyjnych. Wszystkie inne funkcje w C++ Build Insights SDK mogą być wykonywane bez nich.

### <a name="sdk-functions-related-to-trace-collection"></a>Funkcje SDK związane z kolekcją śledzenia

| Funkcjonalność | Interfejs API języka C++ | C API |
|--|--|--|
| Rozpoczynanie śledzenia | [StartTracingSession (StartTracingSession)](functions/start-tracing-session.md) | [StartTracingSessionA](functions/start-tracing-session-a.md)<br />[StartTracingSessionW](functions/start-tracing-session-w.md) |
| Zatrzymywanie śledzenia | [StopTracingSession (StopTracingSession)](functions/stop-tracing-session.md) | [StopTracingSessionA](functions/stop-tracing-session-a.md)<br />[StopTracingSessionW](functions/stop-tracing-session-w.md) |
| Zatrzymanie śladu i<br />natychmiast analizując wynik | [StopAndAnalyzeTracingSession (StopAndAnalyzeTracingSession)](functions/stop-and-analyze-tracing-session.md) | [StopAndAnalyzeTracingSessionA](functions/stop-and-analyze-tracing-session-a.md)<br />[StopAndAnalyzeTracingSession (StopAndAnalyzeTracingSession)](functions/stop-and-analyze-tracing-session-w.md) |
| Zatrzymanie śladu i<br />natychmiast nalogowanie wyniku | [StopAndRelogTracingSession (StopAndRelogTracingSession)](functions/stop-and-relog-tracing-session.md) | [StopAndRelogTracingSessionA](functions/stop-and-relog-tracing-session-a.md)<br />[StopAndRelogTracingSessionW](functions/stop-and-relog-tracing-session-w.md) |

Sekcje, które należy wykonać pokazują, jak skonfigurować analizę lub sesji ponownego rejestrowania. Jest to wymagane dla połączonych funkcji, takich jak [StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session.md).

## <a name="consuming-a-trace"></a>Korzystanie ze śladu

Po uzyskaniu śledzenia ETW użyj pakietu SDK aplikacji C++ Build Insights, aby go rozpakować. Zestaw SDK udostępnia zdarzenia w formacie, który umożliwia szybkie tworzenie narzędzi. Firma Microsoft nie zaleca korzystania z surowego śledzenia ETW bez użycia sdk. Format zdarzenia używany przez MSVC jest nieudokumentowany, zoptymalizowany do skalowania do ogromnych kompilacji i trudny do wyrozumiałego. Ponadto interfejs API SDK kompilacji języka C++ jest stabilny, podczas gdy nieprzetworzony format śledzenia ETW może ulec zmianie bez powiadomienia.

### <a name="sdk-types-and-functions-related-to-trace-consumption"></a>Typy i funkcje SDK związane z zużyciem śledzenia

| Funkcjonalność | Interfejs API języka C++ | C API | Uwagi |
|--|--|--|--|
| Konfigurowanie wywołań zwrotnych zdarzeń | [IAnalyzer ( IAnalyzer )](other-types/ianalyzer-class.md)<br />[Rejestrator IRelogger](other-types/irelogger-class.md) | [ANALYSIS_CALLBACKS](other-types/analysis-callbacks-struct.md)<br />[RELOG_CALLBACKS](other-types/relog-callbacks-struct.md) | C++ Build Insights SDK udostępnia zdarzenia za pośrednictwem funkcji wywołania zwrotnego. W języku C++ zaimplementuj funkcje wywołania zwrotnego, tworząc klasy analizatora lub reloggera, która dziedziczy interfejs IAnalyzer lub IRelogger. W języku C zaimplementuj wywołania zwrotne w funkcjach globalnych i podaj do nich wskaźniki w strukturze ANALYSIS_CALLBACKS lub RELOG_CALLBACKS. |
| Grupy budowlane | [Grupa MakeStaticAnalyzer](functions/make-static-analyzer-group.md)<br />[Grupa MakeStaticRelogger](functions/make-static-relogger-group.md)<br />[Grupa MakeDynamicAnalyzer](functions/make-dynamic-analyzer-group.md)<br />[Grupa MakeDynamicRelogger](functions/make-dynamic-relogger-group.md) |  | Interfejs API języka C++ udostępnia funkcje i typy pomocnika do grupowania wielu analizatorów i obiektów reloggera razem. Grupy to schludny sposób dzielenia złożonej analizy na prostsze kroki. [vcperf](https://github.com/microsoft/vcperf) jest zorganizowany w ten sposób. |
| Analizowanie lub ponowne rejestrowanie | [Analiza](functions/analyze.md)<br />[Ponownego zarejestrowania](functions/relog.md) | [AnalizaA](functions/analyze-a.md)<br />[AnalizaW](functions/analyze-w.md)<br />[Reloga ( RelogA )](functions/relog-a.md)<br />[RelogW (relogw)](functions/relog-w.md) |  |

### <a name="analyzing-and-relogging"></a>Analizowanie i ponowne rejestrowanie

Korzystanie śledzenia odbywa się za pośrednictwem sesji analizy lub sesji ponownego rejestrowania.

Przy użyciu regularnej analizy jest odpowiedni dla większości scenariuszy. Ta metoda zapewnia elastyczność, aby wybrać `printf` format wyjściowy: tekst, xml, JSON, bazy danych, REST wywołania i tak dalej.

Ponowne rejestrowanie jest przeznaczone do analiz specjalnych, które muszą być potrzebne do wytworzenia pliku wyjściowego ETW. Za pomocą ponownego rejestrowania można przetłumaczyć zdarzenia usługi C++ Build Insights na własny format zdarzenia ETW. Odpowiednie użycie ponownego rejestrowania byłoby podłączyć dane usługi C++ Build Insights do istniejących narzędzi i infrastruktury ETW. Na przykład [vcperf](https://github.com/microsoft/vcperf) korzysta z interfejsów ponownego rejestrowania. To dlatego, że musi produkować dane Analizator wydajności systemu Windows, narzędzie ETW, można zrozumieć. Niektóre wcześniejsze wiedzy o tym, jak działa ETW jest wymagane, jeśli planujesz przy użyciu interfejsów ponownego rejestrowania.

### <a name="creating-analyzer-groups"></a>Tworzenie grup analizatorów

Ważne jest, aby wiedzieć, jak tworzyć grupy. Oto przykład, który pokazuje, jak utworzyć grupę analizatora, która drukuje *Hello, świat!* dla każdego zdarzenia rozpoczęcia działania, które otrzymuje.

```cpp
using namespace Microsoft::Cpp::BuildInsights;

class Hello : public IAnalyzer
{
public:
    AnalysisControl OnStartActivity(
        const EventStack& eventStack) override
    {
        std::cout << "Hello, " << std::endl;
        return AnalysisControl::CONTINUE;
    }
};

class World : public IAnalyzer
{
public:
    AnalysisControl OnStartActivity(
        const EventStack& eventStack) override
    {
        std::cout << "world!" << std::endl;
        return AnalysisControl::CONTINUE;
    }
};

int main()
{
    Hello hello;
    World world;

    // Let's make Hello the first analyzer in the group
    // so that it receives events and prints "Hello, "
    // first.
    auto group = MakeStaticAnalyzerGroup(&hello, &world);

    unsigned numberOfAnalysisPasses = 1;

    // Calling this function initiates the analysis and
    // forwards all events from "inputTrace.etl" to my analyzer
    // group.
    Analyze("inputTrace.etl", numberOfAnalysisPasses, group);

    return 0;
}
```

## <a name="using-events"></a>Korzystanie ze zdarzeń

### <a name="sdk-types-and-functions-related-to-events"></a>Typy i funkcje SDK związane ze zdarzeniami

| Funkcjonalność | Interfejs API języka C++ | C API | Uwagi |
|--|--|--|--|
| Dopasowywanie i filtrowanie zdarzeń | [Funkcja MatchEventStackInMember](functions/match-event-stack-in-member-function.md)<br />[MatchEventStack (własnik dopasowywki)](functions/match-event-stack.md)<br />[Funkcja MatchEventInMemberFunction](functions/match-event-in-member-function.md)<br />[MatchEvent ( MatchEvent )](functions/match-event.md) |  | Interfejs API języka C++ oferuje funkcje, które ułatwiają wyodrębnianie zdarzeń, na których Ci zależy ze śladów. Za pomocą interfejsu API języka C to filtrowanie musi odbywać się ręcznie. |
| Typy danych zdarzeń | [Działanie](cpp-event-data-types/activity.md)<br />[BackEndPass (BackEndPass)](cpp-event-data-types/back-end-pass.md)<br />[Dół](cpp-event-data-types/bottom-up.md)<br />[Biblioteka C1DLL](cpp-event-data-types/c1-dll.md)<br />[Biblioteka C2DLL](cpp-event-data-types/c2-dll.md)<br />[CodeGeneration (Pojęć kodowe)](cpp-event-data-types/code-generation.md)<br />[Commandline](cpp-event-data-types/command-line.md)<br />[Kompilator](cpp-event-data-types/compiler.md)<br />[KompilatorPrzechajnik](cpp-event-data-types/compiler-pass.md)<br />[ŚrodowiskoWaralne](cpp-event-data-types/environment-variable.md)<br />[Zdarzenie](cpp-event-data-types/event.md)<br />[Grupa zdarzeń](cpp-event-data-types/event-group.md)<br />[WydarzenieStack](cpp-event-data-types/event-stack.md)<br />[Plik wykonywalnyImageOutput](cpp-event-data-types/executable-image-output.md)<br />[ExpOutput (ExpOutput)](cpp-event-data-types/exp-output.md)<br />[FileInput (Plucie pliku)](cpp-event-data-types/file-input.md)<br />[FileOutput (FileOutput)](cpp-event-data-types/file-output.md)<br />[ForceInlinee (Linia siłowa)](cpp-event-data-types/force-inlinee.md)<br />[Plik frontu](cpp-event-data-types/front-end-file.md)<br />[Grupa plików frontu](cpp-event-data-types/front-end-file-group.md)<br />[FrontEndPass (Karnet frontu)](cpp-event-data-types/front-end-pass.md)<br />[Funkcja](cpp-event-data-types/function.md)<br />[ImpLibOutput (ImpLibOutput)](cpp-event-data-types/imp-lib-output.md)<br />[Wywołania](cpp-event-data-types/invocation.md)<br />[Grupa invocation](cpp-event-data-types/invocation-group.md)<br />[LibOutput (LibOutput)](cpp-event-data-types/lib-output.md)<br />[Konsolidator](cpp-event-data-types/linker.md)<br />[Grupa konsoli](cpp-event-data-types/linker-group.md)<br />[LinkerPass (LinkerPass)](cpp-event-data-types/linker-pass.md)<br />[Ltcg](cpp-event-data-types/ltcg.md)<br />[ObjOutput (ObjOutput)](cpp-event-data-types/obj-output.md)<br />[OpticF ( OptICF )](cpp-event-data-types/opt-icf.md)<br />[OptLBR (właso)](cpp-event-data-types/opt-lbr.md)<br />[OptRef (Odz.](cpp-event-data-types/opt-ref.md)<br />[Przepustka 1](cpp-event-data-types/pass1.md)<br />[Przepustka 2](cpp-event-data-types/pass2.md)<br />[PreLTCGOptRef](cpp-event-data-types/pre-ltcg-opt-ref.md)<br />[ProsteVent](cpp-event-data-types/simple-event.md)<br />[Nazwa symbolu](cpp-event-data-types/symbol-name.md)<br />[SzablonInstantiation](cpp-event-data-types/template-instantiation.md)<br />[Grupa szablonów](cpp-event-data-types/template-instantiation-group.md)<br />[Wątku](cpp-event-data-types/thread.md)<br />[Doliczanie do góry](cpp-event-data-types/top-down.md)<br />[Traceinfo](cpp-event-data-types/trace-info.md)<br />[WholeProgramAnalysis](cpp-event-data-types/whole-program-analysis.md) | [CL_PASS_DATA](c-event-data-types/cl-pass-data-struct.md)<br />[EVENT_COLLECTION_DATA](c-event-data-types/event-collection-data-struct.md)<br />[EVENT_DATA](c-event-data-types/event-data-struct.md)<br />[EVENT_ID](c-event-data-types/event-id-enum.md)<br />[FILE_DATA](c-event-data-types/file-data-struct.md)<br />[FILE_TYPE_CODE](c-event-data-types/file-type-code-enum.md)<br />[FRONT_END_FILE_DATA](c-event-data-types/front-end-file-data-struct.md)<br />[FUNCTION_DATA](c-event-data-types/function-data-struct.md)<br />[FUNCTION_FORCE_INLINEE_DATA](c-event-data-types/function-force-inlinee-data-struct.md)<br />[INVOCATION_DATA](c-event-data-types/invocation-data-struct.md)<br />[INVOCATION_VERSION_DATA](c-event-data-types/invocation-version-data-struct.md)<br />[MSVC_TOOL_CODE](c-event-data-types/msvc-tool-code-enum.md)<br />[NAME_VALUE_PAIR_DATA](c-event-data-types/name-value-pair-data-struct.md)<br />[SYMBOL_NAME_DATA](c-event-data-types/symbol-name-data-struct.md)<br />[TEMPLATE_INSTANTIATION_DATA](c-event-data-types/template-instantiation-data-struct.md)<br />[TEMPLATE_INSTANTIATION_KIND_CODE](c-event-data-types/template-instantiation-kind-code-enum.md)<br />[TRACE_INFO_DATA](c-event-data-types/trace-info-data-struct.md)<br />[TRANSLATION_UNIT_PASS_CODE](c-event-data-types/translation-unit-pass-code-enum.md) |  |

### <a name="activities-and-simple-events"></a>Aktywności i proste wydarzenia

Wydarzenia są dostępne w dwóch kategoriach: *działania* i *proste wydarzenia.* Działania są procesami w czasie, które mają początek i koniec. Proste zdarzenia są zdarzeniami punktualnymi i nie mają czasu trwania. Podczas analizowania śladów MSVC za pomocą SDK analizy kompilacji języka C++, otrzymasz oddzielne zdarzenia po uruchomieniu i zatrzymaniu działania. Otrzymasz tylko jedno zdarzenie, gdy wystąpi proste zdarzenie.

### <a name="parent-child-relationships"></a>Relacje rodzic-dziecko

Działania i proste zdarzenia są ze sobą powiązane za pośrednictwem relacji nadrzędny-podrzędny. Element nadrzędny działania lub zdarzenia prostego jest obejmujące działania, w którym występują. Na przykład podczas kompilowania pliku źródłowego kompilator musi przeanalizować plik, a następnie wygenerować kod. Analizy i generowania kodu działania są zarówno elementy podrzędne działania kompilatora.

Proste zdarzenia nie mają czasu trwania, więc nic innego nie może się zdarzyć w nich. W związku z tym nigdy nie mają dzieci.

Relacje nadrzędny-podrzędny każdego działania i zdarzenia prostego są wskazane w [tabeli zdarzeń](event-table.md). Znajomość tych relacji jest ważne podczas korzystania z c++ build insights zdarzeń. Często będziesz musiał polegać na nich, aby zrozumieć pełny kontekst zdarzenia.

### <a name="properties"></a>Właściwości

Wszystkie zdarzenia mają następujące właściwości:

| Właściwość | Opis |
|--|--|
| Identyfikator typu | Liczba, która jednoznacznie identyfikuje typ zdarzenia. |
| Identyfikator wystąpienia | Liczba, która jednoznacznie identyfikuje zdarzenie w obrębie śledzenia. Jeśli dwa zdarzenia tego samego typu występują w śledzenia, oba uzyskać unikatowy identyfikator wystąpienia. |
| Godzina rozpoczęcia | Czas rozpoczęcia działania lub czas, w którym wystąpiło proste zdarzenie. |
| Identyfikator procesu | Liczba identyfikująca proces, w którym wystąpiło zdarzenie. |
| Identyfikator wątku | Liczba identyfikująca wątek, w którym wystąpiło zdarzenie. |
| Indeks procesora | Indeks od zera wskazujący, który procesor logiczny zdarzenie zostało wyemitowane przez. |
| Nazwa wydarzenia | Ciąg opisujący typ zdarzenia. |

Wszystkie działania inne niż zdarzenia proste mają również następujące właściwości:

| Właściwość | Opis |
|--|--|
| Czas zatrzymania | Czas, w którym działanie się zatrzymało. |
| Czas wyłączności | Czas spędzony w działaniu, z wyłączeniem czasu spędzonego w jego zajęciach podrzędnych. |
| Czas procesora | Czas, który procesor cpu spędził wykonywania kodu w wątku dołączone do działania. Nie zawiera czasu, gdy wątek dołączony do działania był uśpiony. |
| Ekskluzywny czas procesora | Tak samo jak czas procesora CPU, ale z wyłączeniem czasu procesora CPU spędzonego przez działania podrzędne. |
| Odpowiedzialność za czas zegara ściennego | Wkład działalności w ogólny czas zegara ściennego. Odpowiedzialność za czas zegara ściennego uwzględnia równoległość między działaniami. Załóżmy na przykład, że dwa niepowiązanych działań są uruchamiane równolegle. Oba mają czas trwania 10 sekund, a dokładnie ten sam czas rozpoczęcia i zatrzymania. W takim przypadku build insights przypisuje zarówno odpowiedzialność zegara ściennego 5 sekund. Z drugiej strony, jeśli te działania uruchomić jeden po drugim bez nakładania się, są one przypisane odpowiedzialność zegara ściennego 10 sekund. |
| Wyłączna odpowiedzialność za czas zegara ściennego | Tak samo jak odpowiedzialność czasu zegara ściennego, ale wyklucza odpowiedzialność czasu zegara ściennego za działania dziecka. |

Niektóre wydarzenia mają swoje własne właściwości poza tymi, o których mowa. W takim przypadku te dodatkowe właściwości są wymienione w [tabeli zdarzeń](event-table.md).

### <a name="consuming-events-provided-by-the-c-build-insights-sdk"></a>Korzystanie ze zdarzeń dostarczanych przez sdk analizy kompilacji języka C++

#### <a name="the-event-stack"></a>Stos zdarzeń

Ilekroć zestaw SDK kompilacji języka C++ daje zdarzenie, jest w postaci stosu. Ostatni wpis w stosie jest bieżącym zdarzeniem, a wpisy przed nim są jego hierarchii nadrzędnej. Na przykład [LTCG](event-table.md#ltcg) start i stop zdarzenia występują podczas przebiegu 1 konsolidatora. W takim przypadku \[stos, który otrzymasz, zawiera: [LINKER](event-table.md#linker), [PASS1](event-table.md#pass1), LTCG\]. Hierarchia nadrzędna jest wygodna, ponieważ można prześledzić zdarzenie do jego katalogu głównego. Jeśli działanie LTCG wymienione powyżej jest powolne, można natychmiast dowiedzieć się, które wywołanie konsolidator był zaangażowany.

#### <a name="matching-events-and-event-stacks"></a>Pasujące zdarzenia i stosy zdarzeń

Zestaw SDK kompilacji aplikacji C++ umożliwia każde zdarzenie śledzenia, ale przez większość czasu zależy Ci tylko na podzbiorze. W niektórych przypadkach możesz dotyczyć tylko podzbioru *stosów zdarzeń.* Zestaw SDK udostępnia udogodnienia ułatwiające szybkie wyodrębnianie potrzebnych zdarzeń lub stosu zdarzeń i odrzucenie tych, których nie potrzebujesz. Odbywa się to za pomocą tych funkcji dopasowania:

|  |  |
|--|--|
| [MatchEvent ( MatchEvent )](functions/match-event.md) | Zachowaj zdarzenie, jeśli pasuje do jednego z określonych typów. Do przodu dopasowane zdarzenia do lambda lub innego typu wywoływane. Hierarchia nadrzędna zdarzenia nie jest brana pod uwagę przez tę funkcję. |
| [Funkcja MatchEventInMemberFunction](functions/match-event-in-member-function.md) | Zachowaj zdarzenie, jeśli pasuje do typu określonego w parametrze funkcji elementu członkowskiego. Do przodu dopasowane zdarzenia do funkcji elementu członkowskiego. Hierarchia nadrzędna zdarzenia nie jest brana pod uwagę przez tę funkcję. |
| [MatchEventStack (własnik dopasowywki)](functions/match-event-stack.md) | Zachowaj zdarzenie, jeśli zarówno zdarzenie, jak i jego hierarchia nadrzędna są zgodne z określonymi typami. Prześlij dalej zdarzenie i dopasowane zdarzenia hierarchii nadrzędnej do lambda lub innego typu wywoływanego. |
| [Funkcja MatchEventStackInMember](functions/match-event-stack-in-member-function.md) | Zachowaj zdarzenie, jeśli zarówno zdarzenie, jak i jego hierarchia nadrzędna są zgodne z typami określonymi na liście parametrów funkcji elementu członkowskiego. Prześlij dalej zdarzenie i dopasowane zdarzenia hierarchii nadrzędnej do funkcji elementu członkowskiego. |

Funkcje dopasowywania stosu zdarzeń, takie jak `MatchEventStack` zezwalaj na przerwy podczas opisywania hierarchii nadrzędnej, aby dopasować. Na przykład, można powiedzieć, że \[jesteś zainteresowany [linker](event-table.md#linker), [LTCG](event-table.md#ltcg) \] stosu. Byłoby to również \[zgodne z LINKER,\] [PASS1](event-table.md#pass1), LTCG stosu. Ostatni określony typ musi być typem zdarzenia, aby dopasować i nie jest częścią hierarchii nadrzędnej.

#### <a name="capture-classes"></a>Przechwytywanie klas

Korzystanie `Match*` z funkcji wymaga określenia typów, które mają być zgodne. Te typy są wybierane z listy *klas przechwytywania*. Klasy przechwytywania są dostępne w kilku kategoriach, opisanych poniżej.

| Kategoria | Opis |
|--|--|
| Exact | Te klasy przechwytywania są używane do dopasowania określonego typu zdarzenia i żaden inny. Przykładem jest [kompilator](cpp-event-data-types/compiler.md) klasy, która pasuje [do zdarzenia KOMPILATOR.](event-table.md#compiler) |
| Symbol wieloznaczny | Te klasy przechwytywania mogą służyć do dopasowania dowolnego zdarzenia z listy zdarzeń, które obsługują. Na przykład [symbol wieloznaczny działania](cpp-event-data-types/activity.md) pasuje do dowolnego zdarzenia działania. Innym przykładem jest [symbol wieloznaczny CompilerPass,](cpp-event-data-types/compiler-pass.md) który może być zgodny [z FRONT_END_PASS](event-table.md#front-end-pass) lub [BACK_END_PASS](event-table.md#back-end-pass) zdarzenia. |
| Grupa | Nazwy klas przechwytywania grup kończą się w *grupie*. Są one używane do dopasowania wielu zdarzeń tego samego typu w wierszu, ignorując luki. Mają one sens tylko podczas dopasowywania zdarzeń cyklicznych, ponieważ nie wiesz, ile istnieje w stosie zdarzeń. Na przykład [działanie FRONT_END_FILE](event-table.md#front-end-file) dzieje się za każdym razem, gdy kompilator analizuje plik. To działanie jest cykliczne, ponieważ kompilator może znaleźć include dyrektywy podczas analizowania pliku. [Klasa FrontEndFile](cpp-event-data-types/front-end-file.md) pasuje tylko do jednego zdarzenia FRONT_END_FILE w stosie. Użyj [Klasy FrontEndFileGroup,](cpp-event-data-types/front-end-file-group.md) aby dopasować całą hierarchię dołączania. |
| Grupa symboli wieloznacznych | Grupa symboli wieloznacznych łączy właściwości symboli wieloznacznych i grup. Jedyną klasą tej kategorii jest [InvocationGroup](cpp-event-data-types/invocation-group.md), które pasują i przechwytują wszystkie zdarzenia [LINKER](event-table.md#linker) i [KOMPILATOR](event-table.md#compiler) w stosie pojedynczych zdarzeń. |

Zapoznaj się z [tabelą zdarzeń,](event-table.md) aby dowiedzieć się, które klasy przechwytywania mogą być używane do dopasowania każdego zdarzenia.

#### <a name="after-matching-using-captured-events"></a>Po dopasowaniu: używanie przechwyconych zdarzeń

Po pomyślnym zakończeniu dopasowania `Match*` funkcje konstruują obiekty klasy przechwytywania i przekazuje je do określonej funkcji. Użyj tych obiektów klasy przechwytywania, aby uzyskać dostęp do właściwości zdarzeń.

#### <a name="example"></a>Przykład

```cpp
AnalysisControl MyAnalyzer::OnStartActivity(const EventStack& eventStack)
{
    // The event types to match are specified in the PrintIncludes function
    // signature.  
    MatchEventStackInMemberFunction(eventStack, this, &MyAnalyzer::PrintIncludes);
}

// We want to capture event stacks where:
// 1. The current event is a FrontEndFile activity.
// 2. The current FrontEndFile activity has at least one parent FrontEndFile activity
//    and possibly many.
void PrintIncludes(FrontEndFileGroup parentIncludes, FrontEndFile currentFile)
{
    // Once we reach this point, the event stack we are interested in has been matched.
    // The current FrontEndFile activity has been captured into 'currentFile', and
    // its entire inclusion hierarchy has been captured in 'parentIncludes'.

    cout << "The current file being parsed is: " << currentFile.Path() << endl;
    cout << "This file was reached through the following inclusions:" << endl;

    for (auto& f : parentIncludes)
    {
        cout << f.Path() << endl;
    }
}
```

::: moniker-end
