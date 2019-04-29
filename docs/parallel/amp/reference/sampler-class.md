---
title: sampler — Klasa
ms.date: 06/28/2018
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
ms.assetid: 9a6a9807-497d-402d-b092-8c4d86275b80
ms.openlocfilehash: 1a66e4d025a7592b78839dbe5f25f9103da41224
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352596"
---
# <a name="sampler-class"></a>sampler — Klasa

Klasa próbnik agreguje informacje o konfiguracji pobierania próbek służący do pobierania próbek tekstury.

## <a name="syntax"></a>Składnia

```cpp
class sampler;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[sampler Constructor](#ctor)|Przeciążone. Konstruuje wystąpienie próbnika.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[get_address_mode](#get_address_mode)|Zwraca `address_mode` skojarzony z próbnikiem.|
|[get_border_color](#get_border_color)|Zwraca kolor obramowania, który jest skojarzony z próbnikiem.|
|[get_filter_mode](#get_filter_mode)|Zwraca `filter_mode` skojarzony z próbnikiem.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[operator=](#operator_eq)|Przeciążone. Operator przypisania.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[address_mode](#address_mode)|Pobiera tryb adresu `sampler` obiektu.|
|[border_color](#border_color)|Pobiera kolor obramowania `sampler` obiektu.|
|[filter_mode](#filter_mode)|Pobiera tryb filtra obiektu `sampler` obiektu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`sampler`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp_graphics.h

**Namespace:** concurrency::graphics

##  <a name="ctor"></a> Przykłady

Tworzy wystąpienie klasy [sampler, klasa](sampler-class.md).

```cpp
sampler() restrict(cpu);    // [1] default constructor

sampler(                    // [2] constructor
    filter_mode _Filter_mode) restrict(cpu);

sampler(                    // [3] constructor
    address_mode _Address_mode,
    float_4 _Border_color = float_4(0.0f,
    0.0f,
    0.0f,
    0.0f)) restrict(cpu);

sampler(                    // [4] constructor
    filter_mode _Filter_mode,
    address_mode _Address_mode,
    float_4 _Border_color = float_4(0.0f,
    0.0f,
    0.0f,
    0.0f)) restrict(cpu);

sampler(                    // [5] copy constructor
    const sampler& _Other) restrict(amp,
    cpu);

sampler(                    // [6] move constructor
    sampler&& _Other) restrict(amp,
    cpu);
```

### <a name="parameters"></a>Parametry

*_Filter_mode*<br/>
Tryb filtru do używana podczas próbkowania.

*_Address_mode*<br/>
Tryb adresowania, który ma być używany do pobierania próbek dla wszystkich wymiarów.

*_Border_color*<br/>
Kolor obramowania do użycia, jeśli trybem adresu jest address_border. Wartość domyślna to `float_4(0.0f, 0.0f, 0.0f, 0.0f)`.

*_Inne*<br/>
[5] Konstruktor kopiujący `sampler` obiekt do skopiowania w nowe `sampler` wystąpienia.

[6] Konstruktor przenoszący `sampler` obiekt do przeniesienia w nowe `sampler` wystąpienia.

##  <a name="address_mode"></a> address_mode —

Pobiera tryb adresu `sampler` obiektu.

```cpp
__declspec(property(get= get_address_mode)) Concurrency::graphics::address_mode address_mode;
```

##  <a name="border_color"></a> border_color

Pobiera kolor obramowania `sampler` obiektu.

```cpp
__declspec(property(get= get_border_color)) Concurrency::graphics::float_4 border_color;
```

##  <a name="filter_mode"></a> filter_mode —

Pobiera tryb filtra obiektu `sampler` obiektu.

```cpp
__declspec(property(get= get_filter_mode)) Concurrency::graphics::filter_mode filter_mode;
```

##  <a name="get_address_mode"></a> get_address_mode

Zwraca tryb filtra skonfigurowany dla `sampler`.

```cpp
Concurrency::graphics::address_mode get_address_mode() const __GPU;
```

### <a name="return-value"></a>Wartość zwracana

Tryb adresu, który jest skonfigurowany dla próbnika.

##  <a name="get_border_color"></a> get_border_color

Zwraca kolor obramowania, który jest skonfigurowany dla tego `sampler`.

```cpp
Concurrency::graphics::float_4 get_border_color() const restrict(amp, cpu);
```

### <a name="return-value"></a>Wartość zwracana

Float_4, który zawiera kolor obramowania.

##  <a name="get_filter_mode"></a> get_filter_mode

Zwraca tryb filtra skonfigurowany dla `sampler`.

```cpp
Concurrency::graphics::filter_mode get_filter_mode() const restrict(amp, cpu);
```

### <a name="return-value"></a>Wartość zwracana

Tryb filtru, który jest skonfigurowany dla próbnika.

##  <a name="operator_eq"></a> operator =

Przypisuje wartość innego obiektu próbnik do istniejącego próbnika.

```cpp
sampler& operator= (    // [1] copy assignment operator
    const sampler& _Other) restrict(amp, cpu);

sampler& operator= (    // [2] move assignment operator
    sampler&& _Other) restrict(amp, cpu);
```

### <a name="parameters"></a>Parametry

*_Inne*<br/>
[1] Kopiuj Operator przypisania `sampler` obiektu do skopiowania do tego `sampler`.

[2] Operator przypisania przenoszenia `sampler` obiektu do przeniesienia do tego `sampler`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do wystąpienia przykładowego.

## <a name="see-also"></a>Zobacz także

[Concurrency::graphics, przestrzeń nazw](concurrency-graphics-namespace.md)
