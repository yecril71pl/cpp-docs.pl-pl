---
title: writeonly_texture_view, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- writeonly_texture_view
- AMP_GRAPHICS/writeonly_texture_view
- AMP_GRAPHICS/Concurrency::graphics::writeonly_texture_view
- AMP_GRAPHICS/Concurrency::graphics::writeonly_texture_view::set
- AMP_GRAPHICS/Concurrency::graphics::rank Constant
dev_langs:
- C++
ms.assetid: 8d117ad3-0a1c-41ae-b29c-7c95fdd4d04d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd92e403d9c83bf50bea2703cef6a4255c6245e3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46414686"
---
# <a name="writeonlytextureview-class"></a>writeonly_texture_view — Klasa

Zapewnia writeonly dostęp do tekstury.

## <a name="syntax"></a>Składnia

```
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

#### <a name="parameters"></a>Parametry

*value_type*<br/>
Typ elementów tekstury.

*_Rank*<br/>
Ranga tekstury.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`scalar_type`||
|`value_type`|Typ elementów tekstury.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[writeonly_texture_view konstruktora](#ctor)|Inicjuje nowe wystąpienie klasy `writeonly_texture_view` klasy.|
|[~ writeonly_texture_view — destruktor](#ctor)|Niszczy `writeonly_texture_view` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[set](#set)|Ustawia wartość elementu wskazywanego przez określony indeks.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[operator=](#operator_eq)|Kopiuje określony `writeonly_texture_view` obiektu do wskazanego.|

### <a name="public-constants"></a>Publiczne stałe

|Nazwa|Opis|
|----------|-----------------|
|[Rank — stała](#rank)|Zwraca rangę obiektu `writeonly_texture_view` obiektu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`_Texture_base`

`writeonly_texture_view`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp_graphics.h

**Namespace:** Concurrency::graphics

##  <a name="dtor"></a> ~ writeonly_texture_view

Niszczy `writeonly_texture_view` obiektu.

```
~writeonly_texture_view() restrict(amp,cpu);
```

##  <a name="operator_eq"></a> operator =

Kopiuje określony `writeonly_texture_view` obiektu do wskazanego.

```
writeonly_texture_view<value_type, _Rank>& operator= (
    const writeonly_texture_view<value_type, _Rank>& _Other) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Inne*<br/>
`writeonly_texture_view` obiekt do skopiowania.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `writeonly_texture_view` obiektu.

##  <a name="rank"></a> Ranga

Zwraca rangę obiektu `writeonly_texture_view` obiektu.

```
static const int rank = _Rank;
```

##  <a name="set"></a> Zestaw

Ustawia wartość elementu wskazywanego przez określony indeks.

```
void set(
    const index<_Rank>& _Index,
    const value_type& value) const restrict(amp);
```

### <a name="parameters"></a>Parametry

*Parametr _Index*<br/>
Indeks elementu.

*value*<br/>
Nowa wartość elementu.

##  <a name="ctor"></a> writeonly_texture_view

Inicjuje nowe wystąpienie klasy `writeonly_texture_view` klasy.

```
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
Typ elementów tekstury.

*_Src*<br/>
Teksturę, która służy do tworzenia `writeonly_texture_view`.

## <a name="see-also"></a>Zobacz też

[Concurrency::graphics, przestrzeń nazw](concurrency-graphics-namespace.md)
