---
title: Concurrency::graphics — Przestrzeń nazw
ms.date: 11/04/2016
f1_keywords:
- AMP_GRAPHICS/Concurrency
ms.assetid: 4529d3b1-d7da-4ffb-82bf-080915e0f23e
ms.openlocfilehash: c7e3b245c8d9e6ba0c563a63910fadd678523087
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139449"
---
# <a name="concurrencygraphics-namespace"></a>Concurrency::graphics — Przestrzeń nazw

Przestrzeń nazw Graphics zawiera typy i funkcje, które są przeznaczone do programowania grafiki.

## <a name="syntax"></a>Składnia

```cpp
namespace graphics;
```

## <a name="members"></a>Members

### <a name="namespaces"></a>Przestrzenie nazw

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Concurrency::graphics::direct3d, przestrzeń nazw](concurrency-graphics-direct3d-namespace.md)|Udostępnia funkcje dla międzyoperacyjności Direct3D.|

### <a name="typedefs"></a>Typedefs

|Name (Nazwa)|Opis|
|----------|-----------------|
|`uint`|Typ elementu klasy [uint_2](uint-2-class.md), [klasy uint_3](uint-3-class.md)i [klasy uint_4](uint-4-class.md). Zdefiniowane jako `typedef unsigned int uint;`.|

### <a name="enumerations"></a>Wyliczenia

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Address_mode Wyliczenie](concurrency-graphics-namespace-enums.md#address_mode).|Określa tryby adresów obsługiwane dla pobierania próbek tekstury.|
|[filter_mode, Wyliczenie](concurrency-graphics-namespace-enums.md#filter_mode)|Określa tryby filtru obsługiwane przez próbkowanie tekstury.|

### <a name="classes"></a>Klasy

|Name (Nazwa)|Opis|
|----------|-----------------|
|[texture, klasa](texture-class.md)|Tekstura jest agregacją danych na accelerator_view w domenie zakresu. Jest to zbiór zmiennych, po jednym dla każdego elementu w domenie zakresów. Każda zmienna przechowuje wartość odpowiadającą typowi C++ pierwotnemu (bez znaku int, int, float, Double) lub typu skalarnego, lub unorm (zdefiniowana w elemencie concurrency:: Graphics) lub kwalifikujących się krótkich typów wektorów zdefiniowanych w concurrency:: Graphics.|
|[writeonly_texture_view, klasa](writeonly-texture-view-class.md)|Writeonly_texture_view zapewnia dostęp do tekstury.|
|[double_2, klasa](double-2-class.md)|Reprezentuje krótki wektor 2 `double` wartości.|
|[double_3, klasa](double-3-class.md)|Reprezentuje krótki wektor wartości 3 `double`.|
|[double_4, klasa](double-4-class.md)|Reprezentuje krótki wektor 4 `double` wartości.|
|[float_2, klasa](float-2-class.md)|Reprezentuje krótki wektor 2 `float` wartości.|
|[float_3, klasa](float-3-class.md)|Reprezentuje krótki wektor wartości 3 `float`.|
|[float_4, klasa](float-4-class.md)|Reprezentuje krótki wektor 4 `float` wartości.|
|[int_2, klasa](int-2-class.md)|Reprezentuje krótki wektor 2 `int` wartości.|
|[int_3, klasa](int-3-class.md)|Reprezentuje krótki wektor wartości 3 `int`.|
|[int_4, klasa](int-4-class.md)|Reprezentuje krótki wektor 4 `int` wartości.|
|[norm_2, klasa](norm-2-class.md)|Reprezentuje krótki wektor 2 `norm` wartości.|
|[norm_3, klasa](norm-3-class.md)|Reprezentuje krótki wektor wartości 3 `norm`.|
|[norm_4, klasa](norm-4-class.md)|Reprezentuje krótki wektor 4 `norm` wartości.|
|[uint_2, klasa](uint-2-class.md)|Reprezentuje krótki wektor 2 `uint` wartości.|
|[uint_3, klasa](uint-3-class.md)|Reprezentuje krótki wektor wartości 3 `uint`.|
|[uint_4, klasa](uint-4-class.md)|Reprezentuje krótki wektor 4 `uint` wartości.|
|[unorm_2, klasa](unorm-2-class.md)|Reprezentuje krótki wektor 2 `unorm` wartości.|
|[unorm_3, klasa](unorm-3-class.md)|Reprezentuje krótki wektor wartości 3 `unorm`.|
|[unorm_4, klasa](unorm-4-class.md)|Reprezentuje krótki wektor 4 `unorm` wartości.|
|[sampler, klasa](sampler-class.md)|Reprezentuje konfigurację próbnika używaną do próbkowania tekstury.|
|[short_vector, struktura](short-vector-structure.md)|Udostępnia podstawową implementację krótkiego wektora wartości.|
|[short_vector_traits, struktura](short-vector-traits-structure.md)|Zapewnia pobieranie długości i typu krótkiego wektora.|
|[texture_view, klasa](texture-view-class.md)|Zapewnia dostęp do odczytu i zapisu do tekstury.|

### <a name="functions"></a>Funkcje

|Name (Nazwa)|Opis|
|----------|-----------------|
|[kopiowane](concurrency-graphics-namespace-functions.md#copy)|Przeciążone. Kopiuje zawartość tekstury źródłowej do buforu hosta docelowego.|
|[copy_async](concurrency-graphics-namespace-functions.md#copy_async)|Przeciążone. Asynchronicznie kopiuje zawartość tekstury źródłowej do buforu hosta docelowego.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp_graphics. h

**Przestrzeń nazw:** Współbieżności

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
