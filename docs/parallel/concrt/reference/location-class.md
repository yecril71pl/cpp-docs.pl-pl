---
title: location — Klasa
ms.date: 11/04/2016
f1_keywords:
- location
- CONCRT/concurrency::location
- CONCRT/concurrency::location::location
- CONCRT/concurrency::location::current
- CONCRT/concurrency::location::from_numa_node
helpviewer_keywords:
- location class
ms.assetid: c3289f51-5bf1-4dff-a18d-d0dab8e5d9c7
ms.openlocfilehash: 848be3131e23ff53f2dec16364b132ee7c218195
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87182697"
---
# <a name="location-class"></a>location — Klasa

Abstrakcja fizycznej lokalizacji na sprzęcie.

## <a name="syntax"></a>Składnia

```cpp
class location;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[przeniesienie](#ctor)|Przeciążone. Konstruuje `location` obiekt.|
|[~ Location — destruktor](#dtor)|Niszczy `location` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[bieżący](#current)|Zwraca `location` obiekt reprezentujący najbardziej charakterystyczne miejsce wykonywane przez wątek wywołujący.|
|[from_numa_node](#from_numa_node)|Zwraca `location` obiekt, który reprezentuje dany węzeł NUMA.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[operator! =](#operator_neq)|Określa, czy dwa `location` obiekty reprezentują różne lokalizacje.|
|[operator =](#operator_eq)|Przypisuje do tego zawartość innego `location` obiektu.|
|[operator = =](#operator_eq_eq)|Określa, czy dwa `location` obiekty reprezentują tę samą lokalizację.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`location`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h

**Przestrzeń nazw:** współbieżność

## <a name="location"></a><a name="dtor"></a>~ Lokalizacja

Niszczy `location` obiekt.

```cpp
~location();
```

## <a name="current"></a><a name="current"></a>obecne

Zwraca `location` obiekt reprezentujący najbardziej charakterystyczne miejsce wykonywane przez wątek wywołujący.

```cpp
static location __cdecl current();
```

### <a name="return-value"></a>Wartość zwracana

Lokalizacja reprezentująca najbardziej charakterystyczne miejsce wykonywane przez wątek wywołujący.

## <a name="from_numa_node"></a><a name="from_numa_node"></a>from_numa_node

Zwraca `location` obiekt, który reprezentuje dany węzeł NUMA.

```cpp
static location __cdecl from_numa_node(unsigned short _NumaNodeNumber);
```

### <a name="parameters"></a>Parametry

*_NumaNodeNumber*<br/>
Numer węzła NUMA służący do konstruowania lokalizacji.

### <a name="return-value"></a>Wartość zwracana

Lokalizacja reprezentująca węzeł NUMA określony przez `_NumaNodeNumber` parametr.

## <a name="location"></a><a name="ctor"></a>przeniesienie

Konstruuje `location` obiekt.

```cpp
location();

location(
    const location& _Src);

location(
    T _LocationType,
    unsigned int _Id,
    unsigned int _BindingId = 0,
    _Inout_opt_ void* _PBinding = NULL);
```

### <a name="parameters"></a>Parametry

*_Src*<br/>

*_LocationType*<br/>

*_Id*<br/>

*_BindingId*<br/>

*_PBinding*<br/>
Obowiązkowe Wskaźnik powiązania.

### <a name="remarks"></a>Uwagi

Domyślna lokalizacja skonstruowana reprezentuje system jako całość.

## <a name="operator"></a><a name="operator_neq"></a>operator! =

Określa, czy dwa `location` obiekty reprezentują różne lokalizacje.

```cpp
bool operator!= (const location& _Rhs) const;
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Argument operacji `location` .

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli dwie lokalizacje są różne, **`false`** w przeciwnym razie.

## <a name="operator"></a><a name="operator_eq"></a>operator =

Przypisuje do tego zawartość innego `location` obiektu.

```cpp
location& operator= (const location& _Rhs);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Obiekt źródłowy `location` .

### <a name="return-value"></a>Wartość zwracana

## <a name="operator"></a><a name="operator_eq_eq"></a>operator = =

Określa, czy dwa `location` obiekty reprezentują tę samą lokalizację.

```cpp
bool operator== (const location& _Rhs) const;
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Argument operacji `location` .

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli dwie lokalizacje są identyczne i **`false`** w przeciwnym razie.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
