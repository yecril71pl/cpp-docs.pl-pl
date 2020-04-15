---
title: TraceInfo, klasa
description: Odwołanie do klasy SDK TraceInfo kompilacji języka C++.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TraceInfo
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 75d53937e3999f5692dee0ecf419e0ce5f49a274
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324175"
---
# <a name="traceinfo-class"></a>TraceInfo, klasa

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `TraceInfo` jest używana do uzyskiwania dostępu do przydatnych właściwości śledzenia analizowane lub ponownie rejestrowane.

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

Odejmij `StartTimestamp` `StopTimestamp` od uzyskania liczby kleszczy, które upłynęło podczas całego śledzenia. Służy `TickFrequency` do konwertowania wartości wynikowej na jednostkę czasu. Na przykład konwersji znaczników na czas, zobacz [EVENT_DATA](../c-event-data-types/event-data-struct.md).

Jeśli nie chcesz konwertować znaczników `TraceInfo` samodzielnie, klasa zapewnia funkcję elementu członkowskiego, która zwraca czas trwania śledzenia w nanosekundach. Użyj standardowej biblioteki C++, `chrono` aby przekonwertować tę wartość na inne jednostki czasu.

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

[Traceinfo](#trace-info)

### <a name="functions"></a>Funkcje

[Czas trwania](#duration)
[LogicalProcessorCount](#logical-processor-count)
[StartTimestamp](#start-timestamp)
[StopTimestamp](#stop-timestamp)
[TickFrequency](#tick-frequency)

## <a name="duration"></a><a name="duration"></a>Długość

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>Wartość zwracana

Czas trwania działania w nanosekundach.

## <a name="logicalprocessorcount"></a><a name="logical-processor-count"></a>Licznik logicznyprocesorów

```cpp
const unsigned long& LogicalProcessorCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba procesorów logicznych na komputerze, na którym zebrano ślad.

## <a name="starttimestamp"></a><a name="start-timestamp"></a>Sygnatura starttimestamp

```cpp
const long long& StartTimestamp() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość znacznika przechwycona w momencie rozpoczęcia śledzenia.

## <a name="stoptimestamp"></a><a name="stop-timestamp"></a>StopTimestamp (StopTimestamp)

```cpp
const long long& StopTimestamp() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość znacznika przechwycona w momencie zatrzymania śledzenia.

## <a name="tickfrequency"></a><a name="tick-frequency"></a>Częstotliwość ticków

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba znaczników na sekundę do użycia podczas oceny czasu trwania mierzonego w kleszczach.

## <a name="traceinfo"></a><a name="trace-info"></a>Traceinfo

```cpp
TraceInfo(const TRACE_INFO_DATA& data);
```

### <a name="parameters"></a>Parametry

*Danych*\
Dane zawierające informacje o śledzeniu.

::: moniker-end
