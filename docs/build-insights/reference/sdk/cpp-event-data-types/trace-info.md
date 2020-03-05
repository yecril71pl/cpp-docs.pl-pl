---
title: Klasa TraceInfo
description: Odwołanie C++ do klasy TraceInfo zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TraceInfo
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5cf32c8dc954a803a11888231d35b1050ac81cc3
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332944"
---
# <a name="traceinfo-class"></a>Klasa TraceInfo

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `TraceInfo` jest używana w celu uzyskania dostępu do przydatnych właściwości dotyczących analizowanego lub zarejestrowanego śledzenia.

## <a name="syntax"></a>Składnia

```cpp
class TraceInfo
{
public:
    TraceInfo(const TRACE_INFO_DATA& data);

    const unsigned long& LogicalProcessorCount() const;

    const long long& TickFrequency() const;
    const long long& StartTimestamp() const;
    const long long& StopTimestamp() const;

    std::chrono::nanoseconds Duration() const;
};
```

## <a name="remarks"></a>Uwagi

Odejmij `StartTimestamp` od `StopTimestamp`, aby uzyskać liczbę taktów, które upłynęły podczas całego śledzenia. Użyj `TickFrequency`, aby przekonwertować wartość wyniku na jednostkę czasu. Aby zapoznać się z przykładem konwertowania taktów na czas, zobacz [EVENT_DATA](../c-event-data-types/event-data-struct.md).

Jeśli nie chcesz samodzielnie konwertować taktów, Klasa `TraceInfo` udostępnia funkcję członkowską, która zwraca czas trwania śledzenia w nanosekundach. Użyj standardowej C++ biblioteki `chrono`, aby przekonwertować tę wartość na inne jednostki czasu.

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

[TraceInfo](#trace-info)

### <a name="functions"></a>Funkcje

[Duration](#duration)
[LogicalProcessorCount](#logical-processor-count)
[StartTimestamp](#start-timestamp)
[StopTimestamp](#stop-timestamp)
[TickFrequency](#tick-frequency)

## <a name="duration"></a>Trwania

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>Wartość zwracana

Czas trwania działania w nanosekundach.

## <a name="logical-processor-count"></a>LogicalProcessorCount

```cpp
const unsigned long& LogicalProcessorCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba procesorów logicznych na komputerze, na którym zebrano dane śledzenia.

## <a name="start-timestamp"></a>StartTimestamp

```cpp
const long long& StartTimestamp() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość taktu przechwycona w momencie rozpoczęcia śledzenia.

## <a name="stop-timestamp"></a>StopTimestamp

```cpp
const long long& StopTimestamp() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość taktu przechwycona w momencie zatrzymania śledzenia.

## <a name="tick-frequency"></a>TickFrequency

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba taktów na sekundę do użycia podczas oceniania czasu trwania mierzoną w taktach.

## <a name="trace-info"></a>TraceInfo

```cpp
TraceInfo(const TRACE_INFO_DATA& data);
```

### <a name="parameters"></a>Parametry

\ *danych*
Dane zawierające informacje o śledzeniu.

::: moniker-end
