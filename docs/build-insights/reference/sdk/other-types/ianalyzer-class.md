---
title: Klasa IAnalyzer
description: Odwołanie do klasy SDK IAnalyzer kompilacji języka C++.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- IAnalyzer
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: be9d80bb94450458c73fd6ce8d908985ba6f293d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329175"
---
# <a name="ianalyzer-class"></a>Klasa IAnalyzer

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `IAnalyzer` udostępnia interfejs do analizowania śledzenia zdarzeń dla systemu Windows (ETW) śledzenia. Jest on używany z [MakeDynamicAnalyzerGroup](../functions/make-dynamic-analyzer-group.md), [MakeDynamicReloggerGroup](../functions/make-dynamic-relogger-group.md), [MakeStaticAnalyzerGroup](../functions/make-dynamic-analyzer-group.md)i [MakeStaticReloggerGroup.](../functions/make-static-analyzer-group.md) Użyj `IAnalyzer` jako klasy podstawowej do tworzenia własnego analizatora, który może być częścią analizatora lub grupy relogger.

## <a name="syntax"></a>Składnia

```cpp
class IAnalyzer : public IRelogger
{
public:
    virtual AnalysisControl OnStartActivity(const EventStack& eventStack);
    virtual AnalysisControl OnStopActivity(const EventStack& eventStack)
    virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack);
    virtual AnalysisControl OnBeginAnalysis();
    virtual AnalysisControl OnEndAnalysis();
    virtual AnalysisControl OnBeginAnalysisPass();
    virtual AnalysisControl OnEndAnalysisPass();

    AnalysisControl OnStartActivity(const EventStack& eventStack,
        const void* relogSession) final;

    AnalysisControl OnStopActivity(const EventStack& eventStack,
        const void* relogSession) final;

    AnalysisControl OnSimpleEvent(const EventStack& eventStack,
        const void* relogSession) final;

    AnalysisControl OnBeginRelogging() final;
    AnalysisControl OnEndRelogging() final;
    AnalysisControl OnBeginReloggingPass() final;
    AnalysisControl OnEndReloggingPass() final;

    virtual ~IAnalyzer();
};
```

## <a name="remarks"></a>Uwagi

Klasy, które `IAnalyzer` wynikają z mogą być używane jako analizatory i reloggers. Gdy jest używany jako reloggers, relogger specyficzne funkcje przekierowanie do ich odpowiednika analizatora. Odwrotna nie jest prawdziwa: klasa, `IRelogger` która wywodzi się z nie można użyć jako analizatora. Za pomocą analizatora w grupie relogger jest typowy pattern. Po umieszczeniu we wczesnej pozycji grupy reloggera analizator może wstępnie obliczyć informacje i udostępnić je dla reloggerów w późniejszych pozycjach.

Domyślna wartość zwracana dla wszystkich funkcji, `AnalysisControl::CONTINUE`które nie są zastępowane, to . Aby uzyskać więcej informacji, zobacz [AnalysisControl](analysis-control-enum-class.md).

## <a name="members"></a>Elementy członkowskie

Oprócz elementu członkowskiego [OnTraceInfo](irelogger-class.md#on-trace-info) `IRelogger` z `IAnalyzer` interfejsu, klasa zawiera następujące elementy członkowskie:

### <a name="destructor"></a>Destruktor

[~IAnalyzer](#ianalyzer-destructor)

### <a name="functions"></a>Funkcje

[OnBeginAnalysis](#on-begin-analysis)\
[OnBeginAnalysisPrzejasca](#on-begin-analysis-pass)\
[OnBeginRelogging (OnBeginRelogging)](#on-begin-relogging)\
[OnBeginReloggingPass](#on-begin-relogging-pass)\
[OnEndAnalysis (Analiza Onendanaliza)](#on-end-analysis)\
[OnEndAnalysisPrzejaści](#on-end-analysis-pass)\
[Rejestrowanie onend](#on-end-relogging)\
[OnEndReloggingPass (OnEndReloggingPass)](#on-end-relogging-pass)\
[OnProszewen](#on-simple-event)\
[OnStartAktywność](#on-start-activity)\
[OnStopActivity (Nieaktywność)](#on-stop-activity)

## <a name="ianalyzer"></a><a name="ianalyzer-destructor"></a>~IAnalyzer

Niszczy klasę IAnalyzer.

```cpp
virtual ~IAnalyzer();
```

## <a name="onbeginanalysis"></a><a name="on-begin-analysis"></a>OnBeginAnalysis

Dla analizatorów część grupy analizatora ta funkcja jest wywoływana przed rozpoczęciem pierwszego przebiegu analizy. W przypadku analizatorów część grupy relogger, ta funkcja jest wywoływana przed rozpoczęciem przekazywania ponownego rejestrowania. Dla analizatorów część analizatora i grupy relogger tej samej sesji ponownego rejestrowania, ta funkcja jest wywoływana dwa razy przed rozpoczęciem pierwszego przebiegu analizy.

```cpp
virtual AnalysisControl OnBeginAnalysis();
```

### <a name="return-value"></a>Wartość zwracana

[AnalysisControl](analysis-control-enum-class.md) kod, który opisuje, co powinno się zdarzyć dalej.

## <a name="onbeginanalysispass"></a><a name="on-begin-analysis-pass"></a>OnBeginAnalysisPrzejasca

Dla analizatorów część grupy analizatora ta funkcja jest wywoływana na początku każdego przebiegu analizy. Dla analizatorów część grupy reloggera ta funkcja jest wywoływana na początku przebiegu reloggera. Dla analizatorów część analizatora i grupy relogger tej samej sesji ponownego rejestrowania, ta funkcja jest wywoływana na początku każdego przebiegu analizy i na początku przebiegu reloggera.

```cpp
virtual AnalysisControl OnBeginAnalysisPass();
```

### <a name="return-value"></a>Wartość zwracana

[AnalysisControl](analysis-control-enum-class.md) kod, który opisuje, co powinno się zdarzyć dalej.

## <a name="onbeginrelogging"></a><a name="on-begin-relogging"></a>OnBeginRelogging (OnBeginRelogging)

```cpp
AnalysisControl OnBeginRelogging() final;
```

Tej funkcji nie można zastąpić. Jest wywoływana przez C++ Build Insights SDK, gdy analizator jest częścią grupy relogger. Ta funkcja przekierowuje wywołanie do [OnBeginAnalysis](#on-begin-analysis).

### <a name="return-value"></a>Wartość zwracana

Wynik [wywołania OnBeginAnalysis.](#on-begin-analysis)

## <a name="onbeginreloggingpass"></a><a name="on-begin-relogging-pass"></a>OnBeginReloggingPass

Tej funkcji nie można zastąpić. Jest wywoływana przez C++ Build Insights SDK, gdy analizator jest częścią grupy relogger. Ta funkcja przekierowuje wywołanie do [OnBeginAnalysisPass](#on-begin-analysis-pass).

```cpp
AnalysisControl OnBeginReloggingPass() final;
```

### <a name="return-value"></a>Wartość zwracana

Wynik [wywołania OnBeginAnalysisPass.](#on-begin-analysis-pass)

## <a name="onendanalysis"></a><a name="on-end-analysis"></a>OnEndAnalysis (Analiza Onendanaliza)

W przypadku analizatorów, które są częścią grupy analizatora, ta funkcja jest wywoływana po zakończeniu ostatniego przebiegu analizy. W przypadku analizatorów, które są częścią grupy reloggera, ta funkcja jest wywoływana po zakończeniu przekazywania ponownego rejestrowania. W przypadku analizatorów, które są częścią grupy analizatora i reloggera tej samej sesji ponownego rejestrowania, ta funkcja jest wywoływana dwa razy:

1. po zakończeniu wszystkich przebiegów analizy i przed rozpoczęciem przełęczy relogging, oraz
1. po zakończeniu karty zalogowania.

```cpp
virtual AnalysisControl OnEndAnalysis();
```

### <a name="return-value"></a>Wartość zwracana

[AnalysisControl](analysis-control-enum-class.md) kod, który opisuje, co powinno się zdarzyć dalej.

## <a name="onendanalysispass"></a><a name="on-end-analysis-pass"></a>OnEndAnalysisPrzejaści

Dla analizatorów część grupy analizatora ta funkcja jest wywoływana na końcu każdego przebiegu analizy. Dla analizatorów część grupy relogger, ta funkcja jest wywoływana na końcu przebiegu relogger. Dla analizatorów część analizatora i grupy relogger tej samej sesji ponownego rejestrowania, ta funkcja jest wywoływana na końcu każdego przebiegu analizy i na końcu przebiegu reloggera.

```cpp
virtual AnalysisControl OnEndAnalysisPass();
```

### <a name="return-value"></a>Wartość zwracana

[AnalysisControl](analysis-control-enum-class.md) kod, który opisuje, co powinno się zdarzyć dalej.

## <a name="onendrelogging"></a><a name="on-end-relogging"></a>Rejestrowanie onend

Tej funkcji nie można zastąpić. Jest wywoływana przez C++ Build Insights SDK, gdy analizator jest częścią grupy relogger. Ta funkcja przekierowuje wywołanie do [OnEndAnalysis](#on-end-analysis).

```cpp
AnalysisControl OnEndRelogging() final;
```

### <a name="return-value"></a>Wartość zwracana

Wynik wywołania [OnEndAnalysis.](#on-end-analysis)

## <a name="onendreloggingpass"></a><a name="on-end-relogging-pass"></a>OnEndReloggingPass (OnEndReloggingPass)

Tej funkcji nie można zastąpić. Jest wywoływana przez C++ Build Insights SDK, gdy analizator jest częścią grupy relogger. Ta funkcja przekierowuje wywołanie do [OnEndAnalysisPass](#on-end-analysis-pass).

```cpp
AnalysisControl OnEndReloggingPass() final;
```

### <a name="return-value"></a>Wartość zwracana

Wynik [wywołania OnEndAnalysisPass.](#on-end-analysis-pass)

## <a name="onsimpleevent"></a><a name="on-simple-event"></a>OnProszewen

Ta funkcja jest wywoływana podczas przetwarzania prostego zdarzenia. Nie można zastąpić drugiej wersji tej funkcji. Jest wywoływana przez C++ Build Insights SDK, gdy analizator jest częścią grupy relogger. Wszystkie wywołania w wersji 2 są przekierowywane do wersji 1.

### <a name="version-1"></a>Wersja 1

```cpp
virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack);
```

### <a name="version-2"></a>Wersja 2

```cpp
AnalysisControl OnSimpleEvent(const EventStack& eventStack,
        const void* relogSession) final;
```

### <a name="parameters"></a>Parametry

*eventStack (własówce wydarzenia)*\
Stos zdarzeń dla tego prostego zdarzenia. Aby uzyskać więcej informacji na temat stosów zdarzeń, zobacz [Zdarzenia](../event-table.md).

*relogSesja*\
Ten parametr jest nieużywane.

### <a name="return-value"></a>Wartość zwracana

[AnalysisControl](analysis-control-enum-class.md) kod, który opisuje, co powinno się zdarzyć dalej.

## <a name="onstartactivity"></a><a name="on-start-activity"></a>OnStartAktywność

Ta funkcja jest wywoływana podczas przetwarzania zdarzenia rozpoczęcia działania. Nie można zastąpić drugiej wersji tej funkcji. Jest wywoływana przez C++ Build Insights SDK, gdy analizator jest częścią grupy relogger. Wszystkie wywołania w wersji 2 są przekierowywane do wersji 1.

### <a name="version-1"></a>Wersja 1

```cpp
virtual AnalysisControl OnStartActivity(const EventStack& eventStack);
```

### <a name="version-2"></a>Wersja 2

```cpp
AnalysisControl OnStartActivity(const EventStack& eventStack,
        const void* relogSession) final;
```

### <a name="parameters"></a>Parametry

*eventStack (własówce wydarzenia)*\
Stos zdarzeń dla tego zdarzenia rozpoczęcia działania. Aby uzyskać więcej informacji na temat stosów zdarzeń, zobacz [Zdarzenia](../event-table.md).

*relogSesja*\
Ten parametr jest nieużywane.

### <a name="return-value"></a>Wartość zwracana

[AnalysisControl](analysis-control-enum-class.md) kod, który opisuje, co powinno się zdarzyć dalej.

## <a name="onstopactivity"></a><a name="on-stop-activity"></a>OnStopActivity (Nieaktywność)

Ta funkcja jest wywoływana podczas przetwarzania zdarzenia zatrzymania działania. Nie można zastąpić drugiej wersji tej funkcji. Jest wywoływana przez C++ Build Insights SDK, gdy analizator jest częścią grupy relogger. Wszystkie wywołania w wersji 2 są przekierowywane do wersji 1.

### <a name="version-1"></a>Wersja 1

```cpp
virtual AnalysisControl OnStopActivity(const EventStack& eventStack);
```

### <a name="version-2"></a>Wersja 2

```cpp
AnalysisControl OnStopActivity(const EventStack& eventStack,
        const void* relogSession) final;
```

### <a name="parameters"></a>Parametry

*eventStack (własówce wydarzenia)*\
Stos zdarzeń dla tego zdarzenia zatrzymania działania. Aby uzyskać więcej informacji na temat stosów zdarzeń, zobacz [Zdarzenia](../event-table.md).

*relogSesja*\
Ten parametr jest nieużywane.

### <a name="return-value"></a>Wartość zwracana

[AnalysisControl](analysis-control-enum-class.md) kod, który opisuje, co powinno się zdarzyć dalej.

::: moniker-end
