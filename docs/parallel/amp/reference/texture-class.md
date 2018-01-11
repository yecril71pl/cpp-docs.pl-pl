---
title: "Texture — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- texture
- AMP_GRAPHICS/texture
- AMP_GRAPHICS/concurrency::graphics::texture::texture
- AMP_GRAPHICS/concurrency::graphics::texture::copy_to
- AMP_GRAPHICS/concurrency::graphics::texture::data
- AMP_GRAPHICS/concurrency::graphics::texture::get
- AMP_GRAPHICS/concurrency::graphics::texture::get_associated_accelerator_view
- AMP_GRAPHICS/concurrency::graphics::texture::get_depth_pitch
- AMP_GRAPHICS/concurrency::graphics::texture::get_row_pitch
- AMP_GRAPHICS/concurrency::graphics::texture::set
- AMP_GRAPHICS/concurrency::graphics::texture::rank
- AMP_GRAPHICS/concurrency::graphics::texture::associated_accelerator_view
- AMP_GRAPHICS/concurrency::graphics::texture::depth_pitch
- AMP_GRAPHICS/concurrency::graphics::texture::row_pitch
dev_langs: C++
ms.assetid: 16e85d4d-e80a-474a-995d-8bf63fbdf34c
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6131f2349a065052c9860038ca4b9f08de89f37d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="texture-class"></a>texture — Klasa
Tekstura jest agregacji na danych `accelerator_view` w domenie zakresu. Jest kolekcja zmiennych, po jednej dla każdego elementu w zakresie domeny. Każda zmienna przechowuje wartość odpowiadającą typów pierwotnych języka C++ ( `unsigned int`, `int`, `float`, `double`), typem skalarnym ( `norm`, lub `unorm`), lub typu krótkich wektora.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <typename value_type,  int _Rank>  
class texture;  
```  
  
#### <a name="parameters"></a>Parametry  
 `value_type`  
 Typ elementów w tekstury.  
  
 `_Rank`  
 Pozycja tekstury.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`scalar_type`|Typy skalarne.|  
|`value_type`|Typy wartości.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Texture — Konstruktor](#ctor)|Inicjuje nowe wystąpienie klasy `texture` klasy.|  
|[~ texture — destruktor](#ctor)|Niszczy `texture` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[copy_to](#copy_to)|Kopie `texture` obiektu docelowego, wykonując kopię bezpośrednich.|  
|[dane](#data)|Zwraca wskaźnik Procesora do danych pierwotnych z tym tekstury.|  
|[get](#get)|Zwraca wartość elementu pod określonym indeksem.|  
|[get_associated_accelerator_view](#get_associated_accelerator_view)|Zwraca [accelerator_view](accelerator-view-class.md) czyli preferowanych cel dla tego tekstury ma zostać skopiowany na.|  
|[get_depth_pitch](#get_depth_pitch)|Zwraca liczbę bajtów między każdy Wycinek głębokości 3D przemieszczania tekstury na Procesor.|  
|[get_row_pitch](#get_row_pitch)|Zwraca liczbę bajtów między każdego wiersza w 2W i 3W przemieszczania tekstury procesora.|  
|[set](#set)|Ustawia wartość elementu pod określonym indeksem.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Operator()](#operator_call)|Zwraca wartość elementu określoną przez parametry.|  
|[Operator]](#operator_at)|Zwraca element pod określonym indeksem.|  
|[operator =](#operator_eq)|Kopiuje określony [tekstury](texture-class.md) obiektu do tego.|  
  
### <a name="public-constants"></a>Publiczny — stałe  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Rank — stała](#rank)|Pobiera pozycję `texture` obiektu.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[associated_accelerator_view —](#associated_accelerator_view)|Pobiera [accelerator_view](accelerator-view-class.md) czyli preferowanych cel dla tego tekstury ma zostać skopiowany na.|  
|[depth_pitch](#depth_pitch)|Pobiera liczbę bajtów między każdy Wycinek głębokości tekstury 3D przemieszczania procesora.|  
|[row_pitch](#row_pitch)|Pobiera liczbę bajtów między każdego wiersza w 2W i 3W przemieszczania tekstury na Procesor.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `_Texture_base`  
  
 `texture`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** amp_graphics.h  
  
 **Namespace:** Concurrency::graphics  
  
##  <a name="dtor"></a>~ tekstury 

 Niszczy `texture` obiektu.  
  
```  
~texture() restrict(cpu);
```  
  
##  <a name="associated_accelerator_view"></a>associated_accelerator_view — 

 Pobiera [accelerator_view](accelerator-view-class.md) czyli preferowanych cel dla tego tekstury ma zostać skopiowany na.  
  
```  
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;  
```  
  
##  <a name="copy_to"></a>copy_to 

 Kopie `texture` obiektu docelowego, wykonując kopię bezpośrednich.  
  
```  
void copy_to(texture& _Dest) const; 
void copy_to(writeonly_texture_view<value_type, _Rank>& _Dest) const; 
```  
  
### <a name="parameters"></a>Parametry  
 `_Dest`  
 Obiekt przeznaczony do skopiowania do.  
  
 `_Rank`  
 Pozycja tekstury.  
  
 `value_type`  
 Typ elementów w tekstury.  
  
##  <a name="data"></a>dane 

 Zwraca wskaźnik Procesora do danych pierwotnych z tym tekstury.  
  
```  
void* data() restrict(cpu);

 
const void* data() const restrict(cpu);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do danych pierwotnych tekstury.  
  
##  <a name="depth_pitch"></a>depth_pitch 

 Pobiera liczbę bajtów między każdy Wycinek głębokości tekstury 3D przemieszczania procesora.  
  
```  
__declspec(property(get= get_depth_pitch)) unsigned int depth_pitch;  
```  
  
##  <a name="get"></a>Pobierz 

 Zwraca wartość elementu pod określonym indeksem.  
  
```  
const value_type get(const index<_Rank>& _Index) const restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Index`  
 Indeks elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość elementu pod określonym indeksem.  
  
##  <a name="get_associated_accelerator_view"></a>get_associated_accelerator_view 

 Zwraca accelerator_view, preferowane docelowego dla tego tekstury ma zostać skopiowany na.  
  
```  
Concurrency::accelerator_view get_associated_accelerator_view() const restrict(cpu);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 [Accelerator_view](accelerator-view-class.md) czyli preferowanych cel dla tego tekstury ma zostać skopiowany na.  
  
##  <a name="get_depth_pitch"></a>get_depth_pitch 

 Zwraca liczbę bajtów między każdy Wycinek głębokości 3D przemieszczania tekstury na Procesor.  
  
```  
unsigned int get_depth_pitch() const restrict(cpu);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba bajtów między każdy Wycinek głębokości 3D przemieszczania tekstury na Procesor.  
  
##  <a name="get_row_pitch"></a>get_row_pitch 

 Zwraca liczbę bajtów między każdego wiersza w 2 wymiarów tekstury tymczasowej lub Wycinek głębokości tekstury przemieszczania 3-wymiarową każdego wiersza.  
  
```  
unsigned int get_row_pitch() const restrict(cpu);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba bajtów między każdego wiersza w 2 wymiarów tekstury tymczasowej lub Wycinek głębokości tekstury przemieszczania 3-wymiarową każdego wiersza.  
  
##  <a name="operator_call"></a>Operator() 

 Zwraca wartość elementu określoną przez parametry.  
  
```  
const value_type operator() (
    const index<_Rank>& _Index) const restrict(amp);

 
const value_type operator() (
    int _I0) const restrict(amp);

 
const value_type operator() (
    int _I0,  
    int _I1) const restrict(amp);

 
const value_type operator() (
    int _I0,  
    int _I1,  
    int _I2) const restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Index`  
 Indeks.  
  
 `_I0`  
 Najbardziej znaczące składnik indeksu.  
  
 `_I1`  
 Składnik dalej do większość — znaczące indeksu.  
  
 `_I2`  
 Najmniej znaczący składnik indeksu.  
  
 `_Rank`  
 Ranga indeksu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość elementu jest określona przez parametry.  
  
##  <a name="operator_at"></a>Operator] 

 Zwraca element pod określonym indeksem.  
  
```  
const value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

 
const value_type operator[] (int _I0) const restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Index`  
 Indeks.  
  
 `_I0`  
 Indeks.  
  
### <a name="return-value"></a>Wartość zwracana  
 Element pod określonym indeksem.  
  
##  <a name="operator_eq"></a>operator = 

 Kopiuje określony [tekstury](texture-class.md) obiektu do tego.  
  
```  
texture& operator= (
    const texture& _Other);

 
texture& operator= (
    texture<value_type, _Rank>&& _Other);
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `texture` Obiektu do skopiowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do tego `texture` obiektu.  
  
##  <a name="rank"></a>Ranga 

 Pobiera pozycję `texture` obiektu.  
  
```  
static const int rank = _Rank;  
```  
  
##  <a name="row_pitch"></a>row_pitch 

 Pobiera liczbę bajtów między każdego wiersza w 2W i 3W przemieszczania tekstury na Procesor.  
  
```  
__declspec(property(get= get_row_pitch)) unsigned int row_pitch;  
```  
  
##  <a name="set"></a>zestaw 

 Ustawia wartość elementu pod określonym indeksem.  
  
```  
void set(
    const index<_Rank>& _Index,  
    const value_type& value) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Index`  
 Indeks elementu.  
  
 `_Rank`  
 Ranga indeksu.  
  
 `value`  
 Nowa wartość elementu.  
  
##  <a name="ctor"></a>tekstury 

 Inicjuje nowe wystąpienie klasy `texture` klasy.  
  
```  
texture(const Concurrency::extent<_Rank>& _Ext) restrict(cpu);
 
texture(int _E0) restrict(cpu);
 
texture(int _E0, int _E1) restrict(cpu);
 
texture(int _E0, int _E1, int _E2) restrict(cpu);
 
texture(
    const Concurrency::extent<_Rank>& _Ext,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);
 
texture(
    int _E0,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);
 
texture(
    int _E0,  
    int _E1,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);
 
texture(
    int _E0,  
    int _E1,  
    int _E2,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);


template<typename _Input_iterator>  
texture(
    const Concurrency::extent<_Rank>& _Ext, 
    _Input_iterator _Src_first, 
    _Input_iterator _Src_last) restrict(cpu);

 
template<typename _Input_iterator>  
texture(
    int _E0, _Input_iterator _Src_first, _Input_iterator _Src_last) restrict(cpu);

 
template<typename _Input_iterator>  
texture(
    int _E0,  
    int _E1, 
    _Input_iterator _Src_first, 
    _Input_iterator _Src_last) restrict(cpu);

 
template<typename _Input_iterator>  
texture(
    int _E0,  
    int _E1,  
    int _E2, 
    _Input_iterator _Src_first, 
    _Input_iterator _Src_last) restrict(cpu);

 
template<typename _Input_iterator>  
texture(
    const Concurrency::extent<_Rank>& _Ext, 
    _Input_iterator _Src_first, 
    _Input_iterator _Src_last,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
template<typename _Input_iterator>  
texture(
    int _E0, 
    _Input_iterator _Src_first, 
    _Input_iterator _Src_last,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
template<typename _Input_iterator>  
texture(
    int _E0,  
    int _E1, 
    _Input_iterator _Src_first, 
    _Input_iterator _Src_last,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
template<typename _Input_iterator>  
texture(
    int _E0,  
    int _E1,  
    int _E2, 
    _Input_iterator _Src_first, 
    _Input_iterator _Src_last,  
    const Concurrency::accelerator_view& _Av) restrict(cpu))  ;  
 
texture(
    int _E0,  
    unsigned int _Bits_per_scalar_element) restrict(cpu);

 
texture(
    int _E0,  
    int _E1,  
    unsigned int _Bits_per_scalar_element) restrict(cpu);

 
texture(
    int _E0,  
    int _E1,  
    int _E2,  
    unsigned int _Bits_per_scalar_element) restrict(cpu);

 
texture(
    const Concurrency::extent<_Rank>& _Ext,  
    unsigned int _Bits_per_scalar_element,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
texture(
    int _E0,  
    unsigned int _Bits_per_scalar_element,  
    const Concurrency::accelerator_view& _Av)  ;  
 
texture(
    int _E0,  
    int _E1,  
    unsigned int _Bits_per_scalar_element,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
texture(
    int _E0,  
    int _E1,  
    int _E2,  
    unsigned int _Bits_per_scalar_element,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
texture(
    const Concurrency::extent<_Rank>& _Ext,  
    _In_ void* _Source,  
    unsigned int _Src_byte_size,  
    unsigned int _Bits_per_scalar_element) restrict(cpu);

 
texture(
    int _E0,  
    _In_ void* _Source,  
    unsigned int _Src_byte_size,  
    unsigned int _Bits_per_scalar_element) restrict(cpu);

 
texture(
    int _E0,  
    int _E1,  
    _In_ void* _Source,  
    unsigned int _Src_byte_size,  
    unsigned int _Bits_per_scalar_element) restrict(cpu);

 
texture(
    int _E0,  
    int _E1,  
    int _E2,  
    _In_ void* _Source,  
    unsigned int _Src_byte_size,  
    unsigned int _Bits_per_scalar_element) restrict(cpu);

 
texture(
    const Concurrency::extent<_Rank>& _Ext,  
    _In_ void* _Source,  
    unsigned int _Src_byte_size,  
    unsigned int _Bits_per_scalar_element,  
    const Concurrency::accelerator_view& _Av)  ;  
 
texture(
    int _E0,  
    _In_ void* _Source,  
    unsigned int _Src_byte_size,  
    unsigned int _Bits_per_scalar_element,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
texture(
    int _E0,  
    int _E1,  
    _In_ void* _Source,  
    unsigned int _Src_byte_size,  
    unsigned int _Bits_per_scalar_element,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
texture(
    int _E0,  
    int _E1,  
    int _E2,  
    _In_ void* _Source,  
    unsigned int _Src_byte_size,  
    unsigned int _Bits_per_scalar_element,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
texture(
    const texture& _Src,  
    const Concurrency::accelerator_view& _Acc_view);

 
texture(
    texture&& _Other);

 
texture(
    const Concurrency::extent<_Rank>& _Ext,   
    unsigned int _Bits_per_scalar_element,   
    const Concurrency::accelerator_view& _Av);

 
texture(
    const texture& _Src);
```  
  
### <a name="parameters"></a>Parametry  
 `_Acc_view`  
 [Accelerator_view](accelerator-view-class.md) , który określa lokalizację tekstury.  
  
 `_Av`  
 [Accelerator_view](accelerator-view-class.md) , który określa lokalizację tekstury.  
  
 `_Associated_av`  
 Accelerator_view określająca preferowany celu kopiuje do lub z tym tekstury.  
  
 `_Bits_per_scalar_element`  
 Liczba bitów na każdy element skalarne w źródłowym typie skalarne tekstury. Ogólnie rzecz biorąc obsługiwana wartość to 8, 16 i 32 oraz 64. Jeśli określono 0, liczba bitów jest taki sam jak źródłowy scalar_type. 64 jest prawidłowa tylko dla tekstury oparte o podwójnej precyzji.  
  
 `_Ext`  
 Zakres w każdym wymiarów tekstury.  
  
 `_E0`  
 Najbardziej znaczący składnik tekstury.  
  
 `_E1`  
 Składnik dalej do większość — znaczące tekstury.  
  
 `_E2`  
 Najmniej znaczący składnik zakres tekstury.  
  
 `_Input_iterator`  
 Typ wejściowy interator.  
  
 `_Mipmap_levels`  
 Liczba poziomów mipmap w podstawowej tekstury. Jeśli określono wartość 0, tekstury będzie miał pełny zakres poziomy mipmap dół najmniejszy rozmiar dla określonego zakresu.  
  
 `_Rank`  
 Ranga tego zakresu.  
  
 `_Source`  
 Wskaźnik do buforu hosta.  
  
 `_Src`  
 Aby tekstury do skopiowania.  
  
 `_Src_byte_size`  
 Liczba bajtów w buforze źródła.  
  
 `_Src_first`  
 Iterator początek w kontenerze źródła.  
  
 `_Src_last`  
 Końcowy iteratora w kontenerze źródła.  
  
 `_Other`  
 Inne źródła danych.  
  
 `_Rank`  
 Ranga sekcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Concurrency::graphics, przestrzeń nazw](concurrency-graphics-namespace.md)
