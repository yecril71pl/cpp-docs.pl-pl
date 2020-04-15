---
title: Klasa RawEvent
description: Odwołanie do klasy SDK RawEvent w języku C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RawEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 83629457ac3a0d1f991f6b084af2f3400612b2ac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324382"
---
# <a name="rawevent-class"></a>Klasa RawEvent

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `RawEvent` jest używana do reprezentowania zdarzenia ogólnego w [EventStack](event-stack.md).

## <a name="syntax"></a>Składnia

```cpp
class RawEvent
{
public:
    RawEvent(const EVENT_DATA& event);

    const unsigned short&        EventId() const;
    const unsigned long long&    EventInstanceId() const;
    const long long&             TickFrequency() const;
    const long long&             StartTimestamp() const;
    const long long&             StopTimestamp() const;
    const long long&             ExclusiveDurationTicks() const;
    const long long&             CPUTicks() const;
    const long long&             ExclusiveCPUTicks() const;
    const long long&             WallClockTimeResponsibilityTicks() const;
    const long long&             ExclusiveWallClockTimeResponsibilityTicks() const;
    const void*                  Data() const;
    const unsigned long&         ProcessId() const;
    const unsigned long&         ThreadId() const;
    const unsigned short&        ProcessorIndex() const;
    const char*                  EventName() const;
    const wchar_t*               EventWideName() const;

    std::chrono::nanoseconds Duration() const;
    std::chrono::nanoseconds ExclusiveDuration() const;
    std::chrono::nanoseconds CPUTime() const ;
    std::chrono::nanoseconds ExclusiveCPUTime() const;
    std::chrono::nanoseconds WallClockTimeResponsibility() const;
    std::chrono::nanoseconds ExclusiveWallClockTimeResponsibility() const;
};
```

## <a name="remarks"></a>Uwagi

Kilka funkcji członkowskich `RawEvent` w klasie zwraca liczbę znaczników. Usługa C++ Build Insights używa licznika wydajności systemu Windows jako źródła znaczników. Liczba znaczników musi być używana z częstotliwością znaczników, aby przekształcić ją w jednostkę czasu, taką jak sekundy. Funkcja `TickFrequency` elementu członkowskiego może zostać wywołana w celu uzyskania częstotliwości znaczników. Zobacz stronę [EVENT_DATA,](../c-event-data-types/event-data-struct.md#tick-conversion-example) aby zapoznać się z przykładem sposobu konwertowania znaczników na jednostkę czasu.

Jeśli nie chcesz konwertować znaczników `RawEvent` samodzielnie, klasa udostępnia funkcje członkowskie, które zwracają wartości czasu w nanosekundach. Użyj standardowej biblioteki C++, `chrono` aby przekonwertować nanosekundy na inne jednostki czasu.

## <a name="members"></a>Elementy członkowskie

### <a name="constructor"></a>Konstruktor

[RawEvent ( RawEvent )](#raw-event)

### <a name="functions"></a>Funkcje

[Procesory](#cpu-ticks)\
[Czas procesora](#cpu-time)\
[Danych](#data)\
[Długość](#duration)\
[Nazwa](#event-id)
[zdarzenia](#event-name) [Identyfikator](#event-instance-id)
zdarzenia EventId\
[Nazwa zdarzenia](#event-wide-name)\
[Ekskluzywne akputicks](#exclusive-cpu-ticks)\
[ExclusiveCPUTime](#exclusive-cpu-time)\
[Wyłącznośćducja](#exclusive-duration)\
[EkskluzywnedurationTicks](#exclusive-duration-ticks)\
[ExclusiveWallClockOdpowiedzialność za](#exclusive-wall-clock-time-responsibility)\
[ExclusiveWallClockTimeResponsibilityTicks](#exclusive-wall-clock-time-responsibility-ticks)\
[Processid](#process-id)\
[ProcesorIndex](#processor-index)\
[Sygnatura starttimestamp](#start-timestamp)\
[StopTimestamp (StopTimestamp)](#stop-timestamp)\
[Threadid](#thread-id)\
[Częstotliwość ticków](#tick-frequency)\
[WallClockTimeOdpowiedzialność](#wall-clock-time-responsibility)\
[WallClockTimeOdpowiedzialnośćOdpowiedziTicks](#wall-clock-time-responsibility-ticks)

## <a name="rawevent"></a><a name="raw-event"></a>RawEvent ( RawEvent )

```cpp
RawEvent(const EVENT_DATA& data);
```

### <a name="parameters"></a>Parametry

*Zdarzenie*\
Dane dotyczące zdarzenia.

## <a name="cputicks"></a><a name="cpu-ticks"></a>Procesory

```cpp
const long long& CPUTicks() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba znaczników procesora CPU, które wystąpiły podczas tego działania. Znacznik procesora różni się od zwykłego kleszcza. Znaczniki procesora CPU są liczone tylko wtedy, gdy procesor jest wykonywany kod w działaniu. Znaczniki procesora CPU nie są liczone, gdy wątek skojarzony z aktywnością jest uśpiony.

## <a name="cputime"></a><a name="cpu-time"></a>Czas procesora

```cpp
std::chrono::nanoseconds CPUTime()() const;
```

### <a name="return-value"></a>Wartość zwracana

Czas wykonywania kodu przez procesor CPU w ramach tego działania. Ta wartość może być wyższa niż czas trwania działania, jeśli działania podrzędne są wykonywane w oddzielnych wątkach. Wartość jest zwracana w nanosekundach.

## <a name="data"></a><a name="data"></a>Danych

```cpp
const void* Data() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do dodatkowych danych zawartych w tym zdarzeniu. Aby uzyskać więcej informacji na temat interpretowania tego pola, zobacz [EVENT_DATA](../c-event-data-types/event-data-struct.md).

## <a name="duration"></a><a name="duration"></a>Długość

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>Wartość zwracana

Czas trwania działania w nanosekundach.

## <a name="eventid"></a><a name="event-id"></a>Eventid

```cpp
const unsigned short& EventId() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba identyfikująca typ zdarzenia. Aby uzyskać listę identyfikatorów zdarzeń, zobacz [EVENT_ID](../c-event-data-types/event-id-enum.md).

## <a name="eventinstanceid"></a><a name="event-instance-id"></a>Identyfikator wystąpienia zdarzenia

```cpp
const unsigned long long& EventInstanceId() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba, która jednoznacznie identyfikuje zdarzenie wewnątrz śledzenia. Ta wartość nie zmienia się podczas analizowania lub ponownego rejestrowania tego samego śledzenia wiele razy. Ta wartość służy do identyfikowania tego samego zdarzenia w wielu analizach lub ponownego rejestrowania przebiegów przez ten sam ślad.

## <a name="eventname"></a><a name="event-name"></a>Eventname

```cpp
const char* EventName() const;
```

### <a name="return-value"></a>Wartość zwracana

Ciąg ANSI zawierający nazwę typu zdarzenia identyfikowanego przez [EventId](#event-id).

## <a name="eventwidename"></a><a name="event-wide-name"></a>Nazwa zdarzenia

```cpp
const wchar_t* EventWideName() const;
```

### <a name="return-value"></a>Wartość zwracana

Szeroki ciąg zawierający nazwę typu zdarzenia identyfikowanego przez [EventId](#event-id).

## <a name="exclusivecputicks"></a><a name="exclusive-cpu-ticks"></a>Ekskluzywne akputicks

```cpp
const long long& ExclusiveCPUTicks() const;
```

### <a name="return-value"></a>Wartość zwracana

Tak samo jak [CPUTicks](#cpu-ticks), ale nie w tym kleszcze procesora CPU, które wystąpiły w działaniach podrzędnych.

## <a name="exclusivecputime"></a><a name="exclusive-cpu-time"></a>ExclusiveCPUTime

```cpp
std::chrono::nanoseconds ExclusiveCPUTime() const;
```

### <a name="return-value"></a>Wartość zwracana

Tak samo jak [CPUTime](#cpu-time), z tą różnicą, że czas procesora CPU działań podrzędnych nie jest uwzględniony.

## <a name="exclusiveduration"></a><a name="exclusive-duration"></a>Wyłącznośćducja

```cpp
std::chrono::nanoseconds ExclusiveDuration() const;
```

### <a name="return-value"></a>Wartość zwracana

Czas trwania działania w nanosekundach, nie licząc czasu spędzonego na zajęciach dla dzieci.

## <a name="exclusivedurationticks"></a><a name="exclusive-duration-ticks"></a>EkskluzywnedurationTicks

```cpp
const long long& ExclusiveDurationTicks() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba znaczników, które wystąpiły w tym działaniu, z wyłączeniem liczby znaczników, które wystąpiły w działaniach podrzędnych.

## <a name="exclusivewallclocktimeresponsibility"></a><a name="exclusive-wall-clock-time-responsibility"></a>ExclusiveWallClockOdpowiedzialność za

```cpp
std::chrono::nanoseconds ExclusiveWallClockTimeResponsibility() const;
```

### <a name="return-value"></a>Wartość zwracana

Tak samo jak [WallClockTimeOdpowiedzialność ,](#wall-clock-time-responsibility)ale nie w tym odpowiedzialność czasu zegara ściennego działań podrzędnych.

## <a name="exclusivewallclocktimeresponsibilityticks"></a><a name="exclusive-wall-clock-time-responsibility-ticks"></a>ExclusiveWallClockTimeResponsibilityTicks

```cpp
const long long& ExclusiveWallClockTimeResponsibilityTicks() const;
```

### <a name="return-value"></a>Wartość zwracana

Tak samo jak [WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks), ale nie wliczając w to odpowiedzialność za czas ścienny aktywności podrzędnych.

## <a name="processid"></a><a name="process-id"></a>Processid

```cpp
const unsigned long& ProcessId() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator procesu, w którym wystąpiło zdarzenie.

## <a name="processorindex"></a><a name="processor-index"></a>ProcesorIndex

```cpp
const unsigned short& ProcessorIndex() const;
```

### <a name="return-value"></a>Wartość zwracana

Indeks od zera dla procesora logicznego, na którym wystąpiło zdarzenie.

## <a name="starttimestamp"></a><a name="start-timestamp"></a>Sygnatura starttimestamp

```cpp
const long long& StartTimestamp() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość znacznika przechwycona w momencie rozpoczęcia działania.

## <a name="stoptimestamp"></a><a name="stop-timestamp"></a>StopTimestamp (StopTimestamp)

```cpp
const long long& StopTimestamp() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość znacznika przechwycona w momencie zatrzymania działania.

## <a name="threadid"></a><a name="thread-id"></a>Threadid

```cpp
const unsigned long& ThreadId() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator wątku, w którym wystąpiło zdarzenie.

## <a name="tickfrequency"></a><a name="tick-frequency"></a>Częstotliwość ticków

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba znaczników na sekundę do użycia podczas oceny czasu trwania mierzonego w znacznikach dla tego zdarzenia.

## <a name="wallclocktimeresponsibility"></a><a name="wall-clock-time-responsibility"></a>WallClockTimeOdpowiedzialność

```cpp
std::chrono::nanoseconds WallClockTimeResponsibility() const;
```

### <a name="return-value"></a>Wartość zwracana

Odpowiedzialność czasu zegara ściennego tego działania, w nanosekundach. Aby uzyskać więcej informacji na temat tego, co oznacza odpowiedzialność za czas zegara ściennego, zobacz [WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks).

## <a name="wallclocktimeresponsibilityticks"></a><a name="wall-clock-time-responsibility-ticks"></a>WallClockTimeOdpowiedzialnośćOdpowiedziTicks

```cpp
const long long& WallClockTimeResponsibilityTicks() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba znaczników, która reprezentuje wkład tego działania w ogólny czas zegara ściennego. Odpowiedzialność za czas zegara ściennego różni się od zwykłego kleszcza. Odpowiedzialność zegara ściennego uwzględnia równoległość między działaniami. Dwa równoległe działania mogą mieć czas trwania 50 znaczników i ten sam czas rozpoczęcia i zatrzymania. W takim przypadku oba otrzymują przypisaną odpowiedzialność za czas zegara ściennego 25 znaczników.

::: moniker-end
