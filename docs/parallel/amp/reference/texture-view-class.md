---
title: texture_view — Klasa
ms.date: 11/04/2016
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
ms.assetid: 6ec2e289-1626-4727-9592-07981cf1d27d
ms.openlocfilehash: 0f2b627afa216f03592fe913afece1a80f5bd5a6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351524"
---
# <a name="textureview-class"></a>texture_view — Klasa

Zapewnia dostęp do odczytu i zapisu do tekstury. `texture_view` należy używać tylko do odczytu tekstur, których typ wartości to `int`, `unsigned int`, lub `float` , które mają domyślne 32-bitowym bpse. Do odczytywania innych formatów tekstury, użyj `texture_view<const value_type, _Rank>`.

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

*value_type*<br/>
Typ elementów w agregacji tekstury.

*_Rank*<br/>
Ranga `texture_view`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`value_type`|Typ elementów w agregacjach tekstury.|
|`coordinates_type`|Typ współrzędnej używanej do określania teksela w `texture_view`— czyli `short_vector` , ma taką samą rangę, co skojarzona Tekstura, który ma typ wartości `float`.|
|`gather_return_type`|Zwracany typ używany do zbierania operacji — czyli pozycja 4 `short_vector` , zawierająca cztery składniki jednolitego koloru zebrane z czterech próbkowanych wartości teksel.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[texture_view konstruktora](#ctor)|Przeciążone. Konstruuje `texture_view` wystąpienia.|
|[~ texture_view — destruktor](#ctor)|Niszczy `texture_view` wystąpienia.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[gather_alpha](#gather_alpha)|Przeciążone. Pobiera próbki tekstury na określonych współrzędnych przy użyciu określonej konfiguracji pobierania próbek i zwraca składniki alfa (w) z czterech próbkowanych tekseli.|
|[gather_blue](#gather_blue)|Przeciążone. Pobiera próbki tekstury na określonych współrzędnych przy użyciu określonej konfiguracji pobierania próbek i zwraca składniki niebieskie (z) z czterech próbkowanych tekseli.|
|[gather_green](#gather_green)|Przeciążone. Pobiera próbki tekstury na określonych współrzędnych przy użyciu określonej konfiguracji pobierania próbek i zwraca składniki zielone (y) z czterech próbkowanych tekseli.|
|[gather_red](#gather_red)|Przeciążone. Pobiera próbki tekstury na określonych współrzędnych przy użyciu określonej konfiguracji pobierania próbek i zwraca składniki czerwone (x) z czterech próbkowanych tekseli.|
|[get](#get)|Przeciążone. Pobiera wartość elementu według indeksu.|
|[sample](#sample)|Przeciążone. Pobiera próbki tekstury na określonych współrzędnych i poziomie szczegółowości przy użyciu określonej konfiguracji pobierania próbek.|
|[set](#set)|Ustawia wartość elementu według indeksu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[operator()](#operator_call)|Przeciążone. Pobiera wartość elementu według indeksu.|
|[Operator\[\]](#operator_at)|Przeciążone. Pobiera wartość elementu według indeksu.|
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

*_Src*<br/>
[1, 2] Konstruktor `texture` na którym zapisywalny `texture_view` zostanie utworzony.

[3, 4] Konstruktor `texture` na którym bez możliwości zapisu `texture_view` zostanie utworzony.

*_Inne*<br/>
[5] Konstruktor kopiujący zapisywalnego źródła `texture_view`.

[6, 7] Kopiowanie konstruktora bez możliwości zapisu źródła `texture_view`.

*_Mipmap_level*<br/>
Specyficzny poziom mipmappingu w źródle `texture` którym ten zapisywalny `texture_view` wiąże. Wartość domyślna to 0, co oznacza najwyższego poziomu (najbardziej szczegółowy) poziom mip.

*_Most_detailed_mip*<br/>
Najwyższego poziomu (najbardziej szczegółowy) poziom mip dla widoku, odnoszący się do określonego `texture_view` obiektu.

*_Mip_levels*<br/>
Liczba poziomów mipmappingu dostępnych `texture_view`.

##  <a name="gather_red"></a> gather_red

Pobiera próbki tekstury na określonych współrzędnych przy użyciu określonej konfiguracji pobierania próbek i zwraca składniki czerwone (x) z czterech próbkowanych tekseli.

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

*_Address_mode*<br/>
Tryb adresu do użycia do przykładu `texture_view`. Tryb adresu jest taka sama dla wszystkich wymiarów.

*_Sampler*<br/>
Konfiguracja próbnika do użycia do przykładu `texture_view`.

*_Coord*<br/>
Współrzędne miejsca pobierania próbki. Ułamkowe wartości współrzędnych są używane do interpolacji między przykładowymi tekselami.

### <a name="return-value"></a>Wartość zwracana

Pozycja 4 wektora krótkiego, zawierająca składnik czerwony (x) 4 próbkowanych wartości teksel.

##  <a name="gather_green"></a> gather_green

Pobiera próbki tekstury na określonych współrzędnych przy użyciu określonej konfiguracji pobierania próbek i zwraca składniki zielone (y) z czterech próbkowanych tekseli.

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

*_Address_mode*<br/>
Tryb adresu do użycia do przykładu `texture_view`. Tryb adresu jest taka sama dla wszystkich wymiarów.

*_Sampler*<br/>
Konfiguracja próbnika do użycia do przykładu `texture_view`.

*_Coord*<br/>
Współrzędne miejsca pobierania próbki. Ułamkowe wartości współrzędnych są używane do interpolacji między przykładowymi tekselami.

### <a name="return-value"></a>Wartość zwracana

Pozycja 4 wektora krótkiego, zawierająca składnik zielony (y) 4 próbkowanych wartości teksel.

##  <a name="gather_blue"></a> gather_blue

Pobiera próbki tekstury na określonych współrzędnych przy użyciu określonej konfiguracji pobierania próbek i zwraca składniki niebieskie (z) z czterech próbkowanych tekseli.

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

*_Address_mode*<br/>
Tryb adresu do użycia do przykładu `texture_view`. Tryb adresu jest taka sama dla wszystkich wymiarów.

*_Sampler*<br/>
Konfiguracja próbnika do użycia do przykładu `texture_view`.

*_Coord*<br/>
Współrzędne miejsca pobierania próbki. Ułamkowe wartości współrzędnych są używane do interpolacji między przykładowymi tekselami.

### <a name="return-value"></a>Wartość zwracana

Pozycja 4 wektora krótkiego, zawierająca składnik czerwony (x) 4 próbkowanych wartości teksel.

##  <a name="gather_alpha"></a> gather_alpha

Pobiera próbki tekstury na określonych współrzędnych przy użyciu określonej konfiguracji pobierania próbek i zwraca składniki alfa (w) z czterech próbkowanych tekseli.

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

*_Address_mode*<br/>
Tryb adresu do użycia do przykładu `texture_view`. Tryb adresu jest taka sama dla wszystkich wymiarów.

*_Sampler*<br/>
Konfiguracja próbnika do użycia do przykładu `texture_view`.

*_Coord*<br/>
Współrzędne miejsca pobierania próbki. Ułamkowe wartości współrzędnych są używane do interpolacji między przykładowymi tekselami.

### <a name="return-value"></a>Wartość zwracana

Pozycja 4 wektora krótkiego zawierający alfa (w) składnik 4 próbkowanych wartości teksel.

##  <a name="get"></a> Pobierz

Pobiera wartość elementu wskazywanego przez określony indeks.

```
const value_type get(
    const index<_Rank>& _Index) const restrict(amp);

value_type get(
    const index<_Rank>& _Index,
    unsigned int _Mip_level = 0) const restrict(amp);
```

### <a name="parameters"></a>Parametry

*Parametr _Index*<br/>
Indeks elementu do pobrania, prawdopodobnie wielowymiarowy.

*_Mip_level*<br/>
Poziom mipmappingu, z którego możemy uzyskać wartość. Wartość domyślna 0 reprezentuje najbardziej szczegółowy poziom mipmappingu.

### <a name="return-value"></a>Wartość zwracana

Wartość elementu.

##  <a name="operator_eq"></a> operator =

Przypisuje widok samej struktury, jak określony `texture_view` tej `texture_view` wystąpienia.

```
texture_view<value_type, _Rank>& operator= (// [1] copy constructor
    const texture_view<value_type, _Rank>& _Other) restrict(amp, cpu);

texture_view<const value_type, _Rank>& operator= (// [2] copy constructor
    const texture_view<value_type, _Rank>& _Other) restrict(cpu);

texture_view<const value_type, _Rank>& operator= (// [3] copy constructor
    const texture_view<const value_type, _Rank>& _Other) restrict(amp, cpu);
```

### <a name="parameters"></a>Parametry

*_Inne*<br/>
[1, 2] Konstruktor kopiujący A zapisywalny `texture_view` obiektu.

[3] Konstruktor kopiujący A bez możliwości zapisu `texture_view` obiektu.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `texture_view` wystąpienia.

##  <a name="operator_at"></a> Operator]

Zwraca wartość elementu według indeksu.

```
const value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

const value_type operator[] (int _I0) const restrict(amp);

value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

value_type operator[] (int _I0) const restrict(amp);
```

### <a name="parameters"></a>Parametry

*Parametr _Index*<br/>
Indeks, prawdopodobnie wielowymiarowy.

*_I0*<br/>
Indeks jednowymiarowy.

### <a name="return-value"></a>Wartość zwracana

Wartość elementu indeksowana przez `_Index`.

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

*Parametr _Index*<br/>
Indeks, prawdopodobnie wielowymiarowy.

*_I0*<br/>
Najbardziej znaczący składnik indeksu.

*_I1*<br/>
Dalej do najbardziej znaczący składnik indeksu.

*_I2*<br/>
Najmniej znaczący składnik indeksu.

### <a name="return-value"></a>Wartość zwracana

Wartość elementu indeksowana przez `_Index`.

##  <a name="sample"></a> Próbki

Pobiera próbki tekstury na określonych współrzędnych i poziomie szczegółowości przy użyciu określonej konfiguracji pobierania próbek.

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

*_Filter_mode*<br/>
Tryb filtru do użycia do próby texture_view. Tryb filtru jest taki sam dla minimalizacji, maksymalizacji i filtrów mipmap.

*_Address_mode*<br/>
Tryb adresu do użycia do próby texture_view. Tryb adresu jest taka sama dla wszystkich wymiarów.

*_Sampler*<br/>
Konfiguracja próbnika do użycia podczas próbkowania texture_view.

*_Coord*<br/>
Współrzędne miejsca pobierania próbki. Ułamkowe wartości współrzędnych są używane do interpolacji między wartościami tekseli.

*_Level_of_detail*<br/>
Wartość określa poziom mipmappingu do próbkowania. Ułamkowe wartości są używane do interpolacji między dwoma poziomami mipmap. Domyślny poziom szczegółowości to 0, co oznacza najbardziej szczegółowy poziom mip.

### <a name="return-value"></a>Wartość zwracana

Interpolowana wartość przykładowa.

##  <a name="set"></a> Zestaw

Ustawia wartość elementu pod określonym indeksem na określoną wartość.

```
void set(
    const index<_Rank>& _Index,
    const value_type& value) const restrict(amp);
```

### <a name="parameters"></a>Parametry

*Parametr _Index*<br/>
Indeks elementu, aby ustawić, prawdopodobnie wielowymiarowy.

*value*<br/>
Wartość do ustawienia elementu.

##  <a name="value_type"></a> value_type

Typ wartości elementów texture_view.

```
typedef typename const value_type value_type;
```

## <a name="see-also"></a>Zobacz także

[Concurrency::graphics, przestrzeń nazw](concurrency-graphics-namespace.md)
