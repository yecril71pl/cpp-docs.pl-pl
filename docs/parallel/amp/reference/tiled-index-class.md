---
title: tiled_index — Klasa
ms.date: 03/27/2019
f1_keywords:
- tiled_index
- AMP/tiled_index
- AMP/Concurrency::tiled_index::tiled_index
- AMP/Concurrency::tiled_index::get_tile_extent
- AMP/Concurrency::tiled_index::barrier
- AMP/Concurrency::tiled_index::global
- AMP/Concurrency::tiled_index::local
- AMP/Concurrency::tiled_index::rank
- AMP/Concurrency::tiled_index::tile
- AMP/Concurrency::tiled_index::tile_dim0
- AMP/Concurrency::tiled_index::tile_dim1
- AMP/Concurrency::tiled_index::tile_dim2
- AMP/Concurrency::tiled_index::tile_origin
- AMP/Concurrency::tiled_index::tile_extent
helpviewer_keywords:
- tiled_index class
ms.assetid: 0ce2ae26-f1bb-4436-b473-a9e1b619bb38
ms.openlocfilehash: 9d295093031eaee0a2d4dd83aa931060e6eebc07
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832273"
---
# <a name="tiled_index-class"></a>tiled_index — Klasa

Zapewnia indeks w obiekcie [tiled_extent](tiled-extent-class.md) . Ta klasa ma właściwości umożliwiające dostęp do elementów względem lokalnego źródła kafelka i względem pierwotnego źródła. Aby uzyskać więcej informacji o sąsiadujących miejscach, zobacz [Używanie kafelków](../../../parallel/amp/using-tiles.md).

## <a name="syntax"></a>Składnia

```cpp
template <
    int _Dim0,
    int _Dim1 = 0,
    int _Dim2 = 0
>
class tiled_index : public _Tiled_index_base<3>;

template <
    int _Dim0,
    int _Dim1
>
class tiled_index<_Dim0, _Dim1, 0> : public _Tiled_index_base<2>;

template <
    int _Dim0
>
class tiled_index<_Dim0, 0, 0> : public _Tiled_index_base<1>;
```

### <a name="parameters"></a>Parametry

*_Dim0*<br/>
Długość najbardziej znaczącego wymiaru.

*_Dim1*<br/>
Długość następnego do najbardziej znaczącego wymiaru.

*_Dim2*<br/>
Długość najmniej znaczącego wymiaru.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Konstruktor tiled_index](#ctor)|Inicjuje nowe wystąpienie klasy `tile_index`.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[get_tile_extent](#tiled_index__get_tile_extent)|Zwraca obiekt [zakresu](extent-class.md) , który ma wartości `tiled_index` argumentów szablonu `_Dim0` , `_Dim1` i `_Dim2` .|

### <a name="public-constants"></a>Stałe publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Stała bariery](#tiled_index__barrier)|Przechowuje [tile_barrier](tile-barrier-class.md) obiektu, który reprezentuje barierę w bieżącym kafelku wątków.|
|[Stała globalna](#tiled_index__global)|Przechowuje obiekt [indeksu](index-class.md) rangi 1, 2 lub 3, który reprezentuje indeks globalny w obiekcie siatki.|
|[Stała lokalna](#tiled_index__local)|Przechowuje `index` obiekt rangi 1, 2 lub 3, który reprezentuje indeks względny w bieżącym kafelku obiektu [tiled_extent](tiled-extent-class.md) .|
|[Stała rangi](#tiled_index__rank)|Przechowuje rangę `tiled_index` obiektu.|
|[Stała kafelka](#tiled_index__tile)|Przechowuje `index` obiekt o rangi 1, 2 lub 3, który reprezentuje współrzędne bieżącego kafelka `tiled_extent` obiektu.|
|[tile_dim0 stała](#tiled_index__tile_dim0)|Przechowuje długość najbardziej znaczącego wymiaru.|
|[tile_dim1 stała](#tiled_index__tile_dim1)|Przechowuje Długość następnego do najbardziej znaczącego wymiaru.|
|[tile_dim2 stała](#tiled_index__tile_dim2)|Przechowuje długość najmniej znaczącego wymiaru.|
|[tile_origin stała](#tiled_index__tile_origin)|Przechowuje `index` obiekt rangi 1, 2 lub 3, który reprezentuje globalne współrzędne pochodzenia bieżącego kafelka w `tiled_extent` obiekcie.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[tile_extent](#tile_extent)|Pobiera obiekt [zakresu](extent-class.md) , który ma wartości `tiled_index` `tiled_index` argumentów szablonu argumentów szablonu `_Dim0` , `_Dim1` i `_Dim2` .|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`_Tiled_index_base`

`tiled_index`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp. h

**Przestrzeń nazw:** Współbieżności

## <a name="tiled_index-constructor"></a><a name="ctor"></a> Konstruktor tiled_index

Inicjuje nowe wystąpienie klasy `tiled_index`.

### <a name="syntax"></a>Składnia

```cpp
tiled_index(
    const index<rank>& _Global,
    const index<rank>& _Local,
    const index<rank>& _Tile,
    const index<rank>& _Tile_origin,
    const tile_barrier& _Barrier ) restrict(amp,cpu);

tiled_index(
    const tiled_index& _Other ) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Global*<br/>
Globalny [indeks](index-class.md) skonstruowany `tiled_index` .

*_Local*<br/>
Lokalny [indeks](index-class.md) skonstruowanego `tiled_index`

*_Tile*<br/>
[Indeks](index-class.md) kafelków skonstruowanego`tiled_index`

*_Tile_origin*<br/>
[Indeks](index-class.md) początku kafelka skonstruowanego`tiled_index`

*_Barrier*<br/>
Obiekt [tile_barrier](tile-barrier-class.md) skonstruowany `tiled_index` .

*_Other*<br/>
`tile_index`Obiekt, który ma zostać skopiowany do skonstruowanego obiektu `tiled_index` .

### <a name="overloads"></a>Przeciążenia

|Nazwa|Opis|
|-|-|
|`tiled_index(const index<rank>& _Global, const index<rank>& _Local, const index<rank>& _Tile, const index<rank>& _Tile_origin, const tile_barrier& _Barrier restrict(amp,cpu);`|Inicjuje nowe wystąpienie `tile_index` klasy z indeksu kafelka w globalnych współrzędnych i względne położenie na kafelku we współrzędnych lokalnych. `_Global`Parametry i `_Tile_origin` są obliczane.|
|`tiled_index(    const tiled_index& _Other) restrict(amp,cpu);`|Inicjuje nowe wystąpienie `tile_index` klasy przez skopiowanie określonego `tiled_index` obiektu.|

## <a name="get_tile_extent"></a><a name="tiled_index__get_tile_extent"></a> get_tile_extent

Zwraca obiekt [zakresu](extent-class.md) , który ma wartości `tiled_index` argumentów szablonu `_Dim0` , `_Dim1` i `_Dim2` .

### <a name="syntax"></a>Składnia

```cpp
extent<rank> get_tile_extent()restrict(amp,cpu);
```

### <a name="return-value"></a>Wartość zwracana

`extent`Obiekt, który ma wartości `tiled_index` argumentów szablonu `_Dim0` , `_Dim1` i `_Dim2` .

## <a name="barrier"></a><a name="tiled_index__barrier"></a> barier

Przechowuje [tile_barrier](tile-barrier-class.md) obiektu, który reprezentuje barierę w bieżącym kafelku wątków.

### <a name="syntax"></a>Składnia

```cpp
const tile_barrier barrier;
```

## <a name="global"></a><a name="tiled_index__global"></a> globalne

Przechowuje obiekt [indeksu](index-class.md) rangi 1, 2 lub 3, który reprezentuje globalny indeks obiektu.

### <a name="syntax"></a>Składnia

```cpp
const index<rank> global;
```

## <a name="local"></a><a name="tiled_index__local"></a> LAN

Przechowuje obiekt [indeksu](index-class.md) rangi 1, 2 lub 3, który reprezentuje indeks względny w bieżącym kafelku obiektu [tiled_extent](tiled-extent-class.md) .

### <a name="syntax"></a>Składnia

```cpp
const index<rank> local;
```

## <a name="rank"></a><a name="tiled_index__rank"></a> stopni

Przechowuje rangę `tiled_index` obiektu.

### <a name="syntax"></a>Składnia

```cpp
static const int rank = _Rank;
```

## <a name="tile"></a><a name="tiled_index__tile"></a> tabliczek

Przechowuje obiekt [indeksu](index-class.md) rangi 1, 2 lub 3, który reprezentuje współrzędne bieżącego kafelka obiektu [tiled_extent](tiled-extent-class.md) .

### <a name="syntax"></a>Składnia

```cpp
const index<rank> tile;
```

## <a name="tile_dim0"></a><a name="tiled_index__tile_dim0"></a> tile_dim0

Przechowuje długość najbardziej znaczącego wymiaru.

### <a name="syntax"></a>Składnia

```cpp
static const int tile_dim0 = _Dim0;
```

## <a name="tile_dim1"></a><a name="tiled_index__tile_dim1"></a> tile_dim1

Przechowuje Długość następnego do najbardziej znaczącego wymiaru.

### <a name="syntax"></a>Składnia

```cpp
static const int tile_dim1 = _Dim1;
```

## <a name="tile_dim2"></a><a name="tiled_index__tile_dim2"></a> tile_dim2

Przechowuje długość najmniej znaczącego wymiaru.

### <a name="syntax"></a>Składnia

```cpp
static const int tile_dim2 = _Dim2;
```

## <a name="tile_origin"></a><a name="tiled_index__tile_origin"></a> tile_origin

Przechowuje obiekt [indeksu](index-class.md) rangi 1, 2 lub 3, który reprezentuje globalne współrzędne pochodzenia bieżącego kafelka w obiekcie [tiled_extent](tiled-extent-class.md) .

### <a name="syntax"></a>Składnia

```cpp
const index<rank> tile_origin
```

## <a name="tile_extent"></a><a name="tile_extent"></a> tile_extent

Pobiera obiekt [zakresu](extent-class.md) , który ma wartości `tiled_index` `tiled_index` argumentów szablonu argumentów szablonu `_Dim0` , `_Dim1` i `_Dim2` .

### <a name="syntax"></a>Składnia

```cpp
__declspec(property(get= get_tile_extent)) extent<rank> tile_extent;
```

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
