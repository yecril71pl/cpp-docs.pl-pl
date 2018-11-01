---
title: Concurrency::graphics — Przestrzeń nazw
ms.date: 11/04/2016
f1_keywords:
- AMP_GRAPHICS/Concurrency
ms.assetid: 4529d3b1-d7da-4ffb-82bf-080915e0f23e
ms.openlocfilehash: 5bff3bbba3c2ba9e6c51ee20c8701c80a557707f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500493"
---
# <a name="concurrencygraphics-namespace"></a>Concurrency::graphics — Przestrzeń nazw

Przestrzeń nazw graficznych zawiera typy i funkcje, które są przeznaczone do programowania grafiki.

## <a name="syntax"></a>Składnia

```
namespace graphics;
```

## <a name="members"></a>Elementy członkowskie

### <a name="namespaces"></a>Namespaces

|Nazwa|Opis|
|----------|-----------------|
|[Concurrency::graphics::direct3d, przestrzeń nazw](concurrency-graphics-direct3d-namespace.md)|Oferuje funkcje międzyoperacyjności interfejsu Direct3D.|

### <a name="typedefs"></a>Typedefs

|Nazwa|Opis|
|----------|-----------------|
|`uint`|Typ elementu [uint_2, klasa](uint-2-class.md), [uint_3, klasa](uint-3-class.md), i [uint_4, klasa](uint-4-class.md). Definiowany jako `typedef unsigned int uint;`.|

### <a name="enumerations"></a>Wyliczenia

|Nazwa|Opis|
|----------|-----------------|
|[address_mode — wyliczenie](concurrency-graphics-namespace-enums.md#address_mode).|Określa tryby adresowania obsługiwane dla pobierania próbek tekstury.|
|[filter_mode — wyliczenie](concurrency-graphics-namespace-enums.md#filter_mode)|Określa tryby filtrowania obsługiwane dla pobierania próbek tekstury.|

### <a name="classes"></a>Klasy

|Nazwa|Opis|
|----------|-----------------|
|[texture, klasa](texture-class.md)|Tekstura jest agregacją danych na obiekcie accelerator_view w domenie zakresu. Jest to zbiór zmiennych, jeden dla każdego elementu w zakresie domeny. Każda zmienna przechowuje wartość odpowiadającą typowi pierwotnemu C++ (unsigned int, int, float, double) lub skalar typu norm lub unorm (zdefiniowane w concurrency::graphics) lub kwalifikujące się krótkimi wektorami zdefiniowanych w concurrency::graphics.|
|[writeonly_texture_view, klasa](writeonly-texture-view-class.md)|Writeonly_texture_view dostarcza writeonly dostęp do tekstury.|
|[double_2, klasa](double-2-class.md)|Reprezentuje krótki wektor 2 `double` wartości.|
|[double_3, klasa](double-3-class.md)|Reprezentuje krótki wektor składający się z 3 `double` wartości.|
|[double_4, klasa](double-4-class.md)|Reprezentuje krótki wektor 4 `double` wartości.|
|[float_2, klasa](float-2-class.md)|Reprezentuje krótki wektor 2 `float` wartości.|
|[float_3, klasa](float-3-class.md)|Reprezentuje krótki wektor składający się z 3 `float` wartości.|
|[float_4, klasa](float-4-class.md)|Reprezentuje krótki wektor 4 `float` wartości.|
|[int_2, klasa](int-2-class.md)|Reprezentuje krótki wektor 2 `int` wartości.|
|[int_3, klasa](int-3-class.md)|Reprezentuje krótki wektor składający się z 3 `int` wartości.|
|[int_4, klasa](int-4-class.md)|Reprezentuje krótki wektor 4 `int` wartości.|
|[norm_2, klasa](norm-2-class.md)|Reprezentuje krótki wektor 2 `norm` wartości.|
|[norm_3, klasa](norm-3-class.md)|Reprezentuje krótki wektor składający się z 3 `norm` wartości.|
|[norm_4, klasa](norm-4-class.md)|Reprezentuje krótki wektor 4 `norm` wartości.|
|[uint_2, klasa](uint-2-class.md)|Reprezentuje krótki wektor 2 `uint` wartości.|
|[uint_3, klasa](uint-3-class.md)|Reprezentuje krótki wektor składający się z 3 `uint` wartości.|
|[uint_4, klasa](uint-4-class.md)|Reprezentuje krótki wektor 4 `uint` wartości.|
|[unorm_2, klasa](unorm-2-class.md)|Reprezentuje krótki wektor 2 `unorm` wartości.|
|[unorm_3, klasa](unorm-3-class.md)|Reprezentuje krótki wektor składający się z 3 `unorm` wartości.|
|[unorm_4, klasa](unorm-4-class.md)|Reprezentuje krótki wektor 4 `unorm` wartości.|
|[sampler, klasa](sampler-class.md)|Reprezentuje konfigurację próbnik używaną do pobierania próbek tekstury.|
|[short_vector, struktura](short-vector-structure.md)|Dostarcza podstawową implementację krótkiego wektora wartości.|
|[short_vector_traits, struktura](short-vector-traits-structure.md)|Umożliwia pobranie długości i typu krótkiego wektora.|
|[texture_view, klasa](texture-view-class.md)|Zapewnia dostęp do odczytu i zapisu do tekstury.|

### <a name="functions"></a>Funkcje

|Nazwa|Opis|
|----------|-----------------|
|[Kopiuj](concurrency-graphics-namespace-functions.md#copy)|Przeciążone. Kopiuje zawartość źródła tekstury do buforu hosta docelowego.|
|[copy_async](concurrency-graphics-namespace-functions.md#copy_async)|Przeciążone. Asynchronicznie kopiuje zawartość źródła tekstury do buforu hosta docelowego.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp_graphics.h

**Namespace:** współbieżności

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
