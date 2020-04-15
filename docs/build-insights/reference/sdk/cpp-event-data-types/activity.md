---
title: Klasa aktywności
description: Odwołanie do klasy działania SDK kompilacji języka C++.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Activity
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2ea04150aec9c0b2366d97e6e4c15de557a4f47c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325248"
---
# <a name="activity-class"></a>Klasa aktywności

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `Activity` jest używana z funkcjami [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)i [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Użyj go, aby dopasować dowolne zdarzenie aktywności. Zapoznaj się z [tabelą zdarzeń,](../event-table.md) aby zobaczyć `Activity` wszystkie zdarzenia, które mogą być dopasowane przez klasę.

## <a name="syntax"></a>Składnia

```cpp
class Activity : public Event
{
public:
    Activity(const RawEvent& event);

    const long long& StartTimestamp() const;
    const long long& StopTimestamp() const;
    const long long& ExclusiveDurationTicks() const;
    const long long& CPUTicks() const;
    const long long& ExclusiveCPUTicks() const;
    const long long& WallClockTimeResponsibilityTicks() const;
    const long long& ExclusiveWallClockTimeResponsibilityTicks() const;

    std::chrono::nanoseconds Duration() const;
    std::chrono::nanoseconds ExclusiveDuration() const;
    std::chrono::nanoseconds CPUTime() const ;
    std::chrono::nanoseconds ExclusiveCPUTime() const;
    std::chrono::nanoseconds WallClockTimeResponsibility() const;
    std::chrono::nanoseconds ExclusiveWallClockTimeResponsibility() const;
};
```

## <a name="remarks"></a>Uwagi

Kilka funkcji członkowskich `Activity` w klasie zwraca liczbę znaczników. Usługa C++ Build Insights używa licznika wydajności systemu Windows jako źródła znaczników. Liczba znaczników musi być używana z częstotliwością znaczników, aby przekształcić ją w jednostkę czasu, taką jak sekundy. Funkcja `TickFrequency` elementu członkowskiego, dostępna w klasie podstawowej [zdarzenia,](event.md) może zostać wywołana w celu uzyskania częstotliwości znaczników. Strona [EVENT_DATA](../c-event-data-types/event-data-struct.md#tick-conversion-example) zawiera przykład konwersji znaczników na jednostkę czasu.

Jeśli nie chcesz samodzielnie konwertować znaczników na `Activity` jednostki czasu, klasa udostępnia funkcje członkowskie, które zwracają wartości czasu w nanosekundach. Użyj standardowej biblioteki C++, `chrono` aby przekonwertować je na inne jednostki czasu.

## <a name="members"></a>Elementy członkowskie

Wraz z jego członków [Event](event.md) odziedziczonych po `Activity` event klasy podstawowej, klasa zawiera następujące elementy członkowskie:

### <a name="constructor"></a>Konstruktor

[Działanie](#activity)

### <a name="functions"></a>Funkcje

[Procesory](#cpu-ticks)\
[Czas procesora](#cpu-time)\
[Długość](#duration)\
[Ekskluzywne akputicks](#exclusive-cpu-ticks)\
[ExclusiveCPUTime](#exclusive-cpu-time)\
[Wyłącznośćducja](#exclusive-duration)\
[EkskluzywnedurationTicks](#exclusive-duration-ticks)\
[ExclusiveWallClockOdpowiedzialność za](#exclusive-wall-clock-time-responsibility)\
[ExclusiveWallClockTimeResponsibilityTicks](#exclusive-wall-clock-time-responsibility-ticks)\
[Sygnatura starttimestamp](#start-timestamp)\
[StopTimestamp (StopTimestamp)](#stop-timestamp)\
[WallClockTimeOdpowiedzialność](#wall-clock-time-responsibility)\
[WallClockTimeOdpowiedzialnośćOdpowiedziTicks](#wall-clock-time-responsibility-ticks)

## <a name="activity"></a><a name="activity"></a>Działania

```cpp
Activity(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Zdarzenie*\
Każde zdarzenie aktywności.

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

## <a name="duration"></a><a name="duration"></a>Długość

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>Wartość zwracana

Czas trwania działania w nanosekundach.

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
