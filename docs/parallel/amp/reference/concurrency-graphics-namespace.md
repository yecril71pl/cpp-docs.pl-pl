---
title: CONCURRENCY::Graphics Namespace | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: AMP_GRAPHICS/Concurrency
dev_langs: C++
ms.assetid: 4529d3b1-d7da-4ffb-82bf-080915e0f23e
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: aef7e219190584ec91b08e9c44b4c921ec91d787
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="concurrencygraphics-namespace"></a>Concurrency::graphics — Przestrzeń nazw
Grafika przestrzeń nazw zawiera typy i funkcje, które są przeznaczone do programowania grafiki.  
  
## <a name="syntax"></a>Składnia  
  
```  
namespace graphics;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="namespaces"></a>Namespaces  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Concurrency::graphics::direct3d, przestrzeń nazw](concurrency-graphics-direct3d-namespace.md)|Udostępnia funkcje dla międzyoperacyjności z modelem Direct3D.|  
  
### <a name="typedefs"></a>Typedefs  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`uint`|Typ elementu [uint_2 — klasa](uint-2-class.md), [uint_3 — klasa](uint-3-class.md), i [uint_4 — klasa](uint-4-class.md). Zdefiniowane jako `typedef unsigned int uint;`.|  
  
### <a name="enumerations"></a>Wyliczenia  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[address_mode — wyliczenie](concurrency-graphics-namespace-enums.md#address_mode).|Określa obsługuje do próbkowania tekstury tryby adres.|  
|[filter_mode — wyliczenie](concurrency-graphics-namespace-enums.md#filter_mode)|Określa obsługuje do próbkowania tekstury tryby filtru.|  
  
### <a name="classes"></a>Klasy  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[texture, klasa](texture-class.md)|Tekstura jest agregacji na accelerator_view w domenie zakres danych. Jest kolekcja zmiennych, po jednej dla każdego elementu w zakresie domeny. Każda zmienna przechowuje wartość odpowiadającą pierwotnych typów języka C++ (unsigned int, int, float, double) lub typu skalarnej normy, lub unorm — (zdefiniowany w concurrency::graphics) lub typy wektorów krótkich kwalifikujących się zdefiniowane w concurrency::graphics.|  
|[writeonly_texture_view, klasa](writeonly-texture-view-class.md)|Writeonly_texture_view udostępnia writeonly tekstury.|  
|[double_2, klasa](double-2-class.md)|Reprezentuje krótki wektorowa 2 `double` wartości.|  
|[double_3, klasa](double-3-class.md)|Reprezentuje krótki wektor 3 `double` wartości.|  
|[double_4, klasa](double-4-class.md)|Reprezentuje krótki wektor 4 `double` wartości.|  
|[float_2, klasa](float-2-class.md)|Reprezentuje krótki wektorowa 2 `float` wartości.|  
|[float_3, klasa](float-3-class.md)|Reprezentuje krótki wektor 3 `float` wartości.|  
|[float_4, klasa](float-4-class.md)|Reprezentuje krótki wektor 4 `float` wartości.|  
|[int_2, klasa](int-2-class.md)|Reprezentuje krótki wektorowa 2 `int` wartości.|  
|[int_3, klasa](int-3-class.md)|Reprezentuje krótki wektor 3 `int` wartości.|  
|[int_4, klasa](int-4-class.md)|Reprezentuje krótki wektor 4 `int` wartości.|  
|[norm_2, klasa](norm-2-class.md)|Reprezentuje krótki wektorowa 2 `norm` wartości.|  
|[norm_3, klasa](norm-3-class.md)|Reprezentuje krótki wektor 3 `norm` wartości.|  
|[norm_4, klasa](norm-4-class.md)|Reprezentuje krótki wektor 4 `norm` wartości.|  
|[uint_2, klasa](uint-2-class.md)|Reprezentuje krótki wektorowa 2 `uint` wartości.|  
|[uint_3, klasa](uint-3-class.md)|Reprezentuje krótki wektor 3 `uint` wartości.|  
|[uint_4, klasa](uint-4-class.md)|Reprezentuje krótki wektor 4 `uint` wartości.|  
|[unorm_2, klasa](unorm-2-class.md)|Reprezentuje krótki wektorowa 2 `unorm` wartości.|  
|[unorm_3, klasa](unorm-3-class.md)|Reprezentuje krótki wektor 3 `unorm` wartości.|  
|[unorm_4, klasa](unorm-4-class.md)|Reprezentuje krótki wektor 4 `unorm` wartości.|  
|[sampler, klasa](sampler-class.md)|Reprezentuje konfigurację przykłady użyta do próbkowania tekstury.|  
|[short_vector, struktura](short-vector-structure.md)|Udostępnia podstawową implementację krótkich wektora wartości.|  
|[short_vector_traits, struktura](short-vector-traits-structure.md)|Zapewnia pobieranie długości i rodzaj krótkich wektora.|  
|[texture_view, klasa](texture-view-class.md)|Zapewnia dostęp do odczytu i zapisu do tekstury.|  
  
### <a name="functions"></a>Funkcje  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Kopiuj](concurrency-graphics-namespace-functions.md#copy)|Przeciążone. Kopiuje zawartość tekstury źródła do buforu hosta docelowego.|  
|[copy_async —](concurrency-graphics-namespace-functions.md#copy_async)|Przeciążone. Asynchronicznie kopiuje zawartość tekstury źródła do buforu hosta docelowego.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** amp_graphics.h  
  
 **Namespace:** współbieżności  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
