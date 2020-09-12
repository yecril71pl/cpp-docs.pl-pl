---
title: Zestaw SDK ze szczegółowymi informacjami o kompilowaniu w języku C++
description: Omówienie zestawu SDK usługi Visual Studio C++ build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Analyzing
- Relogging
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6f53a9b6c682a0af7d8a01f6378ed0574d8fa4ca
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041175"
---
# <a name="c-build-insights-sdk"></a>Zestaw SDK ze szczegółowymi informacjami o kompilowaniu w języku C++

::: moniker range="<=vs-2015"

Zestaw SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora **wersji** programu Visual Studio dla tego artykułu na visual Studio 2017 lub visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Zestaw SDK usługi Build Insights to zbiór interfejsów API, które umożliwiają tworzenie spersonalizowanych narzędzi na platformie C++ build Insights. Ta strona zawiera ogólne omówienie ułatwiające rozpoczęcie pracy.

## <a name="obtaining-the-sdk"></a>Uzyskiwanie zestawu SDK

Zestaw SDK kompilacji usługi Build Insights można pobrać jako pakiet NuGet, wykonując następujące czynności:

1. W programie Visual Studio 2017 lub nowszym Utwórz nowy projekt w języku C++.
1. W okienku **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt.
1. Wybierz pozycję **Zarządzaj pakietami NuGet** z menu kontekstowego.
1. W prawym górnym rogu wybierz źródło pakietu **NuGet.org** .
1. Wyszukaj najnowszą wersję pakietu Microsoft. cpp. BuildInsights.
1. Wybierz pozycję **Zainstaluj**.
1. Zaakceptuj licencję.

Zapoznaj się z informacjami na temat ogólnych pojęć związanych z zestawem SDK. Możesz również uzyskać dostęp do oficjalnych [przykładów usługi Build Insights](https://github.com/microsoft/cpp-build-insights-samples) w witrynie GitHub, aby zobaczyć przykłady rzeczywistych aplikacji w języku c++, które używają zestawu SDK.

## <a name="collecting-a-trace"></a>Zbieranie śladu

Korzystanie z zestawu SDK usługi Build Insights do analizowania zdarzeń wychodzących z MSVC łańcucha narzędzi wymaga najpierw zebrania śladu. Zestaw SDK wykorzystuje śledzenie zdarzeń systemu Windows (ETW) jako podstawową technologię śledzenia. Zbieranie śladów można wykonać na dwa sposoby:

### <a name="method-1-using-vcperf-in-visual-studio-2019-and-above"></a>Metoda 1. Używanie vcperf w programie Visual Studio 2019 lub nowszym

1. Otwórz wiersz polecenia narzędzi x64 Native Tools z podwyższonym poziomem uprawnień dla programu VS 2019.
1. Uruchom następujące polecenie: `vcperf /start MySessionName`
1. Skompilowanie projektu.
1. Uruchom następujące polecenie: `vcperf /stopnoanalyze MySessionName outputTraceFile.etl`

   > [!IMPORTANT]
   > Użyj `/stopnoanalyze` polecenia podczas zatrzymywania śledzenia za pomocą vcperf. Nie można użyć zestawu SDK usługi Build Insights do analizowania śladów zatrzymanych przez regularne `/stop` polecenie.

### <a name="method-2-programmatically"></a>Metoda 2. programowane

Użyj dowolnej z tych funkcji zbierania danych śledzenia zestawu SDK w usłudze C++ build Insights do programistycznego uruchamiania i zatrzymywania śledzenia. **Program wykonujący te wywołania funkcji musi mieć uprawnienia administracyjne.** Tylko funkcje uruchamiania i zatrzymywania śledzenia wymagają uprawnień administracyjnych. Wszystkie inne funkcje w zestawie SDK usługi Build Insights można wykonać bez nich.

### <a name="sdk-functions-related-to-trace-collection"></a>Funkcje zestawu SDK powiązane z kolekcją śledzenia

| Funkcjonalność | Interfejs API języka C++ | INTERFEJS API JĘZYKA C |
|--|--|--|
| Rozpoczynanie śledzenia | [StartTracingSession](functions/start-tracing-session.md) | [StartTracingSessionA](functions/start-tracing-session-a.md)<br />[StartTracingSessionW](functions/start-tracing-session-w.md) |
| Zatrzymywanie śledzenia | [StopTracingSession](functions/stop-tracing-session.md) | [StopTracingSessionA](functions/stop-tracing-session-a.md)<br />[StopTracingSessionW](functions/stop-tracing-session-w.md) |
| Zatrzymywanie śledzenia i<br />natychmiastowe analizowanie wyniku | [StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session.md) | [StopAndAnalyzeTracingSessionA](functions/stop-and-analyze-tracing-session-a.md)<br />[StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session-w.md) |
| Zatrzymywanie śledzenia i<br />Natychmiastowe rejestrowanie wyniku | [StopAndRelogTracingSession](functions/stop-and-relog-tracing-session.md) | [StopAndRelogTracingSessionA](functions/stop-and-relog-tracing-session-a.md)<br />[StopAndRelogTracingSessionW](functions/stop-and-relog-tracing-session-w.md) |

W poniższych sekcjach przedstawiono sposób konfigurowania analizy lub sesji ponownego rejestrowania. Jest to wymagane w przypadku funkcji połączonych funkcji, takich jak [StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session.md).

## <a name="consuming-a-trace"></a>Zużywanie śladu

Po utworzeniu śledzenia ETW Użyj zestawu SDK usługi Build Insights, aby go rozpakować. Zestaw SDK udostępnia zdarzenia w formacie, który umożliwia szybkie tworzenie narzędzi. Nie zalecamy korzystania z nieprzetworzonego śledzenia ETW bez użycia zestawu SDK. Format zdarzenia używany przez MSVC jest nieudokumentowany, zoptymalizowany pod kątem skalowania do dużych kompilacji i trudno jest zrozumieć. Ponadto interfejs API zestawu SDK usługi Build Insights jest stabilny, podczas gdy pierwotny format śledzenia ETW może ulec zmianie bez powiadomienia.

### <a name="sdk-types-and-functions-related-to-trace-consumption"></a>Typy i funkcje zestawu SDK związane z użyciem śledzenia

| Funkcjonalność | Interfejs API języka C++ | INTERFEJS API JĘZYKA C | Uwagi |
|--|--|--|--|
| Konfigurowanie wywołań zwrotnych zdarzeń | [IAnalyzer](other-types/ianalyzer-class.md)<br />[IRelogger](other-types/irelogger-class.md) | [ANALYSIS_CALLBACKS](other-types/analysis-callbacks-struct.md)<br />[RELOG_CALLBACKS](other-types/relog-callbacks-struct.md) | Zestaw SDK usługi Build Insights w wersji C++ udostępnia zdarzenia za pomocą funkcji wywołania zwrotnego. W języku C++ zaimplementuj funkcje wywołania zwrotnego, tworząc Analizator lub klasę rerejestratora, która dziedziczy interfejs IAnalyzer lub IRelogger. W języku C Zaimplementuj wywołania zwrotne w funkcjach globalnych i podaj do nich wskaźniki w strukturze ANALYSIS_CALLBACKS lub RELOG_CALLBACKS. |
| Kompilowanie grup | [MakeStaticAnalyzerGroup](functions/make-static-analyzer-group.md)<br />[MakeStaticReloggerGroup](functions/make-static-relogger-group.md)<br />[MakeDynamicAnalyzerGroup](functions/make-dynamic-analyzer-group.md)<br />[MakeDynamicReloggerGroup](functions/make-dynamic-relogger-group.md) |  | Interfejs API języka C++ udostępnia funkcje i typy pomocnika do grupowania wielu obiektów analizatora i ponownego rejestratora. Grupy to sposób, aby podzielić złożoną analizę na prostsze czynności. [vcperf](https://github.com/microsoft/vcperf) jest zorganizowany w ten sposób. |
| Analizowanie i ponowne rejestrowanie | [Analiza](functions/analyze.md)<br />[Relog](functions/relog.md) | [AnalyzeA](functions/analyze-a.md)<br />[AnalyzeW](functions/analyze-w.md)<br />[RelogA](functions/relog-a.md)<br />[RelogW](functions/relog-w.md) |  |

### <a name="analyzing-and-relogging"></a>Analizowanie i ponowne rejestrowanie

Używanie śledzenia odbywa się za pomocą sesji analizy lub sesji rejestrowania.

Używanie regularnej analizy jest odpowiednie dla większości scenariuszy. Ta metoda zapewnia elastyczność wybierania formatu danych wyjściowych: `printf` tekst, XML, JSON, baza danych, wywołania REST itd.

Ponowne rejestrowanie dotyczy analiz specjalnych, które wymagają utworzenia pliku wyjściowego ETW. Przy użyciu ponownego rejestrowania można przetłumaczyć zdarzenia usługi C++ build Insights na własny format zdarzenia ETW. Odpowiednim zastosowaniem ponownego rejestrowania będzie podłączać dane kompilacji C++ do istniejących narzędzi i infrastruktury funkcji ETW. Na przykład [vcperf](https://github.com/microsoft/vcperf) korzysta z interfejsów rejestrowania. Jest to spowodowane tym, że musi utworzyć dane analizatora wydajności systemu Windows, narzędzie ETW, które może zrozumieć. Niektóre z wcześniejszych informacji na temat działania funkcji ETW są wymagane, jeśli planujesz korzystanie z interfejsów rejestrowania.

### <a name="creating-analyzer-groups"></a>Tworzenie grup analizatora

Ważne jest, aby dowiedzieć się, jak tworzyć grupy. Oto przykład, który pokazuje, jak utworzyć grupę analizatorów, która drukuje *Hello, World!* dla każdego zdarzenia uruchomienia działania, które odbiera.

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

## <a name="using-events"></a>Korzystanie z zdarzeń

### <a name="sdk-types-and-functions-related-to-events"></a>Typy i funkcje zestawu SDK związane ze zdarzeniami

| Funkcjonalność | Interfejs API języka C++ | INTERFEJS API JĘZYKA C | Uwagi |
|--|--|--|--|
| Dopasowywanie i filtrowanie zdarzeń | [MatchEventStackInMemberFunction](functions/match-event-stack-in-member-function.md)<br />[MatchEventStack](functions/match-event-stack.md)<br />[MatchEventInMemberFunction](functions/match-event-in-member-function.md)<br />[MatchEvent](functions/match-event.md) |  | Interfejs API języka C++ oferuje funkcje, które ułatwiają wyodrębnienie zdarzeń, z których korzystasz ze śladów. Korzystając z interfejsu API języka C, to filtrowanie musi być wykonywane ręcznie. |
| Typy danych zdarzenia | [Działanie](cpp-event-data-types/activity.md)<br />[BackEndPass](cpp-event-data-types/back-end-pass.md)<br />[BottomUp](cpp-event-data-types/bottom-up.md)<br />[C1DLL](cpp-event-data-types/c1-dll.md)<br />[C2DLL](cpp-event-data-types/c2-dll.md)<br />[CodeGeneration](cpp-event-data-types/code-generation.md)<br />[CommandLine](cpp-event-data-types/command-line.md)<br />[Compiler](cpp-event-data-types/compiler.md)<br />[CompilerPass](cpp-event-data-types/compiler-pass.md)<br />[EnvironmentVariable](cpp-event-data-types/environment-variable.md)<br />[Wydarzenie](cpp-event-data-types/event.md)<br />[EventGroup](cpp-event-data-types/event-group.md)<br />[EventStack](cpp-event-data-types/event-stack.md)<br />[ExecutableImageOutput](cpp-event-data-types/executable-image-output.md)<br />[ExpOutput](cpp-event-data-types/exp-output.md)<br />[FileInput](cpp-event-data-types/file-input.md)<br />[FileOutput](cpp-event-data-types/file-output.md)<br />[ForceInlinee](cpp-event-data-types/force-inlinee.md)<br />[FrontEndFile](cpp-event-data-types/front-end-file.md)<br />[FrontEndFileGroup](cpp-event-data-types/front-end-file-group.md)<br />[FrontEndPass](cpp-event-data-types/front-end-pass.md)<br />[Funkcja](cpp-event-data-types/function.md)<br />[ImpLibOutput](cpp-event-data-types/imp-lib-output.md)<br />[Invocation](cpp-event-data-types/invocation.md)<br />[InvocationGroup](cpp-event-data-types/invocation-group.md)<br />[LibOutput](cpp-event-data-types/lib-output.md)<br />[Konsolidator](cpp-event-data-types/linker.md)<br />[LinkerGroup](cpp-event-data-types/linker-group.md)<br />[LinkerPass](cpp-event-data-types/linker-pass.md)<br />[LTCG](cpp-event-data-types/ltcg.md)<br />[ObjOutput](cpp-event-data-types/obj-output.md)<br />[OptICF](cpp-event-data-types/opt-icf.md)<br />[OptLBR](cpp-event-data-types/opt-lbr.md)<br />[OptRef](cpp-event-data-types/opt-ref.md)<br />[Pass1](cpp-event-data-types/pass1.md)<br />[Pass2](cpp-event-data-types/pass2.md)<br />[PreLTCGOptRef](cpp-event-data-types/pre-ltcg-opt-ref.md)<br />[SimpleEvent](cpp-event-data-types/simple-event.md)<br />[SymbolName](cpp-event-data-types/symbol-name.md)<br />[TemplateInstantiation](cpp-event-data-types/template-instantiation.md)<br />[TemplateInstantiationGroup](cpp-event-data-types/template-instantiation-group.md)<br />[Nici](cpp-event-data-types/thread.md)<br />[TopDown](cpp-event-data-types/top-down.md)<br />[TraceInfo](cpp-event-data-types/trace-info.md)<br />[WholeProgramAnalysis](cpp-event-data-types/whole-program-analysis.md) | [CL_PASS_DATA](c-event-data-types/cl-pass-data-struct.md)<br />[EVENT_COLLECTION_DATA](c-event-data-types/event-collection-data-struct.md)<br />[EVENT_DATA](c-event-data-types/event-data-struct.md)<br />[EVENT_ID](c-event-data-types/event-id-enum.md)<br />[FILE_DATA](c-event-data-types/file-data-struct.md)<br />[FILE_TYPE_CODE](c-event-data-types/file-type-code-enum.md)<br />[FRONT_END_FILE_DATA](c-event-data-types/front-end-file-data-struct.md)<br />[FUNCTION_DATA](c-event-data-types/function-data-struct.md)<br />[FUNCTION_FORCE_INLINEE_DATA](c-event-data-types/function-force-inlinee-data-struct.md)<br />[INVOCATION_DATA](c-event-data-types/invocation-data-struct.md)<br />[INVOCATION_VERSION_DATA](c-event-data-types/invocation-version-data-struct.md)<br />[MSVC_TOOL_CODE](c-event-data-types/msvc-tool-code-enum.md)<br />[NAME_VALUE_PAIR_DATA](c-event-data-types/name-value-pair-data-struct.md)<br />[SYMBOL_NAME_DATA](c-event-data-types/symbol-name-data-struct.md)<br />[TEMPLATE_INSTANTIATION_DATA](c-event-data-types/template-instantiation-data-struct.md)<br />[TEMPLATE_INSTANTIATION_KIND_CODE](c-event-data-types/template-instantiation-kind-code-enum.md)<br />[TRACE_INFO_DATA](c-event-data-types/trace-info-data-struct.md)<br />[TRANSLATION_UNIT_PASS_CODE](c-event-data-types/translation-unit-pass-code-enum.md) |  |

### <a name="activities-and-simple-events"></a>Działania i zdarzenia proste

Zdarzenia są dostępne w dwóch kategoriach: *działania* i *proste zdarzenia*. Działania są ciągłymi procesami, które mają początek i zakończenie. Proste zdarzenia to punktualne wystąpienia i nie mają czasu trwania. Podczas analizowania śladów MSVC za pomocą zestawu SDK języka C++ build Insights otrzymasz oddzielne zdarzenia, gdy działanie zostanie uruchomione i zatrzymane. Po wystąpieniu prostego zdarzenia otrzymasz tylko jedno zdarzenie.

### <a name="parent-child-relationships"></a>Relacje nadrzędny-podrzędny

Działania i proste zdarzenia są ze sobą powiązane za pośrednictwem relacji nadrzędny-podrzędny. Elementem nadrzędnym działania lub prostego zdarzenia jest działanie obejmujące, w którym występują. Na przykład podczas kompilowania pliku źródłowego kompilator musi analizować plik, a następnie generować kod. Operacje analizowania i generowania kodu są elementami podrzędnymi działania kompilatora.

Proste zdarzenia nie mają czasu trwania, dlatego nie może wystąpić żadne inne inne elementy. W związku z tym nigdy nie mają żadnych elementów podrzędnych.

Relacje nadrzędny-podrzędny każdego działania i prostego zdarzenia są wskazane w [tabeli zdarzeń](event-table.md). Znajomość tych relacji jest ważna podczas zużywania zdarzeń w usłudze C++ build Insights. Często należy polegać na nich, aby zrozumieć pełen kontekst zdarzenia.

### <a name="properties"></a>Właściwości

Wszystkie zdarzenia mają następujące właściwości:

| Właściwość | Opis |
|--|--|
| Identyfikator typu | Liczba, która jednoznacznie identyfikuje typ zdarzenia. |
| Identyfikator wystąpienia | Liczba, która jednoznacznie identyfikuje zdarzenie w wyniku śledzenia. Jeśli dwa zdarzenia tego samego typu występują w ślad, oba otrzymują unikatowy identyfikator wystąpienia. |
| Godzina rozpoczęcia | Godzina rozpoczęcia działania lub czas wystąpienia prostego zdarzenia. |
| Identyfikator procesu | Liczba, która identyfikuje proces, w którym wystąpiło zdarzenie. |
| Identyfikator wątku | Liczba, która identyfikuje wątek, w którym wystąpiło zdarzenie. |
| Indeks procesora | Indeks (liczony od zera) wskazujący, który procesor logiczny został wyemitowany przez zdarzenie. |
| Nazwa zdarzenia | Ciąg opisujący typ zdarzenia. |

Wszystkie działania inne niż zdarzenia proste mają również następujące właściwości:

| Właściwość | Opis |
|--|--|
| Czas zakończenia | Czas zatrzymania działania. |
| Wyłączny czas trwania | Czas spędzony na działaniu, z wyłączeniem czasu spędzonego na działaniach podrzędnych. |
| Czas procesora CPU | Czas poświęcany przez procesor na wykonanie kodu w wątku dołączonym do działania. Nie obejmuje czasu, gdy wątek dołączony do działania był uśpiony. |
| Wyłączny czas procesora CPU | Taka sama jak czas procesora CPU, ale z wyłączeniem czasu procesora CPU przez działania podrzędne. |
| Odpowiedzialność za czas zegara | Wkład działania do ogólnego czasu zegarka. Odpowiedzialność za czas zegara jest uwzględniana równolegle między działaniami. Załóżmy na przykład, że dwa niepowiązane działania są uruchamiane równolegle. Oba mają długość równą 10 sekund i dokładnie te same godziny rozpoczęcia i zakończenia. W takim przypadku kompilacja usługi Build Insights przypisze Czas zegarowy do 5 sekund. W przeciwieństwie do tego, czy te działania działają jeden po drugim bez nakładania się, oba te zadania są przypisane do czasu, który jest odpowiedzialny za czas zegara przez 10 sekund. |
| Wyłączna odpowiedzialność za czas zegara ściany | Analogicznie do odpowiedzialności za czas zegara ściennego, ale wyklucza to odpowiedzialność za czas zegara ściany w działaniach podrzędnych. |

Niektóre zdarzenia mają własne właściwości wykraczające poza wymienione powyżej. W takim przypadku te dodatkowe właściwości są wymienione w [tabeli zdarzeń](event-table.md).

### <a name="consuming-events-provided-by-the-c-build-insights-sdk"></a>Zużywanie zdarzeń dostarczonych przez zestaw SDK usługi Build Insights

#### <a name="the-event-stack"></a>Stos zdarzeń

Za każdym razem, gdy zestaw SDK usługi Build Insights zawiera zdarzenie, znajduje się w formie stosu. Ostatni wpis w stosie to bieżące zdarzenie, a wpisy, zanim są jego hierarchią nadrzędną. Na przykład [LTCG](event-table.md#ltcg) zdarzenia uruchamiania i zatrzymywania występują podczas przebiegu 1 konsolidatora. W takim przypadku otrzymany stos zawiera: \[ [konsolidator](event-table.md#linker), [PASS1](event-table.md#pass1), LTCG \] . Hierarchia nadrzędna jest wygodna, ponieważ można śledzić zdarzenia do jego katalogu głównego. Jeśli działanie LTCG wymienione powyżej jest powolne, możesz od razu sprawdzić, które wywołanie konsolidatora zostało uwzględnione.

#### <a name="matching-events-and-event-stacks"></a>Zgodne zdarzenia i stosy zdarzeń

Zestaw SDK usługi Build Insights w wersji zapoznawczej udostępnia każde zdarzenie w śladach, ale większość z nich zajmuje się tylko ich podzbiorem. W niektórych przypadkach można zadbać o to tylko podzbiór *stosów zdarzeń*. Zestaw SDK udostępnia funkcje ułatwiające szybkie wyodrębnienie potrzebnych zdarzeń lub stosu zdarzeń oraz odrzucanie tych elementów. Jest to wykonywane przez następujące zgodne funkcje:

| Funkcja | Opis |
|--|--|
| [MatchEvent](functions/match-event.md) | Zachowaj zdarzenie, jeśli odpowiada jednemu z określonych typów. Przekazuj zdarzenia dopasowane do typu lambda lub innego elementu, który można wywołać. Hierarchia nadrzędna zdarzenia nie jest uważana za tę funkcję. |
| [MatchEventInMemberFunction](functions/match-event-in-member-function.md) | Zachowaj zdarzenie, jeśli jest ono zgodne z typem określonym w parametrze funkcji składowej. Przekazuj zdarzenia dopasowane do funkcji członkowskiej. Hierarchia nadrzędna zdarzenia nie jest uważana za tę funkcję. |
| [MatchEventStack](functions/match-event-stack.md) | Zachowaj zdarzenie, jeśli zarówno zdarzenie, jak i jego hierarchia nadrzędna są zgodne z określonymi typami. Prześlij dalej zdarzenie i dopasowane zdarzenia nadrzędnej hierarchii do typu lambda lub innego, który można wywołać. |
| [MatchEventStackInMemberFunction](functions/match-event-stack-in-member-function.md) | Zachowaj zdarzenie, jeśli zarówno zdarzenie, jak i jego hierarchia nadrzędna są zgodne z typami określonymi na liście parametrów funkcji składowej. Prześlij dalej zdarzenie i dopasowane zdarzenia nadrzędnej hierarchii do funkcji członkowskiej. |

Funkcja dopasowania stosu zdarzeń, taka jak `MatchEventStack` Zezwalaj na przerwy podczas opisywania hierarchii nadrzędnej do dopasowania. Na przykład możesz powiedzieć, że interesuje Cię program \[ [konsolidator](event-table.md#linker), stos [LTCG](event-table.md#ltcg) \] . Również dopasowuje się do \[ stosu konsolidatora, [PASS1](event-table.md#pass1)LTCG \] . Ostatni określony typ musi być typem zdarzenia do dopasowania i nie jest częścią hierarchii nadrzędnej.

#### <a name="capture-classes"></a>Klasy przechwytywania

Korzystanie z `Match*` funkcji wymaga określenia typów, które mają być zgodne. Te typy są wybierane z listy *klas przechwytywania*. Klasy przechwytywania pochodzą z kilku kategorii opisanych poniżej.

| Kategoria | Opis |
|--|--|
| Exact | Te klasy przechwytywania są używane do dopasowania określonego typu zdarzenia i nie są inne. Przykładem jest Klasa [kompilatora](cpp-event-data-types/compiler.md) , która odpowiada zdarzeniu [kompilatora](event-table.md#compiler) . |
| Znaku | Te klasy przechwytywania mogą służyć do dopasowania dowolnego zdarzenia z listy zdarzeń, które są przez nie obsługiwane. Na przykład symbol wieloznaczny [działania](cpp-event-data-types/activity.md) pasuje do dowolnego zdarzenia działania. Innym przykładem jest [CompilerPass](cpp-event-data-types/compiler-pass.md) symbol wieloznaczny, który może pasować do [FRONT_END_PASS](event-table.md#front-end-pass) lub [BACK_END_PASS](event-table.md#back-end-pass) zdarzenia. |
| Group (Grupa) | Nazwy klas przechwytywania grupy kończą się w *grupie*. Są one używane do dopasowania wielu zdarzeń tego samego typu w wierszu, ignorując luki. Są one sensowne tylko podczas dopasowywania zdarzeń cyklicznych, ponieważ nie wiadomo, ile istnieje w stosie zdarzeń. Na przykład działanie [FRONT_END_FILE](event-table.md#front-end-file) odbywa się za każdym razem, gdy kompilator analizuje plik. To działanie jest cykliczne, ponieważ kompilator może znaleźć dyrektywę include podczas analizy pliku. Klasa [FrontEndFile](cpp-event-data-types/front-end-file.md) dopasowuje tylko jedno zdarzenie FRONT_END_FILE w stosie. Użyj klasy [FrontEndFileGroup](cpp-event-data-types/front-end-file-group.md) , aby dopasować całą hierarchię dołączania. |
| Grupa symboli wieloznacznych | Grupa symboli wieloznacznych łączy Właściwości symboli wieloznacznych i grup. Jedyną klasą tej kategorii jest [wywołanie](cpp-event-data-types/invocation-group.md), które dopasowuje i przechwytuje wszystkie zdarzenia [konsolidatora](event-table.md#linker) i [kompilatora](event-table.md#compiler) w pojedynczym stosie zdarzeń. |

Zapoznaj się z [tabelą zdarzeń](event-table.md) , aby dowiedzieć się, które klasy przechwytywania mogą być używane do dopasowania poszczególnych zdarzeń.

#### <a name="after-matching-using-captured-events"></a>Po dopasowaniu: używanie przechwyconych zdarzeń

Po pomyślnym zakończeniu dopasowania `Match*` funkcje konstruują obiekty klasy przechwytywania i przekazują je do określonej funkcji. Użyj tych obiektów klasy przechwytywania, aby uzyskać dostęp do właściwości zdarzenia.

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
