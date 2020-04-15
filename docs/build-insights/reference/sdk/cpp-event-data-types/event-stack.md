---
title: Klasa EventStack
description: Odwołanie do klasy SDK EventStack aplikacji C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EventStack
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: eaaaedcbf57fdaf8e437a80a7823488febac3e1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324983"
---
# <a name="eventstack-class"></a>Klasa EventStack

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `EventStack` jest kolekcją [Event](event.md) obiektów. Wszystkie zdarzenia odebrane z SDK analizy kompilacji języka `EventStack` C++ są w postaci obiektu. Ostatni wpis w tym stosie jest zdarzeniem aktualnie przetwarzane. Wpisy poprzedzające ostatni wpis są hierarchią nadrzędną bieżącego zdarzenia. Aby uzyskać więcej informacji na temat modelu zdarzeń używanego w usłudze C++ Build Insights, zobacz [tabelę zdarzeń](../event-table.md).

## <a name="syntax"></a>Składnia

```cpp
class EventStack
{
public:
    EventStack(const EVENT_COLLECTION_DATA& data);

    size_t      Size() const;
    RawEvent    Back() const;
    RawEvent    operator[] (size_t index) const;
};
```

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

[WydarzenieStack](#event-stack)

### <a name="functions"></a>Funkcje

[Operator](#back)
[tylny[]](#subscript-operator)
[Rozmiar](#size)

## <a name="back"></a><a name="back"></a>Wstecz

```cpp
RawEvent Back() const;
```

### <a name="return-value"></a>Wartość zwracana

[RawEvent](raw-event.md) obiektu, który reprezentuje ostatni wpis w stosie. Ostatni wpis w stosie zdarzeń jest zdarzenie, które zostało wyzwolone.

## <a name="eventstack"></a><a name="event-stack"></a>WydarzenieStack

```cpp
EventStack(const EVENT_COLLECTION_DATA& data);
```

### <a name="parameters"></a>Parametry

*Danych*\
Nieprzetworzone `EventStack` dane, z których jest zbudowany.

### <a name="remarks"></a>Uwagi

Zazwyczaj nie trzeba tworzyć `EventStack` obiektów samodzielnie. Są one dostarczane przez C++ Build Insights SDK, gdy zdarzenia są przetwarzane podczas analizy lub sesji ponownego rejestrowania.

## <a name="operator"></a><a name="subscript-operator"></a>operator[]

```cpp
RawEvent operator[] (size_t index) const;
```

### <a name="parameters"></a>Parametry

*Indeks*\
Indeks elementu, aby uzyskać dostęp w stosie zdarzeń.

### <a name="return-value"></a>Wartość zwracana

[RawEvent](raw-event.md) obiektu, który reprezentuje zdarzenie przechowywane w pozycji wskazanej przez *indeks* w stosie zdarzeń.

## <a name="size"></a><a name="size"></a>Rozmiar

```cpp
size_t Size() const;
```

### <a name="return-value"></a>Wartość zwracana

Rozmiar stosu zdarzeń.

::: moniker-end
