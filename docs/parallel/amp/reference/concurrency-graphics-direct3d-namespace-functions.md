---
title: Concurrency::graphics::direct3d, funkcje przestrzeni nazw
ms.date: 11/04/2016
f1_keywords:
- amp_graphics/Concurrency::graphics::direct3d::get_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_texture
ms.assetid: 11ee1d42-333e-4ae9-95ac-4cf68c06d13d
ms.openlocfilehash: 665732700ee6b85425f332a0eb96a5b75864a74e
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126971"
---
# <a name="concurrencygraphicsdirect3d-namespace-functions"></a>Concurrency::graphics::direct3d, funkcje przestrzeni nazw

||||
|-|-|-|
|[get_sampler](#get_sampler)|[get_texture](#get_texture)|[make_sampler](#make_sampler)|
|[make_texture](#make_texture)|[msad4](#msad4)|

## <a name="get_sampler"></a>get_sampler

Pobierz interfejs stanu próbkowania D3D w danym widoku akceleratora, który reprezentuje określony obiekt próbnika.

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

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik interfejsu IUnknown odpowiadający stanowi próbnika D3D, który reprezentuje dany próbnik.

## <a name="get_texture"></a>get_texture

Pobiera interfejs tekstury Direct3D stanowiący podstawę określonego obiektu [tekstury](texture-class.md) .

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
Widok tekstury lub tekstury skojarzony z accelerator_view, dla którego zwracany jest źródłowy interfejs tekstury Direct3D.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik interfejsu IUnknown odpowiadający teksturze Direct3D bazowej tekstury.

## <a name="make_sampler"></a>make_sampler

Utwórz próbkę ze wskaźnika interfejsu stanu elementu próbkowania D3D.

```cpp
sampler make_sampler(_In_ IUnknown* _D3D_sampler) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_D3D_sampler*<br/>
Wskaźnik interfejsu IUnknown stanu próbnika D3D, z którego ma zostać utworzony próbnik.

### <a name="return-value"></a>Wartość zwrócona

Próbnik reprezentuje podany stan próbnika D3D.

## <a name="make_texture"></a>make_texture

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
Typ elementów w tekstury.

*_Rank*<br/>
Ranga tekstury.

*_Av*<br/>
Widok akceleratora D3D, na którym ma zostać utworzona tekstura.

*_D3D_texture*<br/>
Wskaźnik interfejsu IUnknown tekstury D3D, z którego ma zostać utworzona tekstura.

*_View_format*<br/>
Format DXGI, który ma być używany dla widoków utworzonych na podstawie tej tekstury. Przekaż DXGI_FORMAT_UNKNOWN (wartość domyślna), aby utworzyć format z bazowego formatu _D3D_texture i value_type tego szablonu. Podany format musi być zgodny z źródłowym formatem _D3D_texture.

### <a name="return-value"></a>Wartość zwrócona

Tekstura przy użyciu podanej tekstury D3D.

## <a name="msad4"></a>msad4

Porównuje 4-bajtową wartość odniesienia i 8-bajtową wartość źródła i gromadzi wektor 4 sum. Każda suma odnosi się do zamaskowanej sumy bezwzględnych różnic różnych bajtów między wartością referencyjną a wartością źródłową.

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
Tablica źródłowa 8 bajtów w wektorze dwóch wartości uint.

*_Accum*<br/>
Wektor 4 wartości, który ma zostać dodany do maskowanej sumy bezwzględnych różnic różnych bajtów między wartością referencyjną a wartością źródłową.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wektor 4 sum. Każda suma odnosi się do zamaskowanej sumy bezwzględnych różnic różnych bajtów między wartością referencyjną a wartością źródłową.

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp_graphics. h

**Przestrzeń nazw:** Concurrency:: Graphics::d irect3d

## <a name="see-also"></a>Zobacz też

[Concurrency::graphics::direct3d, przestrzeń nazw](concurrency-graphics-direct3d-namespace.md)
