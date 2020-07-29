---
title: extent — Klasa (C++ AMP)
ms.date: 03/27/2019
f1_keywords:
- extent
- AMP/extent
- AMP/Concurrency::extent::extent
- AMP/Concurrency::extent::contains
- AMP/Concurrency::extent::size
- AMP/Concurrency::extent::tile
- AMP/Concurrency::extent::rank Constant
helpviewer_keywords:
- extent structure
ms.assetid: edb5de3d-3935-4dbb-8365-4cc6c4fb0269
ms.openlocfilehash: b9fd0ffb0c3ac6e0b80823e9f31c3615a045262b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222735"
---
# <a name="extent-class-c-amp"></a>extent — Klasa (C++ AMP)

Reprezentuje wektora *n* wartości całkowitych, które określają granice przestrzeni *n*-wymiarowej, która ma początek 0. Wartości w wektorze są uporządkowane od najbardziej do najmniej znaczących.

## <a name="syntax"></a>Składnia

```cpp
template <int _Rank>
class extent;
```

### <a name="parameters"></a>Parametry

*_Rank*<br/>
Ranga `extent` obiektu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp. h

**Przestrzeń nazw:** Współbieżności

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Konstruktor zakresów](#ctor)|Inicjuje nowe wystąpienie klasy `extent`.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[wyświetlana](#contains)|Sprawdza, czy określony `extent` obiekt ma określoną rangę.|
|[zmienia](#size)|Zwraca łączny rozmiar liniowy zakresu (w jednostkach elementów).|
|[kafelek](#tile)|Tworzy `tiled_extent` obiekt z zakresem kafelków przyznanych przez określone wymiary.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[zakład](#operator_min)|Zwraca nowy `extent` obiekt, który jest tworzony przez odjęcie `index` elementów od odpowiednich `extent` elementów.|
|[operator--](#operator_min_min)|Zmniejsza każdy element `extent` obiektu.|
|[operator% =](#operator_mod_eq)|Oblicza moduł (resztę) każdego elementu w obiekcie, `extent` gdy ten element jest podzielony przez liczbę.|
|[operator * =](#operator_star_eq)|Mnoży każdy element `extent` obiektu przez liczbę.|
|[operator/=](#operator_min_eq)|Dzieli każdy element `extent` obiektu przez liczbę.|
|[zakres:: operator\[\]](#operator_at)|Zwraca element, który znajduje się w określonym indeksie.|
|[operator +](#operator_add)|Zwraca nowy `extent` obiekt, który został utworzony przez dodanie odpowiadających `index` im `extent` elementów i.|
|[operator + +](#operator_add_add)|Zwiększa każdy element `extent` obiektu.|
|[operator + =](#operator_add_eq)|Dodaje określoną liczbę do każdego elementu `extent` obiektu.|
|[operator =](#operator_eq)|Kopiuje zawartość innego `extent` obiektu do tego.|
|[operator-=](#operator_min_eq)|Odejmuje określoną liczbę od każdego elementu `extent` obiektu.|

### <a name="public-constants"></a>Stałe publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Stała rangi](#rank_constant)|Pobiera rangę `extent` obiektu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`extent`

## <a name="contains"></a><a name="contains"></a>wyświetlana

Wskazuje, czy określona wartość [indeksu](index-class.md) jest zawarta w obiekcie "zakres".

### <a name="syntax"></a>Składnia

```cpp
bool contains(const index<rank>& _Index) const restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
`index`Wartość do przetestowania.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli określona wartość *indeksu* jest zawarta w `extent` obiekcie; w przeciwnym razie **`false`** .

## <a name="extent"></a><a name="ctor"></a>rozmiaru

Inicjuje nowe wystąpienie klasy "zakres".

### <a name="syntax"></a>Składnia

```cpp
extent() restrict(amp,cpu);
extent(const extent<_Rank>& _Other) restrict(amp,cpu);
explicit extent(int _I) restrict(amp,cpu);
extent(int _I0,  int _I1) restrict(amp,cpu);
extent(int _I0,  int _I1, int _I2) restrict(amp,cpu);
explicit extent(const int _Array[_Rank])restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Array*<br/>
Tablica `_Rank` liczb całkowitych, która jest używana do tworzenia nowego `extent` obiektu.

*_I*<br/>
Długość zakresu.

*_I0*<br/>
Długość najbardziej znaczącego wymiaru.

*_I1*<br/>
Długość kolejnego najbardziej znaczącego wymiaru.

*_I2*<br/>
Długość najmniej znaczącego wymiaru.

*_Other*<br/>
`extent`Obiekt, na którym `extent` bazuje Nowy obiekt.

## <a name="remarks"></a>Uwagi

Konstruktor domyślny inicjuje `extent` obiekt mający rangę trzech.

Jeśli tablica jest używana do konstruowania `extent` obiektu, Długość tablicy musi być zgodna z rangą `extent` obiektu.

## <a name="operator"></a><a name="operator_mod_eq"></a>operator% =

Oblicza moduł (resztę) każdego elementu w zakresie, gdy ten element jest podzielony przez liczbę.

### <a name="syntax"></a>Składnia

```cpp
extent<_Rank>& operator%=(int _Rhs) restrict(cpu, direct3d);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Liczba, w której ma zostać znaleziony moduł.

### <a name="return-value"></a>Wartość zwracana

Obiekt `extent`.

## <a name="operator"></a><a name="operator_star_eq"></a>operator * =

Mnoży każdy element w obiekcie "zakres" przez określoną liczbę.

### <a name="syntax"></a>Składnia

```cpp
extent<_Rank>& operator*=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Liczba do pomnożenia.

### <a name="return-value"></a>Wartość zwracana

Obiekt `extent`.

## <a name="operator"></a><a name="operator_add"></a>operator +

Zwraca nowy `extent` obiekt utworzony przez dodanie odpowiadających `index` elementów i `extent` .

### <a name="syntax"></a>Składnia

```cpp
extent<_Rank> operator+(const index<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
`index`Obiekt, który zawiera elementy do dodania.

### <a name="return-value"></a>Wartość zwracana

Nowy obiekt `extent`.

## <a name="operator"></a><a name="operator_add_add"></a>operator + +

Zwiększa każdy element obiektu "zakres".

### <a name="syntax"></a>Składnia

```cpp
extent<_Rank>& operator++() restrict(amp,cpu);
extent<_Rank> operator++(int)restrict(amp,cpu);
```

### <a name="return-value"></a>Wartość zwracana

Dla operatora prefiksu `extent` obiekt ( **`*this`** ). Nowy obiekt dla operatora sufiksu `extent` .

## <a name="operator"></a><a name="operator_add_eq"></a>operator + =

Dodaje określoną liczbę do każdego elementu obiektu "zakres".

### <a name="syntax"></a>Składnia

```cpp
extent<_Rank>& operator+=(const extent<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator+=(const index<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator+=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Liczba, indeks lub zakres do dodania.

### <a name="return-value"></a>Wartość zwracana

Obiekt wyników `extent` .

## <a name="operator-"></a><a name="operator_min"></a>zakład

Tworzy nowy `extent` obiekt przez odjęcie każdego elementu w określonym `index` obiekcie od odpowiedniego elementu w tym `extent` obiekcie.

### <a name="syntax"></a>Składnia

```cpp
extent<_Rank> operator-(const index<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
`index`Obiekt, który zawiera elementy do odejmowania.

### <a name="return-value"></a>Wartość zwracana

Nowy obiekt `extent`.

## <a name="operator--"></a><a name="operator_min_min"></a>operator--

Zmniejsza każdy element w obiekcie "zakres".

### <a name="syntax"></a>Składnia

```cpp
extent<_Rank>& operator--() restrict(amp,cpu);
extent<_Rank> operator--(int)restrict(amp,cpu);
```

### <a name="return-value"></a>Wartość zwracana

Dla operatora prefiksu `extent` obiekt ( **`*this`** ). Nowy obiekt dla operatora sufiksu `extent` .

## <a name="operator"></a><a name="operator_div_eq"></a>operator/=

Dzieli każdy element w obiekcie "zakres" przez określoną liczbę.

### <a name="syntax"></a>Składnia

```cpp
extent<_Rank>& operator/=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Liczba, przez którą ma zostać podzielona wartość.

### <a name="return-value"></a>Wartość zwracana

Obiekt `extent`.

## <a name="operator-"></a><a name="operator_min_eq"></a>operator-=

Odejmuje określoną liczbę od każdego elementu obiektu "zakres".

### <a name="syntax"></a>Składnia

```cpp
extent<_Rank>& operator-=(const extent<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator-=(const index<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator-=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Liczba do odjęcia.

### <a name="return-value"></a>Wartość zwracana

Obiekt wyników `extent` .

## <a name="operator"></a><a name="operator_eq"></a>operator =

Kopiuje zawartość innego obiektu "zakres" do tego elementu.

### <a name="syntax"></a>Składnia

```cpp
extent<_Rank>& operator=(const extent<_Rank>& _Other) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
`extent`Obiekt, z którego mają zostać skopiowane.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do tego `extent` obiektu.

## <a name="extentoperator-"></a><a name="operator_at"></a>zakres:: operator\[\]

Zwraca element, który znajduje się w określonym indeksie.

### <a name="syntax"></a>Składnia

```cpp
int operator[](unsigned int _Index) const restrict(amp,cpu);
int& operator[](unsigned int _Index) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Liczba całkowita z zakresu od 0 do rangi minus 1.

### <a name="return-value"></a>Wartość zwracana

Element o określonym indeksie.

## <a name="rank"></a><a name="rank_constant"></a>stopni

Przechowuje rangę obiektu "zakres".

### <a name="syntax"></a>Składnia

```cpp
static const int rank = _Rank;
```

## <a name="size"></a><a name="size"></a>zmienia

Zwraca łączny rozmiar liniowy `extent` obiektu (w jednostkach elementów).

### <a name="syntax"></a>Składnia

```cpp
unsigned int size() const restrict(amp,cpu);
```

## <a name="tile"></a><a name="tile"></a>tabliczek

Tworzy obiekt tiled_extent o określonym wymiarze kafelka.

```cpp
template <int _Dim0>
tiled_extent<_Dim0> tile() const ;

template <int _Dim0, int _Dim1>
tiled_extent<_Dim0, _Dim1> tile() const ;

template <int _Dim0, int _Dim1, int _Dim2>
tiled_extent<_Dim0, _Dim1, _Dim2> tile() const ;
```

### <a name="parameters"></a>Parametry

*_Dim0*<br/>
Najbardziej znaczący składnik zakresu.
*_Dim1*<br/>
Najbardziej znaczący składnik najbardziej znaczącego fragmentu.
*_Dim2*<br/>
Najmniej znaczący składnik w zakresie rozpiętym.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
