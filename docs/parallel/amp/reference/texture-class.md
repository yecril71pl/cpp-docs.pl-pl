---
title: texture — Klasa
ms.date: 11/04/2016
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
ms.assetid: 16e85d4d-e80a-474a-995d-8bf63fbdf34c
ms.openlocfilehash: b8a37293166ec21aeb9410f05fb70c9753ec4f22
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230418"
---
# <a name="texture-class"></a>texture — Klasa

Tekstura jest agregacją danych `accelerator_view` w domenie zakresu. Jest to zbiór zmiennych, po jednym dla każdego elementu w domenie zakresów. Każda zmienna przechowuje wartość odpowiadającą typowi pierwotnemu C++ ( **`unsigned int`** , **`int`** ,, **`float`** **`double`** ), typ skalarny ( `norm` , lub `unorm` ) lub krótki typ wektora.

## <a name="syntax"></a>Składnia

```cpp
template <typename value_type,  int _Rank>
class texture;
```

### <a name="parameters"></a>Parametry

*value_type*<br/>
Typ elementów w tekstury.

*_Rank*<br/>
Ranga tekstury.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`scalar_type`|Typy skalarne.|
|`value_type`|Typy wartości.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Konstruktor tekstury](#ctor)|Inicjuje nowe wystąpienie klasy `texture`.|
|[~ Destruktor tekstury](#ctor)|Niszczy `texture` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[copy_to](#copy_to)|Kopiuje `texture` obiekt do miejsca docelowego, wykonując kopię głęboką.|
|[data](#data)|Zwraca wskaźnik procesora CPU do danych pierwotnych tej tekstury.|
|[Pobierz](#get)|Zwraca wartość elementu w określonym indeksie.|
|[get_associated_accelerator_view](#get_associated_accelerator_view)|Zwraca [accelerator_view](accelerator-view-class.md) , który jest preferowanym obiektem docelowym dla tej tekstury, do której ma zostać skopiowane.|
|[get_depth_pitch](#get_depth_pitch)|Zwraca liczbę bajtów między każdym wycinkiem głębokości w tekstury przemieszczania 3D na PROCESORze.|
|[get_row_pitch](#get_row_pitch)|Zwraca liczbę bajtów między każdym wierszem w tekstury przemieszczania 2D lub 3W na PROCESORze.|
|[zbiór](#set)|Ustawia wartość elementu w określonym indeksie.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[operator ()](#operator_call)|Zwraca wartość elementu, która jest określona przez parametry.|
|[operator\[\]](#operator_at)|Zwraca element, który znajduje się w określonym indeksie.|
|[operator =](#operator_eq)|Kopiuje określony obiekt [tekstury](texture-class.md) do tego.|

### <a name="public-constants"></a>Stałe publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Stała rangi](#rank)|Pobiera rangę `texture` obiektu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[associated_accelerator_view](#associated_accelerator_view)|Pobiera [accelerator_view](accelerator-view-class.md) , który jest preferowanym obiektem docelowym dla tej tekstury, do której będzie kopiowany.|
|[depth_pitch](#depth_pitch)|Pobiera liczbę bajtów między każdym wycinkem głębokości w tekstury przemieszczania 3D na PROCESORze.|
|[row_pitch](#row_pitch)|Pobiera liczbę bajtów między każdym wierszem w tekstury przemieszczania 2D lub 3D na PROCESORze.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`_Texture_base`

`texture`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp_graphics. h

**Przestrzeń nazw:** Concurrency:: Graphics

## <a name="texture"></a><a name="dtor"></a>~ Texture

Niszczy `texture` obiekt.

```cpp
~texture() restrict(cpu);
```

## <a name="associated_accelerator_view"></a><a name="associated_accelerator_view"></a>associated_accelerator_view

Pobiera [accelerator_view](accelerator-view-class.md) , który jest preferowanym obiektem docelowym dla tej tekstury, do której będzie kopiowany.

```cpp
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;
```

## <a name="copy_to"></a><a name="copy_to"></a>copy_to

Kopiuje `texture` obiekt do miejsca docelowego, wykonując kopię głęboką.

```cpp
void copy_to(texture& _Dest) const;
void copy_to(writeonly_texture_view<value_type, _Rank>& _Dest) const;
```

### <a name="parameters"></a>Parametry

*_Dest*<br/>
Obiekt do skopiowania.

*_Rank*<br/>
Ranga tekstury.

*value_type*<br/>
Typ elementów w tekstury.

## <a name="data"></a><a name="data"></a>Data

Zwraca wskaźnik procesora CPU do danych pierwotnych tej tekstury.

```cpp
void* data() restrict(cpu);

const void* data() const restrict(cpu);
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do danych pierwotnych tekstury.

## <a name="depth_pitch"></a><a name="depth_pitch"></a>depth_pitch

Pobiera liczbę bajtów między każdym wycinkem głębokości w tekstury przemieszczania 3D na PROCESORze.

```cpp
__declspec(property(get= get_depth_pitch)) unsigned int depth_pitch;
```

## <a name="get"></a><a name="get"></a>Pobierz

Zwraca wartość elementu w określonym indeksie.

```cpp
const value_type get(const index<_Rank>& _Index) const restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Indeks elementu.

### <a name="return-value"></a>Wartość zwracana

Wartość elementu w określonym indeksie.

## <a name="get_associated_accelerator_view"></a><a name="get_associated_accelerator_view"></a>get_associated_accelerator_view

Zwraca accelerator_view, który jest preferowanym obiektem docelowym dla tej tekstury, do której ma zostać skopiowane.

```cpp
Concurrency::accelerator_view get_associated_accelerator_view() const restrict(cpu);
```

### <a name="return-value"></a>Wartość zwracana

[Accelerator_view](accelerator-view-class.md) to preferowany element docelowy dla tej tekstury, do której ma zostać skopiowany.

## <a name="get_depth_pitch"></a><a name="get_depth_pitch"></a>get_depth_pitch

Zwraca liczbę bajtów między każdym wycinkiem głębokości w tekstury przemieszczania 3D na PROCESORze.

```cpp
unsigned int get_depth_pitch() const restrict(cpu);
```

### <a name="return-value"></a>Wartość zwracana

Liczba bajtów między każdym wycinkem głębokości w tekstury przemieszczania 3D na PROCESORze.

## <a name="get_row_pitch"></a><a name="get_row_pitch"></a>get_row_pitch

Zwraca liczbę bajtów między każdym wierszem w 2-wymiarowej teksturze tymczasowej lub między każdym wierszem wycinka głębi w 3-wymiarowej teksturze tymczasowej.

```cpp
unsigned int get_row_pitch() const restrict(cpu);
```

### <a name="return-value"></a>Wartość zwracana

Liczba bajtów między każdym wierszem w 2-wymiarowej teksturze tymczasowej lub między każdym wierszem wycinka głębi w 3-wymiarowej teksturze tymczasowej.

## <a name="operator"></a><a name="operator_call"></a>operator ()

Zwraca wartość elementu, która jest określona przez parametry.

```cpp
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

*_Index*<br/>
Indeks.

*_I0*<br/>
Najbardziej znaczący składnik indeksu.

*_I1*<br/>
Najbardziej znaczący składnik indeksu.

*_I2*<br/>
Najmniej znaczący składnik indeksu.

*_Rank*<br/>
Ranga indeksu.

### <a name="return-value"></a>Wartość zwracana

Wartość elementu, która jest określona przez parametry.

## <a name="operator"></a><a name="operator_at"></a>operator []

Zwraca element, który znajduje się w określonym indeksie.

```cpp
const value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

const value_type operator[] (int _I0) const restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Indeks.

*_I0*<br/>
Indeks.

### <a name="return-value"></a>Wartość zwracana

Element o określonym indeksie.

## <a name="operator"></a><a name="operator_eq"></a>operator =

Kopiuje określony obiekt [tekstury](texture-class.md) do tego.

```cpp
texture& operator= (
    const texture& _Other);

texture& operator= (
    texture<value_type, _Rank>&& _Other);
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
`texture`Obiekt, z którego mają zostać skopiowane.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do tego `texture` obiektu.

## <a name="rank"></a><a name="rank"></a>stopni

Pobiera rangę `texture` obiektu.

```cpp
static const int rank = _Rank;
```

## <a name="row_pitch"></a><a name="row_pitch"></a>row_pitch

Pobiera liczbę bajtów między każdym wierszem w tekstury przemieszczania 2D lub 3D na PROCESORze.

```cpp
__declspec(property(get= get_row_pitch)) unsigned int row_pitch;
```

## <a name="set"></a><a name="set"></a>zbiór

Ustawia wartość elementu w określonym indeksie.

```cpp
void set(
    const index<_Rank>& _Index,
    const value_type& value) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Indeks elementu.

*_Rank*<br/>
Ranga indeksu.

*wartościami*<br/>
Nowa wartość elementu.

## <a name="texture"></a><a name="ctor"></a>głębokości

Inicjuje nowe wystąpienie klasy `texture`.

```cpp
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

*_Acc_view*<br/>
[Accelerator_view](accelerator-view-class.md) określający lokalizację tekstury.

*_Av*<br/>
[Accelerator_view](accelerator-view-class.md) określający lokalizację tekstury.

*_Associated_av*<br/>
Accelerator_view, który określa preferowany element docelowy dla kopii do lub z tej tekstury.

*_Bits_per_scalar_element*<br/>
Liczba bitów na każdy element skalarny w podstawowym typie skalarnym tekstury. Ogólnie rzecz biorąc, obsługiwana wartość to 8, 16, 32 i 64. Jeśli określono wartość 0, liczba bitów jest taka sama jak scalar_type źródłowa. 64 jest prawidłowy tylko dla tekstur opartych na podwójnej precyzji.

*_Ext*<br/>
Zakres w każdym wymiarze tekstury.

*_E0*<br/>
Najbardziej znaczący składnik tekstury.

*_E1*<br/>
Najbardziej znaczący składnik tekstury.

*_E2*<br/>
Najmniej znaczący składnik zakresu tekstury.

*_Input_iterator*<br/>
Typ iteratora wejściowego.

*_Mipmap_levels*<br/>
Liczba poziomów mipmappingu w tekstury źródłowej. Jeśli określono wartość 0, tekstura będzie mieć pełny zakres mipmappingu poziomów w dół do najmniejszego możliwego rozmiaru w określonym zakresie.

*_Rank*<br/>
Ranga zakresu.

*_Source*<br/>
Wskaźnik do buforu hosta.

*_Src*<br/>
Do tekstury do skopiowania.

*_Src_byte_size*<br/>
Liczba bajtów w buforze źródłowym.

*_Src_first*<br/>
Początkowy iterator do kontenera źródłowego.

*_Src_last*<br/>
Końcowy iterator do kontenera źródłowego.

*_Other*<br/>
Inne źródło danych.

*_Rank*<br/>
Ranga sekcji.

## <a name="see-also"></a>Zobacz także

[Concurrency::graphics — Przestrzeń nazw](concurrency-graphics-namespace.md)
