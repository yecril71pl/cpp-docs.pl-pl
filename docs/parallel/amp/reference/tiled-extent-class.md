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
ms.openlocfilehash: e2248c770c7eedde59d1cb592f7d5d7c1bfbde9a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126425"
---
# <a name="tiled_extent-class"></a>tiled_extent — Klasa

Obiekt `tiled_extent` jest obiektem `extent` od jednego do trzech wymiarów dzielących miejsce na jeden, dwa-lub trójwymiarowe kafelki.

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
Długość najbardziej znaczącego wymiaru.

*_Dim1*<br/>
Długość następnego do najbardziej znaczącego wymiaru.

*_Dim2*<br/>
Długość najmniej znaczącego wymiaru.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Konstruktor tiled_extent](#ctor)|Inicjuje nowe wystąpienie klasy `tiled_extent`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[get_tile_extent](#get_tile_extent)|Zwraca obiekt `extent`, który przechwytuje wartości argumentów szablonu `tiled_extent` `_Dim0`, `_Dim1`i `_Dim2`.|
|[konsolę](#pad)|Zwraca nowy obiekt `tiled_extent` z dopasowanymi zakresami, tak aby był równy podzielenia przez wymiary kafelków.|
|[obciąć](#truncate)|Zwraca nowy obiekt `tiled_extent` z przypiętymi zakresami ustawionymi w dół tak, aby były one równo widoczne przez wymiary kafelków.|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[operator =](#operator_eq)|Kopiuje zawartość określonego obiektu `tiled_index` do tego.|

### <a name="public-constants"></a>Stałe publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[tile_dim0 stała](#tile_dim0)|Przechowuje długość najbardziej znaczącego wymiaru.|
|[tile_dim1 stała](#tile_dim1)|Przechowuje Długość następnego do najbardziej znaczącego wymiaru.|
|[tile_dim2 stała](#tile_dim2)|Przechowuje długość najmniej znaczącego wymiaru.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Name (Nazwa)|Opis|
|----------|-----------------|
|[tile_extent](#tile_extent)|Pobiera obiekt `extent`, który przechwytuje wartości argumentów szablonu `tiled_extent` `_Dim0`, `_Dim1`i `_Dim2`.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`extent`

`tiled_extent`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp. h

**Przestrzeń nazw:** Współbieżności

## <a name="ctor"></a> Konstruktor tiled_extent

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
Obiekt `extent` lub `tiled_extent` do skopiowania.

## <a name="get_tile_extent"></a> get_tile_extent

Zwraca obiekt `extent`, który przechwytuje wartości argumentów szablonu `tiled_extent` `_Dim0`, `_Dim1`i `_Dim2`.

### <a name="syntax"></a>Składnia

```cpp
Concurrency::extent<rank> get_tile_extent() const restrict(amp,cpu);
```

### <a name="return-value"></a>Wartość zwrócona

Obiekt `extent`, który przechwytuje wymiary tego wystąpienia `tiled_extent`.

## <a name="pad"></a> konsola

Zwraca nowy obiekt `tiled_extent` z dopasowanymi zakresami, tak aby był równy podzielenia przez wymiary kafelków.

### <a name="syntax"></a>Składnia

```cpp
tiled_extent pad() const;
```

### <a name="return-value"></a>Wartość zwrócona

Nowy obiekt `tiled_extent` według wartości.
## <a name="truncate"></a> Obetnij

Zwraca nowy obiekt `tiled_extent` z przypiętymi zakresami ustawionymi w dół tak, aby były one równo widoczne przez wymiary kafelków.

### <a name="syntax"></a>Składnia

```cpp
tiled_extent truncate() const;
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca nowy obiekt `tiled_extent` z przypiętymi zakresami ustawionymi w dół tak, aby były one równo widoczne przez wymiary kafelków.

## <a name="operator_eq"></a> operator =

Kopiuje zawartość określonego obiektu `tiled_index` do tego.

### <a name="syntax"></a>Składnia

```cpp
tiled_extent&  operator= (
    const tiled_extent& _Other ) restrict (amp, cpu);
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
Obiekt `tiled_index`, z którego ma być kopiowany.

### <a name="return-value"></a>Wartość zwrócona

Odwołanie do tego wystąpienia `tiled_index`.

## <a name="tile_dim0"></a> tile_dim0

Przechowuje długość najbardziej znaczącego wymiaru.

### <a name="syntax"></a>Składnia

```cpp
static const int tile_dim0 = _Dim0;
```

## <a name="tile_dim1"></a> tile_dim1

Przechowuje Długość następnego do najbardziej znaczącego wymiaru.

### <a name="syntax"></a>Składnia

```cpp
static const int tile_dim1 = _Dim1;
```

## <a name="tile_dim2"></a> tile_dim2

Przechowuje długość najmniej znaczącego wymiaru.

### <a name="syntax"></a>Składnia

```cpp
static const int tile_dim2 = _Dim2;
```

## <a name="tile_extent"></a> tile_extent
  Pobiera obiekt `extent`, który przechwytuje wartości argumentów szablonu `tiled_extent` `_Dim0`, `_Dim1`i `_Dim2`.

### <a name="syntax"></a>Składnia

```cpp
__declspec(property(get= get_tile_extent)) Concurrency::extent<rank> tile_extent;
```

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
