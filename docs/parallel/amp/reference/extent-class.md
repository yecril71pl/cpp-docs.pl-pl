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
ms.openlocfilehash: 3e8dae7b76ea2efc852486a19f5d298cda477012
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126724"
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
Ranga obiektu `extent`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp. h

**Przestrzeń nazw:** Współbieżności

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Konstruktor zakresów](#ctor)|Inicjuje nowe wystąpienie klasy `extent`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[wyświetlana](#contains)|Sprawdza, czy określony obiekt `extent` ma określoną rangę.|
|[zmienia](#size)|Zwraca łączny rozmiar liniowy zakresu (w jednostkach elementów).|
|[tabliczek](#tile)|Tworzy obiekt `tiled_extent` z zakresami kafelków podanymi przez określone wymiary.|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[zakład](#operator_min)|Zwraca nowy obiekt `extent`, który jest tworzony przez odjęcie elementów `index` z odpowiednich `extent` elementów.|
|[operator--](#operator_min_min)|Zmniejsza każdy element obiektu `extent`.|
|[operator% =](#operator_mod_eq)|Oblicza moduł (resztę) każdego elementu w obiekcie `extent`, gdy ten element jest dzielony przez liczbę.|
|[operator * =](#operator_star_eq)|Mnoży każdy element obiektu `extent` przez liczbę.|
|[operator/=](#operator_min_eq)|Dzieli każdy element obiektu `extent` przez liczbę.|
|[zakres:: operator\[\]](#operator_at)|Zwraca element, który znajduje się w określonym indeksie.|
|[operator +](#operator_add)|Zwraca nowy obiekt `extent`, który jest tworzony przez dodanie odpowiednich `index` i `extent` elementów.|
|[operator + +](#operator_add_add)|Zwiększa każdy element obiektu `extent`.|
|[operator + =](#operator_add_eq)|Dodaje określoną liczbę do każdego elementu obiektu `extent`.|
|[operator =](#operator_eq)|Kopiuje zawartość innego obiektu `extent` do tego.|
|[operator-=](#operator_min_eq)|Odejmuje określoną liczbę od każdego elementu `extent` obiektu.|

### <a name="public-constants"></a>Stałe publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Stała rangi](#rank_constant)|Pobiera rangę obiektu `extent`.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`extent`

## <a name="contains"></a>wyświetlana

Wskazuje, czy określona wartość [indeksu](index-class.md) jest zawarta w obiekcie "zakres".

### <a name="syntax"></a>Składnia

```cpp
bool contains(const index<rank>& _Index) const restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Wartość `index` do przetestowania.

### <a name="return-value"></a>Wartość zwrócona

**wartość true** , jeśli określona wartość *indeksu* jest zawarta w obiekcie `extent`; w przeciwnym razie **false**.

## <a name="ctor"></a>rozmiaru

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
Tablica `_Rank` liczb całkowitych, która jest używana do tworzenia nowego obiektu `extent`.

*_I*<br/>
Długość zakresu.

*_I0*<br/>
Długość najbardziej znaczącego wymiaru.

*_I1*<br/>
Długość kolejnego najbardziej znaczącego wymiaru.

*_I2*<br/>
Długość najmniej znaczącego wymiaru.

*_Other*<br/>
Obiekt `extent`, na którym jest oparty nowy obiekt `extent`.

## <a name="remarks"></a>Uwagi

Konstruktor domyślny inicjuje obiekt `extent`, który ma rangę trzech.

Jeśli tablica jest używana do konstruowania obiektu `extent`, Długość tablicy musi być zgodna z rangą `extent` obiektu.

## <a name="operator_mod_eq"></a>operator% =

Oblicza moduł (resztę) każdego elementu w zakresie, gdy ten element jest podzielony przez liczbę.

### <a name="syntax"></a>Składnia

```cpp
extent<_Rank>& operator%=(int _Rhs) restrict(cpu, direct3d);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Liczba, w której ma zostać znaleziony moduł.

### <a name="return-value"></a>Wartość zwrócona

Obiekt `extent`.

## <a name="operator_star_eq"></a>operator * =

Mnoży każdy element w obiekcie "zakres" przez określoną liczbę.

### <a name="syntax"></a>Składnia

```cpp
extent<_Rank>& operator*=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Liczba do pomnożenia.

### <a name="return-value"></a>Wartość zwrócona

Obiekt `extent`.

## <a name="operator_add"></a>operator +

Zwraca nowy obiekt `extent` utworzony przez dodanie odpowiednich `index` i `extent` elementów.

### <a name="syntax"></a>Składnia

```cpp
extent<_Rank> operator+(const index<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Obiekt `index`, który zawiera elementy do dodania.

### <a name="return-value"></a>Wartość zwrócona

Nowy obiekt `extent`.

## <a name="operator_add_add"></a>operator + +

Zwiększa każdy element obiektu "zakres".

### <a name="syntax"></a>Składnia

```cpp
extent<_Rank>& operator++() restrict(amp,cpu);
extent<_Rank> operator++(int)restrict(amp,cpu);
```

### <a name="return-value"></a>Wartość zwrócona

Dla operatora prefiksu obiekt `extent` (`*this`). Dla operatora sufiksu nowy obiekt `extent`.

## <a name="operator_add_eq"></a>operator + =

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

### <a name="return-value"></a>Wartość zwrócona

Otrzymany `extent` obiekt.

## <a name="operator_min"></a>zakład

Tworzy nowy obiekt `extent` poprzez odjęcie każdego elementu w określonym obiekcie `index` z odpowiedniego elementu w tym obiekcie `extent`.

### <a name="syntax"></a>Składnia

```cpp
extent<_Rank> operator-(const index<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Obiekt `index`, który zawiera elementy do odejmowania.

### <a name="return-value"></a>Wartość zwrócona

Nowy obiekt `extent`.

## <a name="operator_min_min"></a>operator--

Zmniejsza każdy element w obiekcie "zakres".

### <a name="syntax"></a>Składnia

```cpp
extent<_Rank>& operator--() restrict(amp,cpu);
extent<_Rank> operator--(int)restrict(amp,cpu);
```

### <a name="return-value"></a>Wartość zwrócona

Dla operatora prefiksu obiekt `extent` (`*this`). Dla operatora sufiksu nowy obiekt `extent`.

## <a name="operator_div_eq"></a>operator/=

Dzieli każdy element w obiekcie "zakres" przez określoną liczbę.

### <a name="syntax"></a>Składnia

```cpp
extent<_Rank>& operator/=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Liczba, przez którą ma zostać podzielona wartość.

### <a name="return-value"></a>Wartość zwrócona

Obiekt `extent`.

## <a name="operator_min_eq"></a>operator-=

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

### <a name="return-value"></a>Wartość zwrócona

Otrzymany `extent` obiekt.

## <a name="operator_eq"></a>operator =

Kopiuje zawartość innego obiektu "zakres" do tego elementu.

### <a name="syntax"></a>Składnia

```cpp
extent<_Rank>& operator=(const extent<_Rank>& _Other) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
Obiekt `extent`, z którego ma być kopiowany.

### <a name="return-value"></a>Wartość zwrócona

Odwołanie do tego obiektu `extent`.

## <a name="operator_at"></a>zakres:: operator \[\]

Zwraca element, który znajduje się w określonym indeksie.

### <a name="syntax"></a>Składnia

```cpp
int operator[](unsigned int _Index) const restrict(amp,cpu);
int& operator[](unsigned int _Index) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Liczba całkowita z zakresu od 0 do rangi minus 1.

### <a name="return-value"></a>Wartość zwrócona

Element o określonym indeksie.

## <a name="rank_constant"></a>stopni

Przechowuje rangę obiektu "zakres".

### <a name="syntax"></a>Składnia

```cpp
static const int rank = _Rank;
```

## <a name="size"></a>zmienia

Zwraca łączny rozmiar liniowy obiektu `extent` (w jednostkach elementów).

### <a name="syntax"></a>Składnia

```cpp
unsigned int size() const restrict(amp,cpu);
```

## <a name="tile"></a>tabliczek

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

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
