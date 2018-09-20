---
title: Extent — klasa (C++ AMP) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- extent
- AMP/extent
- AMP/Concurrency::extent::extent
- AMP/Concurrency::extent::contains
- AMP/Concurrency::extent::size
- AMP/Concurrency::extent::tile
- AMP/Concurrency::extent::rank Constant
dev_langs:
- C++
helpviewer_keywords:
- extent structure
ms.assetid: edb5de3d-3935-4dbb-8365-4cc6c4fb0269
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 71a02b89e7b2098f8a125d1477cff2a0d1cda30a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429971"
---
# <a name="extent-class-c-amp"></a>extent — Klasa (C++ AMP)

Reprezentuje wektor *N* wartości całkowitych, które określają granice przestrzeni *N*-wymiarowej, która pochodzi od 0. Wartości w wektorze są uporządkowane od najbardziej do najmniej znaczących.

### <a name="syntax"></a>Składnia

```
template <int _Rank>
class extent;
```

### <a name="parameters"></a>Parametry

*_Rank*<br/>
Ranga `extent` obiektu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp.h

**Namespace:** współbieżności

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Konstruktor zakresu](#ctor)|Inicjuje nowe wystąpienie klasy `extent` klasy.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[zawiera](#contains)|Sprawdza, czy określony `extent` obiekt ma określony stopień.|
|[Rozmiar](#size)|Zwraca całkowity rozmiar liniowy zakresu (w jednostkach elementów).|
|[Kafelek](#tile)|Tworzy `tiled_extent` obiektu z fragmentów zadanych przez określone wymiary.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[operator-](#operator_min)|Zwraca nowy `extent` obiektu, który jest tworzony przez odjęcie `index` elementów od odpowiadających im `extent` elementów.|
|[operator--](#operator_min_min)|Zmniejsza o jeden każdy element obiektu `extent` obiektu.|
|[operator%=](#operator_mod_eq)|Oblicza moduł (resztę) każdego elementu w `extent` obiektu, gdy ten element jest dzielona przez liczbę.|
|[operator*=](#operator_star_eq)|Mnoży każdy element obiektu `extent` przez liczbę.|
|[operator / =](#operator_min_eq)|Dzieli każdy element obiektu `extent` przez liczbę.|
|[Extent::operator\[\]](#operator_at)|Zwraca element, który jest umieszczony pod określonym indeksem.|
|[operator +](#operator_add)|Zwraca nowy `extent` obiektu, który jest tworzony przez dodanie odpowiadających im `index` i `extent` elementów.|
|[operator++](#operator_add_add)|Zwiększa każdy element obiektu `extent` obiektu.|
|[operator+=](#operator_add_eq)|Dodaje określoną liczbę do każdego elementu `extent` obiektu.|
|[operator=](#operator_eq)|Kopiuje zawartość innego `extent` obiektu do wskazanego.|
|[operator-=](#operator_min_eq)|Odejmuje określoną liczbę od każdego elementu obiektu `extent` obiektu.|

### <a name="public-constants"></a>Publiczne stałe

|Nazwa|Opis|
|----------|-----------------|
|[Rank — stała](#rank)|Zwraca rangę obiektu `extent` obiektu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`extent`

## <a name="contains"></a> zawiera

Wskazuje, czy określony [indeksu](index-class.md) wartość znajduje się w obiekcie "zakresu".

### <a name="syntax"></a>Składnia

```
bool contains(const index<rank>& _Index) const restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*Parametr _Index*<br/>
`index` Wartość do sprawdzenia.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli określony `index` wartość jest zawarta w `extent` obiektu; w przeciwnym razie `false`.

##  <a name="ctor"></a> zakres

Inicjuje nowe wystąpienie klasy "zakresu".

### <a name="syntax"></a>Składnia

```
extent() restrict(amp,cpu);
extent(const extent<_Rank>& _Other) restrict(amp,cpu);
explicit extent(int _I) restrict(amp,cpu);
extent(int _I0,  int _I1) restrict(amp,cpu);
extent(int _I0,  int _I1, int _I2) restrict(amp,cpu);
explicit extent(const int _Array[_Rank])restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Array*<br/>
Tablica `_Rank` liczb całkowitych, które służy do tworzenia nowego `extent` obiektu.

*_I*<br/>
Długość zakresu.

*_I0*<br/>
Długość najbardziej znaczącego wymiaru.

*_I1*<br/>
Długość następnego do najbardziej znaczący wymiar.

*_I2*<br/>
Długość najmniej znaczącego wymiaru.

*_Inne*<br/>
`extent` Obiektu, na którym nowym `extent` opiera się obiekt.

## <a name="remarks"></a>Uwagi

Konstruktor bezparametrowy inicjuje `extent` obiekt, który ma trójwymiarowy.

Jeśli tablica jest używana do konstruowania `extent` obiektu, długość tablicy musi odpowiadać randze obiektu `extent` obiektu.

##  <a name="operator_mod_eq"></a> operator % =

Oblicza moduł (resztę) każdego elementu w zakresie, gdy ten element jest dzielona przez liczbę.

### <a name="syntax"></a>Składnia

```
extent<_Rank>& operator%=(int _Rhs) restrict(cpu, direct3d);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Numer, aby znaleźć moduł.

### <a name="return-value"></a>Wartość zwracana

`extent` Obiektu.

##  <a name="operator_star_eq"></a> operator * =

Mnoży każdy element w obiekcie "zakres" przez określoną liczbę.

### <a name="syntax"></a>Składnia

```
extent<_Rank>& operator*=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Liczbę Aby pomnożyć.

### <a name="return-value"></a>Wartość zwracana

`extent` Obiektu.

## <a name="operator_add"></a> operator +

Zwraca nowy `extent` obiekt utworzony przez dodanie odpowiadających im `index` i `extent` elementów.

### <a name="syntax"></a>Składnia

```
extent<_Rank> operator+(const index<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
`index` Obiekt, który zawiera elementy do dodania.

### <a name="return-value"></a>Wartość zwracana

Nowy `extent` obiektu.

##  <a name="operator_add_add"></a> operator ++

Zwiększa każdy element obiektu "zakres".

### <a name="syntax"></a>Składnia

```
extent<_Rank>& operator++() restrict(amp,cpu);
extent<_Rank> operator++(int)restrict(amp,cpu);
```

### <a name="return-value"></a>Wartość zwracana

Dla operatora prefiksowego `extent` obiektu (`*this`). Dla operatora sufiksowego nowy `extent` obiektu.

##  <a name="operator_add_eq"></a> += — operator

Dodaje określoną liczbę do każdego elementu obiektu "zakres".

### <a name="syntax"></a>Składnia

```
extent<_Rank>& operator+=(const extent<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator+=(const index<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator+=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Liczba, indeks lub zakres do dodania.

### <a name="return-value"></a>Wartość zwracana

Wartość wynikowa `extent` obiektu.

##  <a name="operator_min"></a> operator-

Tworzy nową `extent` obiektu przez odjęcie każdego elementu w określonym `index` obiekt odpowiadający mu element w tym `extent` obiektu.

### <a name="syntax"></a>Składnia

```
extent<_Rank> operator-(const index<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
`index` Obiekt, który zawiera elementy do odjęcia.

### <a name="return-value"></a>Wartość zwracana

Nowy `extent` obiektu.

##  <a name="operator_min_min"></a> operator--

Zmniejsza o jeden każdy element w obiekcie "zakresu".

### <a name="syntax"></a>Składnia

```
extent<_Rank>& operator--() restrict(amp,cpu);
extent<_Rank> operator--(int)restrict(amp,cpu);
```

### <a name="return-value"></a>Wartość zwracana

Dla operatora prefiksowego `extent` obiektu (`*this`). Dla operatora sufiksowego nowy `extent` obiektu.

##  <a name="operator_div_eq"></a> operator / =

Dzieli każdy element w obiekcie "zakres" przez określoną liczbę.

### <a name="syntax"></a>Składnia

```
extent<_Rank>& operator/=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Liczba do podzielenia przez.

### <a name="return-value"></a>Wartość zwracana

`extent` Obiektu.

##  <a name="operator_min_eq"></a> operator-=

Odejmuje określoną liczbę od każdego elementu obiektu "zakres".

### <a name="syntax"></a>Składnia

```
extent<_Rank>& operator-=(const extent<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator-=(const index<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator-=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Liczba odejmowana.

### <a name="return-value"></a>Wartość zwracana

Wartość wynikowa `extent` obiektu.

##  <a name="operator_eq"></a> operator =

Kopiuje zawartość innego obiektu "zakres" do tego.

### <a name="syntax"></a>Składnia

```
extent<_Rank>& operator=(const extent<_Rank>& _Other) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Inne*<br/>
`extent` Obiektu do skopiowania.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `extent` obiektu.

##  <a name="operator_at"></a> Extent::operator \[\]

Zwraca element, który jest umieszczony pod określonym indeksem.

### <a name="syntax"></a>Składnia

```
int operator[](unsigned int _Index) const restrict(amp,cpu);
int& operator[](unsigned int _Index) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*Parametr _Index*<br/>
Liczba całkowita z zakresu od 0 do rangi minus 1.

### <a name="return-value"></a>Wartość zwracana

Element, który jest umieszczony pod określonym indeksem.

##  <a name="rank_constant"></a> Ranga

Przechowuje rangę obiektu "zakres".

### <a name="syntax"></a>Składnia

```
static const int rank = _Rank;
```

##  <a name="size"></a> Rozmiar

Zwraca całkowity rozmiar liniowy `extent` obiektu (w jednostkach elementów).

### <a name="syntax"></a>Składnia

```
unsigned int size() const restrict(amp,cpu);
```

## <a name="tile"></a> Kafelek

Tworzy obiekt tiled_extent z wymiary określonego fragmentu.

```
template <int _Dim0>
tiled_extent<_Dim0> tile() const ;

template <int _Dim0, int _Dim1>
tiled_extent<_Dim0, _Dim1> tile() const ;

template <int _Dim0, int _Dim1, int _Dim2>
tiled_extent<_Dim0, _Dim1, _Dim2> tile() const ;
```
### <a name="parameters"></a>Parametry

*_Dim0*<br/>
Najbardziej znaczący składnik w zakresie poddanym fragmentacji.
*_Dim1*<br/>
Dalej do najbardziej znaczący składnik w zakresie poddanym fragmentacji.
*_Dim2*<br/>
Najmniej znaczący składnik w zakresie poddanym fragmentacji.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
