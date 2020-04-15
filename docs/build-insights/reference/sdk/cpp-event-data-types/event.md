---
title: Klasa zdarzenia
description: Odwołanie do klasy SDK SDK kompilacji języka C++.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Event
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 25d58f642a1c314e48ddff62553394bcc65e4717
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324962"
---
# <a name="event-class"></a>Klasa zdarzenia

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `Event` jest używana z funkcjami [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)i [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Użyj go, aby dopasować do każdego zdarzenia.

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

[Zdarzenie](#entity)

### <a name="functions"></a>Funkcje

[Identyfikator](#data)
[zdarzenia](#event-id) danych\
[Identyfikator wystąpienia zdarzenia](#event-instance-id)\
[Eventname](#event-name)\
[Nazwa zdarzenia](#event-wide-name)\
[Processid](#process-id)\
[ProcesorIndex](#processor-index)\
[Threadid](#thread-id)\
[Częstotliwość ticków](#tick-frequency)\
[Sygnatura czasowa](#timestamp)

## <a name="event"></a><a name="entity"></a>Zdarzenie

```cpp
Event(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Zdarzenie*\
Każde zdarzenie.

## <a name="data"></a><a name="data"></a>Danych

```cpp
const void* Data() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do dodatkowych danych zawartych w tym zdarzeniu. Aby uzyskać więcej informacji na temat interpretowania tego pola, zobacz [EVENT_DATA](../c-event-data-types/event-data-struct.md).

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

Szeroki ciąg zawierający nazwę zdarzenia identyfikowanego przez [EventId](#event-id).

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

## <a name="timestamp"></a><a name="timestamp"></a>Sygnatury czasowej

```cpp
const long long& Timestamp() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli zdarzenie jest działaniem, ta funkcja zwraca wartość znacznika przechwyconą w momencie rozpoczęcia działania. W przypadku zdarzenia prostego ta funkcja zwraca wartość znacznika przechwyconą w momencie wystąpienia zdarzenia.

::: moniker-end
