---
title: Concurrency::graphics::direct3d — Przestrzeń nazw
ms.date: 11/04/2016
f1_keywords:
- amp_graphics/Concurrency::graphics::direct3d
- amp_short_vectors/Concurrency::graphics::direct3d
ms.assetid: be283331-07cf-46e4-91a1-e8aa85d4ec8e
ms.openlocfilehash: 4911787fd17877769eb723cf1e61e29fe626a783
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139435"
---
# <a name="concurrencygraphicsdirect3d-namespace"></a>Concurrency::graphics::direct3d — Przestrzeń nazw

Zapewnia metody [get_texture](concurrency-graphics-direct3d-namespace-functions.md#get_texture) i [make_texture](concurrency-graphics-direct3d-namespace-functions.md#make_texture) .

## <a name="syntax"></a>Składnia

```cpp
namespace direct3d;
```

## <a name="members"></a>Members

### <a name="functions"></a>Funkcje

|Name (Nazwa)<br /><br /> Opis|
|--------------------------|
|[get_sampler](concurrency-graphics-direct3d-namespace-functions.md#get_sampler)<br /><br /> Pobierz interfejs stanu próbnika Direct3D w danym widoku akceleratora, który reprezentuje określony obiekt próbnika.|
|[get_texture](concurrency-graphics-direct3d-namespace-functions.md#get_texture)<br /><br /> Pobiera interfejs tekstury Direct3D stanowiący podstawę określonego obiektu [tekstury](texture-class.md) .|
|[make_sampler](concurrency-graphics-direct3d-namespace-functions.md#make_sampler)<br /><br /> Utwórz próbnik ze wskaźnika interfejsu stanu próbnika Direct3D.|
|[make_texture](concurrency-graphics-direct3d-namespace-functions.md#make_texture)<br /><br /> Tworzy obiekt [tekstury](texture-class.md) przy użyciu określonych parametrów.|
|[msad4](concurrency-graphics-direct3d-namespace-functions.md#msad4)<br /><br /> Porównuje 4-bajtową wartość odniesienia i 8-bajtową wartość źródła i gromadzi wektor 4 sum.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp_graphics. h

**Przestrzeń nazw:** Concurrency:: Graphics

## <a name="see-also"></a>Zobacz też

[Concurrency::graphics, przestrzeń nazw](concurrency-graphics-namespace.md)
