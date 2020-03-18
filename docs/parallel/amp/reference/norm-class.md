---
title: norm — Klasa
ms.date: 11/04/2016
f1_keywords:
- AMP_SHORT_VECTORS/norm
- AMP_SHORT_VECTORS/Concurrency::graphics::norm Constructor
ms.assetid: 73002f3d-c25e-4119-bcd3-4c46c9b6abf1
ms.openlocfilehash: b5740f33dea6aad79770f77f179803023432248a
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447523"
---
# <a name="norm-class"></a>norm — Klasa

Reprezentuje numer norm. Każdy element jest liczbą zmiennoprzecinkową z zakresu [-1.0 f, 1.0 f].

## <a name="syntax"></a>Składnia

```cpp
class norm;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Konstruktor norm](#ctor)|Przeciążone. Konstruktor domyślny. Zainicjuj do 0.0 f.|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|Norma:: operator-||
|Norma:: operator--||
|Norma:: operator float|Operator konwersji. Przekonwertuj numer normy na wartość zmiennoprzecinkową.|
|Norma:: operator * =||
|Norma:: operator/=||
|Norma:: operator + +||
|Norma:: operator + =||
|Norma:: operator =||
|Norma:: operator-=||

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`norm`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp_short_vectors. h

**Przestrzeń nazw:** Concurrency:: Graphics

## <a name="ctor"></a>oblicza

Konstruktor domyślny. Zainicjuj do 0.0 f.

```cpp
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
Wartość używana do inicjowania.

*_Other*<br/>
Obiekt używany do inicjowania.

## <a name="see-also"></a>Zobacz też

[Concurrency::graphics, przestrzeń nazw](concurrency-graphics-namespace.md)
