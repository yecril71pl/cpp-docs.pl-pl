---
title: Klasa IRelogger
description: Odwołanie C++ do klasy IRelogger zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- IRelogger
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d0796cec3fe4ac6183279e8d8013a9550f18b61c
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332447"
---
# <a name="irelogger-class"></a>Klasa IRelogger

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `IRelogger` udostępnia interfejs do rejestrowania śledzenia zdarzeń systemu Windows (ETW). Jest on używany z funkcjami [MakeDynamicReloggerGroup](../functions/make-dynamic-relogger-group.md) i [MakeStaticReloggerGroup](../functions/make-static-analyzer-group.md) . Użyj `IRelogger` jako klasy bazowej do utworzenia własnego modułu rejestrującego, który może być częścią grupy rejestratora.

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

Domyślna wartość zwracana dla wszystkich funkcji, które nie są zastępowane, jest `AnalysisControl::CONTINUE`. Aby uzyskać więcej informacji, zobacz [AnalysisControl](analysis-control-enum-class.md).

## <a name="members"></a>Elementy członkowskie

### <a name="destructor"></a>Destruktor

[~ IRelogger](#irelogger-destructor)

### <a name="functions"></a>Funkcje

[OnBeginRelogging](#on-begin-relogging)\
[OnBeginReloggingPass](#on-begin-relogging-pass)\
[OnEndRelogging](#on-end-relogging)\
[OnEndReloggingPass](#on-end-relogging-pass)\
[OnSimpleEvent](#on-simple-event)\
\ [OnStart](#on-start-activity)
\ [OnStop](#on-stop-activity)
[OnTraceInfo](#on-trace-info)

## <a name="irelogger-destructor"></a>~ IRelogger

Niszczy klasę IRelogger.

```cpp
virtual ~IRelogger();
```

## <a name="on-begin-relogging"></a>OnBeginRelogging

Ta funkcja jest wywoływana przed rozpoczęciem przebiegu rejestrowania.

```cpp
virtual AnalysisControl OnBeginRelogging();
```

### <a name="return-value"></a>Wartość zwracana

Kod [AnalysisControl](analysis-control-enum-class.md) , który opisuje, co należy zrobić dalej.

## <a name="on-begin-relogging-pass"></a>OnBeginReloggingPass

Ta funkcja jest wywoływana na początku przebiegu rejestrowania.

```cpp
virtual AnalysisControl OnBeginReloggingPass();
```

### <a name="return-value"></a>Wartość zwracana

Kod [AnalysisControl](analysis-control-enum-class.md) , który opisuje, co należy zrobić dalej.

## <a name="on-end-relogging"></a>OnEndRelogging

Ta funkcja jest wywoływana po zakończeniu przebiegu rejestrowania.

```cpp
virtual AnalysisControl OnEndRelogging();
```

### <a name="return-value"></a>Wartość zwracana

Kod [AnalysisControl](analysis-control-enum-class.md) , który opisuje, co należy zrobić dalej.

## <a name="on-end-relogging-pass"></a>OnEndReloggingPass

Ta funkcja jest wywoływana po zakończeniu przebiegu rejestrowania.

```cpp
virtual AnalysisControl OnEndReloggingPass();
```

### <a name="return-value"></a>Wartość zwracana

Kod [AnalysisControl](analysis-control-enum-class.md) , który opisuje, co należy zrobić dalej.

## <a name="on-simple-event"></a>OnSimpleEvent

```cpp
virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack);
```

Ta funkcja jest wywoływana, gdy trwa przetwarzanie prostego zdarzenia.

### <a name="parameters"></a>Parametry

*eventStack*\
Stos zdarzeń dla tego prostego zdarzenia. Aby uzyskać więcej informacji na stosach zdarzeń, zobacz [zdarzenia](../event-table.md).

### <a name="return-value"></a>Wartość zwracana

Kod [AnalysisControl](analysis-control-enum-class.md) , który opisuje, co należy zrobić dalej.

## <a name="on-start-activity"></a>OnStart

```cpp
virtual AnalysisControl OnStartActivity(const EventStack& eventStack);
```

Ta funkcja jest wywoływana, gdy trwa przetwarzanie zdarzenia uruchomienia działania.

### <a name="parameters"></a>Parametry

*eventStack*\
Stos zdarzeń dla tego zdarzenia uruchomienia działania. Aby uzyskać więcej informacji na stosach zdarzeń, zobacz [zdarzenia](../event-table.md).

### <a name="return-value"></a>Wartość zwracana

Kod [AnalysisControl](analysis-control-enum-class.md) , który opisuje, co należy zrobić dalej.

## <a name="on-stop-activity"></a>Onzatrzymania

Ta funkcja jest wywoływana, gdy trwa przetwarzanie zdarzenia zatrzymania działania.

```cpp
virtual AnalysisControl OnStopActivity(const EventStack& eventStack);
```

### <a name="parameters"></a>Parametry

*eventStack*\
Stos zdarzeń dla tego zdarzenia zatrzymania działania. Aby uzyskać więcej informacji na stosach zdarzeń, zobacz [zdarzenia](../event-table.md).

### <a name="return-value"></a>Wartość zwracana

Kod [AnalysisControl](analysis-control-enum-class.md) , który opisuje, co należy zrobić dalej.

## <a name="on-trace-info"></a>OnTraceInfo

```cpp
virtual AnalysisControl OnTraceInfo(const TraceInfo& traceInfo);
```

Ta funkcja jest wywoływana raz na początku każdej analizy lub zarejestrowaniu przebiegu.

### <a name="parameters"></a>Parametry

*traceInfo*\
Obiekt [TraceInfo](../cpp-event-data-types/trace-info.md) , który zawiera użyteczne właściwości dotyczące używanego śledzenia.

### <a name="return-value"></a>Wartość zwracana

Kod [AnalysisControl](analysis-control-enum-class.md) , który opisuje, co należy zrobić dalej.

::: moniker-end
