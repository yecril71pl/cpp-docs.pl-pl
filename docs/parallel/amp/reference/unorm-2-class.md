---
title: unorm_2 — Klasa
ms.date: 11/04/2016
f1_keywords:
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator+=
- amp_short_vectors/Concurrency::graphics::unnorm_2::y
- amp_short_vectors/Concurrency::graphics::unnorm_2::set_y
- amp_short_vectors/Concurrency::graphics::unnorm_2::x
- amp_short_vectors/Concurrency::graphics::unnorm_2::get_yx
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator--
- amp_short_vectors/Concurrency::graphics::unnorm_2::set_xy
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator*=
- amp_short_vectors/Concurrency::graphics::unnorm_2::xy
- amp_short_vectors/Concurrency::graphics::unnorm_2::get_y
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator=
- amp_short_vectors/Concurrency::graphics::unnorm_2::set_x
- amp_short_vectors/Concurrency::graphics::unnorm_2::rg
- amp_short_vectors/Concurrency::graphics::unorm_2
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator-=
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator/=
- amp_short_vectors/Concurrency::graphics::unnorm_2::get_xy
- amp_short_vectors/Concurrency::graphics::unnorm_2::set_yx
- amp_short_vectors/Concurrency::graphics::unnorm_2::yx
- amp_short_vectors/Concurrency::graphics::unnorm_2::gr
- amp_short_vectors/Concurrency::graphics::unnorm_2::r
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator-
- amp_short_vectors/Concurrency::graphics::unnorm_2::get_x
- amp_short_vectors/Concurrency::graphics::unnorm_2::g
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator++
ms.assetid: 62e88ea7-e29f-4f62-95ce-61a1f39f5e34
ms.openlocfilehash: 325a1532a079c8eff9c8dcdc5410dcbfe58fb914
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126217"
---
# <a name="unorm_2-class"></a>unorm_2 — Klasa

Reprezentuje krótki wektor dwóch nieoznaczonych liczb zwykłych.

## <a name="syntax"></a>Składnia

```cpp
class unorm_2;
```

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Publiczne definicje typów

|Name (Nazwa)|Opis|
|----------|-----------------|
|`value_type`||

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Konstruktor unorm_2](#ctor)|Przeciążone. Konstruktor domyślny, inicjuje wszystkie elementy z wartością 0.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|unorm_2::get_x||
|unorm_2::get_xy||
|unorm_2:: get_y||
|unorm_2::get_yx||
|unorm_2::ref_g||
|unorm_2:: ref_r||
|unorm_2::ref_x||
|unorm_2:: ref_y||
|unorm_2::set_x||
|unorm_2:: set_xy||
|unorm_2:: set_y||
|unorm_2:: set_yx||

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|unorm_2:: operator--||
|unorm_2:: operator * =||
|unorm_2:: operator/=||
|unorm_2:: operator + +||
|unorm_2:: operator + =||
|unorm_2:: operator =||
|unorm_2:: operator-=||

### <a name="public-constants"></a>Stałe publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|unorm_2::size — Stała||

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Name (Nazwa)|Opis|
|----------|-----------------|
|unorm_2:: g||
|unorm_2:: GR||
|unorm_2:: r||
|unorm_2::rg||
|unorm_2:: x||
|unorm_2:: XY||
|unorm_2:: y||
|unorm_2:: yx||

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`unorm_2`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp_short_vectors. h

**Przestrzeń nazw:** Concurrency:: Graphics

## <a name="ctor"></a>unorm_2

Konstruktor domyślny, inicjuje wszystkie elementy z wartością 0.

```cpp
unorm_2() restrict(amp,
    cpu);

unorm_2(
    unorm _V0,
    unorm _V1) restrict(amp,
    cpu);

unorm_2(
    float _V0,
    float _V1) restrict(amp,
    cpu);

unorm_2(
    unorm _V) restrict(amp,
    cpu);

explicit unorm_2(
    float _V) restrict(amp,
    cpu);

unorm_2(
    const unorm_2& _Other) restrict(amp,
    cpu);

explicit inline unorm_2(
    const uint_2& _Other) restrict(amp,
    cpu);

explicit inline unorm_2(
    const int_2& _Other) restrict(amp,
    cpu);

explicit inline unorm_2(
    const float_2& _Other) restrict(amp,
    cpu);

explicit inline unorm_2(
    const norm_2& _Other) restrict(amp,
    cpu);

explicit inline unorm_2(
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

## <a name="unorm_2__size"></a>zmienia

```cpp
static const int size = 2;
```

## <a name="see-also"></a>Zobacz też

[Concurrency::graphics, przestrzeń nazw](concurrency-graphics-namespace.md)
