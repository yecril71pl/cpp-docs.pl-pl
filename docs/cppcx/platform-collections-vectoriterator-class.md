---
title: 'Platform::Collections:: vectoriterator, klasa | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorIterator::VectorIterator
dev_langs:
- C++
helpviewer_keywords:
- VectorIterator Class
ms.assetid: d531cb42-27e0-48a6-bf5e-c265891a18ff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: af033a2e67885b35bb0f6341cb50f022efb14c53
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42613046"
---
# <a name="platformcollectionsvectoriterator-class"></a>Platform::Collections:: vectoriterator, klasa
Zawiera obiekty opracowane na podstawie interfejs Windows Runtime IVector iteratorów standardowej biblioteki szablonów.  
  
 VectorIterator jest iteratorem serwera proxy, który przechowuje elementy typu VectorProxy\<T >. Jednak obiekt serwera proxy prawie nigdy nie jest widoczne dla kodu użytkownika. Aby uzyskać więcej informacji, zobacz [kolekcje (C + +/ CX)](../cppcx/collections-c-cx.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
template <typename T>  
class VectorIterator;  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Element typename VectorIterator szablonu klasy.  
  
### <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Publiczne definicje typów  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`difference_type`|Różnica wskaźników przy obliczaniu (ptrdiff_t —).|  
|`iterator_category`|Kategoria iteratora dostępu swobodnego (:: std::random_access_iterator_tag).|  
|`pointer`|Wskaźnik do typu wewnętrznego Platform::Collections::Details::VectorProxy\<T >, która jest wymagane do wykonania VectorIterator.|  
|`reference`|Odwołanie do typu wewnętrznego Platform::Collections::Details::VectorProxy\<T >, to znaczy wymagane do wykonania VectorIterator.|  
|`value_type`|`T` Typename.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[VectorIterator::VectorIterator](#ctor)|Inicjuje nowe wystąpienie klasy VectorIterator.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[VectorIterator::operator-— Operator](#operator-minus)|Odejmuje określoną liczbę elementów z bieżącego iteratora reaguje iterator nowych lub określony iteratora z bieżącego iteratora reaguje liczbę elementów między Iteratory.|  
|[VectorIterator::operator — Operator](#operator-decrement)|Zmniejsza bieżące VectorIterator.|  
|[VectorIterator::operator! = — Operator](#operator-inequality)|Wskazuje, czy bieżący VectorIterator nie jest równa określonej VectorIterator.|  
|[VectorIterator::operator * — Operator](#operator-dereference)|Pobiera odwołanie do elementu określonego przez bieżący VectorIterator.|  
|[VectorIterator::operator\[\]](#operator-at)|Pobiera odwołanie do elementu, który jest określony przesunięcia z bieżącej VectorIterator.|  
|[VectorIterator::operator + — Operator](#operator-plus)|Zwraca VectorIterator, która odwołuje się do elementu w określonym przemieszczenia VectorIterator określony.|  
|[VectorIterator::operator ++ — Operator](#operator-increment)|Zwiększa narastająco VectorIterator bieżącego.|  
|[VectorIterator::operator += — Operator](#operator-plus-assign)|Zwiększa bieżącego VectorIterator o określonym przemieszczenia.|  
|[VectorIterator::operator < — Operator](#operator-less-than)|Wskazuje, czy bieżący VectorIterator jest mniejsza niż określony VectorIterator.|  
|[VectorIterator::operator\<= — Operator](#operator-less-than-or-equals)|Wskazuje, czy bieżący VectorIterator jest mniejsza niż lub równa określonej VectorIterator.|  
|[VectorIterator::operator-= — Operator](#operator-subtract-assign)|Zmniejsza bieżące VectorIterator przemieszczenie określony.|  
|[VectorIterator::operator == — Operator](#operator-equality)|Wskazuje, czy bieżący VectorIterator jest równe określonej VectorIterator.|  
|[VectorIterator::operator > — Operator](#operator-greater-than)|Wskazuje, czy bieżący VectorIterator jest większy niż określony VectorIterator.|  
|[VectorIterator::operator -> — Operator](#operator-arrow)|Pobiera adres elementu przywoływane przez bieżący VectorIterator.|  
|[VectorIterator::operator > = — Operator](#operator-greater-than-or-equal)|Wskazuje, czy bieżący VectorIterator jest większa niż lub równa określonej VectorIterator.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `VectorIterator`  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** collection.h  
  
 **Namespace:** Platform::Collections  

## <a name="operator-arrow"></a>  VectorIterator::operator -&gt; — Operator
Pobiera adres elementu przywoływane przez bieżący VectorIterator.  
  
### <a name="syntax"></a>Składnia  
  
```  
Detail::ArrowProxy<T> operator->() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość elementu, który odwołuje się do bieżącego VectorIterator.  
  
 Typ wartości zwracanej jest nieokreślonego typu wewnętrznego, który jest wymagany do wykonania tego operatora.  
  


## <a name="operator-decrement"></a>  VectorIterator::operator — Operator
Zmniejsza bieżące VectorIterator.  
  
### <a name="syntax"></a>Składnia  
  
```  
  
VectorIterator& operator--();  
VectorIterator operator--(int);  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy zmniejsza składni, a następnie zwraca bieżący VectorIterator. Składnia drugiego zwraca kopię bieżącego VectorIterator, a następnie zmniejsza VectorIterator bieżącego.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy składni VectorIterator decrements wstępnie VectorIterator bieżącego.  
  
 Składnia drugiego decrements po bieżącym VectorIterator. `int` Typu w drugim składni wskazuje to operacja dekrementacji po nie operandu rzeczywistej liczby całkowitej.  
  


## <a name="operator-dereference"></a>  VectorIterator::operator\* — Operator
Pobiera adres określony przez VectorIterator bieżący element.  
  
### <a name="syntax"></a>Składnia  
  
```  
reference operator*() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Element określony przez bieżący VectorIterator.  
  


## <a name="operator-equality"></a>  VectorIterator::operator == — Operator
Wskazuje, czy bieżący VectorIterator jest równe określonej VectorIterator.  
  
### <a name="syntax"></a>Składnia  
  
```  
bool operator==(const VectorIterator& other) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 VectorIterator innego.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli bieżący VectorIterator jest równa `other`; w przeciwnym razie `false`.  
  


## <a name="operator-greater-than"></a>  VectorIterator::operator&gt; — Operator
Wskazuje, czy bieżący VectorIterator jest większy niż określony VectorIterator.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
  
bool operator>(const VectorIterator& other) const   
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 VectorIterator innego.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli bieżący VectorIterator jest większa niż `other`; w przeciwnym razie `false`.  
  


## <a name="operator-greater-than-or-equals"></a>  VectorIterator::operator&gt;= — Operator
Wskazuje, czy bieżący VectorIterator jest większa niż lub równa określonej VectorIterator.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
  
bool operator>=(const VectorIterator& other) const   
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 VectorIterator innego.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli bieżący VectorIterator jest większa niż lub równa `other`; w przeciwnym razie `false`.    


## <a name="operator-increment"></a>  VectorIterator::operator ++ — Operator
Zwiększa narastająco VectorIterator bieżącego.  
  
### <a name="syntax"></a>Składnia  
  
```    
VectorIterator& operator++();  
VectorIterator operator++(int);  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy składni zwiększa, a następnie zwraca bieżący VectorIterator. Drugiej składni zwraca kopię bieżącego VectorIterator, a następnie zwiększa VectorIterator bieżącego.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy składni VectorIterator zwiększa wstępnie VectorIterator bieżącego.  
  
 Składnia drugiego zwiększa po bieżącym VectorIterator. `int` Typu w drugim składni wskazuje operacji po inkrementacji, nie operandu rzeczywistej liczby całkowitej.  
  


## <a name="operator-inequality"></a>  VectorIterator::operator! = — Operator
Wskazuje, czy bieżący VectorIterator nie jest równa określonej VectorIterator.  
  
### <a name="syntax"></a>Składnia  
  
```  
bool operator!=(const VectorIterator& other) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 VectorIterator innego.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli bieżący VectorIterator nie jest równa `other`; w przeciwnym razie `false`.  
  


## <a name="operator-less-than"></a>  VectorIterator::operator&lt; — Operator
Wskazuje, czy bieżący VectorIterator jest mniejsza niż określony VectorIterator.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
  
bool operator<(const VectorIterator& other) const   
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 VectorIterator innego.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli bieżący VectorIterator jest mniejsza niż `other`; w przeciwnym razie `false`.  
  


## <a name="operator-less-than-or-equals"></a>  VectorIterator::operator&lt;= — Operator
Wskazuje, czy bieżący VectorIterator jest mniejsza niż lub równa określonej VectorIterator.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
  
bool operator<=(const VectorIterator& other) const   
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 VectorIterator innego.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` czy bieżący VectorIterator jest mniejszy niż lub równe `other`; w przeciwnym razie `false`.  
  


## <a name="operator-minus"></a>  VectorIterator::operator-— Operator
Odejmuje określoną liczbę elementów z bieżącego iteratora reaguje iterator nowych lub określony iteratora z bieżącego iteratora reaguje liczbę elementów między Iteratory.  
  
### <a name="syntax"></a>Składnia  
  
```  
  
VectorIterator operator-(difference_type n) const;  
  
difference_type operator-(const VectorIterator& other) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `n`  
 Liczba elementów.  
  
 `other`  
 VectorIterator innego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy składnia operator zwraca obiekt VectorIterator `n` elementy mniejszą niż bieżący VectorIterator. Drugi składni operator zwraca liczbę elementów między bieżącą i `other` VectorIterator.  
  


## <a name="operator-plus-assign"></a>  VectorIterator::operator += — Operator
Zwiększa bieżącego VectorIterator o określonym przemieszczenia.  
  
### <a name="syntax"></a>Składnia  
  
```  
VectorIterator& operator+=(difference_type n);  
```  
  
### <a name="parameters"></a>Parametry  
 `n`  
 Przesunięcie liczby całkowitej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zaktualizowano VectorIterator.  
  


## <a name="operator-plus"></a>  ectorIterator::operator + — Operator
Zwraca VectorIterator, która odwołuje się do elementu w określonym przemieszczenia VectorIterator określony.  
  
### <a name="syntax"></a>Składnia  
  
```  
  
VectorIterator operator+(difference_type n);  
  
template <typename T>  
inline VectorIterator<T> operator+(
  ptrdiff_t n, 
  const VectorIterator<T>& i);  
  
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 W drugim składnia elementu VectorIterator typename.  
  
 `n`  
 Przesunięcie liczby całkowitej.  
  
 `i`  
 W drugim składni VectorIterator.  
  
### <a name="return-value"></a>Wartość zwracana  
 W pierwszym składni VectorIterator, która odwołuje się do elementu w określonym przemieszczenia VectorIterator bieżącego.  
  
 W drugim składni VectorIterator, który odwołuje się do elementu w określonej przesunięcie od początku parametru `i`.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy przykład składni  
  


## <a name="operator-minus-equals"></a>  VectorIterator::operator-= — Operator
Zmniejsza bieżące VectorIterator przemieszczenie określony.  
  
### <a name="syntax"></a>Składnia  
  
```  
VectorIterator& operator-=(difference_type n);  
```  
  
### <a name="parameters"></a>Parametry  
 `n`  
 Przesunięcie liczby całkowitej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zaktualizowano VectorIterator.  
  


## <a name="operator-at"></a>  VectorIterator::operator\[\]
Pobiera odwołanie do elementu, który jest określony przesunięcia z bieżącej VectorIterator.  
  
### <a name="syntax"></a>Składnia  
  
```    
reference operator[](difference_type n) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `n`  
 Przesunięcie liczby całkowitej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Element, który jest przesunięty przez `n` elementy z bieżącego VectorIterator.  
  


## <a name="ctor"></a>  Konstruktor VectorIterator::VectorIterator
Inicjuje nowe wystąpienie klasy VectorIterator.  
  
### <a name="syntax"></a>Składnia  
  
```    
VectorIterator();  
  
explicit VectorIterator(  
   Windows::Foundation::Collections::IVector<T>^ v);  
```  
  
### <a name="parameters"></a>Parametry  
 `v`  
 IVector\<T > obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy przykład składni jest konstruktor domyślny. Drugi przykład składni jest jawny Konstruktor, który służy do konstruowania VectorIterator z IVector\<T > obiektu.  
  


  
## <a name="see-also"></a>Zobacz też  
 [Namespace platformy](platform-namespace-c-cx.md)