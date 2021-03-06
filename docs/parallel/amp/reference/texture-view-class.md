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
ms.openlocfilehash: 1fa21f2a5a5c1d004fc23d70b686d7e45bbcac81
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215910"
---
# <a name="texture_view-class"></a>texture_view — Klasa

Zapewnia dostęp do odczytu i zapisu do tekstury. `texture_view`można go użyć tylko do odczytu tekstur, których typem wartości jest **`int`** , **`unsigned int`** , lub **`float`** , które mają domyślnie 32-bitowy BPSE. Aby odczytać inne formaty tekstury, użyj `texture_view<const value_type, _Rank>` .

## <a name="syntax"></a>Składnia

```cpp
template<typename value_type,int _Rank>
class texture_view;

template<typename value_type, int _Rank>
class texture_view
   : public details::_Texture_base<value_type, _Rank>;

template<typename value_type, int _Rank>
class texture_view<const value_type, _Rank>
   : public details::_Texture_base<value_type, _Rank>;
```

### <a name="parameters"></a>Parametry

*value_type*<br/>
Typ elementów w agregacji tekstury.

*_Rank*<br/>
Ranga `texture_view` .

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`value_type`|Typ elementów w agregacji tekstury.|
|`coordinates_type`|Typ współrzędnej używanej do określenia Texel w elemencie `texture_view` — czyli, `short_vector` który ma taką samą rangę, jak skojarzona tekstura, która ma typ wartości **`float`** .|
|`gather_return_type`|Zwracany typ używany do zbierania operacji — to znaczy ranga 4, `short_vector` która przechowuje cztery jednorodne składniki kolorów zebrane z czterech Texel wartości próbkowania.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Konstruktor texture_view](#ctor)|Przeciążone. Konstruuje `texture_view` wystąpienie.|
|[~ texture_view destruktor](#ctor)|Niszczy `texture_view` wystąpienie.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[gather_alpha](#gather_alpha)|Przeciążone. Próbki tekstury na określonych współrzędnych przy użyciu określonej konfiguracji pobierania próbek i zwraca składniki alfa (w) z czterech próbkowanych tekseli.|
|[gather_blue](#gather_blue)|Przeciążone. Próbki tekstury na określonych współrzędnych przy użyciu określonej konfiguracji pobierania próbek i zwraca składniki niebieskie (z) z czterech próbkowanych tekseli.|
|[gather_green](#gather_green)|Przeciążone. Próbki tekstury na określonych współrzędnych przy użyciu określonej konfiguracji pobierania próbek i zwraca składniki zielone (y) z czterech próbkowanych tekseli.|
|[gather_red](#gather_red)|Przeciążone. Próbkuje teksturę na określonych współrzędnych przy użyciu określonej konfiguracji pobierania próbek i zwraca składniki czerwone (x) z czterech próbkowanych tekseli.|
|[Pobierz](#get)|Przeciążone. Pobiera wartość elementu według indeksu.|
|[Northwind](#sample)|Przeciążone. Próbki tekstury na określonych współrzędnych i poziomie szczegółowości przy użyciu określonej konfiguracji próbkowania.|
|[zbiór](#set)|Ustawia wartość elementu według indeksu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[operator ()](#operator_call)|Przeciążone. Pobiera wartość elementu według indeksu.|
|[operator\[\]](#operator_at)|Przeciążone. Pobiera wartość elementu według indeksu.|
|[operator =](#operator_eq)|Przeciążone. Operator przypisania.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[value_type](#value_type)|Typ wartości elementów `texture_view` .|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`_Texture_base`

`texture_view`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp_graphics. h

**Przestrzeń nazw:** concurrency:: Graphics

## <a name="texture_view"></a><a name="dtor"></a>~ texture_view

Niszczy `texture_view` wystąpienie.

```cpp
~texture_view() restrict(amp, cpu);
```

## <a name="texture_view"></a><a name="ctor"></a>texture_view

Konstruuje `texture_view` wystąpienie.

```cpp
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
[1, 2] Konstruktor, `texture` w którym `texture_view` jest tworzony zapisywalny.

[3, 4] Konstruktor, `texture` w którym jest tworzony nie zapisywalny `texture_view` .

*_Other*<br/>
[5] Kopiuj Konstruktor do zapisywalnego źródła `texture_view` .

[6, 7] Kopiuj Konstruktor do źródła bez możliwości zapisu `texture_view` .

*_Mipmap_level*<br/>
Określony poziom mipmappingu na źródle `texture` , z którym jest powiązane to zapisywalne `texture_view` . Wartość domyślna to 0, co oznacza najwyższy poziom (najbardziej szczegółowy) poziom MIP.

*_Most_detailed_mip*<br/>
Najwyższy poziom (najbardziej szczegółowy) poziom MIP dla widoku względem określonego `texture_view` obiektu.

*_Mip_levels*<br/>
Liczba poziomów mipmappingu dostępnych za pomocą `texture_view` .

## <a name="gather_red"></a><a name="gather_red"></a>gather_red

Próbkuje teksturę na określonych współrzędnych przy użyciu określonej konfiguracji pobierania próbek i zwraca składniki czerwone (x) z czterech próbkowanych tekseli.

```cpp
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
Tryb adresu, który ma być używany do próbkowania `texture_view` . Tryb adresu jest taki sam dla wszystkich wymiarów.

*_Sampler*<br/>
Konfiguracja próbnika do użycia do próbkowania `texture_view` .

*_Coord*<br/>
Współrzędne, z których ma zostać pobrana próba. Wartości współrzędnych ułamkowych są używane do interpolacji między przykładowym tekseli.

### <a name="return-value"></a>Wartość zwracana

Krótka wektor rangi 4 zawierający składnik czerwony (x) z 4 próbkowanych wartości Texel.

## <a name="gather_green"></a><a name="gather_green"></a>gather_green

Próbki tekstury na określonych współrzędnych przy użyciu określonej konfiguracji pobierania próbek i zwraca składniki zielone (y) z czterech próbkowanych tekseli.

```cpp
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
Tryb adresu, który ma być używany do próbkowania `texture_view` . Tryb adresu jest taki sam dla wszystkich wymiarów.

*_Sampler*<br/>
Konfiguracja próbnika do użycia do próbkowania `texture_view` .

*_Coord*<br/>
Współrzędne, z których ma zostać pobrana próba. Wartości współrzędnych ułamkowych są używane do interpolacji między przykładowym tekseli.

### <a name="return-value"></a>Wartość zwracana

Krótka wektor rangi 4 zawierający zielony składnik (y) wartości Texel 4 próbki.

## <a name="gather_blue"></a><a name="gather_blue"></a>gather_blue

Próbki tekstury na określonych współrzędnych przy użyciu określonej konfiguracji pobierania próbek i zwraca składniki niebieskie (z) z czterech próbkowanych tekseli.

```cpp
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
Tryb adresu, który ma być używany do próbkowania `texture_view` . Tryb adresu jest taki sam dla wszystkich wymiarów.

*_Sampler*<br/>
Konfiguracja próbnika do użycia do próbkowania `texture_view` .

*_Coord*<br/>
Współrzędne, z których ma zostać pobrana próba. Wartości współrzędnych ułamkowych są używane do interpolacji między przykładowym tekseli.

### <a name="return-value"></a>Wartość zwracana

Krótka wektor rangi 4 zawierający składnik czerwony (x) z 4 próbkowanych wartości Texel.

## <a name="gather_alpha"></a><a name="gather_alpha"></a>gather_alpha

Próbki tekstury na określonych współrzędnych przy użyciu określonej konfiguracji pobierania próbek i zwraca składniki alfa (w) z czterech próbkowanych tekseli.

```cpp
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
Tryb adresu, który ma być używany do próbkowania `texture_view` . Tryb adresu jest taki sam dla wszystkich wymiarów.

*_Sampler*<br/>
Konfiguracja próbnika do użycia do próbkowania `texture_view` .

*_Coord*<br/>
Współrzędne, z których ma zostać pobrana próba. Wartości współrzędnych ułamkowych są używane do interpolacji między przykładowym tekseli.

### <a name="return-value"></a>Wartość zwracana

Krótka wektor rangi 4 zawierający składnik alfa (w) z 4 próbkowanych wartości Texel.

## <a name="get"></a><a name="get"></a>Pobierz

Pobiera wartość elementu w określonym indeksie.

```cpp
const value_type get(
    const index<_Rank>& _Index) const restrict(amp);

value_type get(
    const index<_Rank>& _Index,
    unsigned int _Mip_level = 0) const restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Indeks elementu, który ma zostać pobrany, prawdopodobnie wielowymiarowy.

*_Mip_level*<br/>
Poziom mipmappingu, z którego ma zostać pobrana wartość. Wartość domyślna 0 reprezentuje najbardziej szczegółowy poziom mipmappingu.

### <a name="return-value"></a>Wartość zwracana

Wartość elementu.

## <a name="operator"></a><a name="operator_eq"></a>operator =

Przypisuje widok takiej samej tekstury jak określony `texture_view` dla tego `texture_view` wystąpienia.

```cpp
texture_view<value_type, _Rank>& operator= (// [1] copy constructor
    const texture_view<value_type, _Rank>& _Other) restrict(amp, cpu);

texture_view<const value_type, _Rank>& operator= (// [2] copy constructor
    const texture_view<value_type, _Rank>& _Other) restrict(cpu);

texture_view<const value_type, _Rank>& operator= (// [3] copy constructor
    const texture_view<const value_type, _Rank>& _Other) restrict(amp, cpu);
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
[1, 2] Kopiuj Konstruktor jako zapisywalny `texture_view` obiekt.

[3] Skopiuj Konstruktor do obiektu, który nie jest zapisywalny `texture_view` .

### <a name="return-value"></a>Wartość zwracana

Odwołanie do tego `texture_view` wystąpienia.

## <a name="operator"></a><a name="operator_at"></a>operator []

Zwraca wartość elementu według indeksu.

```cpp
const value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

const value_type operator[] (int _I0) const restrict(amp);

value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

value_type operator[] (int _I0) const restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Indeks, prawdopodobnie wielowymiarowy.

*_I0*<br/>
Indeks jednowymiarowy.

### <a name="return-value"></a>Wartość zwracana

Wartość elementu indeksowanego przez `_Index` .

## <a name="operator"></a><a name="operator_call"></a>operator ()

Zwraca wartość elementu według indeksu.

```cpp
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

*_Index*<br/>
Indeks, prawdopodobnie wielowymiarowy.

*_I0*<br/>
Najbardziej znaczący składnik indeksu.

*_I1*<br/>
Najbardziej znaczący składnik indeksu.

*_I2*<br/>
Najmniej znaczący składnik indeksu.

### <a name="return-value"></a>Wartość zwracana

Wartość elementu indeksowanego przez `_Index` .

## <a name="sample"></a><a name="sample"></a>Northwind

Próbki tekstury na określonych współrzędnych i poziomie szczegółowości przy użyciu określonej konfiguracji próbkowania.

```cpp
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
Tryb filtru, który ma być używany do próbkowania texture_view. Tryb filtru jest taki sam dla minimalizacji, maksymalizacji i filtrów mipmappingu.

*_Address_mode*<br/>
Tryb adresu, który ma być używany do próbkowania texture_view. Tryb adresu jest taki sam dla wszystkich wymiarów.

*_Sampler*<br/>
Konfiguracja próbnika do użycia do próbkowania texture_view.

*_Coord*<br/>
Współrzędne, z których ma zostać pobrana próba. Wartości współrzędnych ułamkowych są używane do interpolacji między wartościami Texel.

*_Level_of_detail*<br/>
Wartość określa poziom mipmappingu do próbkowania. Wartości ułamkowe służą do interpolacji między dwoma poziomami mipmappingu. Domyślny poziom szczegółowości to 0, który reprezentuje najbardziej szczegółowy poziom MIP.

### <a name="return-value"></a>Wartość zwracana

Wartość próbki interpolowanej.

## <a name="set"></a><a name="set"></a>zbiór

Ustawia wartość elementu w określonym indeksie dla określonej wartości.

```cpp
void set(
    const index<_Rank>& _Index,
    const value_type& value) const restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Indeks elementu, który ma zostać ustawiony, prawdopodobnie wielowymiarowy.

*wartościami*<br/>
Wartość, dla której ma zostać ustawiony element.

## <a name="value_type"></a><a name="value_type"></a>value_type

Typ wartości elementów texture_view.

```cpp
typedef typename const value_type value_type;
```

## <a name="see-also"></a>Zobacz także

[Concurrency::graphics — Przestrzeń nazw](concurrency-graphics-namespace.md)
