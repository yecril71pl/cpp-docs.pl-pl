---
title: Concurrency::graphics::direct3d, funkcje przestrzeni nazw
ms.date: 11/04/2016
f1_keywords:
- amp_graphics/Concurrency::graphics::direct3d::get_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_texture
ms.assetid: 11ee1d42-333e-4ae9-95ac-4cf68c06d13d
ms.openlocfilehash: 330c1aa94b1d122901fc23576686032400249d31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376391"
---
# <a name="concurrencygraphicsdirect3d-namespace-functions"></a>Concurrency::graphics::direct3d, funkcje przestrzeni nazw

||||
|-|-|-|
|[get_sampler](#get_sampler)|[get_texture](#get_texture)|[make_sampler](#make_sampler)|
|[make_texture](#make_texture)|[msad4](#msad4)|

## <a name="get_sampler"></a><a name="get_sampler"></a>get_sampler

Pobierz interfejs stanu próbnika D3D w danym widoku akceleratora, który reprezentuje określony obiekt próbnika.

```cpp
IUnknown* get_sampler(
    const Concurrency::accelerator_view& _Av,
    const sampler& _Sampler) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Av*<br/>
Widok akceleratora D3D, na którym ma zostać utworzony stan próbnika D3D.

*_Sampler*<br/>
Obiekt próbnika, dla którego tworzony jest podstawowy interfejs stanu próbnika D3D.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik interfejsu IUnknown odpowiadający stanowi próbnika D3D reprezentującego danego próbnika.

## <a name="get_texture"></a><a name="get_texture"></a>get_texture

Pobiera interfejs tekstury Direct3D leżący u podstaw określonego obiektu [tekstury.](texture-class.md)

```cpp
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
Widok tekstury lub tekstury skojarzony z accelerator_view dla którego zwracany jest podstawowy interfejs tekstury Direct3D.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik interfejsu IUnknown odpowiadający teksturze Direct3D leżącej u podstaw tekstury.

## <a name="make_sampler"></a><a name="make_sampler"></a>make_sampler

Utwórz próbnik ze wskaźnika stanu próbnika D3D.

```cpp
sampler make_sampler(_In_ IUnknown* _D3D_sampler) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_D3D_sampler*<br/>
IUnknown wskaźnik interfejsu stanu próbnika D3D, aby utworzyć próbnik z.

### <a name="return-value"></a>Wartość zwracana

Próbnik reprezentuje podany stan próbnika D3D.

## <a name="make_texture"></a><a name="make_texture"></a>make_texture

Tworzy obiekt [tekstury](texture-class.md) przy użyciu określonych parametrów.

```cpp
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
Typ elementów w teksturze.

*_Rank*<br/>
Ranga tekstury.

*_Av*<br/>
Widok akceleratora D3D, na którym ma zostać utworzona tekstura.

*_D3D_texture*<br/>
IUnknown wskaźnik interfejsu tekstury D3D do tworzenia tekstury z.

*_View_format*<br/>
Format DXGI używany do widoków utworzonych z tej tekstury. Przekaż DXGI_FORMAT_UNKNOWN (domyślnie), aby wyprowadzić format z podstawowego formatu _D3D_texture i value_type tego szablonu. Podany format musi być zgodny z podstawowym formatem _D3D_texture.

### <a name="return-value"></a>Wartość zwracana

Tekstura przy użyciu dostarczonej tekstury D3D.

## <a name="msad4"></a><a name="msad4"></a>msad4

Porównuje 4-bajtową wartość referencyjną i 8-bajtową wartość źródłową i gromadzi wektor 4 sum. Każda suma odpowiada zamaskowanej sumie bezwzględnych różnic różnych linii trasowania bajtów między wartością odniesienia a wartością źródłową.

```cpp
inline uint4 msad4(
    uint _Reference,
    uint2 _Source,
    uint4 _Accum) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Reference*<br/>
Tablica odwołań 4 bajtów w jednej wartości uint

*_Source*<br/>
Tablica źródłowsza 8 bajtów w wektorze dwóch wartości uint.

*_Accum*<br/>
Wektor 4 wartości, które mają zostać dodane do zamaskowanych sum różnic bezwzględnych różnych linii trasowania bajtów między wartością odniesienia a wartością źródłową.

### <a name="return-value"></a>Wartość zwracana

Zwraca wektor 4 sum. Każda suma odpowiada zamaskowanej sumie bezwzględnych różnic różnych linii trasowania bajtów między wartością odniesienia a wartością źródłową.

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp_graphics.h

**Obszar nazw:** Współbieżność::grafika::direct3d

## <a name="see-also"></a>Zobacz też

[Współbieżność::grafika::drektodowy obszar nazw](concurrency-graphics-direct3d-namespace.md)
