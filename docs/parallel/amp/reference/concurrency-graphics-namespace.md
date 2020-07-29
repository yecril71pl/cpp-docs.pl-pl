---
title: Concurrency::graphics — Przestrzeń nazw
ms.date: 11/04/2016
f1_keywords:
- AMP_GRAPHICS/Concurrency
ms.assetid: 4529d3b1-d7da-4ffb-82bf-080915e0f23e
ms.openlocfilehash: 942b3bbace85fa297bba6cd4b509f67006a4aed3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226740"
---
# <a name="concurrencygraphics-namespace"></a>Concurrency::graphics — Przestrzeń nazw

Przestrzeń nazw Graphics zawiera typy i funkcje, które są przeznaczone do programowania grafiki.

## <a name="syntax"></a>Składnia

```cpp
namespace graphics;
```

## <a name="members"></a>Elementy członkowskie

### <a name="namespaces"></a>Namespaces

|Nazwa|Opis|
|----------|-----------------|
|[Concurrency:: Graphics::d irect3d przestrzeń nazw](concurrency-graphics-direct3d-namespace.md)|Udostępnia funkcje dla międzyoperacyjności Direct3D.|

### <a name="typedefs"></a>Typedefs

|Nazwa|Opis|
|----------|-----------------|
|`uint`|Typ elementu klasy [uint_2](uint-2-class.md), [klasy uint_3](uint-3-class.md)i [klasy uint_4](uint-4-class.md). Zdefiniowane jako `typedef unsigned int uint;` .|

### <a name="enumerations"></a>Wyliczenia

|Nazwa|Opis|
|----------|-----------------|
|[Address_mode Wyliczenie](concurrency-graphics-namespace-enums.md#address_mode).|Określa tryby adresów obsługiwane dla pobierania próbek tekstury.|
|[filter_mode, Wyliczenie](concurrency-graphics-namespace-enums.md#filter_mode)|Określa tryby filtru obsługiwane przez próbkowanie tekstury.|

### <a name="classes"></a>Klasy

|Nazwa|Opis|
|----------|-----------------|
|[Texture — Klasa](texture-class.md)|Tekstura jest agregacją danych na accelerator_view w domenie zakresu. Jest to zbiór zmiennych, po jednym dla każdego elementu w domenie zakresów. Każda zmienna przechowuje wartość odpowiadającą typowi pierwotnemu C++ (bez znaku int, int, float, Double) lub typu skalarnego, lub unorm (zdefiniowanego w concurrency:: Graphics) lub kwalifikujących się krótkich typów wektorów zdefiniowanych w concurrency:: Graphics.|
|[Klasa writeonly_texture_view](writeonly-texture-view-class.md)|Writeonly_texture_view zapewnia dostęp do tekstury.|
|[Klasa double_2](double-2-class.md)|Reprezentuje krótki wektor 2 **`double`** wartości.|
|[Klasa double_3](double-3-class.md)|Reprezentuje krótki wektor składający się z 3 **`double`** wartości.|
|[Klasa double_4](double-4-class.md)|Reprezentuje krótki wektor 4 **`double`** wartości.|
|[Klasa float_2](float-2-class.md)|Reprezentuje krótki wektor 2 **`float`** wartości.|
|[Klasa float_3](float-3-class.md)|Reprezentuje krótki wektor składający się z 3 **`float`** wartości.|
|[Klasa float_4](float-4-class.md)|Reprezentuje krótki wektor 4 **`float`** wartości.|
|[Klasa int_2](int-2-class.md)|Reprezentuje krótki wektor 2 **`int`** wartości.|
|[Klasa int_3](int-3-class.md)|Reprezentuje krótki wektor składający się z 3 **`int`** wartości.|
|[Klasa int_4](int-4-class.md)|Reprezentuje krótki wektor 4 **`int`** wartości.|
|[Klasa norm_2](norm-2-class.md)|Reprezentuje krótki wektor 2 `norm` wartości.|
|[Klasa norm_3](norm-3-class.md)|Reprezentuje krótki wektor składający się z 3 `norm` wartości.|
|[Klasa norm_4](norm-4-class.md)|Reprezentuje krótki wektor 4 `norm` wartości.|
|[Klasa uint_2](uint-2-class.md)|Reprezentuje krótki wektor 2 `uint` wartości.|
|[Klasa uint_3](uint-3-class.md)|Reprezentuje krótki wektor składający się z 3 `uint` wartości.|
|[Klasa uint_4](uint-4-class.md)|Reprezentuje krótki wektor 4 `uint` wartości.|
|[Klasa unorm_2](unorm-2-class.md)|Reprezentuje krótki wektor 2 `unorm` wartości.|
|[Klasa unorm_3](unorm-3-class.md)|Reprezentuje krótki wektor składający się z 3 `unorm` wartości.|
|[Klasa unorm_4](unorm-4-class.md)|Reprezentuje krótki wektor 4 `unorm` wartości.|
|[Klasa próbnika](sampler-class.md)|Reprezentuje konfigurację próbnika używaną do próbkowania tekstury.|
|[short_vector — Struktura](short-vector-structure.md)|Udostępnia podstawową implementację krótkiego wektora wartości.|
|[short_vector_traits — Struktura](short-vector-traits-structure.md)|Zapewnia pobieranie długości i typu krótkiego wektora.|
|[Klasa texture_view](texture-view-class.md)|Zapewnia dostęp do odczytu i zapisu do tekstury.|

### <a name="functions"></a>Funkcje

|Nazwa|Opis|
|----------|-----------------|
|[kopiowane](concurrency-graphics-namespace-functions.md#copy)|Przeciążone. Kopiuje zawartość tekstury źródłowej do buforu hosta docelowego.|
|[copy_async](concurrency-graphics-namespace-functions.md#copy_async)|Przeciążone. Asynchronicznie kopiuje zawartość tekstury źródłowej do buforu hosta docelowego.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp_graphics. h

**Przestrzeń nazw:** Współbieżności

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
