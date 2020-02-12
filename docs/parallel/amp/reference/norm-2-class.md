---
title: norm_2 — Klasa
ms.date: 11/04/2016
f1_keywords:
- amp_short_vectors/Concurrency::graphics::norm_2::set_x
- amp_short_vectors/Concurrency::graphics::norm_2::set_xy
- amp_short_vectors/Concurrency::graphics::norm_2::g
- amp_short_vectors/Concurrency::graphics::norm_2::get_yx
- amp_short_vectors/Concurrency::graphics::norm_2::set_yx
- amp_short_vectors/Concurrency::graphics::norm_2::operator-=
- amp_short_vectors/Concurrency::graphics::norm_2::operator/=
- amp_short_vectors/Concurrency::graphics::norm_2::operator*=
- amp_short_vectors/Concurrency::graphics::norm_2::yx
- amp_short_vectors/Concurrency::graphics::norm_2::y
- amp_short_vectors/Concurrency::graphics::norm_2::xy
- amp_short_vectors/Concurrency::graphics::norm_2::operator++
- amp_short_vectors/Concurrency::graphics::norm_2::operator-
- amp_short_vectors/Concurrency::graphics::norm_2::rg
- amp_short_vectors/Concurrency::graphics::norm_2::operator=
- amp_short_vectors/Concurrency::graphics::norm_2::get_y
- amp_short_vectors/Concurrency::graphics::norm_2::r
- amp_short_vectors/Concurrency::graphics::norm_2::get_x
- amp_short_vectors/Concurrency::graphics::norm_2::get_xy
- amp_short_vectors/Concurrency::graphics::norm_2::gr
- amp_short_vectors/Concurrency::graphics::norm_2::set_y
- amp_short_vectors/Concurrency::graphics::norm_2::x
- amp_short_vectors/Concurrency::graphics::norm_2::operator+=
- amp_short_vectors/Concurrency::graphics::norm_2
- amp_short_vectors/Concurrency::graphics::norm_2::operator--
ms.assetid: 80703f9b-61f4-414a-93fd-bc774f7d3393
ms.openlocfilehash: 09bd33b5a8d9148c7959f69fcab4a260fe05c332
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126503"
---
# <a name="norm_2-class"></a>norm_2 — Klasa

Reprezentuje krótki wektor dwóch liczb normalnych.

## <a name="syntax"></a>Składnia

```cpp
class norm_2;
```

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Publiczne definicje typów

|Name (Nazwa)|Opis|
|----------|-----------------|
|`value_type`||

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Konstruktor norm_2](#ctor)|Przeciążone. Konstruktor domyślny, inicjuje wszystkie elementy z wartością 0.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|norm_2::get_x||
|norm_2::get_xy||
|norm_2:: get_y||
|norm_2::get_yx||
|norm_2::ref_g||
|norm_2:: ref_r||
|norm_2::ref_x||
|norm_2:: ref_y||
|norm_2::set_x||
|norm_2::set_xy||
|norm_2:: set_y||
|norm_2:: set_yx||

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|norm_2:: operator-||
|norm_2:: operator--||
|norm_2:: operator * =||
|norm_2:: operator/=||
|norm_2:: operator + +||
|norm_2:: operator + =||
|norm_2:: operator =||
|norm_2:: operator-=||

### <a name="public-constants"></a>Stałe publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Stała rozmiaru](#norm_2__size)||

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Name (Nazwa)|Opis|
|----------|-----------------|
|norm_2:: g||
|norm_2:: GR||
|norm_2:: r||
|norm_2::rg||
|norm_2:: x||
|norm_2:: XY||
|norm_2:: y||
|norm_2:: yx||

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`norm_2`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp_short_vectors. h

**Przestrzeń nazw:** Concurrency:: Graphics

## <a name="ctor"></a>norm_2

Konstruktor domyślny, inicjuje wszystkie elementy z wartością 0.

```cpp
norm_2() restrict(amp,
    cpu);

norm_2(
    norm _V0,
    norm _V1) restrict(amp,
    cpu);

norm_2(
    float _V0,
    float _V1) restrict(amp,
    cpu);

norm_2(
    unorm _V0,
    unorm _V1) restrict(amp,
    cpu);

norm_2(
    norm _V) restrict(amp,
    cpu);

explicit norm_2(
    float _V) restrict(amp,
    cpu);

norm_2(
    const norm_2& _Other) restrict(amp,
    cpu);

explicit inline norm_2(
    const uint_2& _Other) restrict(amp,
    cpu);

explicit inline norm_2(
    const int_2& _Other) restrict(amp,
    cpu);

explicit inline norm_2(
    const float_2& _Other) restrict(amp,
    cpu);

explicit inline norm_2(
    const unorm_2& _Other) restrict(amp,
    cpu);

explicit inline norm_2(
    const double_2& _Other) restrict(amp,
    cpu);
```

### <a name="parameters"></a>Parametry

*_V0*<br/>
Wartość, aby zainicjować element 0.

*_V1*<br/>
Wartość do zainicjowania elementu 1.

*_V*<br/>
Wartość dla inicjalizacji.

*_Other*<br/>
Obiekt używany do inicjowania.

## <a name="norm_2__size"></a>zmienia

```cpp
static const int size = 2;
```

## <a name="see-also"></a>Zobacz też

[Concurrency::graphics, przestrzeń nazw](concurrency-graphics-namespace.md)
