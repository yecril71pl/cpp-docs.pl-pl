---
title: Klasa EventGroup
description: Odwołanie do klasy SDK SDK eventgroup kompilacji języka C++.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EventGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 596c18ca0e9b4d7b26c4ed5209b16871952c4af2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324987"
---
# <a name="eventgroup-class"></a>Klasa EventGroup

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Szablon `EventGroup` klasy jest klasą podstawową dla wszystkich klas przechwytywania grupy.

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

*Bezczynność* Typ działania zawarty w grupie.

## <a name="members"></a>Elementy członkowskie

### <a name="functions"></a>Funkcje

[Tylny](#back)
[początek](#begin)
[end](#end)
[operator[]](#subscript-operator)
[Size](#size) [Front](#front)Operator frontu[] Rozmiar


## <a name="back"></a><a name="back"></a>Wstecz

```cpp
const TActivity& Back() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do ostatniego zdarzenia działania w grupie.

## <a name="begin"></a><a name="begin"></a>Rozpocząć

```cpp
std::deque<TActivity>::const_iterator begin() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator wskazujący na początku grupy zdarzeń działania.

## <a name="end"></a><a name="end"></a>Końcu

```cpp
std::deque<TActivity>::const_iterator end() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator wskazujący jedną pozycję poza koniec grupy zdarzeń aktywności.

## <a name="front"></a><a name="front"></a>Przednie

```cpp
const TActivity& Front() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do pierwszego zdarzenia działania w grupie.

## <a name="operator"></a><a name="subscript-operator"></a>operator[]

```cpp
const TActivity& operator[](size_t index) const;
```

### <a name="parameters"></a>Parametry

*Indeks*\
Indeks elementu dostępu w grupie zdarzeń działania.

### <a name="return-value"></a>Wartość zwracana

Zdarzenie ze stosu zdarzeń przechowywane w pozycji wskazanej przez *indeks*.

## <a name="size"></a><a name="size"></a>Rozmiar

```cpp
size_t Size() const;
```

### <a name="return-value"></a>Wartość zwracana

Rozmiar grupy zdarzeń.

::: moniker-end
