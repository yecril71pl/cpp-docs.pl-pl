---
title: Klasa platform::Collections::VectorIterator | Dokumentacja firmy Microsoft
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
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: deaab183a092a073c6681004654312485959e924
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="platformcollectionsvectoriterator-class"></a>Klasa platform::Collections::VectorIterator
Udostępnia iteratora standardowa biblioteka szablonów dla obiektów pochodzących z interfejsu IVector środowiska wykonawczego systemu Windows.  
  
 VectorIterator jest iteratora serwera proxy, który przechowuje elementy typu VectorProxy\<T >. Jednak obiekt serwera proxy prawie nigdy nie jest widoczny dla kodu użytkownika. Aby uzyskać więcej informacji, zobacz [kolekcji (C + +/ CX)](../cppcx/collections-c-cx.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
template <typename T>  
class VectorIterator;  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Właściwość typename klasy VectorIterator szablonu.  
  
### <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`difference_type`|Różnica wskaźników (ptrdiff_t —).|  
|`iterator_category`|Kategoria iteratora dostępie swobodnym (:: std::random_access_iterator_tag).|  
|`pointer`|Wskaźnik do typu wewnętrznego Platform::Collections::Details::VectorProxy\<T >, która jest wymagana do wykonania VectorIterator.|  
|`reference`|Odwołanie do typu wewnętrznego Platform::Collections::Details::VectorProxy\<T >,,, który jest wymagane do wykonania VectorIterator.|  
|`value_type`|`T` Typename.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[VectorIterator::VectorIterator](#ctor)|Inicjuje nowe wystąpienie klasy VectorIterator.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[VectorIterator::operator-— Operator](#operator-minus)|Odejmuje określonej liczby elementów z bieżącym iteratora reaguje iteratora nowych lub iteratora określony przez iterator bieżąca liczba elementów między Iteratory reaguje.|  
|[VectorIterator::operator — Operator](#operator-decrement)|Zmniejsza VectorIterator bieżącej.|  
|[VectorIterator::operator! = — Operator](#operator-inequality)|Wskazuje, czy bieżący VectorIterator nie jest równa określonej VectorIterator.|  
|[VectorIterator::operator * — Operator](#operator-dereference)|Pobiera odwołanie do określonego przez VectorIterator bieżącego elementu.|  
|[VectorIterator::operator\[\]](#operator-at)|Pobiera odwołanie do elementu, który jest określony przesunięcia z bieżącej VectorIterator.|  
|[VectorIterator::operator + — Operator](#operator-plus)|Zwraca VectorIterator, która odwołuje się element pod określonym przemieszczenie VectorIterator określony.|  
|[VectorIterator::operator ++ — Operator](#operator-increment)|Zwiększa VectorIterator bieżącej.|  
|[VectorIterator::operator += — Operator](#operator-plus-assign)|Zwiększa bieżącego VectorIterator określonego przesunięcia.|  
|[VectorIterator::operator < — Operator](#operator-less-than)|Wskazuje, czy bieżący VectorIterator jest mniejsza niż określony VectorIterator.|  
|[VectorIterator::operator\<= — Operator](#operator-less-than-or-equals)|Wskazuje, czy bieżący VectorIterator jest mniejsza lub równa określonej VectorIterator.|  
|[VectorIterator::operator-= — Operator](#operator-subtract-assign)|Zmniejsza bieżącego VectorIterator przemieszczenie określony.|  
|[VectorIterator::operator == — Operator](#operator-equality)|Wskazuje, czy bieżący VectorIterator jest równa określonej VectorIterator.|  
|[VectorIterator::operator > — Operator](#operator-greater-than)|Wskazuje, czy bieżący VectorIterator jest większa niż określona VectorIterator.|  
|[VectorIterator::operator -> — Operator](#operator-arrow)|Pobiera adres odwołuje się VectorIterator bieżącego elementu.|  
|[VectorIterator::operator > = — Operator](#operator-greater-than-or-equal)|Wskazuje, czy bieżący VectorIterator jest większa niż lub równa określonej VectorIterator.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `VectorIterator`  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** collection.h  
  
 **Namespace:** Platform::Collections  

## <a name="operator-arrow"></a>  VectorIterator::operator —&gt; — Operator
Pobiera adres odwołuje się VectorIterator bieżącego elementu.  
  
### <a name="syntax"></a>Składnia  
  
```  
Detail::ArrowProxy<T> operator->() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość elementu, do którego odwołuje się do niego VectorIterator bieżącej.  
  
 Typ zwracanej wartości to nieokreślonego typu wewnętrznego wymaganego do wykonania tego operatora.  
  


## <a name="operator-decrement"></a>  VectorIterator::operator — Operator
Zmniejsza VectorIterator bieżącej.  
  
### <a name="syntax"></a>Składnia  
  
```  
  
VectorIterator& operator--();  
VectorIterator operator--(int);  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy zmniejsza składni, a następnie zwraca bieżące VectorIterator. Drugi składni zwraca kopię bieżącego VectorIterator, a następnie zmniejsza VectorIterator bieżącej.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy składni VectorIterator decrements wstępnie VectorIterator bieżącej.  
  
 Drugi składni decrements po bieżącym VectorIterator. `int` Typu w drugiej składni wskazuje operację po dekrementacji nie operand rzeczywista liczba całkowita.  
  


## <a name="operator-dereference"></a>  VectorIterator::operator * — Operator
Pobiera adres określony przez VectorIterator bieżącego elementu.  
  
### <a name="syntax"></a>Składnia  
  
```  
reference operator*() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Element określony przez bieżący VectorIterator.  
  


## <a name="operator-equality"></a>  VectorIterator::operator == — Operator
Wskazuje, czy bieżący VectorIterator jest równa określonej VectorIterator.  
  
### <a name="syntax"></a>Składnia  
  
```  
bool operator==(const VectorIterator& other) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 Inny VectorIterator.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli bieżący VectorIterator jest równa `other`; w przeciwnym razie `false`.  
  


## <a name="operator-greater-than"></a>  VectorIterator::operator&gt; — Operator
Wskazuje, czy bieżący VectorIterator jest większa niż określona VectorIterator.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
  
bool operator>(const VectorIterator& other) const   
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 Inny VectorIterator.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli jest większa niż bieżąca VectorIterator `other`; w przeciwnym razie `false`.  
  


## <a name="operator-greater-than-or-equals"></a>  VectorIterator::operator&gt;= — Operator
Wskazuje, czy bieżący VectorIterator jest większa niż lub równa określonej VectorIterator.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
  
bool operator>=(const VectorIterator& other) const   
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 Inny VectorIterator.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli bieżący VectorIterator jest większa niż lub równa `other`; w przeciwnym razie `false`.    


## <a name="operator-increment"></a>  VectorIterator::operator ++ — Operator
Zwiększa VectorIterator bieżącej.  
  
### <a name="syntax"></a>Składnia  
  
```    
VectorIterator& operator++();  
VectorIterator operator++(int);  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy składni zwiększa, a następnie zwraca bieżące VectorIterator. Drugi składni zwraca kopię bieżącego VectorIterator i następnie zwiększa VectorIterator bieżącej.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy składni VectorIterator zwiększa wstępnie VectorIterator bieżącej.  
  
 Drugi składni zwiększa po bieżącym VectorIterator. `int` Typu w drugiej składni wskazuje operację po przyrostu nie operand rzeczywista liczba całkowita.  
  


## <a name="operator-inequality"></a>  VectorIterator::operator! = — Operator
Wskazuje, czy bieżący VectorIterator nie jest równa określonej VectorIterator.  
  
### <a name="syntax"></a>Składnia  
  
```  
bool operator!=(const VectorIterator& other) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 Inny VectorIterator.  
  
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
 Inny VectorIterator.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli bieżący VectorIterator jest mniejsza niż `other`; w przeciwnym razie `false`.  
  


## <a name="operator-less-than-or-equals"></a>  VectorIterator::operator&lt;= — Operator
Wskazuje, czy bieżący VectorIterator jest mniejsza lub równa określonej VectorIterator.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
  
bool operator<=(const VectorIterator& other) const   
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 Inny VectorIterator.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli bieżący VectorIterator jest mniejsze niż lub równe `other`; w przeciwnym razie `false`.  
  


## <a name="operator-minus"></a>  VectorIterator::operator-— Operator
Odejmuje określonej liczby elementów z bieżącym iteratora reaguje iteratora nowych lub iteratora określony przez iterator bieżąca liczba elementów między Iteratory reaguje.  
  
### <a name="syntax"></a>Składnia  
  
```  
  
VectorIterator operator-(difference_type n) const;  
  
difference_type operator-(const VectorIterator& other) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `n`  
 Liczba elementów.  
  
 `other`  
 Inny VectorIterator.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy składni operatora zwraca obiekt VectorIterator `n` elementy mniejsza niż bieżąca VectorIterator. Drugi składni operatora zwraca liczbę elementów od bieżącego i `other` VectorIterator.  
  


## <a name="operator-plus-assign"></a>  VectorIterator::operator += — Operator
Zwiększa bieżącego VectorIterator określonego przesunięcia.  
  
### <a name="syntax"></a>Składnia  
  
```  
VectorIterator& operator+=(difference_type n);  
```  
  
### <a name="parameters"></a>Parametry  
 `n`  
 Przemieszczenie liczby całkowitej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zaktualizowano VectorIterator.  
  


## <a name="operator-plus"></a>  ectorIterator::operator + — Operator
Zwraca VectorIterator, która odwołuje się element pod określonym przemieszczenie VectorIterator określony.  
  
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
 W drugiej składni typename elementu VectorIterator.  
  
 `n`  
 Przemieszczenie liczby całkowitej.  
  
 `i`  
 W drugiej składni VectorIterator.  
  
### <a name="return-value"></a>Wartość zwracana  
 W pierwszym składni VectorIterator, która odwołuje się element pod określonym przemieszczenie VectorIterator bieżącej.  
  
 W drugim składni VectorIterator, który odwołuje się element pod określonym przesunięcie od początku parametru `i`.  
  
### <a name="remarks"></a>Uwagi  
 W pierwszym przykładzie składni  
  


## <a name="operator-minus-equals"></a>  VectorIterator::operator-= — Operator
Zmniejsza bieżącego VectorIterator przemieszczenie określony.  
  
### <a name="syntax"></a>Składnia  
  
```  
VectorIterator& operator-=(difference_type n);  
```  
  
### <a name="parameters"></a>Parametry  
 `n`  
 Przemieszczenie liczby całkowitej.  
  
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
 Przemieszczenie liczby całkowitej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Element, który jest przesuwane za pomocą `n` elementy z bieżącego VectorIterator.  
  


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
 W pierwszym przykładzie składni jest konstruktora domyślnego. Drugi przykład składni jest jawny Konstruktor, który jest używany do tworzenia VectorIterator z IVector\<T > obiektu.  
  


  
## <a name="see-also"></a>Zobacz też  
 [Namespace platformy](platform-namespace-c-cx.md)