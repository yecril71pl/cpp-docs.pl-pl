---
title: 'CONCURRENCY::Graphics:: Direct3D, funkcje przestrzeni nazw | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- amp_graphics/Concurrency::graphics::direct3d::get_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_texture
dev_langs:
- C++
ms.assetid: 11ee1d42-333e-4ae9-95ac-4cf68c06d13d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 45b9b2b9f6d3ff6b08d7aac2a8ecddafe017fc13
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375696"
---
# <a name="concurrencygraphicsdirect3d-namespace-functions"></a>CONCURRENCY::Graphics:: Direct3D, funkcje przestrzeni nazw

||||
|-|-|-|
|[get_sampler](#get_sampler)|[get_texture](#get_texture)|[make_sampler](#make_sampler)|
|[make_texture](#make_texture)|[msad4](#msad4)|

##  <a name="get_sampler"></a>  get_sampler —

Pobierz interfejsu stanu D3D próbnika w akceleratorze danego widoku, który reprezentuje określony obiekt próbnika.

```
IUnknown* get_sampler(
    const Concurrency::accelerator_view& _Av,
    const sampler& _Sampler) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Av*<br/>
Widok akceleratora D3D, na którym ma zostać utworzony stanowi próbnika D3D.

*_Sampler*<br/>
Obiekt próbnik, dla którego utworzono podstawowy interfejs stanu próbnika D3D.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik interfejsu IUnknown odpowiadający stanowi próbnika D3D, który reprezentuje dany próbnik.

##  <a name="get_texture"></a>  get_texture

Pobiera interfejs tekstur Direct3D podstaw określonego [tekstury](texture-class.md) obiektu.

```
template<
    typename value_type,
    int _Rank
>
_Ret_ IUnknown *get_texture(
    const texture<value_type, _Rank>& _Texture) restrict(cpu);

template<
    typename value_type,
    int _Rank
>
_Ret_ IUnknown *get_texture(
    const writeonly_texture_view<value_type, _Rank>& _Texture) restrict(cpu);

template<
    typename value_type,
    int _Rank
>
_Ret_ IUnknown *get_texture(
    const texture_view<value_type, _Rank>& _Texture) restrict(cpu);

```

### <a name="parameters"></a>Parametry

*value_type*<br/>
Typ elementu tekstury.

*_Rank*<br/>
Ranga tekstury.

*_Texture*<br/>
Tekstury lub widoku tekstury skojarzony z accelerator_view, dla którego zwracany jest interfejs tekstury Direct3D.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik interfejsu IUnknown odpowiadający teksturze Direct3D podstawowej tekstury.

##  <a name="make_sampler"></a>  make_sampler —

Utwórz przykład ze wskaźnika interfejsu stanu D3D próbnika.

```
sampler make_sampler(_In_ IUnknown* _D3D_sampler) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_D3D_sampler*<br/>
Nieznany wskaźnik interfejsu przykładu stanu D3D do tworzenia przykładu.

### <a name="return-value"></a>Wartość zwracana

Próbnik reprezentuje zapewniony stan próbnika D3D.

##  <a name="make_texture"></a>  make_texture

Tworzy [tekstury](texture-class.md) obiektu przy użyciu określonych parametrów.

```
template<
    typename value_type,
    int _Rank
>
texture<value_type, _Rank> make_texture(
    const Concurrency::accelerator_view& _Av,
    _In_ IUnknown* _D3D_texture,
    DXGI_FORMAT _View_format = DXGI_FORMAT_UNKNOWN) restrict(cpu);
```

### <a name="parameters"></a>Parametry

*value_type*<br/>
Typ elementów tekstury.

*_Rank*<br/>
Ranga tekstury.

*_Av*<br/>
Widok akceleratora D3D, na którym ma zostać utworzony tekstury.

*_D3D_texture*<br/>
Wskaźnik interfejsu IUnknown tekstury D3D, aby utworzyć tekstury z.

*_View_format*<br/>
Format DXGI do wykorzystania przez widoki utworzone z tej tekstury. Przekaż DXGI_FORMAT_UNKNOWN (ustawienie domyślne), aby utworzyć format z formatu podstawowego obiektów _D3D_texture i value_type tego szablonu. Podany format musi być zgodny z podstawowym formatem _D3D_texture.

### <a name="return-value"></a>Wartość zwracana

Tekstura używa dostarczonej tekstury D3D.

##  <a name="msad4"></a>  msad4 —

Porównuje 4-bajtową wartość odniesienia i 8-bajtową wartość źródłową i gromadzi wektor 4 sum. Każda suma odpowiada zamaskowanej sumie bezwzględnych różnic różnych dopasowań bajtów między wartością odniesienia i wartością źródłową.

```
inline uint4 msad4(
    uint _Reference,
    uint2 _Source,
    uint4 _Accum) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Referencyjnych*<br/>
Tablica odwołań o rozmiarze 4 bajtów w jednej wartości uint

*_Source*<br/>
Tablica źródłowa o rozmiarze 8 bajtów w wektorze dwóch wartości uint.

*_Accum*<br/>
Wektor 4 wartości do dodania do zamaskowanej sumy bezwzględnych różnic różnych dopasowań bajtów między wartością odniesienia i wartością źródłową.

### <a name="return-value"></a>Wartość zwracana

Zwraca wektor 4 sum. Każda suma odpowiada zamaskowanej sumie bezwzględnych różnic różnych dopasowań bajtów między wartością odniesienia i wartością źródłową.

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp_graphics.h

**Namespace:** CONCURRENCY::Graphics:: Direct3D

## <a name="see-also"></a>Zobacz też

[Concurrency::graphics::direct3d, przestrzeń nazw](concurrency-graphics-direct3d-namespace.md)
