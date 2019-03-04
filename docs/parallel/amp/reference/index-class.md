---
title: index — Klasa
ms.date: 11/04/2016
f1_keywords:
- AMP/index
- AMP/Concurrency::index::index
- AMP/Concurrency::index::rank
helpviewer_keywords:
- index structure
ms.assetid: cbe79b08-0ba7-474c-9828-f1a71da39eb3
ms.openlocfilehash: 054db83e4d8e140af37dcff9a7664ffdf7902325
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57284648"
---
# <a name="index-class"></a>index — Klasa

Definiuje *N*-wymiarowej indeksu pographics-cpp-amp.md.

## <a name="syntax"></a>Składnia

```
template <int _Rank>
class index;
```

#### <a name="parameters"></a>Parametry

*_Rank*<br/>
Ranga lub liczba wymiarów.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Indeks konstruktora](#ctor)|Inicjuje nowe wystąpienie klasy `index` klasy.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[operator--](#operator--)|Zmniejsza o jeden każdy element obiektu `index` obiektu.|
|[Operator(MOD) =](#operator_mod_eq)|Oblicza moduł (resztę) każdego elementu w `index` obiektu, gdy ten element jest dzielona przez liczbę.|
|[operator*=](#operator_star_eq)|Mnoży każdy element obiektu `index` przez liczbę.|
|[operator/=](#operator_div_eq)|Dzieli każdy element obiektu `index` przez liczbę.|
|[index::operator\[\]](#operator_at)|Zwraca element, który jest umieszczony pod określonym indeksem.|
|[operator++](#operator_add_add)|Zwiększa każdy element obiektu `index` obiektu.|
|[operator+=](#operator_add_eq)|Dodaje określoną liczbę do każdego elementu `index` obiektu.|
|[operator=](#operator_eq)|Kopiuje zawartość określonego `index` obiektu do wskazanego.|
|[operator-=](#operator_-_eq)|Odejmuje określoną liczbę od każdego elementu obiektu `index` obiektu.|

### <a name="public-constants"></a>Publiczne stałe

|Nazwa|Opis|
|----------|-----------------|
|[rank Constant](#rank)|Przechowuje rangę `index` obiektu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`index`

## <a name="remarks"></a>Uwagi

`index` Struktury reprezentuje wektor współrzędnych *N* liczb całkowitych, które określa unikatową pozycję w *N*-wymiarowej przestrzeni. Wartości w wektorze są uporządkowane od najbardziej do najmniej znaczących. Można pobrać wartości składników za pomocą [operator =](#operator_eq).

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp.h

**Namespace:** Współbieżność

## <a name="index_ctor"></a> Indeks konstruktora

Inicjuje nowe wystąpienie klasy indeksu.

```
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
Jednowymiarowa tablica wartości rangi.

*_I*<br/>
Lokalizacja indeksu w indeksie jednowymiarowym.

*_I0*<br/>
Długość najbardziej znaczącego wymiaru.

*_I1*<br/>
Długość następnego do najbardziej znaczący wymiar.

*_I2*<br/>
Długość najmniej znaczącego wymiaru.

*_Inne*<br/>
Obiekt indeksu, na którym opiera się nowy obiekt indeksu.

## <a name="operator--"></a>  operator--

Zmniejsza o jeden każdy element obiektu indeksu.
```
index<_Rank>& operator--() restrict(amp,cpu);

index operator--(
   int
) restrict(amp,cpu);
```

### <a name="return-values"></a>Zwracane wartości

Dla operatora prefiksowego obiekt indeksu (* to). Dla operatora sufiksowego, nowy obiekt indeksu.

## <a name="operator_mod_eq"></a>  Operator(MOD) =

Oblicza moduł (resztę) każdego elementu w obiekcie indeksu, gdy ten element jest dzielona przez określoną liczbę.

```
index<_Rank>& operator%=(
   int _Rhs
) restrict(cpu, amp);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Liczba do podzielenia przez, aby znaleźć resztę.

## <a name="return-value"></a>Wartość zwracana
Obiekt indeksu.

## <a name="operator_star_eq"></a>  operator * =

Mnoży każdy element w obiekcie indeksu przez określoną liczbę.
```
index<_Rank>& operator*=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Liczbę Aby pomnożyć.

## <a name="operator_div_eq"></a>  operator / =

Dzieli każdy element w obiekcie indeksu przez określoną liczbę.

```
index<_Rank>& operator/=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Liczba do podzielenia przez.

## <a name="operator_at"></a>  Operator\[\]

Zwraca składnik indeksu w określonej lokalizacji.

```
int operator[] (
   unsigned _Index
) const restrict(amp,cpu);

int& operator[] (
   unsigned _Index
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*Parametr _Index*<br/>
Liczba całkowita z zakresu od 0 do rangi minus 1.

### <a name="return-value"></a>Wartość zwracana

Element, który jest umieszczony pod określonym indeksem.

### <a name="remarks"></a>Uwagi

Poniższy przykład wyświetla wartości składnika indeksu.
```
// Prints 1 2 3.
concurrency::index<3> idx(1, 2, 3);
std::cout << idx[0] << "\n";
std::cout << idx[1] << "\n";
std::cout << idx[2] << "\n";
```

## <a name="operator_add_add"></a>  operator ++

Zwiększa każdy element obiektu indeksu.
```
index<_Rank>& operator++() restrict(amp,cpu);

index<_Rank> operator++(
   int
) restrict(amp,cpu);
```

### <a name="return-value"></a>Wartość zwracana

Dla operatora prefiksowego obiekt indeksu (* to). Dla operatora sufiksowego, nowy obiekt indeksu.

## <a name="operator_add_eq"></a>  += — operator

Dodaje określoną liczbę do każdego elementu obiektu indeksu.
```
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

## <a name="operator_eq"></a>  operator =

Kopiuje zawartość obiektu określonego indeksu do wskazanego.
```
index<_Rank>& operator=(
   const index<_Rank>& _Other
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Inne*<br/>
Obiekt indeksu do skopiowania.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do tego obiektu indeksu.

## <a name="operator_-_eq"></a>  operator-=

Odejmuje określoną liczbę od każdego elementu obiektu indeksu.
```
index<_Rank>& operator-=(
   const index<_Rank>& _Rhs
) restrict(amp,cpu);

index<_Rank>& operator-=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Liczba odejmowana.

### <a name="return-value"></a>Wartość zwracana

Obiekt indeksu.

## <a name="rank"></a>  Ranga
  Pobiera liczbę wymiarów obiektu indeksu.
```
static const int rank = _Rank;
```

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
