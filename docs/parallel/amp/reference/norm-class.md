---
title: norm — Klasa
ms.date: 11/04/2016
f1_keywords:
- norm
- AMP_SHORT_VECTORS/norm
- AMP_SHORT_VECTORS/Concurrency::graphics::norm Constructor
ms.assetid: 73002f3d-c25e-4119-bcd3-4c46c9b6abf1
ms.openlocfilehash: 56f879ef2fc0d3010ab4f64fedaf2570dac565d1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57272428"
---
# <a name="norm-class"></a>norm — Klasa

Reprezentuje liczby normy. Każdy element jest zmiennoprzecinkowy numer punktu z zakresu [-1.0f, 1.0f].

## <a name="syntax"></a>Składnia

```
class norm;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[norm konstruktora](#ctor)|Przeciążone. Domyślny konstruktor. Zainicjuj 0,0.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|norm::operator-||
|norm::operator--||
|norm::operator float|Operator konwersji. Konwertowanie liczby norm zmiennoprzecinkowej wartości.|
|norm::operator*=||
|norm::operator/=||
|norm::operator ++||
|norm::operator+=||
|norm::operator=||
|norm::operator-=||

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`norm`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp_short_vectors.h

**Namespace:** CONCURRENCY::Graphics

##  <a name="ctor"></a> norm

Domyślny konstruktor. Zainicjuj 0,0.

```
norm(
    void) restrict(amp,
    cpu);

explicit norm(
    float _V) restrict(amp,
    cpu);

explicit norm(
    unsigned int _V) restrict(amp,
    cpu);

explicit norm(
    int _V) restrict(amp,
    cpu);

explicit norm(
    double _V) restrict(amp,
    cpu);

norm(
    const norm& _Other) restrict(amp,
    cpu);

norm(
    const unorm& _Other) restrict(amp,
    cpu);
```

### <a name="parameters"></a>Parametry

*_V*<br/>
Wartość wykorzystana do zainicjowania.

*_Inne*<br/>
Obiekt używany do inicjowania.

## <a name="see-also"></a>Zobacz także

[Concurrency::graphics, przestrzeń nazw](concurrency-graphics-namespace.md)
