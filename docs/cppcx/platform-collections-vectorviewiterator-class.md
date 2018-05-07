---
title: Klasa platform::Collections::VectorViewIterator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorViewIterator::VectorViewIterator
dev_langs:
- C++
helpviewer_keywords:
- VectorViewIterator Class
ms.assetid: be3aa1ae-e6ba-4a06-8d6b-86d8128026f7
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e01a6235ccd898e9ae732c89b9f9885db35151cd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="platformcollectionsvectorviewiterator-class"></a>Klasa platform::Collections::VectorViewIterator
Udostępnia iteratora standardowa biblioteka szablonów dla obiektów pochodzących od środowiska wykonawczego systemu Windows`IVectorView` interfejsu.  
  
 `ViewVectorIterator` jest iteratora serwera proxy, który przechowuje elementy typu `VectorProxy<T>`. Jednak obiekt serwera proxy prawie nigdy nie jest widoczny dla kodu użytkownika. Aby uzyskać więcej informacji, zobacz [kolekcji (C + +/ CX)](../cppcx/collections-c-cx.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
template <typename T>  
class VectorViewIterator;  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Właściwość typename klasy VectorViewIterator szablonu.  
  
### <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`difference_type`|Różnica wskaźników (ptrdiff_t —).|  
|`iterator_category`|Kategoria iteratora dostępie swobodnym (:: std::random_access_iterator_tag).|  
|`pointer`|Wskaźnik do typu wewnętrznego, który jest wymagany do wykonania VectorViewIterator.|  
|`reference`|Odwołanie do typu wewnętrznego, który jest wymagany do wykonania VectorViewIterator.|  
|`value_type`|`T` Typename.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[VectorViewIterator::VectorViewIterator](#ctor)|Inicjuje nowe wystąpienie klasy VectorViewIterator.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[VectorViewIterator::operator-— Operator](#operator-minus)|Odejmuje określonej liczby elementów z bieżącym iteratora reaguje iteratora nowych lub iteratora określony przez iterator bieżąca liczba elementów między Iteratory reaguje.|  
|[VectorViewIterator::operator — Operator](#operator-decrement)|Zmniejsza VectorViewIterator bieżącej.|  
|[VectorViewIterator::operator! = — Operator](#operator-inequality)|Wskazuje, czy bieżący VectorViewIterator nie jest równa określonej VectorViewIterator.|  
|[VectorViewIterator::operator * — Operator](#operator-dereference)|Pobiera odwołanie do określonego przez VectorViewIterator bieżącego elementu.|  
|[VectorViewIterator::operator\[\]](#operator-at)|Pobiera odwołanie do elementu, który jest określony przesunięcia z bieżącej VectorViewIterator.|  
|[VectorViewIterator::operator + — Operator](#operator-plus)|Zwraca VectorViewIterator, która odwołuje się element pod określonym przemieszczenie VectorViewIterator określony.|  
|[VectorViewIterator::operator ++ — Operator](#operator-increment)|Zwiększa VectorViewIterator bieżącej.|  
|[VectorViewIterator::operator += — Operator](#operator-plus-assign)|Zwiększa bieżącego VectorViewIterator określonego przesunięcia.|  
|[VectorViewIterator::operator < — Operator](#operator-less-than)|Wskazuje, czy bieżący VectorViewIterator jest mniejsza niż określony VectorViewIterator.|  
|[VectorViewIterator::operator\<= — Operator](#operator-less-than-or-equals)|Wskazuje, czy bieżący VectorViewIterator jest mniejsza lub równa określonej VectorViewIterator.|  
|[VectorViewIterator::operator-= — Operator](#operator-minus-assign)|Zmniejsza bieżącego VectorViewIterator przemieszczenie określony.|  
|[VectorViewIterator::operator == — Operator](#operator-equality)|Wskazuje, czy bieżący VectorViewIterator jest równa określonej VectorViewIterator.|  
|[VectorViewIterator::operator > — Operator](#operator-greater-than)|Wskazuje, czy bieżący VectorViewIterator jest większa niż określona VectorViewIterator.|  
|[VectorViewIterator::operator -> — Operator](#operator-arrow)|Pobiera adres odwołuje się VectorViewIterator bieżącego elementu.|  
|[VectorViewIterator::operator > = — Operator](#operator-greater-than-or-equals)|Wskazuje, czy bieżący VectorViewIterator jest większa niż lub równa określonej VectorViewIterator.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `VectorViewIterator`  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** collection.h  
  
 **Namespace:** Platform::Collections  

## <a name="operator-arrow"></a>  VectorViewIterator::operator —&gt; — Operator
Pobiera adres odwołuje się VectorViewIterator bieżącego elementu.  
  
### <a name="syntax"></a>Składnia  
  
```  
Detail::ArrowProxy<T> operator->() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość elementu, do którego odwołuje się do niego VectorViewIterator bieżącej.  
  
 Typ zwracanej wartości to nieokreślonego typu wewnętrznego wymaganego do wykonania tego operatora.  
  


## <a name="operator-decrement"></a>  VectorViewIterator::operator — Operator
Zmniejsza VectorViewIterator bieżącej.  
  
### <a name="syntax"></a>Składnia  
  
```  
VectorViewIterator& operator--();  
VectorViewIterator operator--(int);  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy zmniejsza składni, a następnie zwraca bieżące VectorViewIterator. Drugi składni zwraca kopię bieżącego VectorViewIterator, a następnie zmniejsza VectorViewIterator bieżącej.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy składni VectorViewIterator decrements wstępnie VectorViewIterator bieżącej.  
  
 Drugi składni decrements po bieżącym VectorViewIterator. `int` Typu w drugiej składni wskazuje operację po dekrementacji nie operand rzeczywista liczba całkowita.  
  


## <a name="operator-dereference"></a>  VectorViewIterator::operator * — Operator
Pobiera odwołanie do określonego przez VectorViewIterator bieżącego elementu.  
  
### <a name="syntax"></a>Składnia  
  
```  
reference operator*() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Element określony przez bieżący VectorViewIterator.  
  


## <a name="operator-equality"></a>  VectorViewIterator::operator == — Operator
Wskazuje, czy bieżący VectorViewIterator jest równa określonej VectorViewIterator.  
  
### <a name="syntax"></a>Składnia  
  
```  
bool operator==(const VectorViewIterator& other) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 Inny VectorViewIterator.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli bieżący VectorViewIterator jest równa `other`; w przeciwnym razie `false`.  
  


## <a name="operator-greater-than"></a>  VectorViewIterator::operator&gt; — Operator
Wskazuje, czy bieżący VectorViewIterator jest większa niż określona VectorViewIterator.  
  
### <a name="syntax"></a>Składnia  
  
```  
  
bool operator>(const VectorViewIterator& other) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 Inny VectorViewIterator.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli jest większa niż bieżąca VectorViewIterator `other`; w przeciwnym razie `false`.  
  


## <a name="operator-greater-than-or-equals"></a>  VectorViewIterator::operator&gt;= — Operator
Wskazuje, czy bieżący VectorViewIterator jest większa niż lub równa określonej VectorViewIterator.  
  
### <a name="syntax"></a>Składnia  
  
```  
  
bool operator>=(const VectorViewIterator& other) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 Inny VectorViewIterator.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli bieżący VectorViewIterator jest większa niż lub równa `other`; w przeciwnym razie `false`.  
  


## <a name="operator-increment"></a>  VectorViewIterator::operator ++ — Operator
Zwiększa VectorViewIterator bieżącej.  
  
### <a name="syntax"></a>Składnia  
  
```  
  
VectorViewIterator& operator++();  
VectorViewIterator operator++(int);  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy składni zwiększa, a następnie zwraca bieżące VectorViewIterator. Drugi składni zwraca kopię bieżącego VectorViewIterator i następnie zwiększa VectorViewIterator bieżącej.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy składni VectorViewIterator zwiększa wstępnie VectorViewIterator bieżącej.  
  
 Drugi składni zwiększa po bieżącym VectorViewIterator. `int` Typu w drugiej składni wskazuje operację po przyrostu nie operand rzeczywista liczba całkowita.  
  


## <a name="operator-inequality"></a>  VectorViewIterator::operator! = — Operator
Wskazuje, czy bieżący VectorViewIterator nie jest równa określonej VectorViewIterator.  
  
### <a name="syntax"></a>Składnia  
  
```  
bool operator!=(const VectorViewIterator& other) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 Inny VectorViewIterator.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli bieżący VectorViewIterator nie jest równa `other`; w przeciwnym razie `false`.  
  


## <a name="operator-less-than"></a>  VectorViewIterator::operator&lt; — Operator
Wskazuje, czy bieżący VectorIterator jest mniejsza niż określony VectorIterator.  
  
### <a name="syntax"></a>Składnia  
  
```  
bool operator<(const VectorViewIterator& other) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 Inny VectorIterator.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli bieżący VectorIterator jest mniejsza niż `other`; w przeciwnym razie `false`.  
  


## <a name="operator-less-than-or-equals"></a>  VectorViewIterator::operator&lt;= — Operator
Wskazuje, czy bieżący VectorIterator jest mniejsza lub równa określonej VectorIterator.  
  
### <a name="syntax"></a>Składnia  
  
```  
  
bool operator<=(const VectorViewIterator& other) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 Inny VectorIterator.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli bieżący VectorIterator jest mniejsze niż lub równe `other`; w przeciwnym razie `false`.  
  


## <a name="operator-minus"></a>  VectorViewIterator::operator-— Operator
Odejmuje określonej liczby elementów z bieżącym iteratora reaguje iteratora nowych lub iteratora określony przez iterator bieżąca liczba elementów między Iteratory reaguje.  
  
### <a name="syntax"></a>Składnia  
  
```  
  
VectorViewIterator operator-(difference_type n) const;  
  
difference_type operator-(const VectorViewIterator& other) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `n`  
 Liczba elementów.  
  
 `other`  
 Inny VectorViewIterator.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy składni operatora zwraca obiekt VectorViewIterator `n` elementy mniejsza niż bieżąca VectorViewIterator. Drugi składni operatora zwraca liczbę elementów od bieżącego i `other` VectorViewIterator.  
  


## <a name="operator-plus-equals"></a>  VectorViewIterator::operator += — Operator
Zwiększa bieżącego VectorViewIterator określonego przesunięcia.  
  
### <a name="syntax"></a>Składnia  
  
```  
VectorViewIterator& operator+=(difference_type n);  
```  
  
### <a name="parameters"></a>Parametry  
 `n`  
 Przemieszczenie liczby całkowitej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zaktualizowano VectorViewIterator.  
  


## <a name="operator-plus"></a>  VectorViewIterator::operator + — Operator
Zwraca VectorViewIterator, która odwołuje się element pod określonym przemieszczenie VectorViewIterator określony.  
  
### <a name="syntax"></a>Składnia  
  
```  
  
VectorViewIterator operator+(difference_type n) const;  
  
template <typename T>   
inline VectorViewIterator<T> operator+  
   (ptrdiff_t n,   
   const VectorViewIterator<T>& i);  
  
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 W drugiej składni typename elementu VectorViewIterator.  
  
 `n`  
 Przemieszczenie liczby całkowitej.  
  
 `i`  
 W drugiej składni VectorViewIterator.  
  
### <a name="return-value"></a>Wartość zwracana  
 W pierwszym składni VectorViewIterator, która odwołuje się element pod określonym przemieszczenie VectorViewIterator bieżącej.  
  
 W drugim składni VectorViewIterator, który odwołuje się element pod określonym przesunięcie od początku parametru `i`.  
  


## <a name="operator-minus-assign"></a>  VectorViewIterator::operator-= — Operator
Zmniejsza bieżącego VectorIterator przemieszczenie określony.  
  
### <a name="syntax"></a>Składnia  
  
```  
VectorViewIterator& operator-=(difference_type n);  
```  
  
### <a name="parameters"></a>Parametry  
 `n`  
 Przemieszczenie liczby całkowitej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zaktualizowano VectorIterator.  
  


## <a name="operator-at"></a>  VectorViewIterator::operator\[\]
Pobiera odwołanie do elementu, który jest określony przesunięcia z bieżącej VectorViewIterator.  
  
### <a name="syntax"></a>Składnia  
  
```  
reference operator[](difference_type n) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `n`  
 Przemieszczenie liczby całkowitej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Element, który jest przesuwane za pomocą `n` elementy z bieżącego VectorViewIterator.  
  


## <a name="ctor"></a>  Konstruktor VectorViewIterator::VectorViewIterator
Inicjuje nowe wystąpienie klasy VectorViewIterator.  
  
### <a name="syntax"></a>Składnia  
  
```  
  
VectorViewIterator();  
  
explicit VectorViewIterator(  
   Windows::Foundation::Collections::IVectorView<T>^ v  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `v`  
 IVectorView\<T > obiektu.  
  
### <a name="remarks"></a>Uwagi  
 W pierwszym przykładzie składni jest konstruktora domyślnego. Drugi przykład składni jest jawny Konstruktor, który jest używany do tworzenia VectorViewIterator z IVectorView\<T > obiektu.  
  

  
## <a name="see-also"></a>Zobacz też  
 [Namespace platformy](platform-namespace-c-cx.md)