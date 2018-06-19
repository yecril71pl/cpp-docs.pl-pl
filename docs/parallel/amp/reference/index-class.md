---
title: Indeks klasy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- AMP/index
- AMP/Concurrency::index::index
- AMP/Concurrency::index::rank
dev_langs:
- C++
helpviewer_keywords:
- index structure
ms.assetid: cbe79b08-0ba7-474c-9828-f1a71da39eb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 594ee94bbbfc19bc6fcceb9ae7f0760d9ec877dc
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33695340"
---
# <a name="index-class"></a>index — Klasa
Definiuje *N*-wymiarowy indeksu pographics-cpp-amp.md.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <int _Rank>  
class index;  
```  
  
#### <a name="parameters"></a>Parametry  
 `_Rank`  
 Ranga lub liczbę wymiarów.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Indeks — Konstruktor](#ctor)|Inicjuje nowe wystąpienie klasy `index` klasy.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[operator--](#operator--)|Zmniejsza każdy element `index` obiektu.|  
|[Operator(MOD) =](#operator_mod_eq)|Oblicza modułu (reszty) poszczególnych elementów `index` obiektu, gdy ten element jest dzielona przez liczbę.|  
|[operator*=](#operator_star_eq)|Mnoży każdy element `index` obiektu liczbą.|  
|[/ = — operator](#operator_div_eq)|Dzieli każdy element `index` obiektu liczbą.|  
|[index::operator\[\]](#operator_at)|Zwraca element pod określonym indeksem.|  
|[operator++](#operator_add_add)|Zwiększa każdy element `index` obiektu.|  
|[operator+=](#operator_add_eq)|Dodaje określoną liczbę do każdego elementu `index` obiektu.|  
|[operator=](#operator_eq)|Kopiuje zawartość określonego `index` obiektu do tego.|  
|[operator-=](#operator_-_eq)|Odejmuje określoną liczbą z każdego elementu `index` obiektu.|  

  
### <a name="public-constants"></a>Publiczny — stałe  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Rank — stała](#rank)|Przechowuje rangę `index` obiektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `index`  
  
## <a name="remarks"></a>Uwagi  
 `index` Struktury reprezentuje współrzędnych wektor *N* liczb całkowitych, które określają unikatowe położenie w *N*-przestrzeni trójwymiarowej. Wartości w wektorze są uporządkowane od najważniejszych do najmniej znaczący. Można pobrać wartości składników za pomocą [operatora =](#operator_eq).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** amp.h  
  
 **Namespace:** współbieżności  


## <a name="index_ctor"></a> Indeks — Konstruktor
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

_Array  
Jednowymiarowa tablica o wartości klasyfikacji.  
_I  
Lokalizacja indeksu w indeksie jednowymiarowa.  
_I0  
Długość najważniejszych wymiaru.  
_I1  
Długość dalej do większość — znaczące wymiaru.  
_I2  
Długość najmniej znaczący wymiaru.  
_Other  
Obiekt indeksu, na której oparto nowy obiekt indeksu.  

## <a name="operator--"></a>  operator--
Zmniejsza każdy element obiekt indeksu.  
```  
index<_Rank>& operator--() restrict(amp,cpu);  

index operator--(
   int
) restrict(amp,cpu);
```  
### <a name="return-values"></a>Zwracane wartości
Dla operatora prefiksu, obiekt indeksu (* to). Dla operatora sufiks nowy obiekt w indeksie.

## <a name="operator_mod_eq"></a>  Operator(MOD) =   
Oblicza modułu (reszty) każdego elementu w obiekcie indeksu, gdy ten element jest dzielona o określoną liczbę.

```  
index<_Rank>& operator%=(
   int _Rhs
) restrict(cpu, amp);
```  
### <a name="parameters"></a>Parametry
_Rhs liczbę do dzielenia przez, aby znaleźć resztę.
Zwraca wartość obiektu indeksu.

## <a name="operator_star_eq"></a>  operator * =   
Mnoży każdego elementu w obiekcie indeksu o określoną liczbę.
```
index<_Rank>& operator*=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry
_Rhs liczbę Aby pomnożyć.

## <a name="operator_div_eq"></a>  / = — operator 
Dzieli każdego elementu w obiekcie indeksu o określoną liczbę.

```
index<_Rank>& operator/=(
   int _Rhs
) restrict(amp,cpu);
``` 
### <a name="parameters"></a>Parametry
_Rhs liczbę do dzielenia przez.

## <a name="operator_at"></a>  Operator\[\]  
Zwraca składnik w określonej lokalizacji indeksu.

```
int operator[] (
   unsigned _Index
) const restrict(amp,cpu);

int& operator[] (
   unsigned _Index
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry
_Index całkowitą z przedziału od 0 do rangi pomniejszonej o 1.

### <a name="return-value"></a>Wartość zwracana
Element pod określonym indeksem.

### <a name="remarks"></a>Uwagi
Poniższy przykład przedstawia wartości składnik indeksu.
```  
// Prints 1 2 3.
concurrency::index<3> idx(1, 2, 3);
std::cout << idx[0] << "\n";
std::cout << idx[1] << "\n";
std::cout << idx[2] << "\n";
```

## <a name="operator_add_add"></a>  operator ++   
Zwiększa każdy element obiekt indeksu.
```  
index<_Rank>& operator++() restrict(amp,cpu);

index<_Rank> operator++(
   int
) restrict(amp,cpu);
```  
### <a name="return-value"></a>Wartość zwracana
Dla operatora prefiksu, obiekt indeksu (* to). Dla operatora sufiks nowy obiekt w indeksie.

## <a name="operator_add_eq"></a>  += — operator   
Dodaje określoną liczbę do każdego elementu obiekt indeksu.
```  
index<_Rank>& operator+=(
   const index<_Rank>& _Rhs
) restrict(amp,cpu);

index<_Rank>& operator+=(
   int _Rhs
) restrict(amp,cpu);
``` 
### <a name="parameters"></a>Parametry
_Rhs numer do dodania.

### <a name="return-value"></a>Wartość zwracana
Obiekt indeksu.

## <a name="operator_eq"></a>  operator =   
Kopiuje zawartość w określonym indeksie obiektu do tego.
```  
index<_Rank>& operator=(
   const index<_Rank>& _Other
) restrict(amp,cpu);
``` 
### <a name="parameters"></a>Parametry
_Other obiekt indeksu do skopiowania.

### <a name="return-value"></a>Wartość zwracana
Odwołanie do tego obiektu indeksu.

## <a name="operator_-_eq"></a>  operator-=
Odejmuje określonej liczby z każdego elementu obiekt indeksu.
```  
index<_Rank>& operator-=(
   const index<_Rank>& _Rhs
) restrict(amp,cpu);

index<_Rank>& operator-=(
   int _Rhs
) restrict(amp,cpu);
```  
### <a name="parameters"></a>Parametry
_Rhs numer do odjęcia.

### <a name="return-value"></a>Wartość zwracana
Obiekt indeksu.   

## <a name="rank"></a>  Ranga  
  Pobiera pozycję obiekt indeksu.
```
static const int rank = _Rank;
``` 
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
