---
title: tiled_extent — Klasa
ms.date: 11/04/2016
f1_keywords:
- tiled_extent
- AMP/tiled_extent
- AMP/Concurrency::tiled_extent::tiled_extent
- AMP/Concurrency::tiled_extent::get_tile_extent
- AMP/Concurrency::tiled_extent::pad
- AMP/Concurrency::tiled_extent::truncate
- AMP/Concurrency::tiled_extent::tile_dim0
- AMP/Concurrency::tiled_extent::tile_dim1
- AMP/Concurrency::tiled_extent::tile_dim2
- AMP/Concurrency::tiled_extent::tile_extent
ms.assetid: 671ecaf8-c7b0-4ac8-bbdc-e30bd92da7c0
ms.openlocfilehash: 77d16eefa61fb30614cb6527792014cc8655abe0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476898"
---
# <a name="tiledextent-class"></a>tiled_extent — Klasa

A `tiled_extent` obiekt jest `extent` obiektu od jednego do trzech wymiarów, dzielący przestrzeń na jedno-, dwu- lub trójwymiarowe fragmenty.

### <a name="syntax"></a>Składnia

```
template <
    int _Dim0,
    int _Dim1,
    int _Dim2
>
class tiled_extent : public Concurrency::extent<3>;

template <
    int _Dim0,
    int _Dim1
>
class tiled_extent<_Dim0, _Dim1, 0> : public Concurrency::extent<2>;

template <
    int _Dim0
>
class tiled_extent<_Dim0, 0, 0> : public Concurrency::extent<1>;
```

### <a name="parameters"></a>Parametry

*_Dim0*<br/>
Długość najbardziej znaczącego wymiaru.

*_Dim1*<br/>
Długość następnego najbardziej znaczącego wymiaru.

*_Dim2*<br/>
Długość najmniej znaczącego wymiaru.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[tiled_extent konstruktora](#ctor)|Inicjuje nowe wystąpienie klasy `tiled_extent` klasy.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[get_tile_extent](#get_tile_extent)|Zwraca `extent` obiekt, który przechwytuje wartości `tiled_extent` argumentów szablonu `_Dim0`, `_Dim1`, i `_Dim2`.|
|[Konsola](#pad)|Zwraca nowy `tiled_extent` obiektu z zakresów powiększonym rozmiarem, aby był podzielny przez wymiary fragmentu.|
|[Obetnij](#truncate)|Zwraca nowy `tiled_extent` obiektu z zakresów pomniejszonym rozmiarem, aby był podzielny przez wymiary fragmentu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[operator=](#operator_eq)|Kopiuje zawartość określonego `tiled_index` obiektu do wskazanego.|

### <a name="public-constants"></a>Publiczne stałe

|Nazwa|Opis|
|----------|-----------------|
|[tile_dim0 — stała](#tile_dim0)|Przechowuje długość najbardziej znaczącego wymiaru.|
|[tile_dim1 — stała](#tile_dim1)|Przechowuje długość następnego najbardziej znaczącego wymiaru.|
|[tile_dim2 — stała](#tile_dim2)|Przechowuje długość najmniej znaczącego wymiaru.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[tile_extent](#tile_extent)|Pobiera `extent` obiekt, który przechwytuje wartości `tiled_extent` argumentów szablonu `_Dim0`, `_Dim1`, i `_Dim2`.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`extent`

`tiled_extent`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp.h

**Namespace:** współbieżności

## <a name="ctor"> </a>  tiled_extent konstruktora

Inicjuje nowe wystąpienie klasy `tiled_extent` klasy.

### <a name="syntax"></a>Składnia

```
tiled_extent();

tiled_extent(
    const Concurrency::extent<rank>& _Other );

tiled_extent(
    const tiled_extent& _Other );
```

### <a name="parameters"></a>Parametry

*_Inne*<br/>
`extent` Lub `tiled_extent` obiektu do skopiowania.

## <a name="get_tile_extent"> </a>  get_tile_extent —

Zwraca `extent` obiekt, który przechwytuje wartości `tiled_extent` argumentów szablonu `_Dim0`, `_Dim1`, i `_Dim2`.

### <a name="syntax"></a>Składnia

```
Concurrency::extent<rank> get_tile_extent() const restrict(amp,cpu);
```

### <a name="return-value"></a>Wartość zwracana

`extent` Obiekt, który przechwytuje wymiary tego `tiled_extent` wystąpienia.

## <a name="pad"> </a>  Konsola

Zwraca nowy `tiled_extent` obiektu z zakresów powiększonym rozmiarem, aby był podzielny przez wymiary fragmentu.

### <a name="syntax"></a>Składnia

```
tiled_extent pad() const;
```

### <a name="return-value"></a>Wartość zwracana

Nowy `tiled_extent` obiekt przez wartość.
## <a name="truncate"> </a>  Obetnij

Zwraca nowy `tiled_extent` obiektu z zakresów pomniejszonym rozmiarem, aby był podzielny przez wymiary fragmentu.

### <a name="syntax"></a>Składnia

```
tiled_extent truncate() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca nowy `tiled_extent` obiektu z zakresów pomniejszonym rozmiarem, aby był podzielny przez wymiary fragmentu.

## <a name="operator_eq"> </a>  operator =

Kopiuje zawartość określonego `tiled_index` obiektu do wskazanego.

### <a name="syntax"></a>Składnia

```
tiled_extent&  operator= (
    const tiled_extent& _Other ) restrict (amp, cpu);
```

### <a name="parameters"></a>Parametry

*_Inne*<br/>
`tiled_index` Obiektu do skopiowania.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `tiled_index` wystąpienia.

## <a name="tile_dim0"> </a>  tile_dim0

Przechowuje długość najbardziej znaczącego wymiaru.

### <a name="syntax"></a>Składnia

```
static const int tile_dim0 = _Dim0;
```

## <a name="tile_dim1"> </a>  tile_dim1

Przechowuje długość następnego najbardziej znaczącego wymiaru.

### <a name="syntax"></a>Składnia

```
static const int tile_dim1 = _Dim1;
```

## <a name="tile_dim2"> </a>  tile_dim2

Przechowuje długość najmniej znaczącego wymiaru.

### <a name="syntax"></a>Składnia

```
static const int tile_dim2 = _Dim2;
```

## <a name="tile_extent"> </a>  tile_extent —
  Pobiera `extent` obiekt, który przechwytuje wartości `tiled_extent` argumentów szablonu `_Dim0`, `_Dim1`, i `_Dim2`.

### <a name="syntax"></a>Składnia

```
__declspec(property(get= get_tile_extent)) Concurrency::extent<rank> tile_extent;
```

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
