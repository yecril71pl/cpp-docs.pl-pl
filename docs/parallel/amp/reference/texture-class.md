---
title: Texture, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: 16e85d4d-e80a-474a-995d-8bf63fbdf34c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7ae251ace53f8a2a591a311cd389f7084099988e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420141"
---
# <a name="texture-class"></a>texture — Klasa

Tekstura jest agregacją danych na `accelerator_view` w domenie zakresu. Jest to zbiór zmiennych, jeden dla każdego elementu w zakresie domeny. Każda zmienna przechowuje wartość odpowiadającą typowi pierwotnemu C++ ( `unsigned int`, `int`, `float`, `double`), typowi skalarnemu ( `norm`, lub `unorm`), lub typowi krótkiego wektora.

## <a name="syntax"></a>Składnia

```
template <typename value_type,  int _Rank>
class texture;
```

#### <a name="parameters"></a>Parametry

*value_type*<br/>
Typ elementów tekstury.

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
|[tekstury, Konstruktor](#ctor)|Inicjuje nowe wystąpienie klasy `texture` klasy.|
|[~ texture — destruktor](#ctor)|Niszczy `texture` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[copy_to](#copy_to)|Kopiuje `texture` obiektu do miejsca docelowego, wykonując kopię głęboką.|
|[Dane](#data)|Zwraca wskaźnik CPU do danych pierwotnych tekstury.|
|[get](#get)|Zwraca wartość elementu wskazywanego przez określony indeks.|
|[get_associated_accelerator_view](#get_associated_accelerator_view)|Zwraca [accelerator_view](accelerator-view-class.md) czyli preferowany cel kopiowania tej tekstury do skopiowania do.|
|[get_depth_pitch](#get_depth_pitch)|Zwraca liczbę bajtów między każdym wycinkiem głębi tymczasowej tekstury 3D na CPU.|
|[get_row_pitch](#get_row_pitch)|Zwraca liczbę bajtów między każdym wierszem w 2 lub tymczasowej tekstury 3D na CPU.|
|[set](#set)|Ustawia wartość elementu wskazywanego przez określony indeks.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[operator()](#operator_call)|Zwraca wartość elementu, która jest określona przez parametry.|
|[Operator]](#operator_at)|Zwraca element, który jest umieszczony pod określonym indeksem.|
|[operator=](#operator_eq)|Kopiuje określony [tekstury](texture-class.md) obiektu do wskazanego.|

### <a name="public-constants"></a>Publiczne stałe

|Nazwa|Opis|
|----------|-----------------|
|[Rank — stała](#rank)|Zwraca rangę obiektu `texture` obiektu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[associated_accelerator_view](#associated_accelerator_view)|Pobiera [accelerator_view](accelerator-view-class.md) czyli preferowany cel kopiowania tej tekstury do skopiowania do.|
|[depth_pitch](#depth_pitch)|Pobiera liczbę bajtów między każdym wycinkiem głębi tymczasowej tekstury 3D na CPU.|
|[row_pitch](#row_pitch)|Pobiera liczbę bajtów między każdym wierszem w 2D i 3D tymczasowej tekstury na CPU.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`_Texture_base`

`texture`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp_graphics.h

**Namespace:** Concurrency::graphics

##  <a name="dtor"></a> ~ tekstury

Niszczy `texture` obiektu.

```
~texture() restrict(cpu);
```

##  <a name="associated_accelerator_view"></a> associated_accelerator_view —

Pobiera [accelerator_view](accelerator-view-class.md) czyli preferowany cel kopiowania tej tekstury do skopiowania do.

```
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;
```

##  <a name="copy_to"></a> copy_to —

Kopiuje `texture` obiektu do miejsca docelowego, wykonując kopię głęboką.

```
void copy_to(texture& _Dest) const;
void copy_to(writeonly_texture_view<value_type, _Rank>& _Dest) const;
```

### <a name="parameters"></a>Parametry

*_Dest*<br/>
Obiekt, który można skopiować do.

*_Rank*<br/>
Ranga tekstury.

*value_type*<br/>
Typ elementów tekstury.

##  <a name="data"></a> Dane

Zwraca wskaźnik CPU do danych pierwotnych tekstury.

```
void* data() restrict(cpu);

const void* data() const restrict(cpu);
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do danych pierwotnych tekstury.

##  <a name="depth_pitch"></a> depth_pitch

Pobiera liczbę bajtów między każdym wycinkiem głębi tymczasowej tekstury 3D na CPU.

```
__declspec(property(get= get_depth_pitch)) unsigned int depth_pitch;
```

##  <a name="get"></a> Pobierz

Zwraca wartość elementu wskazywanego przez określony indeks.

```
const value_type get(const index<_Rank>& _Index) const restrict(amp);
```

### <a name="parameters"></a>Parametry

*Parametr _Index*<br/>
Indeks elementu.

### <a name="return-value"></a>Wartość zwracana

Wartość elementu wskazywanego przez określony indeks.

##  <a name="get_associated_accelerator_view"></a> get_associated_accelerator_view —

Zwraca accelerator_view, czyli preferowany cel kopiowania tej tekstury do skopiowania do.

```
Concurrency::accelerator_view get_associated_accelerator_view() const restrict(cpu);
```

### <a name="return-value"></a>Wartość zwracana

[Accelerator_view](accelerator-view-class.md) czyli preferowany cel kopiowania tej tekstury do skopiowania do.

##  <a name="get_depth_pitch"></a> get_depth_pitch

Zwraca liczbę bajtów między każdym wycinkiem głębi tymczasowej tekstury 3D na CPU.

```
unsigned int get_depth_pitch() const restrict(cpu);
```

### <a name="return-value"></a>Wartość zwracana

Liczba bajtów między każdym wycinkiem głębi tymczasowej tekstury 3D na CPU.

##  <a name="get_row_pitch"></a> get_row_pitch

Zwraca liczbę bajtów między każdym wierszem w 2-wymiarowej teksturze tymczasowej lub między każdym wierszem wycinka głębi w 3-wymiarowej teksturze tymczasowej.

```
unsigned int get_row_pitch() const restrict(cpu);
```

### <a name="return-value"></a>Wartość zwracana

Liczba bajtów między każdym wierszem w 2-wymiarowej teksturze tymczasowej lub między każdym wierszem wycinka głębi w 3-wymiarowej teksturze tymczasowej.

##  <a name="operator_call"></a> Operator()

Zwraca wartość elementu, która jest określona przez parametry.

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

*Parametr _Index*<br/>
Indeks.

*_I0*<br/>
Najbardziej znaczący składnik indeksu.

*_I1*<br/>
Dalej do najbardziej znaczący składnik indeksu.

*_I2*<br/>
Najmniej znaczący składnik indeksu.

*_Rank*<br/>
Ranga indeksu.

### <a name="return-value"></a>Wartość zwracana

Wartość elementu, która jest określona przez parametry.

##  <a name="operator_at"></a> Operator]

Zwraca element, który jest umieszczony pod określonym indeksem.

```
const value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

const value_type operator[] (int _I0) const restrict(amp);
```

### <a name="parameters"></a>Parametry

*Parametr _Index*<br/>
Indeks.

*_I0*<br/>
Indeks.

### <a name="return-value"></a>Wartość zwracana

Element, który jest umieszczony pod określonym indeksem.

##  <a name="operator_eq"></a> operator =

Kopiuje określony [tekstury](texture-class.md) obiektu do wskazanego.

```
texture& operator= (
    const texture& _Other);

texture& operator= (
    texture<value_type, _Rank>&& _Other);
```

### <a name="parameters"></a>Parametry

*_Inne*<br/>
`texture` Obiektu do skopiowania.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `texture` obiektu.

##  <a name="rank"></a> Ranga

Zwraca rangę obiektu `texture` obiektu.

```
static const int rank = _Rank;
```

##  <a name="row_pitch"></a> row_pitch

Pobiera liczbę bajtów między każdym wierszem w 2D i 3D tymczasowej tekstury na CPU.

```
__declspec(property(get= get_row_pitch)) unsigned int row_pitch;
```

##  <a name="set"></a> Zestaw

Ustawia wartość elementu wskazywanego przez określony indeks.

```
void set(
    const index<_Rank>& _Index,
    const value_type& value) restrict(amp);
```

### <a name="parameters"></a>Parametry

*Parametr _Index*<br/>
Indeks elementu.

*_Rank*<br/>
Ranga indeksu.

*value*<br/>
Nowa wartość elementu.

##  <a name="ctor"></a> Tekstury

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

*_Acc_view*<br/>
[Accelerator_view](accelerator-view-class.md) , który określa lokalizację tekstury.

*_Av*<br/>
[Accelerator_view](accelerator-view-class.md) , który określa lokalizację tekstury.

*_Associated_av*<br/>
Accelerator_view Określa preferowany cel kopiowania do lub z tej tekstury.

*_Bits_per_scalar_element*<br/>
Liczba bitów na każdy element skalarny w podstawowym typie skalarnym tekstury. Ogólnie rzecz biorąc obsługiwana wartość to 8, 16, 32 i 64. Jeśli określono wartość 0, liczba bitów jest taka sama jak podstawowym typie skalarnym. 64 jest prawidłowe tylko dla tekstur opartych na podwójnych.

*_Ext*<br/>
Zakres w każdym wymiarze tekstury.

*_E0*<br/>
Najbardziej znaczący składnik tekstury.

*_E1*<br/>
Dalej do najbardziej znaczący składnik tekstury.

*_E2*<br/>
Najmniej znaczący składnik zakresu tekstury.

*_Input_iterator*<br/>
Typ iteratora wejściowego.

*_Mipmap_levels*<br/>
Liczba poziomów mipmappingu w podstawowej teksturze. Jeśli określono wartość 0, Tekstura będzie miała pełną gamę poziomów mipmappingu w dół, aby możliwie jak najmniejszego rozmiaru dla podanego zakresu.

*_Rank*<br/>
Ranga zakresu.

*_Source*<br/>
Wskaźnik do buforu hosta.

*_Src*<br/>
Aby teksturować do kopii.

*_Src_byte_size*<br/>
Liczba bajtów w buforze źródłowym.

*_Src_first*<br/>
Początkowy iterator do kontenera źródłowego.

*_Src_last*<br/>
Końcowy iterator do kontenera źródłowego.

*_Inne*<br/>
Inne źródła danych.

*_Rank*<br/>
Ranga sekcji.

## <a name="see-also"></a>Zobacz też

[Concurrency::graphics, przestrzeń nazw](concurrency-graphics-namespace.md)
