---
title: Klasa IRelogger
description: Odwołanie do klasy IReloggera SDK IReloggera kompilacji języka C++.The C++ Build Insights SDK IRelogger class reference.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- IRelogger
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 146377b2b44df43ed4b2f749efd9fb614a2a09c9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329153"
---
# <a name="irelogger-class"></a>Klasa IRelogger

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `IRelogger` udostępnia interfejs do ponownego rejestrowania śledzenia zdarzeń dla systemu Windows (ETW). Jest on używany z [MakeDynamicReloggerGroup](../functions/make-dynamic-relogger-group.md) i [MakeStaticReloggerGroup](../functions/make-static-analyzer-group.md) funkcji. Użyj `IRelogger` jako klasy podstawowej, aby utworzyć własny relogger, który może być częścią grupy relogger.

## <a name="syntax"></a>Składnia

```cpp
class IRelogger
{
public:
    virtual AnalysisControl OnStartActivity(const EventStack& eventStack,
        const void* relogSession);

    virtual AnalysisControl OnStopActivity(const EventStack& eventStack,
        const void* relogSession);

    virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack,
        const void* relogSession);

    virtual AnalysisControl OnTraceInfo(const TraceInfo& traceInfo);
    virtual AnalysisControl OnBeginRelogging();
    virtual AnalysisControl OnEndRelogging();
    virtual AnalysisControl OnBeginReloggingPass();
    virtual AnalysisControl OnEndReloggingPass() ;

    virtual ~IRelogger();
};
```

## <a name="remarks"></a>Uwagi

Domyślna wartość zwracana dla wszystkich funkcji, `AnalysisControl::CONTINUE`które nie są zastępowane, to . Aby uzyskać więcej informacji, zobacz [AnalysisControl](analysis-control-enum-class.md).

## <a name="members"></a>Elementy członkowskie

### <a name="destructor"></a>Destruktor

[~IRelogger](#irelogger-destructor)

### <a name="functions"></a>Funkcje

[OnBeginRelogging (OnBeginRelogging)](#on-begin-relogging)\
[OnBeginReloggingPass](#on-begin-relogging-pass)\
[Rejestrowanie onend](#on-end-relogging)\
[OnEndReloggingPass (OnEndReloggingPass)](#on-end-relogging-pass)\
[OnProszewen](#on-simple-event)\
[OnStartAktywność](#on-start-activity)\
[OnStopActivity (Nieaktywność)](#on-stop-activity)\
[OnTraceInfo](#on-trace-info)

## <a name="irelogger"></a><a name="irelogger-destructor"></a>~IRelogger

Niszczy IRelogger klasy.

```cpp
virtual ~IRelogger();
```

## <a name="onbeginrelogging"></a><a name="on-begin-relogging"></a>OnBeginRelogging (OnBeginRelogging)

Ta funkcja jest wywoływana przed rozpoczęciem przełęczy ponownego rejestrowania.

```cpp
virtual AnalysisControl OnBeginRelogging();
```

### <a name="return-value"></a>Wartość zwracana

[AnalysisControl](analysis-control-enum-class.md) kod, który opisuje, co powinno się zdarzyć dalej.

## <a name="onbeginreloggingpass"></a><a name="on-begin-relogging-pass"></a>OnBeginReloggingPass

Ta funkcja jest wywoływana na początku przebiegu ponownego rejestrowania.

```cpp
virtual AnalysisControl OnBeginReloggingPass();
```

### <a name="return-value"></a>Wartość zwracana

[AnalysisControl](analysis-control-enum-class.md) kod, który opisuje, co powinno się zdarzyć dalej.

## <a name="onendrelogging"></a><a name="on-end-relogging"></a>Rejestrowanie onend

Ta funkcja jest wywoływana po zakończeniu przełęczy ponownego rejestrowania.

```cpp
virtual AnalysisControl OnEndRelogging();
```

### <a name="return-value"></a>Wartość zwracana

[AnalysisControl](analysis-control-enum-class.md) kod, który opisuje, co powinno się zdarzyć dalej.

## <a name="onendreloggingpass"></a><a name="on-end-relogging-pass"></a>OnEndReloggingPass (OnEndReloggingPass)

Ta funkcja jest wywoływana na końcu przebiegu ponownego rejestrowania.

```cpp
virtual AnalysisControl OnEndReloggingPass();
```

### <a name="return-value"></a>Wartość zwracana

[AnalysisControl](analysis-control-enum-class.md) kod, który opisuje, co powinno się zdarzyć dalej.

## <a name="onsimpleevent"></a><a name="on-simple-event"></a>OnProszewen

```cpp
virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack);
```

Ta funkcja jest wywoływana podczas przetwarzania prostego zdarzenia.

### <a name="parameters"></a>Parametry

*eventStack (własówce wydarzenia)*\
Stos zdarzeń dla tego prostego zdarzenia. Aby uzyskać więcej informacji na temat stosów zdarzeń, zobacz [Zdarzenia](../event-table.md).

### <a name="return-value"></a>Wartość zwracana

[AnalysisControl](analysis-control-enum-class.md) kod, który opisuje, co powinno się zdarzyć dalej.

## <a name="onstartactivity"></a><a name="on-start-activity"></a>OnStartAktywność

```cpp
virtual AnalysisControl OnStartActivity(const EventStack& eventStack);
```

Ta funkcja jest wywoływana podczas przetwarzania zdarzenia rozpoczęcia działania.

### <a name="parameters"></a>Parametry

*eventStack (własówce wydarzenia)*\
Stos zdarzeń dla tego zdarzenia rozpoczęcia działania. Aby uzyskać więcej informacji na temat stosów zdarzeń, zobacz [Zdarzenia](../event-table.md).

### <a name="return-value"></a>Wartość zwracana

[AnalysisControl](analysis-control-enum-class.md) kod, który opisuje, co powinno się zdarzyć dalej.

## <a name="onstopactivity"></a><a name="on-stop-activity"></a>OnStopActivity (Nieaktywność)

Ta funkcja jest wywoływana podczas przetwarzania zdarzenia zatrzymania działania.

```cpp
virtual AnalysisControl OnStopActivity(const EventStack& eventStack);
```

### <a name="parameters"></a>Parametry

*eventStack (własówce wydarzenia)*\
Stos zdarzeń dla tego zdarzenia zatrzymania działania. Aby uzyskać więcej informacji na temat stosów zdarzeń, zobacz [Zdarzenia](../event-table.md).

### <a name="return-value"></a>Wartość zwracana

[AnalysisControl](analysis-control-enum-class.md) kod, który opisuje, co powinno się zdarzyć dalej.

## <a name="ontraceinfo"></a><a name="on-trace-info"></a>OnTraceInfo

```cpp
virtual AnalysisControl OnTraceInfo(const TraceInfo& traceInfo);
```

Ta funkcja jest wywoływana raz na początku każdej analizy lub przełęczy ponownego rejestrowania.

### <a name="parameters"></a>Parametry

*Traceinfo*\
Obiekt [TraceInfo,](../cpp-event-data-types/trace-info.md) który zawiera przydatne właściwości dotyczące używanego śledzenia.

### <a name="return-value"></a>Wartość zwracana

[AnalysisControl](analysis-control-enum-class.md) kod, który opisuje, co powinno się zdarzyć dalej.

::: moniker-end
