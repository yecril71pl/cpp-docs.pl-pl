---
title: index — Klasa
ms.date: 03/27/2019
f1_keywords:
- AMP/index
- AMP/Concurrency::index::index
- AMP/Concurrency::index::rank
helpviewer_keywords:
- index structure
ms.assetid: cbe79b08-0ba7-474c-9828-f1a71da39eb3
ms.openlocfilehash: 50222015e6b365dc161fd4334067c26c7f288337
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365153"
---
# <a name="index-class"></a>index — Klasa

Definiuje wektor indeksu N-wymiarowego. *N*

## <a name="syntax"></a>Składnia

```cpp
template <int _Rank>
class index;
```

### <a name="parameters"></a>Parametry

*_Rank*<br/>
Ranga lub liczba wymiarów.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Konstruktor indeksu](#index_ctor)|Inicjuje nowe wystąpienie klasy `index`.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[operator --](#operator--)|Zmniejsza każdy element `index` obiektu.|
|[operator%=](#operator_mod_eq)|Oblicza moduł (pozostałość) każdego elementu `index` w obiekcie, gdy ten element jest podzielony przez liczbę.|
|[operator*=](#operator_star_eq)|Mnoży każdy `index` element obiektu przez liczbę.|
|[operator/=](#operator_div_eq)|Dzieli każdy element `index` obiektu przez liczbę.|
|[indeks::operator\[\]](#operator_at)|Zwraca element, który znajduje się w określonym indeksie.|
|[operator++](#operator_add_add)|Zwiększa każdy element `index` obiektu.|
|[operator+=](#operator_add_eq)|Dodaje określoną liczbę do `index` każdego elementu obiektu.|
|[operator=](#operator_eq)|Kopiuje zawartość określonego `index` obiektu do tego obiektu.|
|[operator-=](#operator_-_eq)|Odejmuje określoną liczbę od `index` każdego elementu obiektu.|

### <a name="public-constants"></a>Stałe publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Stała ranga](#rank)|Przechowuje rangę `index` obiektu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`index`

## <a name="remarks"></a>Uwagi

Struktura `index` reprezentuje wektor współrzędnych *N* liczby całkowite, który określa unikatową pozycję w przestrzeni *N*-wymiarowe. Wartości wektora są uporządkowane od najbardziej znaczących do najmniej znaczących. Wartości komponentów można pobrać za pomocą [operatora=](#operator_eq).

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp.h

**Obszar nazw:** Współbieżności

## <a name="index-constructor"></a><a name="index_ctor"></a>Konstruktor indeksu

Inicjuje nowe wystąpienie klasy indeksu.

```cpp
index() restrict(amp,cpu);

index(
   const index<_Rank>& _Other
) restrict(amp,cpu);

explicit index(
   int _I
) restrict(amp,cpu);

index(
   int _I0,
   int _I1
) restrict(amp,cpu);

index(
   int _I0,
   int _I1,
   int _I2
) restrict(amp,cpu);

explicit index(
   const int _Array[_Rank]
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Array*<br/>
Tablica jednowymiarowa z wartościami rangi.

*_I*<br/>
Lokalizacja indeksu w indeksie jednowymiarowym.

*_I0*<br/>
Długość najważniejszego wymiaru.

*_I1*<br/>
Długość wymiaru następnego do najbardziej znaczącego.

*_I2*<br/>
Długość najmniej istotnego wymiaru.

*_Other*<br/>
Obiekt indeksu, na którym opiera się nowy obiekt indeksu.

## <a name="operator--"></a><a name="operator--"></a>operator --

Zmniejsza każdy element obiektu indeksu.

```cpp
index<_Rank>& operator--() restrict(amp,cpu);

index operator--(
   int
) restrict(amp,cpu);
```

### <a name="return-values"></a>Zwracane wartości

Dla operatora prefiksu obiektu indeksu (*this). Dla operatora sufiksu nowy obiekt indeksu.

## <a name="operator"></a><a name="operator_mod_eq"></a>operator%=

Oblicza moduł (reszta) każdego elementu w obiekcie indeksu, gdy ten element jest podzielony przez określoną liczbę.

```cpp
index<_Rank>& operator%=(
   int _Rhs
) restrict(cpu, amp);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Liczba do podzielenia przez, aby znaleźć moduł.

## <a name="return-value"></a>Wartość zwracana

Obiekt indeksu.

## <a name="operator"></a><a name="operator_star_eq"></a>operator*=

Mnoży każdy element w obiekcie indeksu przez określoną liczbę.

```cpp
index<_Rank>& operator*=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Liczba do pomnożenia.

## <a name="operator"></a><a name="operator_div_eq"></a>operator/=

Dzieli każdy element w obiekcie indeksu przez określoną liczbę.

```cpp
index<_Rank>& operator/=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Liczba do podzielenia.

## <a name="operator"></a><a name="operator_at"></a>Operator\[\]

Zwraca składnik indeksu w określonej lokalizacji.

```cpp
int operator[] (
   unsigned _Index
) const restrict(amp,cpu);

int& operator[] (
   unsigned _Index
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Liczba całkowita od 0 do rangi minus 1.

### <a name="return-value"></a>Wartość zwracana

Element, który jest w określonym indeksie.

### <a name="remarks"></a>Uwagi

W tym przykładzie są wyświetlane wartości składowe indeksu.

```cpp
// Prints 1 2 3.
concurrency::index<3> idx(1, 2, 3);
std::cout << idx[0] << "\n";
std::cout << idx[1] << "\n";
std::cout << idx[2] << "\n";
```

## <a name="operator"></a><a name="operator_add_add"></a>operator++

Zwiększa każdy element obiektu indeksu.

```cpp
index<_Rank>& operator++() restrict(amp,cpu);

index<_Rank> operator++(
   int
) restrict(amp,cpu);
```

### <a name="return-value"></a>Wartość zwracana

Dla operatora prefiksu obiektu indeksu (*this). Dla operatora sufiksu nowy obiekt indeksu.

## <a name="operator"></a><a name="operator_add_eq"></a>operator+=

Dodaje określoną liczbę do każdego elementu obiektu indeksu.

```cpp
index<_Rank>& operator+=(
   const index<_Rank>& _Rhs
) restrict(amp,cpu);

index<_Rank>& operator+=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Liczba do dodania.

### <a name="return-value"></a>Wartość zwracana

Obiekt indeksu.

## <a name="operator"></a><a name="operator_eq"></a>operator=

Kopiuje zawartość określonego obiektu indeksu do tego obiektu.

```cpp
index<_Rank>& operator=(
   const index<_Rank>& _Other
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
Obiekt indeksu do skopiowania z.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do tego obiektu indeksu.

## <a name="operator-"></a><a name="operator_-_eq"></a>operator-=

Odejmuje określoną liczbę od każdego elementu obiektu indeksu.

```cpp
index<_Rank>& operator-=(
   const index<_Rank>& _Rhs
) restrict(amp,cpu);

index<_Rank>& operator-=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Liczba do odjęcie.

### <a name="return-value"></a>Wartość zwracana

Obiekt indeksu.

## <a name="rank"></a><a name="rank"></a>Rank

Pobiera rangę obiektu indeksu.

```cpp
static const int rank = _Rank;
```

## <a name="see-also"></a>Zobacz też

[Obszar nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
