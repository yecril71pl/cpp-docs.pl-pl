---
title: writeonly_texture_view — Klasa
ms.date: 11/04/2016
f1_keywords:
- writeonly_texture_view
- AMP_GRAPHICS/writeonly_texture_view
- AMP_GRAPHICS/Concurrency::graphics::writeonly_texture_view
- AMP_GRAPHICS/Concurrency::graphics::writeonly_texture_view::set
- AMP_GRAPHICS/Concurrency::graphics::rank Constant
ms.assetid: 8d117ad3-0a1c-41ae-b29c-7c95fdd4d04d
ms.openlocfilehash: 8978a548ed246c59d7e7f007f1180685c7343a14
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126243"
---
# <a name="writeonly_texture_view-class"></a>writeonly_texture_view — Klasa

Zapewnia dostęp do tekstury.

## <a name="syntax"></a>Składnia

```cpp
template <
    typename value_type,
    int _Rank
>
class writeonly_texture_view;

template <
    typename value_type,
    int _Rank
>
class writeonly_texture_view<value_type, _Rank> : public details::_Texture_base<value_type, _Rank>;
```

### <a name="parameters"></a>Parametry

*value_type*<br/>
Typ elementów w tekstury.

*_Rank*<br/>
Ranga tekstury.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Publiczne definicje typów

|Name (Nazwa)|Opis|
|----------|-----------------|
|`scalar_type`||
|`value_type`|Typ elementów w tekstury.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Konstruktor writeonly_texture_view](#ctor)|Inicjuje nowe wystąpienie klasy `writeonly_texture_view`.|
|[~ writeonly_texture_view destruktor](#ctor)|Niszczy obiekt `writeonly_texture_view`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[set](#set)|Ustawia wartość elementu w określonym indeksie.|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[operator =](#operator_eq)|Kopiuje określony obiekt `writeonly_texture_view` do tego.|

### <a name="public-constants"></a>Stałe publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Stała rangi](#rank)|Pobiera rangę obiektu `writeonly_texture_view`.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`_Texture_base`

`writeonly_texture_view`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp_graphics. h

**Przestrzeń nazw:** Concurrency:: Graphics

## <a name="dtor"></a>~ writeonly_texture_view

Niszczy obiekt `writeonly_texture_view`.

```cpp
~writeonly_texture_view() restrict(amp,cpu);
```

## <a name="operator_eq"></a>operator =

Kopiuje określony obiekt `writeonly_texture_view` do tego.

```cpp
writeonly_texture_view<value_type, _Rank>& operator= (
    const writeonly_texture_view<value_type, _Rank>& _Other) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
`writeonly_texture_view` obiekt do skopiowania.

### <a name="return-value"></a>Wartość zwrócona

Odwołanie do tego obiektu `writeonly_texture_view`.

## <a name="rank"></a>stopni

Pobiera rangę obiektu `writeonly_texture_view`.

```cpp
static const int rank = _Rank;
```

## <a name="set"></a>zbiór

Ustawia wartość elementu w określonym indeksie.

```cpp
void set(
    const index<_Rank>& _Index,
    const value_type& value) const restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Indeks elementu.

*value*<br/>
Nowa wartość elementu.

## <a name="ctor"></a>writeonly_texture_view

Inicjuje nowe wystąpienie klasy `writeonly_texture_view`.

```cpp
writeonly_texture_view(
    texture<value_type,
    _Rank>& _Src) restrict(amp);

writeonly_texture_view(
    const writeonly_texture_view<value_type,
    _Rank>& _Src) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rank*<br/>
Ranga tekstury.

*value_type*<br/>
Typ elementów w tekstury.

*_Src*<br/>
Tekstura, która jest używana do tworzenia `writeonly_texture_view`.

## <a name="see-also"></a>Zobacz też

[Concurrency::graphics, przestrzeń nazw](concurrency-graphics-namespace.md)
