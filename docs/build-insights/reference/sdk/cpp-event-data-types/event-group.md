---
title: Event, Klasa
description: Odwołanie C++ do klasy grupy zdarzeń zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EventGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ac8ac70f3fc160714b86dd0c483808a4d06e7699
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333434"
---
# <a name="eventgroup-class"></a>Event, Klasa

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Szablon klasy `EventGroup` jest klasą bazową dla wszystkich klas przechwytywania grup.

## <a name="syntax"></a>Składnia

```cpp
template <typename TActivity>
class EventGroup;
{
public:
    size_t Size() const;

    const TActivity& operator[](size_t index) const;
    const TActivity& Front() const;
    const TActivity& Back() const;

    std::deque<TActivity>::const_iterator begin() const;
    std::deque<TActivity>::const_iterator end() const;
};
```

### <a name="parameters"></a>Parametry

*TActivity* Typ działania zawarty w grupie.

## <a name="members"></a>Elementy członkowskie

### <a name="functions"></a>Funkcje

[Zaplecze](#back)
[begin](#begin)
[End](#end)
[przednim](#front) [operatorem
[]](#subscript-operator)
[rozmiar](#size)

## <a name="back"></a>Wstecz

```cpp
const TActivity& Back() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do ostatniego zdarzenia działania w grupie.

## <a name="begin"></a>zaczną

```cpp
std::deque<TActivity>::const_iterator begin() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator wskazujący początek grupy zdarzeń działania.

## <a name="end"></a>punktów

```cpp
std::deque<TActivity>::const_iterator end() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator wskazujący jedną pozycję poza końcem grupy zdarzeń działania.

## <a name="front"></a>FSB

```cpp
const TActivity& Front() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do pierwszego zdarzenia działania w grupie.

## <a name="subscript-operator"></a>operator []

```cpp
const TActivity& operator[](size_t index) const;
```

### <a name="parameters"></a>Parametry

\ *indeksu*
Indeks elementu, do którego można uzyskać dostęp w grupie zdarzeń działania.

### <a name="return-value"></a>Wartość zwracana

Zdarzenie ze stosu zdarzeń przechowywane w pozycji wskazywanej przez *indeks*.

## <a name="size"></a>Zmienia

```cpp
size_t Size() const;
```

### <a name="return-value"></a>Wartość zwracana

Rozmiar grupy zdarzeń.

::: moniker-end
