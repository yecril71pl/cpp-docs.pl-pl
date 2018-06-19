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
ms.openlocfilehash: 901ba590d208db7c9cf3803e77e8481a2b896ea2
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33693253"
---
# <a name="extent-class-c-amp"></a>extent — Klasa (C++ AMP)
Reprezentuje wektorem *N* całkowitych wartości, które określają granice *N*-przestrzeni trójwymiarowej zawierający początek 0. Wartości w wektorze są uporządkowane od najważniejszych do najmniej znaczący.  
  
### <a name="syntax"></a>Składnia  
  
```  
template <int _Rank>  
class extent;  
```  
  
### <a name="parameters"></a>Parametry  
 `_Rank`  
 Rangę `extent` obiektu.  

 ## <a name="requirements"></a>Wymagania  
 **Nagłówek:** amp.h  
  
 **Namespace:** współbieżności  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Extent — Konstruktor](#ctor)|Inicjuje nowe wystąpienie klasy `extent` klasy.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[zawiera](#contains)|Sprawdza, czy określony `extent` obiekt ma określony rangę.|  
|[Rozmiar](#size)|Zwraca całkowity rozmiar liniowej zakres (w jednostkach elementów).|  
|[Kafelek](#tile)|Tworzy `tiled_extent` obiektu z zakresów kafelka określonego przez określony wymiarów.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[operator-](#operator_min)|Zwraca nowy `extent` obiektu, który jest tworzony przez odjęcie `index` elementy z odpowiedniego `extent` elementów.|  
|[operator--](#operator_min_min)|Zmniejsza każdy element `extent` obiektu.|  
|[operator%=](#operator_mod_eq)|Oblicza modułu (reszty) poszczególnych elementów `extent` obiektu, gdy ten element jest dzielona przez liczbę.|  
|[operator*=](#operator_star_eq)|Mnoży każdy element `extent` obiektu liczbą.|  
|[/ = — operator](#operator_min_eq)|Dzieli każdy element `extent` obiektu liczbą.|  
|[Extent::operator\[\]](#operator_at)|Zwraca element pod określonym indeksem.|  
|[operator +](#operator_add)|Zwraca nowy `extent` obiektu, który jest tworzony przez dodanie odpowiednich `index` i `extent` elementy.|  
|[operator++](#operator_add_add)|Zwiększa każdy element `extent` obiektu.|  
|[operator+=](#operator_add_eq)|Dodaje określoną liczbę do każdego elementu `extent` obiektu.|  
|[operator=](#operator_eq)|Kopiuje zawartość innego `extent` obiektu do tego.|  
|[operator-=](#operator_min_eq)|Odejmuje określoną liczbą z każdego elementu `extent` obiektu.|  

  
### <a name="public-constants"></a>Publiczny — stałe  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Rank — stała](#rank)|Pobiera pozycję `extent` obiektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `extent`  


## <a name="contains"></a> zawiera 

Wskazuje, czy określony [indeksu](index-class.md) wartość znajduje się w obiekcie "zakresu".  
  
### <a name="syntax"></a>Składnia  
  
```  
bool contains(const index<rank>& _Index) const restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>Parametry  
 `_Index`  
 `index` Wartość do sprawdzenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli określony `index` wartość znajduje się w `extent` obiektu; w przeciwnym razie `false`.  
  
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
 `_Array`  
 Tablica `_Rank` liczb całkowitych, które jest używane do tworzenia nowego `extent` obiektu.  
  
 `_I`  
 Długość zakresu.  
  
 `_I0`  
 Długość najważniejszych wymiaru.  
  
 `_I1`  
 Długość dalej do większość — znaczące wymiaru.  
  
 `_I2`  
 Długość najmniej znaczący wymiaru.  
  
 `_Other`  
 `extent` Obiektu, w którym nowy `extent` opiera się obiekt.  
  
## <a name="remarks"></a>Uwagi  
 Inicjuje konstruktora bez parametrów `extent` obiekt, który ma trzy pozycję.  
  
 Jeśli tablica jest używana do konstruowania `extent` obiektu, długość tablicy musi być zgodna rangę `extent` obiektu.  
  
##  <a name="operator_mod_eq"></a> operator % = 

Oblicza modułu (reszty) każdego elementu w zakresie, gdy ten element jest dzielona przez liczbę.  
  
### <a name="syntax"></a>Składnia  
  
```  
extent<_Rank>& operator%=(int _Rhs) restrict(cpu, direct3d);  
```  
  
### <a name="parameters"></a>Parametry  
 `_Rhs`  
 Numer, aby znaleźć resztę z.  
  
### <a name="return-value"></a>Wartość zwracana  
 `extent` Obiektu.  
  
##  <a name="operator_star_eq"></a> operator * = 

Mnoży każdego elementu w obiekcie "zakresu" o określoną liczbę.  
  
### <a name="syntax"></a>Składnia  
  
```  
extent<_Rank>& operator*=(int _Rhs) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>Parametry  
 `_Rhs`  
 Liczbę Aby pomnożyć.  
  
### <a name="return-value"></a>Wartość zwracana  
 `extent` Obiektu.  
  
## <a name="operator_add"></a> operator + 

Zwraca nowy `extent` obiekt utworzony przez dodanie odpowiednich `index` i `extent` elementy.  
  
### <a name="syntax"></a>Składnia  
  
```  
extent<_Rank> operator+(const index<_Rank>& _Rhs) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>Parametry  
 `_Rhs`  
 `index` Obiekt, który zawiera elementy do dodania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Nowe `extent` obiektu.  
  
##  <a name="operator_add_add"></a> operator ++ 

Zwiększa każdego elementu obiektu "zakresu".  
  
### <a name="syntax"></a>Składnia  
  
```  
extent<_Rank>& operator++() restrict(amp,cpu);    
extent<_Rank> operator++(int)restrict(amp,cpu);  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dla operatora prefiksu `extent` obiektu (`*this`). Dla operatora sufiks nowy `extent` obiektu.  
  
##  <a name="operator_add_eq"></a> += — operator 

Dodaje określoną liczbę do każdego elementu obiektu "zakresu".  
  
### <a name="syntax"></a>Składnia  
  
```  
extent<_Rank>& operator+=(const extent<_Rank>& _Rhs) restrict(amp,cpu);    
extent<_Rank>& operator+=(const index<_Rank>& _Rhs) restrict(amp,cpu);    
extent<_Rank>& operator+=(int _Rhs) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>Parametry  
 `_Rhs`  
 Liczba, indeksu lub zakres do dodania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Powstałe w ten sposób `extent` obiektu.  
  
##  <a name="operator_min"></a> operator- 

Tworzy nowy `extent` obiektu przez odjęcie ilości każdego elementu w określonej `index` obiekt odpowiadający mu element w tym `extent` obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```  
extent<_Rank> operator-(const index<_Rank>& _Rhs) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>Parametry  
 `_Rhs`  
 `index` Obiekt, który zawiera elementy do odjęcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Nowe `extent` obiektu.  
  
##  <a name="operator_min_min"></a> operator-- 

Zmniejsza każdego elementu w obiekcie "zakresu".  
  
### <a name="syntax"></a>Składnia  
  
```  
extent<_Rank>& operator--() restrict(amp,cpu);    
extent<_Rank> operator--(int)restrict(amp,cpu);  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dla operatora prefiksu `extent` obiektu (`*this`). Dla operatora sufiks nowy `extent` obiektu.  
  
##  <a name="operator_div_eq"></a> / = — operator 

Dzieli każdego elementu w obiekcie "zakresu" o określoną liczbę.  
  
### <a name="syntax"></a>Składnia  
  
```  
extent<_Rank>& operator/=(int _Rhs) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>Parametry  
 `_Rhs`  
 Liczba do dzielenia przez.  
  
### <a name="return-value"></a>Wartość zwracana  
 `extent` Obiektu.  
  
##  <a name="operator_min_eq"></a> operator-= 

Odejmuje określonej liczby z każdego elementu obiektu "zakresu".  
  
### <a name="syntax"></a>Składnia  
  
```  
extent<_Rank>& operator-=(const extent<_Rank>& _Rhs) restrict(amp,cpu);    
extent<_Rank>& operator-=(const index<_Rank>& _Rhs) restrict(amp,cpu);    
extent<_Rank>& operator-=(int _Rhs) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>Parametry  
 `_Rhs`  
 Numer do odjęcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Powstałe w ten sposób `extent` obiektu.  
  
##  <a name="operator_eq"></a> operator = 

Kopiuje zawartość z innego obiektu "zakres" do tego.  
  
### <a name="syntax"></a>Składnia  
  
```  
extent<_Rank>& operator=(const extent<_Rank>& _Other) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `extent` Obiektu do skopiowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do tego `extent` obiektu.  
  
##  <a name="operator_at"></a> Extent::operator \[\] 
Zwraca element pod określonym indeksem.  
  
### <a name="syntax"></a>Składnia  
  
```  
int operator[](unsigned int _Index) const restrict(amp,cpu);    
int& operator[](unsigned int _Index) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>Parametry  
 `_Index`  
 Liczba całkowita od 0 do rangi pomniejszonej o 1.  
  
### <a name="return-value"></a>Wartość zwracana  
 Element pod określonym indeksem.  
  
##  <a name="rank_constant"></a> Ranga 

Przechowuje rangę obiektu "zakresu".  
  
### <a name="syntax"></a>Składnia  
  
```  
static const int rank = _Rank;  
```  
  
##  <a name="size"></a> Rozmiar 

Zwraca całkowity rozmiar liniowej `extent` obiektu (w jednostkach elementów).  
  
### <a name="syntax"></a>Składnia  

```  
unsigned int size() const restrict(amp,cpu);  
```  
  
## <a name="tile"></a> Kafelek 

Tworzy obiekt tiled_extent — z wymiarów określonego kafelka.

```
template <int _Dim0>
tiled_extent<_Dim0> tile() const ;

template <int _Dim0, int _Dim1>
tiled_extent<_Dim0, _Dim1> tile() const ;

template <int _Dim0, int _Dim1, int _Dim2>
tiled_extent<_Dim0, _Dim1, _Dim2> tile() const ;
```  
### <a name="parameters"></a>Parametry
`_Dim0` Najbardziej znaczący składnik sąsiadującym zakresu.
`_Dim1` Składnik dalej do większość — znaczące sąsiadującym zakresu.
`_Dim2` Najmniej znaczący składnik sąsiadującym zakresu.


  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
