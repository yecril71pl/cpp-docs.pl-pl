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
ms.openlocfilehash: 46a6b3548526f0917c4e022a12bf859242e70b20
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375479"
---
# <a name="tiled_index-class"></a>tiled_index — Klasa

Udostępnia indeks do [obiektu tiled_extent.](tiled-extent-class.md) Ta klasa ma właściwości dostępu do elementów względem lokalnego początku kafelków i względem pochodzenia globalnego. Aby uzyskać więcej informacji o przestrzeniach sąsiadujących, zobacz [Korzystanie z kafelków](../../../parallel/amp/using-tiles.md).

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
Długość najważniejszego wymiaru.

*_Dim1*<br/>
Długość wymiaru następnego do najbardziej znaczącego.

*_Dim2*<br/>
Długość najmniej istotnego wymiaru.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[konstruktor tiled_index](#ctor)|Inicjuje nowe wystąpienie klasy `tile_index`.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[get_tile_extent](#tiled_index__get_tile_extent)|Zwraca obiekt [extent,](extent-class.md) który ma `tiled_index` wartości `_Dim0` `_Dim1`argumentów `_Dim2`szablonu , i .|

### <a name="public-constants"></a>Stałe publiczne

|Nazwa|Opis|
|----------|-----------------|
|[stała bariera](#tiled_index__barrier)|Przechowuje [obiekt tile_barrier,](tile-barrier-class.md) który reprezentuje barierę w bieżącym kafelku wątków.|
|||
|[stała globalna](#tiled_index__global)|Przechowuje obiekt [indeksu](index-class.md) rangi 1, 2 lub 3, który reprezentuje indeks globalny w obiekcie siatki.|
|[lokalna stała](#tiled_index__local)|Przechowuje `index` obiekt rangi 1, 2 lub 3, który reprezentuje indeks względny w bieżącym kafelku [obiektu tiled_extent.](tiled-extent-class.md)|
|[Stała ranga](#tiled_index__rank)|Przechowuje rangę `tiled_index` obiektu.|
|[Stała kafelka](#tiled_index__tile)|Przechowuje `index` obiekt rangi 1, 2 lub 3, który reprezentuje współrzędne bieżącego kafelka `tiled_extent` obiektu.|
|[Stała tile_dim0](#tiled_index__tile_dim0)|Przechowuje długość najważniejszego wymiaru.|
|[Stała tile_dim1](#tiled_index__tile_dim1)|Przechowuje długość wymiaru następnego do najbardziej znaczącego.|
|[Stała tile_dim2](#tiled_index__tile_dim2)|Przechowuje długość najmniej istotnego wymiaru.|
|[Stała tile_origin](#tiled_index__tile_origin)|Przechowuje `index` obiekt rangi 1, 2 lub 3, który reprezentuje globalne współrzędne początku bieżącego kafelka w `tiled_extent` obiekcie.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[tile_extent](#tile_extent)|Pobiera obiekt [extent,](extent-class.md) który ma `tiled_index` wartości `tiled_index` argumentów szablonu argumentów `_Dim0`szablonu , `_Dim1`i `_Dim2`.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`_Tiled_index_base`

`tiled_index`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp.h

**Obszar nazw:** Współbieżności

## <a name="tiled_index-constructor"></a><a name="ctor"></a>konstruktor tiled_index

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
Globalny [indeks](index-class.md) skonstruowanego `tiled_index`.

*_Local*<br/>
Lokalny [indeks](index-class.md) skonstruowanego`tiled_index`

*_Tile*<br/>
[Indeks](index-class.md) kafelków skonstruowanego`tiled_index`

*_Tile_origin*<br/>
[Indeks](index-class.md) pochodzenia kafelków skonstruowanego`tiled_index`

*_Barrier*<br/>
Obiekt [tile_barrier](tile-barrier-class.md) skonstruowanego `tiled_index`.

*_Other*<br/>
Obiekt, `tile_index` który ma zostać skopiowany do skonstruowanego `tiled_index`pliku .

### <a name="overloads"></a>Overloads

|||
|-|-|
|Nazwa|Opis|
|`tiled_index(const index<rank>& _Global, const index<rank>& _Local, const index<rank>& _Tile, const index<rank>& _Tile_origin, const tile_barrier& _Barrier restrict(amp,cpu);`|Inicjuje nowe wystąpienie `tile_index` klasy z indeksu kafelka we współrzędnych globalnych i względnej pozycji na kafelku we współrzędnych lokalnych. Parametry `_Global` `_Tile_origin` i są obliczane.|
|`tiled_index(    const tiled_index& _Other) restrict(amp,cpu);`|Inicjuje nowe wystąpienie klasy, `tile_index` kopiując określony `tiled_index` obiekt.|

## <a name="get_tile_extent"></a><a name="tiled_index__get_tile_extent"></a>get_tile_extent

Zwraca obiekt [extent,](extent-class.md) który ma `tiled_index` wartości `_Dim0` `_Dim1`argumentów `_Dim2`szablonu , i .

### <a name="syntax"></a>Składnia

```cpp
extent<rank> get_tile_extent()restrict(amp,cpu);
```

### <a name="return-value"></a>Wartość zwracana

`extent` Obiekt, który ma wartości `tiled_index` `_Dim0`argumentów `_Dim1`szablonu , i `_Dim2`.

## <a name="barrier"></a><a name="tiled_index__barrier"></a>Barierę

Przechowuje [obiekt tile_barrier,](tile-barrier-class.md) który reprezentuje barierę w bieżącym kafelku wątków.

### <a name="syntax"></a>Składnia

```cpp
const tile_barrier barrier;
```

## <a name="global"></a><a name="tiled_index__global"></a>Globalne

Przechowuje obiekt [indeksu](index-class.md) rangi 1, 2 lub 3, który reprezentuje globalny indeks obiektu.

### <a name="syntax"></a>Składnia

```cpp
const index<rank> global;
```

## <a name="local"></a><a name="tiled_index__local"></a>Lokalnych

Przechowuje obiekt [indeksu](index-class.md) rangi 1, 2 lub 3, który reprezentuje indeks względny w bieżącym kafelku [obiektu tiled_extent.](tiled-extent-class.md)

### <a name="syntax"></a>Składnia

```cpp
const index<rank> local;
```

## <a name="rank"></a><a name="tiled_index__rank"></a>Rank

Przechowuje rangę `tiled_index` obiektu.

### <a name="syntax"></a>Składnia

```cpp
static const int rank = _Rank;
```

## <a name="tile"></a><a name="tiled_index__tile"></a>Płytki

Przechowuje obiekt [indeksu](index-class.md) rangi 1, 2 lub 3, który reprezentuje współrzędne bieżącego kafelka [obiektu tiled_extent.](tiled-extent-class.md)

### <a name="syntax"></a>Składnia

```cpp
const index<rank> tile;
```

## <a name="tile_dim0"></a><a name="tiled_index__tile_dim0"></a>tile_dim0

Przechowuje długość najważniejszego wymiaru.

### <a name="syntax"></a>Składnia

```cpp
static const int tile_dim0 = _Dim0;
```

## <a name="tile_dim1"></a><a name="tiled_index__tile_dim1"></a>tile_dim1

Przechowuje długość wymiaru następnego do najbardziej znaczącego.

### <a name="syntax"></a>Składnia

```cpp
static const int tile_dim1 = _Dim1;
```

## <a name="tile_dim2"></a><a name="tiled_index__tile_dim2"></a>tile_dim2

Przechowuje długość najmniej istotnego wymiaru.

### <a name="syntax"></a>Składnia

```cpp
static const int tile_dim2 = _Dim2;
```

## <a name="tile_origin"></a><a name="tiled_index__tile_origin"></a>tile_origin

Przechowuje obiekt [indeksu](index-class.md) rangi 1, 2 lub 3, który reprezentuje globalne współrzędne początku bieżącego kafelka w [tiled_extent](tiled-extent-class.md) obiektu.

### <a name="syntax"></a>Składnia

```cpp
const index<rank> tile_origin
```

## <a name="tile_extent"></a><a name="tile_extent"></a>tile_extent

Pobiera obiekt [extent,](extent-class.md) który ma `tiled_index` wartości `tiled_index` argumentów szablonu argumentów `_Dim0`szablonu , `_Dim1`i `_Dim2`.

### <a name="syntax"></a>Składnia

```cpp
__declspec(property(get= get_tile_extent)) extent<rank> tile_extent;
```

## <a name="see-also"></a>Zobacz też

[Obszar nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
