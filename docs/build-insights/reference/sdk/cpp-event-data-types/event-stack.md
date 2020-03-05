---
title: Klasa EventStack
description: Odwołanie C++ do klasy EventStack zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EventStack
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6da2fd25082399b82d788c5d119a39e2f7388714
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333406"
---
# <a name="eventstack-class"></a>Klasa EventStack

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `EventStack` jest kolekcją obiektów [zdarzeń](event.md) . Wszystkie zdarzenia otrzymane z zestawu C++ SDK usługi Build Insights są dostępne w postaci obiektu `EventStack`. Ostatni wpis w tym stosie jest aktualnie przetwarzanym zdarzeniem. Wpisy poprzedzające ostatni wpis są hierarchią nadrzędną bieżącego zdarzenia. Aby uzyskać więcej informacji na temat modelu zdarzeń używanego C++ w usłudze Build Insights, zobacz [tabela zdarzeń](../event-table.md).

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

[EventStack](#event-stack)

### <a name="functions"></a>Funkcje

[](#back)
[rozmiar](#size) [operatora
[]](#subscript-operator)

## <a name="back"></a>Wstecz

```cpp
RawEvent Back() const;
```

### <a name="return-value"></a>Wartość zwracana

Obiekt [RawEvent](raw-event.md) , który reprezentuje ostatni wpis w stosie. Ostatnim wpisem w stosie zdarzeń jest zdarzenie, które zostało wyzwolone.

## <a name="event-stack"></a>EventStack

```cpp
EventStack(const EVENT_COLLECTION_DATA& data);
```

### <a name="parameters"></a>Parametry

\ *danych*
Dane pierwotne, z których utworzono `EventStack`.

### <a name="remarks"></a>Uwagi

Nie ma potrzeby zwykle konstruowania obiektów `EventStack`. Są one udostępniane przez zestaw SDK usługi C++ Build Insights, gdy zdarzenia są przetwarzane podczas przeprowadzania analizy lub ponownego rejestrowania sesji.

## <a name="subscript-operator"></a>operator []

```cpp
RawEvent operator[] (size_t index) const;
```

### <a name="parameters"></a>Parametry

\ *indeksu*
Indeks elementu, do którego można uzyskać dostęp w stosie zdarzeń.

### <a name="return-value"></a>Wartość zwracana

Obiekt [RawEvent](raw-event.md) , który reprezentuje zdarzenie przechowywane w pozycji wskazywanej przez *indeks* w stosie zdarzeń.

## <a name="size"></a>Zmienia

```cpp
size_t Size() const;
```

### <a name="return-value"></a>Wartość zwracana

Rozmiar stosu zdarzeń.

::: moniker-end
