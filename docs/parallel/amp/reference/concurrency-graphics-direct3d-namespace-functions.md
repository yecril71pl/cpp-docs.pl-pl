---
title: 'CONCURRENCY::Graphics:: Direct3D — przestrzeń nazw funkcji | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 2ed95ed8df8a42dc62684c71a3005c2f33fecd18
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686337"
---
# <a name="concurrencygraphicsdirect3d-namespace-functions"></a>CONCURRENCY::Graphics:: Direct3D — przestrzeń nazw funkcji
||||  
|-|-|-|  
|[get_sampler](#get_sampler)|[get_texture](#get_texture)|[make_sampler](#make_sampler)|  
|[make_texture](#make_texture)|[msad4](#msad4)|  

 
##  <a name="get_sampler"></a>  get_sampler —  
 Get interfejsu D3D przykłady stanu na danym akceleratora wyświetlić reprezentująca przykłady określonego obiektu.  
  
```  
IUnknown* get_sampler(
    const Concurrency::accelerator_view& _Av,  
    const sampler& _Sampler) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Av`  
 Widok akceleratora D3D, na którym ma być tworzony stanu programu D3D przykłady.  
  
 `_Sampler`  
 Obiekt przykłady, dla której utworzona jest podstawowy interfejs stanu przykłady D3D.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik interfejsu IUnknown odpowiadającego stanu programu D3D przykłady, reprezentujący danego przykłady.  
  
##  <a name="get_texture"></a>  get_texture —  
 Pobiera bazowy określony interfejs tekstury Direct3D [tekstury](texture-class.md) obiektu.  
  
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
 `value_type`  
 Typ elementu tekstury.  
  
 `_Rank`  
 Pozycja tekstury.  
  
 `_Texture`  
 Tekstury lub widok tekstury powiązany z accelerator_view, dla której jest zwracana powiązanego interfejsu tekstury Direct3D.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik interfejsu IUnknown odpowiadający tekstury Direct3D bazowy tekstury.  
  
##  <a name="make_sampler"></a>  make_sampler —  
 Utwórz próbnika ze wskaźnikiem D3D przykłady stanu interfejsu.  
  
```  
sampler make_sampler(_In_ IUnknown* _D3D_sampler) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_D3D_sampler`  
 Wskaźnik interfejsu IUnknown stanu przykłady D3D na tworzenie, przykładów z.  
  
### <a name="return-value"></a>Wartość zwracana  
 Przykłady reprezentuje podany stan przykłady D3D.  
  
##  <a name="make_texture"></a>  make_texture —  
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
 `value_type`  
 Typ elementów w tekstury.  
  
 `_Rank`  
 Pozycja tekstury.  
  
 `_Av`  
 Widok akceleratora D3D, na którym ma być tworzony tekstury.  
  
 `_D3D_texture`  
 Wskaźnik interfejsu IUnknown tekstury D3D utworzyć tekstury z.  
  
 `_View_format`  
 Format DXGI, który ma być używany dla widoków utworzone na podstawie tego tekstury. Przekaż DXGI_FORMAT_UNKNOWN (ustawienie domyślne) wyprowadzenia format z podstawowym formacie _D3D_texture i value_type tego szablonu. Podany format musi być zgodny z formatem podstawowej _D3D_texture.  
  
### <a name="return-value"></a>Wartość zwracana  
 Teksturę za pomocą podanego tekstury D3D.  
  
##  <a name="msad4"></a>  msad4 —  
 Porównuje odwołania 4-bajtowych wartości i wartości 8-bajtowych źródłowej i akumuluje wektor 4 sum. Każda suma odpowiada maskowanego sumę bezwzględną różnice z różnych bajtów Wyrównanie wartości odwołania i wartość źródła.  
  
```  
inline uint4 msad4(
    uint _Reference,  
    uint2 _Source,  
    uint4 _Accum) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Reference`  
 Tablica odwołanie 4 bajty w jedną wartość uint  
  
 `_Source`  
 Źródłowa tablica 8 bajtów w przypadku wektora z dwóch wartości uint.  
  
 `_Accum`  
 Wektor 4 wartości, które mają zostać dodane do maskowanego sumę bezwzględną różnice wyrównanie różnych bajtów między wartości odwołania i wartość źródła.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wektor 4 sum. Każda suma odpowiada maskowanego sumę bezwzględną różnice z różnych bajtów Wyrównanie wartości odwołania i wartość źródła.  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** amp_graphics.h  
  
 **Namespace:** CONCURRENCY::Graphics:: Direct3D — 

## <a name="see-also"></a>Zobacz też  
 [Concurrency::graphics::direct3d, przestrzeń nazw](concurrency-graphics-direct3d-namespace.md)
