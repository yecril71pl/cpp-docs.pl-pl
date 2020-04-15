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
ms.openlocfilehash: ce2710da1a745efedcd6e9e524355eda41e26de2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374708"
---
# <a name="tiled_extent-class"></a>tiled_extent — Klasa

Obiekt `tiled_extent` jest `extent` obiektem o wymiarach od jednego do trzech wymiarów, który dzieli przestrzeń zasięgu na płytki jedno-, dwu- lub trójwymiarowe.

## <a name="syntax"></a>Składnia

```cpp
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
Długość najważniejszego wymiaru.

*_Dim1*<br/>
Długość wymiaru następnego do najbardziej znaczącego.

*_Dim2*<br/>
Długość najmniej istotnego wymiaru.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[konstruktor tiled_extent](#ctor)|Inicjuje nowe wystąpienie klasy `tiled_extent`.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[get_tile_extent](#get_tile_extent)|Zwraca `extent` obiekt, który przechwytuje wartości `tiled_extent` `_Dim0`argumentów `_Dim1`szablonu , i `_Dim2`.|
|[Pad](#pad)|Zwraca nowy `tiled_extent` obiekt o zakresie dostosowanym do równomiernie podzielnych przez wymiary kafelka.|
|[Obciąć](#truncate)|Zwraca nowy `tiled_extent` obiekt o zakresie dostosowanym do równomiernie podzielnych wymiarów kafelka.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[operator=](#operator_eq)|Kopiuje zawartość określonego `tiled_index` obiektu do tego obiektu.|

### <a name="public-constants"></a>Stałe publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Stała tile_dim0](#tile_dim0)|Przechowuje długość najważniejszego wymiaru.|
|[Stała tile_dim1](#tile_dim1)|Przechowuje długość wymiaru następnego do najbardziej znaczącego.|
|[Stała tile_dim2](#tile_dim2)|Przechowuje długość najmniej istotnego wymiaru.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[tile_extent](#tile_extent)|Pobiera `extent` obiekt, który przechwytuje wartości `tiled_extent` `_Dim0`argumentów `_Dim1`szablonu , i `_Dim2`.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`extent`

`tiled_extent`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp.h

**Obszar nazw:** Współbieżności

## <a name="tiled_extent-constructor"></a><a name="ctor"> </a> Konstruktor tiled_extent

Inicjuje nowe wystąpienie klasy `tiled_extent`.

### <a name="syntax"></a>Składnia

```cpp
tiled_extent();

tiled_extent(
    const Concurrency::extent<rank>& _Other );

tiled_extent(
    const tiled_extent& _Other );
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
Lub `extent` `tiled_extent` obiekt do skopiowania.

## <a name="get_tile_extent"></a><a name="get_tile_extent"> </a> get_tile_extent

Zwraca `extent` obiekt, który przechwytuje wartości `tiled_extent` `_Dim0`argumentów `_Dim1`szablonu , i `_Dim2`.

### <a name="syntax"></a>Składnia

```cpp
Concurrency::extent<rank> get_tile_extent() const restrict(amp,cpu);
```

### <a name="return-value"></a>Wartość zwracana

Obiekt, `extent` który przechwytuje wymiary `tiled_extent` tego wystąpienia.

## <a name="pad"></a><a name="pad"> </a> podkładka

Zwraca nowy `tiled_extent` obiekt o zakresie dostosowanym do równomiernie podzielnych przez wymiary kafelka.

### <a name="syntax"></a>Składnia

```cpp
tiled_extent pad() const;
```

### <a name="return-value"></a>Wartość zwracana

Nowy `tiled_extent` obiekt według wartości.

## <a name="truncate"></a><a name="truncate"> </a> obcinanie

Zwraca nowy `tiled_extent` obiekt o zakresie dostosowanym do równomiernie podzielnych wymiarów kafelka.

### <a name="syntax"></a>Składnia

```cpp
tiled_extent truncate() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca nowy `tiled_extent` obiekt o zakresie dostosowanym do równomiernie podzielnych wymiarów kafelka.

## <a name="operator"></a><a name="operator_eq"> </a> operator=

Kopiuje zawartość określonego `tiled_index` obiektu do tego obiektu.

### <a name="syntax"></a>Składnia

```cpp
tiled_extent&  operator= (
    const tiled_extent& _Other ) restrict (amp, cpu);
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
Obiekt `tiled_index` do skopiowania.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `tiled_index` tego wystąpienia.

## <a name="tile_dim0"></a><a name="tile_dim0"> </a> tile_dim0

Przechowuje długość najważniejszego wymiaru.

### <a name="syntax"></a>Składnia

```cpp
static const int tile_dim0 = _Dim0;
```

## <a name="tile_dim1"></a><a name="tile_dim1"> </a> tile_dim1

Przechowuje długość wymiaru następnego do najbardziej znaczącego.

### <a name="syntax"></a>Składnia

```cpp
static const int tile_dim1 = _Dim1;
```

## <a name="tile_dim2"></a><a name="tile_dim2"> </a> tile_dim2

Przechowuje długość najmniej istotnego wymiaru.

### <a name="syntax"></a>Składnia

```cpp
static const int tile_dim2 = _Dim2;
```

## <a name="tile_extent"></a><a name="tile_extent"> </a> tile_extent

Pobiera `extent` obiekt, który przechwytuje wartości `tiled_extent` `_Dim0`argumentów `_Dim1`szablonu , i `_Dim2`.

### <a name="syntax"></a>Składnia

```cpp
__declspec(property(get= get_tile_extent)) Concurrency::extent<rank> tile_extent;
```

## <a name="see-also"></a>Zobacz też

[Obszar nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
