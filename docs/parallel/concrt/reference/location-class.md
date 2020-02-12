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
ms.openlocfilehash: 7f45ff6d3092bd7c27e81adddca72c9411f752d1
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139826"
---
# <a name="location-class"></a>location — Klasa

Abstrakcja fizycznej lokalizacji na sprzęcie.

## <a name="syntax"></a>Składnia

```cpp
class location;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[location](#ctor)|Przeciążone. Konstruuje obiekt `location`.|
|[~ Location — destruktor](#dtor)|Niszczy obiekt `location`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[obecne](#current)|Zwraca obiekt `location` reprezentujący najbardziej charakterystyczne miejsce wykonywane przez wątek wywołujący.|
|[from_numa_node](#from_numa_node)|Zwraca obiekt `location`, który reprezentuje dany węzeł NUMA.|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[operator!=](#operator_neq)|Określa, czy dwa obiekty `location` reprezentują różne lokalizacje.|
|[operator =](#operator_eq)|Przypisuje do niego zawartość innego obiektu `location`.|
|[operator = =](#operator_eq_eq)|Określa, czy dwa obiekty `location` reprezentują tę samą lokalizację.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`location`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h

**Przestrzeń nazw:** współbieżność

## <a name="dtor"></a>~ Lokalizacja

Niszczy obiekt `location`.

```cpp
~location();
```

## <a name="current"></a>obecne

Zwraca obiekt `location` reprezentujący najbardziej charakterystyczne miejsce wykonywane przez wątek wywołujący.

```cpp
static location __cdecl current();
```

### <a name="return-value"></a>Wartość zwrócona

Lokalizacja reprezentująca najbardziej charakterystyczne miejsce wykonywane przez wątek wywołujący.

## <a name="from_numa_node"></a>from_numa_node

Zwraca obiekt `location`, który reprezentuje dany węzeł NUMA.

```cpp
static location __cdecl from_numa_node(unsigned short _NumaNodeNumber);
```

### <a name="parameters"></a>Parametry

*_NumaNodeNumber*<br/>
Numer węzła NUMA służący do konstruowania lokalizacji.

### <a name="return-value"></a>Wartość zwrócona

Lokalizacja reprezentująca węzeł NUMA określony przez parametr `_NumaNodeNumber`.

## <a name="ctor"></a>przeniesienie

Konstruuje obiekt `location`.

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

## <a name="operator_neq"></a>operator! =

Określa, czy dwa obiekty `location` reprezentują różne lokalizacje.

```cpp
bool operator!= (const location& _Rhs) const;
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
`location`operandu.

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli dwie lokalizacje są różne, w przeciwnym razie **false** .

## <a name="operator_eq"></a>operator =

Przypisuje do niego zawartość innego obiektu `location`.

```cpp
location& operator= (const location& _Rhs);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Obiekt źródłowy `location`.

### <a name="return-value"></a>Wartość zwrócona

## <a name="operator_eq_eq"></a>operator = =

Określa, czy dwa obiekty `location` reprezentują tę samą lokalizację.

```cpp
bool operator== (const location& _Rhs) const;
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
`location`operandu.

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli dwie lokalizacje są identyczne i w przeciwnym razie ma **wartość false** .

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
