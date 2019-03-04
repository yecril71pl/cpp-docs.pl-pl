---
title: unorm — Klasa
ms.date: 11/04/2016
f1_keywords:
- unorm
- AMP_SHORT_VECTORS/unorm
- AMP_SHORT_VECTORS/Concurrency::graphics::unorm Constructor
ms.assetid: bc30bd20-6452-4d5f-9158-3b11c4c16ed2
ms.openlocfilehash: 059cd3a388d67e540a91146f2a287c375fb02bd1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57300807"
---
# <a name="unorm-class"></a>unorm — Klasa

Reprezentuje liczby unorm. Każdy element jest zmiennoprzecinkowy numer punktu z zakresu [0.0f, 1,0 f].

## <a name="syntax"></a>Składnia

```
class unorm;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[unorm konstruktora](#ctor)|Przeciążone. Domyślny konstruktor. Zainicjuj 0,0.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|unorm::operator--||
|unorm::operator float|Operator konwersji. Konwertowanie liczby unorm zmiennoprzecinkowej wartości.|
|unorm::operator*=||
|unorm::operator / =||
|unorm::operator ++||
|unorm::operator+=||
|unorm::operator =||
|unorm::operator-=||

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`unorm`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp_short_vectors.h

**Namespace:** CONCURRENCY::Graphics

##  <a name="ctor"></a> unorm

Domyślny konstruktor. Zainicjuj 0,0.

```
unorm(
    void) restrict(amp,
    cpu);

explicit unorm(
    float _V) restrict(amp,
    cpu);

explicit unorm(
    unsigned int _V) restrict(amp,
    cpu);

explicit unorm(
    int _V) restrict(amp,
    cpu);

explicit unorm(
    double _V) restrict(amp,
    cpu);

unorm(
    const unorm& _Other) restrict(amp,
    cpu);

inline explicit unorm(
    const norm& _Other) restrict(amp,
    cpu);
```

### <a name="parameters"></a>Parametry

*_V*<br/>
Wartość wykorzystana do zainicjowania.

*_Inne*<br/>
Norm obiekt używany do inicjowania.

## <a name="see-also"></a>Zobacz także

[Concurrency::graphics, przestrzeń nazw](concurrency-graphics-namespace.md)
