---
title: texture_view — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- texture_view
- AMP_GRAPHICS/texture_view
- AMP_GRAPHICS/Concurrency::graphics::texture_view::texture_view
- AMP_GRAPHICS/Concurrency::graphics::texture_view::gather_alpha
- AMP_GRAPHICS/Concurrency::graphics::texture_view::gather_blue
- AMP_GRAPHICS/Concurrency::graphics::texture_view::gather_green
- AMP_GRAPHICS/Concurrency::graphics::texture_view::gather_red
- AMP_GRAPHICS/Concurrency::graphics::texture_view::get
- AMP_GRAPHICS/Concurrency::graphics::texture_view::sample
- AMP_GRAPHICS/Concurrency::graphics::texture_view::set
- AMP_GRAPHICS/Concurrency::graphics::texture_view::value_type
dev_langs:
- C++
ms.assetid: 6ec2e289-1626-4727-9592-07981cf1d27d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3db02d9cafb87c0f173546687ad01390e09b9f68
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="textureview-class"></a>texture_view — Klasa
Zapewnia dostęp do odczytu i zapisu do tekstury. `texture_view` może służyć tylko do odczytu tekstury, którego typ wartości jest `int`, `unsigned int`, lub `float` , która ma domyślne bpse 32-bitowych. Aby odczytać inne formaty tekstury, należy użyć `texture_view<const value_type, _Rank>`.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename value_type,int _Rank>  
class texture_view;  
 
template<typename value_type, int _Rank>  
class texture_view 
   : public details::_Texture_base<value_type, _Rank>;  
 
template<typename value_type, int _Rank>  
class texture_view<const value_type, _Rank> 
   : public details::_Texture_base<value_type, _Rank>;  
```  
  
#### <a name="parameters"></a>Parametry  
 `value_type`  
 Typ elementów w sposób zagregowany tekstury.  
  
 `_Rank`  
 Rangę `texture_view`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`value_type`|Typ elementów w agregacji tekstury.|  
|`coordinates_type`|Typ współrzędnych używany do określenia teksela w `texture_view`— to znaczy `short_vector` mający taką samą rangę jako tekstury skojarzony, który ma typ wartości `float`.|  
|`gather_return_type`|Zwracany typ używany do zebrania operacje — to znaczy rangę 4 `short_vector` czy blokad czterech składników jednorodnego koloru zbierane z czterech wartości teksela próbkowane.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[texture_view — Konstruktor](#ctor)|Przeciążone. Konstruuje `texture_view` wystąpienia.|  
|[~ texture_view — destruktor](#ctor)|Niszczy `texture_view` wystąpienia.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[gather_alpha](#gather_alpha)|Przeciążone. Przykłady w określonych współrzędnych tekstury za pomocą konfiguracji określonego próbkowania i zwraca składniki alfa (w) cztery tekseli próbki.|  
|[gather_blue](#gather_blue)|Przeciążone. Przykłady w określonych współrzędnych tekstury za pomocą konfiguracji określonego próbkowania i zwraca składniki cztery tekseli próbki niebieski (z).|  
|[gather_green](#gather_green)|Przeciążone. Przykłady w określonych współrzędnych tekstury za pomocą konfiguracji określonego próbkowania i zwraca składniki cztery tekseli próbki zielony (y).|  
|[gather_red](#gather_red)|Przeciążone. Przykłady w określonych współrzędnych tekstury za pomocą konfiguracji określonego próbkowania i zwraca składniki cztery tekseli próbki czerwony (x).|  
|[get](#get)|Przeciążone. Pobiera wartość elementu według indeksu.|  
|[próbki](#sample)|Przeciążone. Przykłady na poziomie szczegółowości i określonych współrzędnych tekstury za pomocą próbkowania określonej konfiguracji.|  
|[set](#set)|Ustawia wartość elementu według indeksu.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[operator()](#operator_call)|Przeciążone. Pobiera wartość elementu według indeksu.|  
|[Operator]](#operator_at)|Przeciążone. Pobiera wartość elementu według indeksu.|  
|[operator=](#operator_eq)|Przeciążone. Operator przypisania.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[value_type](#value_type)|Typ wartości elementów `texture_view`.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `_Texture_base`  
  
 `texture_view`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** amp_graphics.h  
  
 **Namespace:** concurrency::graphics  
  
##  <a name="dtor"></a> ~ texture_view 

 Niszczy `texture_view` wystąpienia.  
  
```  
~texture_view() restrict(amp, cpu);
```  
  
##  <a name="ctor"></a> texture_view 

 Konstruuje `texture_view` wystąpienia.  
  
```  
texture_view(// [1] constructor  
    texture<value_type, _Rank>& _Src) restrict(amp);

 
texture_view(// [2] constructor  
    texture<value_type, _Rank>& _Src,  
    unsigned int _Mipmap_level = 0) restrict(cpu);

 
texture_view(// [3] constructor  
    const texture<value_type, _Rank>& _Src) restrict(amp);

 
texture_view(// [4] constructor  
    const texture<value_type, _Rank>& _Src,  
    unsigned int _Most_detailed_mip,  
    unsigned int _Mip_levels) restrict(cpu);

 
texture_view(// [5] copy constructor  
    const texture_view<value_type, _Rank>& _Other) restrict(amp, cpu);

 
texture_view(// [6] copy constructor  
    const texture_view<const value_type, _Rank>& _Other) restrict(amp, cpu);

 
texture_view(// [7] copy constructor  
    const texture_view<const value_type, _Rank>& _Other,  
    unsigned int _Most_detailed_mip,  
    unsigned int _Mip_levels) restrict(cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_Src`  
 [1, 2] Konstruktor  
 `texture` Na którym zapisywalny `texture_view` jest tworzony.  
  
 [3, 4] Konstruktor  
 `texture` Na którym bez możliwości zapisu `texture_view` jest tworzony.  
  
 `_Other`  
 [5] Copy Constructor  
 Źródło zapisywalny `texture_view`.  
  
 [6, 7] Copy Constructor  
 Bez możliwości zapisu źródła `texture_view`.  
  
 `_Mipmap_level`  
 Poziom mipmap określonego w źródle `texture` to tym zapisywalny `texture_view` wiąże. Wartość domyślna to 0, który reprezentuje poziom mipmapy najwyższego poziomu (najbardziej szczegółowy).  
  
 `_Most_detailed_mip`  
 Najwyższego poziomu (najbardziej szczegółowy) MCI poziomu widoku względem określonego dla `texture_view` obiektu.  
  
 `_Mip_levels`  
 Liczba poziomów mipmap dostępny za pośrednictwem `texture_view`.  
  
##  <a name="gather_red"></a> gather_red 

 Przykłady w określonych współrzędnych tekstury za pomocą konfiguracji określonego próbkowania i zwraca składniki cztery tekseli próbki czerwony (x).  
  
```  
const gather_return_type gather_red(
    const sampler& _Sampler,  
    const coordinates_type& _Coord) const restrict(amp);

 
template<
    address_mode _Address_mode = address_clamp  
>  
const gather_return_type gather_red(
    const coordinates_type& _Coord) const restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Address_mode`  
 Tryb adres, aby używać próby `texture_view`. Tryb adres jest taka sama dla wszystkich wymiarów.  
  
 `_Sampler`  
 Przykłady konfigurację, aby użyć na przykład `texture_view`.  
  
 `_Coord`  
 Współrzędne podjęcie próbki z. Współrzędna ułamkowa służą do interpolowania tekseli próbki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Ranga 4 vector krótkie, zawierający składnika czerwony (x), 4 próbkowany teksela wartości.  
  
##  <a name="gather_green"></a> gather_green 

 Przykłady w określonych współrzędnych tekstury za pomocą konfiguracji określonego próbkowania i zwraca składniki cztery tekseli próbki zielony (y).  
  
```  
const gather_return_type gather_green(
    const sampler& _Sampler,  
    const coordinates_type& _Coord) const restrict(amp);

 
template<
    address_mode _Address_mode = address_clamp  
>  
const gather_return_type gather_green(
    const coordinates_type& _Coord) const restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Address_mode`  
 Tryb adres, aby używać próby `texture_view`. Tryb adres jest taka sama dla wszystkich wymiarów.  
  
 `_Sampler`  
 Przykłady konfigurację, aby użyć na przykład `texture_view`.  
  
 `_Coord`  
 Współrzędne podjęcie próbki z. Współrzędna ułamkowa służą do interpolowania tekseli próbki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Ranga 4 vector krótkie, zawierający składnika zielony (y), 4 próbkowany teksela wartości.  
  
##  <a name="gather_blue"></a> gather_blue 

 Przykłady w określonych współrzędnych tekstury za pomocą konfiguracji określonego próbkowania i zwraca składniki cztery tekseli próbki niebieski (z).  
  
```  
const gather_return_type gather_blue(
    const sampler& _Sampler,  
    const coordinates_type& _Coord) const restrict(amp);

 
template<
    address_mode _Address_mode = address_clamp  
>  
const gather_return_type gather_blue(
    const coordinates_type& _Coord) const restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Address_mode`  
 Tryb adres, aby używać próby `texture_view`. Tryb adres jest taka sama dla wszystkich wymiarów.  
  
 `_Sampler`  
 Przykłady konfigurację, aby użyć na przykład `texture_view`.  
  
 `_Coord`  
 Współrzędne podjęcie próbki z. Współrzędna ułamkowa służą do interpolowania tekseli próbki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Ranga 4 vector krótkie, zawierający składnika czerwony (x), 4 próbkowany teksela wartości.  
  
##  <a name="gather_alpha"></a> gather_alpha 

 Przykłady w określonych współrzędnych tekstury za pomocą konfiguracji określonego próbkowania i zwraca składniki alfa (w) cztery tekseli próbki.  
  
```  
const gather_return_type gather_alpha(
    const sampler& _Sampler,  
    const coordinates_type& _Coord) const restrict(amp);

 
template<
    address_mode _Address_mode = address_clamp  
>  
const gather_return_type gather_alpha(
    const coordinates_type& _Coord) const restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Address_mode`  
 Tryb adres, aby używać próby `texture_view`. Tryb adres jest taka sama dla wszystkich wymiarów.  
  
 `_Sampler`  
 Przykłady konfigurację, aby użyć na przykład `texture_view`.  
  
 `_Coord`  
 Współrzędne podjęcie próbki z. Współrzędna ułamkowa służą do interpolowania tekseli próbki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Ranga 4 krótkich vector zawierający alfa (w) składnik 4 próbkowany teksela wartości.  
  
##  <a name="get"></a> Pobierz 

 Pobiera wartość elementu pod określonym indeksem.  
  
```  
const value_type get(
    const index<_Rank>& _Index) const restrict(amp);

 
value_type get(
    const index<_Rank>& _Index,  
    unsigned int _Mip_level = 0) const restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Index`  
 Indeks elementu do pobrania, prawdopodobnie wielowymiarowych.  
  
 `_Mip_level`  
 Poziomu mipmapowania, z którego możemy pobrać wartość. Wartość domyślna 0 reprezentuje najbardziej szczegółowy poziomu mipmapowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość elementu.  
  
##  <a name="operator_eq"></a> operator = 

 Przypisuje widoku tej samej tekstury jako określony `texture_view` tej `texture_view` wystąpienia.  
  
```  
texture_view<value_type, _Rank>& operator= (// [1] copy constructor  
    const texture_view<value_type, _Rank>& _Other) restrict(amp, cpu);

 
texture_view<const value_type, _Rank>& operator= (// [2] copy constructor  
    const texture_view<value_type, _Rank>& _Other) restrict(cpu);

 
texture_view<const value_type, _Rank>& operator= (// [3] copy constructor  
    const texture_view<const value_type, _Rank>& _Other) restrict(amp, cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 [1, 2] Konstruktor kopiujący  
 Z możliwością zapisu `texture_view` obiektu.  
  
 [3] Copy Constructor  
 Bez możliwości zapisu `texture_view` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do tego `texture_view` wystąpienia.  
  
##  <a name="operator_at"></a> Operator] 

 Zwraca wartość elementu według indeksu.  
  
```  
const value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

 
const value_type operator[] (int _I0) const restrict(amp);

 
value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

 
value_type operator[] (int _I0) const restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Index`  
 Indeks prawdopodobnie wielowymiarowych.  
  
 `_I0`  
 Indeks jednowymiarowa.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość elementu indeksowane według `_Index`.  
  
##  <a name="operator_call"></a> Operator() 

 Zwraca wartość elementu według indeksu.  
  
```  
const value_type operator() (
    const index<_Rank>& _Index) const restrict(amp);

 
const value_type operator() (
    int _I0) const restrict(amp);

 
const value_type operator() (
    int _I0,   int _I1) const restrict(amp);

 
const value_type operator() (
    int _I0,  
    int _I1,  
    int _I2) const restrict(amp);

 
value_type operator() (
    const index<_Rank>& _Index) const restrict(amp);

 
value_type operator() (
    int _I0) const restrict(amp);

 
value_type operator() (
    int _I0,  
    int _I1) const restrict(amp);

 
value_type operator() (
    int _I0,  
    int _I1,  
    int _I2) const restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Index`  
 Indeks prawdopodobnie wielowymiarowych.  
  
 `_I0`  
 Najbardziej znaczące składnik indeksu.  
  
 `_I1`  
 Składnik dalej do większość — znaczące indeksu.  
  
 `_I2`  
 Najmniej znaczący składnik indeksu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość elementu indeksowane według `_Index`.  
  
##  <a name="sample"></a> próbki 

 Przykłady na poziomie szczegółowości i określonych współrzędnych tekstury za pomocą próbkowania określonej konfiguracji.  
  
```  
value_type sample(
    const sampler& _Sampler,  
    const coordinates_type& _Coord,  
    float _Level_of_detail = 0.0f) const restrict(amp);

 
template<
    filter_mode _Filter_mode = filter_linear,  
    address_mode _Address_mode = address_clamp  
>  
value_type sample(
    const coordinates_type& _Coord,  
    float _Level_of_detail = 0.0f) const restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Filter_mode`  
 Tryb filtrowania służące do próbkowania texture_view. Tryb filtru jest taki sam dla minimalizacja maksymalizacyjne i mipmap filtrów.  
  
 `_Address_mode`  
 Tryb adresu na potrzeby próbkowania texture_view. Tryb adres jest taka sama dla wszystkich wymiarów.  
  
 `_Sampler`  
 Przykłady konfiguracji na potrzeby próbkowania texture_view.  
  
 `_Coord`  
 Współrzędne podjęcie próbki z. Współrzędna ułamkowa służą do interpolowania teksela wartości.  
  
 `_Level_of_detail`  
 Wartość określa poziomu mipmapowania do próbkowania. Ułamkowa są używane do interpolowania dwa poziomy mipmap. Domyślny poziom szczegółowości jest 0, co stanowi najbardziej szczegółowy poziom mipmapy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość próbki interpolowanym.  
  
##  <a name="set"></a> zestaw 

 Ustawia wartość elementu pod określonym indeksem z podaną wartością.  
  
```  
void set(
    const index<_Rank>& _Index,  
    const value_type& value) const restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Index`  
 Indeks elementu można ustawić, prawdopodobnie wielowymiarowych.  
  
 `value`  
 Wartość do ustawienia elementu.  
  
##  <a name="value_type"></a> value_type 

 Typ wartości elementów texture_view.  
  
```  
typedef typename const value_type value_type;  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Concurrency::graphics, przestrzeń nazw](concurrency-graphics-namespace.md)
