---
title: double_2 — Klasa
ms.date: 11/04/2016
f1_keywords:
- amp_short_vectors/Concurrency::graphics::double_2::set_x
- amp_short_vectors/Concurrency::graphics::double_2::operator+=
- amp_short_vectors/Concurrency::graphics::double_2::operator=
- amp_short_vectors/Concurrency::graphics::double_2::operator/=
- amp_short_vectors/Concurrency::graphics::double_2::operator*=
- amp_short_vectors/Concurrency::graphics::double_2::yx
- amp_short_vectors/Concurrency::graphics::double_2::y
- amp_short_vectors/Concurrency::graphics::double_2::xy
- amp_short_vectors/Concurrency::graphics::double_2::set_xy
- amp_short_vectors/Concurrency::graphics::double_2::get_yx
- amp_short_vectors/Concurrency::graphics::double_2::set_yx
- amp_short_vectors/Concurrency::graphics::double_2::get_xy
- amp_short_vectors/Concurrency::graphics::double_2::operator++
- amp_short_vectors/Concurrency::graphics::double_2::get_x
- amp_short_vectors/Concurrency::graphics::double_2::operator-=
- amp_short_vectors/Concurrency::graphics::double_2::rg
- amp_short_vectors/Concurrency::graphics::double_2::gr
- amp_short_vectors/Concurrency::graphics::double_2::get_y
- amp_short_vectors/Concurrency::graphics::double_2::x
- amp_short_vectors/Concurrency::graphics::double_2::r
- amp_short_vectors/Concurrency::graphics::double_2::operator--
- amp_short_vectors/Concurrency::graphics::double_2
- amp_short_vectors/Concurrency::graphics::double_2::operator-
- amp_short_vectors/Concurrency::graphics::double_2::g
- amp_short_vectors/Concurrency::graphics::double_2::set_y
ms.assetid: c19c2d21-3cbf-4ce5-b460-3b8253688f82
ms.openlocfilehash: 9482c2839c4963d533eb643fa0ef86a5c66636a4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289653"
---
# <a name="double2-class"></a>double_2 — Klasa

Reprezentuje krótki wektor 2 podwójnej precyzji.

## <a name="syntax"></a>Składnia

```
class double_2;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`value_type`||

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[double_2 — Konstruktor](#ctor)|Przeciążone. Domyślny konstruktor, inicjuje wszystkie elementy wartością 0.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|double_2::get_x||
|double_2::get_xy||
|double_2::get_y||
|double_2::get_yx||
|double_2::ref_g||
|double_2::ref_r||
|double_2::ref_x||
|double_2::ref_y||
|double_2::set_x||
|double_2::set_xy||
|double_2::set_y||
|double_2::set_yx||

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|double_2::operator-||
|double_2::operator--||
|double_2::operator * =||
|double_2::operator / =||
|double_2::operator ++||
|double_2::operator +=||
|double_2::operator =||
|double_2::operator-=||

### <a name="public-constants"></a>Publiczne stałe

|Nazwa|Opis|
|----------|-----------------|
|double_2::size — Stała||

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|double_2::g||
|double_2::gr||
|double_2::r||
|double_2::rg||
|double_2::x||
|double_2::xy||
|double_2::y||
|double_2::yx||

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`double_2`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp_short_vectors.h

**Namespace:** CONCURRENCY::Graphics

##  <a name="ctor"></a> double_2

Domyślny konstruktor, inicjuje wszystkie elementy wartością 0.

```
double_2() restrict(amp,
    cpu);

double_2(
    double _V0,
    double _V1) restrict(amp,
    cpu);

double_2(
    double _V) restrict(amp,
    cpu);

double_2(
    const double_2& _Other) restrict(amp,
    cpu);

explicit inline double_2(
    const uint_2& _Other) restrict(amp,
    cpu);

explicit inline double_2(
    const int_2& _Other) restrict(amp,
    cpu);

explicit inline double_2(
    const float_2& _Other) restrict(amp,
    cpu);

explicit inline double_2(
    const unorm_2& _Other) restrict(amp,
    cpu);

explicit inline double_2(
    const norm_2& _Other) restrict(amp,
    cpu);
```

### <a name="parameters"></a>Parametry

*_V0*<br/>
Wartość do zainicjowania elementu 0.

*_V1*<br/>
Wartość do zainicjowania elementu 1.

*_V*<br/>
Wartość inicjalizacji.

*_Inne*<br/>
Obiekt używany do inicjowania.

##  <a name="double_2__size"></a> Rozmiar

```
static const int size = 2;
```

## <a name="see-also"></a>Zobacz także

[Concurrency::graphics, przestrzeń nazw](concurrency-graphics-namespace.md)
