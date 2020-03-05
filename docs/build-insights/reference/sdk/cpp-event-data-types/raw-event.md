---
title: Klasa RawEvent
description: Odwołanie C++ do klasy RawEvent zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RawEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4088920d6070e14d64ccd046238c1c49b2556ea1
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333063"
---
# <a name="rawevent-class"></a>Klasa RawEvent

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

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

Kilka funkcji Członkowskich w klasie `RawEvent` zwraca liczbę cykli. C++Usługi Build Insights wykorzystują licznik wydajności systemu Windows jako źródło taktów. Liczba cykli musi być używana z częstotliwością taktu, aby przekonwertować ją na jednostkę czasu, taką jak sekundy. Funkcja członkowska `TickFrequency` może zostać wywołana w celu uzyskania częstotliwości taktu. Na stronie [EVENT_DATA](../c-event-data-types/event-data-struct.md#tick-conversion-example) można zobaczyć przykład sposobu konwertowania taktów na jednostkę czasu.

Jeśli nie chcesz samodzielnie konwertować taktów, Klasa `RawEvent` dostarcza funkcje członkowskie, które zwracają wartości czasu w nanosekundach. Standardowa C++ Biblioteka `chrono` umożliwia konwertowanie nanosekund na inne jednostki czasu.

## <a name="members"></a>Elementy członkowskie

### <a name="constructor"></a>Konstruktor

[RawEvent](#raw-event)

### <a name="functions"></a>Funkcje

[CPUTicks](#cpu-ticks)\
[CPUTime](#cpu-time)\
\ [danych](#data)
[Czas trwania](#duration)\
[EventId](#event-id)
[EventInstanceId](#event-instance-id)
[EventName](#event-name)\
[EventWideName](#event-wide-name)\
[ExclusiveCPUTicks](#exclusive-cpu-ticks)\
[ExclusiveCPUTime](#exclusive-cpu-time)\
[ExclusiveDuration](#exclusive-duration)\
[ExclusiveDurationTicks](#exclusive-duration-ticks)\
[ExclusiveWallClockTimeResponsibility](#exclusive-wall-clock-time-responsibility)\
[ExclusiveWallClockTimeResponsibilityTicks](#exclusive-wall-clock-time-responsibility-ticks)\
\ identyfikatora [procesu](#process-id)
[ProcessorIndex](#processor-index)\
[StartTimestamp](#start-timestamp)\
[StopTimestamp](#stop-timestamp)\
[ThreadId](#thread-id)\
[TickFrequency](#tick-frequency)\
[WallClockTimeResponsibility](#wall-clock-time-responsibility)\
[WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks)

## <a name="raw-event"></a>RawEvent

```cpp
RawEvent(const EVENT_DATA& data);
```

### <a name="parameters"></a>Parametry

\ *zdarzeń*
Dane dotyczące zdarzenia.

## <a name="cpu-ticks"></a>CPUTicks

```cpp
const long long& CPUTicks() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba cykli procesora CPU, które wystąpiły w trakcie tego działania. Cykl procesora CPU różni się od zwykłego taktu. Takty procesora są zliczane tylko wtedy, gdy procesor wykonuje kod w działaniu. Takty procesora nie są zliczane, gdy wątek skojarzony z działaniem jest uśpiony.

## <a name="cpu-time"></a>CPUTime

```cpp
std::chrono::nanoseconds CPUTime()() const;
```

### <a name="return-value"></a>Wartość zwracana

Czas wykonywania przez procesor CPU kodu w ramach tego działania. Ta wartość może być większa niż czas trwania działania, jeśli działania podrzędne są wykonywane w oddzielnych wątkach. Wartość jest zwracana w nanosekundach.

## <a name="data"></a>Data

```cpp
const void* Data() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do dodatkowych danych zawartych w tym zdarzeniu. Aby uzyskać więcej informacji na temat interpretowania tego pola, zobacz [EVENT_DATA](../c-event-data-types/event-data-struct.md).

## <a name="duration"></a>Trwania

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>Wartość zwracana

Czas trwania działania w nanosekundach.

## <a name="event-id"></a>EventId

```cpp
const unsigned short& EventId() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba, która identyfikuje typ zdarzenia. Aby uzyskać listę identyfikatorów zdarzeń, zobacz [EVENT_ID](../c-event-data-types/event-id-enum.md).

## <a name="event-instance-id"></a>EventInstanceId

```cpp
const unsigned long long& EventInstanceId() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba, która jednoznacznie identyfikuje zdarzenie wewnątrz śladu. Ta wartość nie ulega zmianie podczas analizowania lub wielokrotnego rejestrowania tego samego śledzenia. Użyj tej wartości, aby zidentyfikować to samo zdarzenie w wielu analizach lub przerejestrowaniu przebiegów tego samego śledzenia.

## <a name="event-name"></a>EventName

```cpp
const char* EventName() const;
```

### <a name="return-value"></a>Wartość zwracana

Ciąg ANSI zawierający nazwę typu zdarzenia identyfikowanego przez [EventID](#event-id).

## <a name="event-wide-name"></a>EventWideName

```cpp
const wchar_t* EventWideName() const;
```

### <a name="return-value"></a>Wartość zwracana

Szeroki ciąg zawierający nazwę typu zdarzenia identyfikowanego przez [EventID](#event-id).

## <a name="exclusive-cpu-ticks"></a>ExclusiveCPUTicks

```cpp
const long long& ExclusiveCPUTicks() const;
```

### <a name="return-value"></a>Wartość zwracana

Analogicznie jak [CPUTicks](#cpu-ticks), ale nie obejmuje taktów procesora, które wystąpiły w działaniach podrzędnych.

## <a name="exclusive-cpu-time"></a>ExclusiveCPUTime

```cpp
std::chrono::nanoseconds ExclusiveCPUTime() const;
```

### <a name="return-value"></a>Wartość zwracana

Analogicznie jak [CPUTime](#cpu-time), z tą różnicą, że czas procesora działań podrzędnych nie jest uwzględniony.

## <a name="exclusive-duration"></a>ExclusiveDuration

```cpp
std::chrono::nanoseconds ExclusiveDuration() const;
```

### <a name="return-value"></a>Wartość zwracana

Czas trwania działania w nanosekundach, bez uwzględniania czasu spędzonego w działaniach podrzędnych.

## <a name="exclusive-duration-ticks"></a>ExclusiveDurationTicks

```cpp
const long long& ExclusiveDurationTicks() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba znaczników, które wystąpiły w tym działaniu, z wyłączeniem liczby taktów, które wystąpiły w działaniach podrzędnych.

## <a name="exclusive-wall-clock-time-responsibility"></a>ExclusiveWallClockTimeResponsibility

```cpp
std::chrono::nanoseconds ExclusiveWallClockTimeResponsibility() const;
```

### <a name="return-value"></a>Wartość zwracana

Analogicznie jak [WallClockTimeResponsibility](#wall-clock-time-responsibility), ale nie obejmuje odpowiedzialności za czas zegara na działania podrzędne.

## <a name="exclusive-wall-clock-time-responsibility-ticks"></a>ExclusiveWallClockTimeResponsibilityTicks

```cpp
const long long& ExclusiveWallClockTimeResponsibilityTicks() const;
```

### <a name="return-value"></a>Wartość zwracana

Analogicznie jak [WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks), ale nie uwzględniające czasu zegarka odpowiedzialności za działania podrzędne.

## <a name="process-id"></a>Identyfikator

```cpp
const unsigned long& ProcessId() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator procesu, w którym wystąpiło zdarzenie.

## <a name="processor-index"></a>ProcessorIndex

```cpp
const unsigned short& ProcessorIndex() const;
```

### <a name="return-value"></a>Wartość zwracana

Indeks (liczony od zera) dla procesora logicznego, w którym wystąpiło zdarzenie.

## <a name="start-timestamp"></a>StartTimestamp

```cpp
const long long& StartTimestamp() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość taktu przechwycona w momencie uruchomienia działania.

## <a name="stop-timestamp"></a>StopTimestamp

```cpp
const long long& StopTimestamp() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość taktu przechwycona w momencie zatrzymania działania.

## <a name="thread-id"></a>ThreadId

```cpp
const unsigned long& ThreadId() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator wątku, w którym wystąpiło zdarzenie.

## <a name="tick-frequency"></a>TickFrequency

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba taktów na sekundę, która ma być używana podczas obliczania czasu trwania mierzoną w taktach dla tego zdarzenia.

## <a name="wall-clock-time-responsibility"></a>WallClockTimeResponsibility

```cpp
std::chrono::nanoseconds WallClockTimeResponsibility() const;
```

### <a name="return-value"></a>Wartość zwracana

Czas zegarowy w nanosekundach, który jest odpowiedzialny za to działanie. Aby uzyskać więcej informacji o tym, co jest odpowiedzialne za czas zegara ściany, zobacz [WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks).

## <a name="wall-clock-time-responsibility-ticks"></a>WallClockTimeResponsibilityTicks

```cpp
const long long& WallClockTimeResponsibilityTicks() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba cykli, która reprezentuje udział tego działania w ogólnym czasie zegara ściany. Cykl odpowiedzialności w czasie zegara ściany różni się od zwykłego taktu. Cykle odpowiedzialności za zegary ścienne są uwzględniane równolegle między działaniami. Dwie działania równoległe mogą mieć czas trwania 50 taktów i ten sam czas rozpoczęcia i zakończenia. W takim przypadku oba te elementy otrzymują przypisany Czas zegarowy do 25 taktów.

::: moniker-end
