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
ms.openlocfilehash: 6bf4b9666d746199cea92fa2bd52b691c67e4a5b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126354"
---
# <a name="texture_view-class"></a>texture_view — Klasa

Zapewnia dostęp do odczytu i zapisu do tekstury. `texture_view` można użyć tylko do odczytu tekstur, których typ wartości to `int`, `unsigned int`lub `float`, które mają domyślny 32-bitowy BPSE. Aby odczytać inne formaty tekstury, użyj `texture_view<const value_type, _Rank>`.

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
Ranga `texture_view`.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Publiczne definicje typów

|Name (Nazwa)|Opis|
|----------|-----------------|
|`value_type`|Typ elementów w agregacji tekstury.|
|`coordinates_type`|Typ współrzędnych służący do określania Texel w `texture_view`— czyli `short_vector`, który ma taką samą rangę, jak skojarzona tekstura, która ma typ wartości `float`.|
|`gather_return_type`|Typ zwracany używany do zbierania operacji — to znaczy `short_vector` rangi 4, który przechowuje cztery jednorodne składniki kolorów zebrane z czterech przykładowych wartości Texel.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Konstruktor texture_view](#ctor)|Przeciążone. Tworzy wystąpienie `texture_view`.|
|[~ texture_view destruktor](#ctor)|Niszczy wystąpienie `texture_view`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[gather_alpha](#gather_alpha)|Przeciążone. Próbki tekstury na określonych współrzędnych przy użyciu określonej konfiguracji pobierania próbek i zwraca składniki alfa (w) z czterech próbkowanych tekseli.|
|[gather_blue](#gather_blue)|Przeciążone. Próbki tekstury na określonych współrzędnych przy użyciu określonej konfiguracji pobierania próbek i zwraca składniki niebieskie (z) z czterech próbkowanych tekseli.|
|[gather_green](#gather_green)|Przeciążone. Próbki tekstury na określonych współrzędnych przy użyciu określonej konfiguracji pobierania próbek i zwraca składniki zielone (y) z czterech próbkowanych tekseli.|
|[gather_red](#gather_red)|Przeciążone. Próbkuje teksturę na określonych współrzędnych przy użyciu określonej konfiguracji pobierania próbek i zwraca składniki czerwone (x) z czterech próbkowanych tekseli.|
|[get](#get)|Przeciążone. Pobiera wartość elementu według indeksu.|
|[Northwind](#sample)|Przeciążone. Próbki tekstury na określonych współrzędnych i poziomie szczegółowości przy użyciu określonej konfiguracji próbkowania.|
|[set](#set)|Ustawia wartość elementu według indeksu.|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[operator ()](#operator_call)|Przeciążone. Pobiera wartość elementu według indeksu.|
|[\[operatora \]](#operator_at)|Przeciążone. Pobiera wartość elementu według indeksu.|
|[operator =](#operator_eq)|Przeciążone. Operator przypisania.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Name (Nazwa)|Opis|
|----------|-----------------|
|[value_type](#value_type)|Typ wartości elementów `texture_view`.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`_Texture_base`

`texture_view`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp_graphics. h

**Przestrzeń nazw:** concurrency:: Graphics

## <a name="dtor"></a>~ texture_view

Niszczy wystąpienie `texture_view`.

```cpp
~texture_view() restrict(amp, cpu);
```

## <a name="ctor"></a>texture_view

Tworzy wystąpienie `texture_view`.

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
[1, 2] Konstruktor `texture`, na którym jest tworzony `texture_view` zapisywalny.

[3, 4] Konstruktor `texture`, na którym jest tworzony `texture_view` niezapisywalny.

*_Other*<br/>
[5] Kopiuj Konstruktor do zapisywalnego `texture_view`.

[6, 7] Skopiuj Konstruktor do źródłowej `texture_view`nie do zapisu.

*_Mipmap_level*<br/>
Określony poziom mipmappingu na źródłowym `texture`, do którego `texture_view` ma to możliwość zapisu. Wartość domyślna to 0, co oznacza najwyższy poziom (najbardziej szczegółowy) poziom MIP.

*_Most_detailed_mip*<br/>
Najwyższy poziom (najbardziej szczegółowy) poziom MIP dla widoku względem określonego obiektu `texture_view`.

*_Mip_levels*<br/>
Liczba poziomów mipmappingu dostępnych za pomocą `texture_view`.

## <a name="gather_red"></a>gather_red

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
Tryb adresu, który ma być używany do próbkowania `texture_view`. Tryb adresu jest taki sam dla wszystkich wymiarów.

*_Sampler*<br/>
Konfiguracja próbnika do użycia do próbkowania `texture_view`.

*_Coord*<br/>
Współrzędne, z których ma zostać pobrana próba. Wartości współrzędnych ułamkowych są używane do interpolacji między przykładowym tekseli.

### <a name="return-value"></a>Wartość zwrócona

Krótka wektor rangi 4 zawierający składnik czerwony (x) z 4 próbkowanych wartości Texel.

## <a name="gather_green"></a>gather_green

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
Tryb adresu, który ma być używany do próbkowania `texture_view`. Tryb adresu jest taki sam dla wszystkich wymiarów.

*_Sampler*<br/>
Konfiguracja próbnika do użycia do próbkowania `texture_view`.

*_Coord*<br/>
Współrzędne, z których ma zostać pobrana próba. Wartości współrzędnych ułamkowych są używane do interpolacji między przykładowym tekseli.

### <a name="return-value"></a>Wartość zwrócona

Krótka wektor rangi 4 zawierający zielony składnik (y) wartości Texel 4 próbki.

## <a name="gather_blue"></a>gather_blue

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
Tryb adresu, który ma być używany do próbkowania `texture_view`. Tryb adresu jest taki sam dla wszystkich wymiarów.

*_Sampler*<br/>
Konfiguracja próbnika do użycia do próbkowania `texture_view`.

*_Coord*<br/>
Współrzędne, z których ma zostać pobrana próba. Wartości współrzędnych ułamkowych są używane do interpolacji między przykładowym tekseli.

### <a name="return-value"></a>Wartość zwrócona

Krótka wektor rangi 4 zawierający składnik czerwony (x) z 4 próbkowanych wartości Texel.

## <a name="gather_alpha"></a>gather_alpha

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
Tryb adresu, który ma być używany do próbkowania `texture_view`. Tryb adresu jest taki sam dla wszystkich wymiarów.

*_Sampler*<br/>
Konfiguracja próbnika do użycia do próbkowania `texture_view`.

*_Coord*<br/>
Współrzędne, z których ma zostać pobrana próba. Wartości współrzędnych ułamkowych są używane do interpolacji między przykładowym tekseli.

### <a name="return-value"></a>Wartość zwrócona

Krótka wektor rangi 4 zawierający składnik alfa (w) z 4 próbkowanych wartości Texel.

## <a name="get"></a>Pobierz

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

### <a name="return-value"></a>Wartość zwrócona

Wartość elementu.

## <a name="operator_eq"></a>operator =

Przypisuje widok tej samej tekstury, co określony `texture_view` do tego wystąpienia `texture_view`.

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
[1, 2] Kopiuj Konstruktor A zapisywalny obiekt `texture_view`.

[3] Kopiuj Konstruktor do niezapisywalnego obiektu `texture_view`.

### <a name="return-value"></a>Wartość zwrócona

Odwołanie do tego wystąpienia `texture_view`.

## <a name="operator_at"></a>operator []

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

### <a name="return-value"></a>Wartość zwrócona

Wartość elementu indeksowana przez `_Index`.

## <a name="operator_call"></a>operator ()

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

### <a name="return-value"></a>Wartość zwrócona

Wartość elementu indeksowana przez `_Index`.

## <a name="sample"></a>Northwind

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

### <a name="return-value"></a>Wartość zwrócona

Wartość próbki interpolowanej.

## <a name="set"></a>zbiór

Ustawia wartość elementu w określonym indeksie dla określonej wartości.

```cpp
void set(
    const index<_Rank>& _Index,
    const value_type& value) const restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Indeks elementu, który ma zostać ustawiony, prawdopodobnie wielowymiarowy.

*value*<br/>
Wartość, dla której ma zostać ustawiony element.

## <a name="value_type"></a>value_type

Typ wartości elementów texture_view.

```cpp
typedef typename const value_type value_type;
```

## <a name="see-also"></a>Zobacz też

[Concurrency::graphics, przestrzeń nazw](concurrency-graphics-namespace.md)
