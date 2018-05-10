---
title: przykłady klas | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- sampler
- AMP_GRAPHICS/sampler
- AMP_GRAPHICS/concurrency::sampler::graphics::sampler
- AMP_GRAPHICS/concurrency::sampler::graphics::get_address_mode
- AMP_GRAPHICS/concurrency::sampler::graphics::get_border_color
- AMP_GRAPHICS/concurrency::sampler::graphics::get_filter_mode
- AMP_GRAPHICS/concurrency::sampler::graphics::address_mode
- AMP_GRAPHICS/concurrency::sampler::graphics::border_color
- AMP_GRAPHICS/concurrency::sampler::graphics::filter_mode
dev_langs:
- C++
ms.assetid: 9a6a9807-497d-402d-b092-8c4d86275b80
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4f9788b62385f7c6f5eb82e3fbc69d63d3120cc2
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="sampler-class"></a>sampler — Klasa
Klasa przykłady agreguje informacje o konfiguracji próbkowania służący do pobierania próbek tekstury.  
  
## <a name="syntax"></a>Składnia  
  
```  
class sampler;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Przykłady — Konstruktor](#ctor)|Przeciążone. Tworzy wystąpienie przykłady.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[get_address_mode](#get_address_mode)|Zwraca `address_mode` który został skojarzony z obiektem przykłady.|  
|[get_border_color](#get_border_color)|Zwraca kolor obramowania, który został skojarzony z obiektem przykłady.|  
|[get_filter_mode](#get_filter_mode)|Zwraca `filter_mode` który został skojarzony z obiektem przykłady.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[operator=](#operator_eq)|Przeciążone. Operator przypisania.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[address_mode](#address_mode)|Pobiera tryb adres `sampler` obiektu.|  
|[border_color](#border_color)|Pobiera kolor obramowania `sampler` obiektu.|  
|[filter_mode](#filter_mode)|Pobiera tryb filtru `sampler` obiektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `sampler`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** amp_graphics.h  
  
 **Namespace:** concurrency::graphics  
  
##  <a name="ctor"></a> Przykłady 

 Tworzy wystąpienie klasy [sampler — klasa](sampler-class.md).  
  
```  
sampler() restrict(cpu);

 *// [1] default constructor  
 
sampler(// [2] constructor  
    filter_mode _Filter_mode) restrict(cpu);

 
sampler(// [3] constructor  
    address_mode _Address_mode,  
    float_4 _Border_color = float_4(0.0f,
    0.0f,
    0.0f,
    0.0f)) restrict(cpu);

 
sampler(// [4] constructor  
    filter_mode _Filter_mode,  
    address_mode _Address_mode,  
    float_4 _Border_color = float_4(0.0f,
    0.0f,
    0.0f,
    0.0f)) restrict(cpu);

 
sampler(// [5] copy constructor  
    const sampler& _Other) restrict(amp,
    cpu);

 
sampler(// [6] move constructor  
    sampler&& _Other) restrict(amp,
    cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_Filter_mode`  
 Tryb filtrowania ma być używana podczas próbkowania.  
  
 `_Address_mode`  
 Tryb adresowania do użycia w próbkowania dla wszystkich wymiarów.  
  
 `_Border_color`  
 Kolor obramowania używany, jeśli tryb adres jest address_border. Wartość domyślna to `float_4(0.0f, 0.0f, 0.0f, 0.0f)`.  
  
 `_Other`  
 [5] Copy Constructor  
 `sampler` Obiekt ma zostać skopiowany do nowego `sampler` wystąpienia.  
  
 [6] Konstruktor przenoszenia  
 `sampler` Obiekt, aby przenieść do nowego `sampler` wystąpienia.  
  
##  <a name="address_mode"></a> address_mode — 

 Pobiera tryb adres `sampler` obiektu.  
  
```  
__declspec(property(get= get_address_mode)) Concurrency::graphics::address_mode address_mode;  
```  
  
##  <a name="border_color"></a> border_color 

 Pobiera kolor obramowania `sampler` obiektu.  
  
```  
__declspec(property(get= get_border_color)) Concurrency::graphics::float_4 border_color;  
```  
  
##  <a name="filter_mode"></a> filter_mode — 

 Pobiera tryb filtru `sampler` obiektu.  
  
```  
__declspec(property(get= get_filter_mode)) Concurrency::graphics::filter_mode filter_mode;  
```  
  
##  <a name="get_address_mode"></a> get_address_mode 

 Zwraca tryb filtru, który jest skonfigurowany dla tego `sampler`.  
  
```  
Concurrency::graphics::address_mode get_address_mode() const __GPU;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Tryb adres, który jest skonfigurowany do próbnika.  
  
##  <a name="get_border_color"></a> get_border_color 

 Zwraca kolor obramowania, który jest skonfigurowany dla tego `sampler`.  
  
```  
Concurrency::graphics::float_4 get_border_color() const restrict(amp, cpu);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Float_4 —, który zawiera kolor obramowania.  
  
##  <a name="get_filter_mode"></a> get_filter_mode 

 Zwraca tryb filtru, który jest skonfigurowany dla tego `sampler`.  
  
```  
Concurrency::graphics::filter_mode get_filter_mode() const restrict(amp, cpu);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Tryb filtru skonfigurowanego do próbnika.  
  
##  <a name="operator_eq"></a> operator = 

 Przypisuje wartość innego obiektu przykłady istniejących przykładów.  
  
```  
sampler& operator= (// [1] copy assignment operator const sampler& _Other) restrict(amp,
    cpu);

 
sampler& operator= (// [2] move assingment operator sampler&& _Other) restrict(amp,
    cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 [1] Operator przypisania kopiowania  
 `sampler` Obiekt ma zostać skopiowany do to `sampler`.  
  
 [2] Operator przypisania przenoszenia  
 `sampler` Obiekt, aby przejść do tego `sampler`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do tego wystąpienia przykłady.  
  
## <a name="see-also"></a>Zobacz też  
 [Concurrency::graphics, przestrzeń nazw](concurrency-graphics-namespace.md)
