---
title: Event — Klasa
description: Odwołanie C++ do klasy zdarzeń zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Event
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 205a4e0ca9dd9449933f38f02d4ceafd5df8ead2
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333399"
---
# <a name="event-class"></a>Event — Klasa

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `Event` jest używana z funkcjami [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)i [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Użyj jej do dopasowania dowolnego zdarzenia.

## <a name="syntax"></a>Składnia

```cpp
class Event
{
public:
    Event(const RawEvent& event);

    const unsigned short&        EventId() const;
    const unsigned long long&    EventInstanceId() const;
    const long long&             TickFrequency() const;
    const long long&             Timestamp() const;
    const unsigned long&         ProcessId() const;
    const unsigned long&         ThreadId() const;
    const unsigned short&        ProcessorIndex() const;
    const char*                  EventName() const;
    const wchar_t*               EventWideName() const;
};
```

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

[Event](#entity)

### <a name="functions"></a>Funkcje

[EventId](#event-id)
[danych](#data)\
[EventInstanceId](#event-instance-id)\
[Eventname](#event-name)\
[EventWideName](#event-wide-name)\
\ identyfikatora [procesu](#process-id)
[ProcessorIndex](#processor-index)\
[ThreadId](#thread-id)\
[TickFrequency](#tick-frequency)\
[Sygnatura czasowa](#timestamp)

## <a name="entity"></a>Wydarzen

```cpp
Event(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

\ *zdarzeń*
Dowolne zdarzenie.

## <a name="data"></a>Data

```cpp
const void* Data() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do dodatkowych danych zawartych w tym zdarzeniu. Aby uzyskać więcej informacji na temat interpretowania tego pola, zobacz [EVENT_DATA](../c-event-data-types/event-data-struct.md).

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

Szeroki ciąg zawierający nazwę zdarzenia identyfikowanego przez [EventID](#event-id).

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

## <a name="timestamp"></a>Znacznik czasu

```cpp
const long long& Timestamp() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli zdarzenie jest działaniem, funkcja ta zwraca wartość taktu przechwyconą w momencie uruchomienia działania. W przypadku prostego zdarzenia ta funkcja zwraca wartość taktu przechwyconą w momencie wystąpienia zdarzenia.

::: moniker-end
