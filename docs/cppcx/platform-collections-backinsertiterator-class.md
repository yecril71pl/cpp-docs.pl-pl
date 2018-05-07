---
title: Klasa platform::Collections::BackInsertIterator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::BackInsertIterator::BackInsertIterator
dev_langs:
- C++
helpviewer_keywords:
- BackInsertIterator Class
ms.assetid: aecee1ff-100d-4129-b84b-1966f0923dbf
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d0be32b550cd0e19facb127ca6a052b03ef1eaf5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="platformcollectionsbackinsertiterator-class"></a>Klasa platform::Collections::BackInsertIterator
Reprezentuje iterację, która wstawia, a nie zastępuje elementy do tyłu końca sekwencyjną kolekcją.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <typename T>  
class BackInsertIterator : 
public ::std::iterator<::std::output_iterator_tag, void, void, void, void>;  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ elementu w bieżącej kolekcji.  
  
### <a name="remarks"></a>Uwagi  
 Klasa BackInsertIterator implementuje zasady wymagane [back_insert_iterator — klasa](../standard-library/back-insert-iterator-class.md).  
  
### <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[BackInsertIterator::BackInsertIterator](#ctor)|Inicjuje nowe wystąpienie klasy BackInsertIterator.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[BackInsertIterator::operator * — Operator](#operator-dereference)|Pobiera odwołanie do bieżącego BackInsertIterator.|  
|[BackInsertIterator::operator ++ — Operator](#operator-increment)|Zwraca odwołanie do bieżącego BackInsertIterator. Iterator pozostaje niezmieniona.|  
|[BackInsertIterator::operator = — Operator](#operator-assign)|Dołącza określony obiekt na koniec bieżącego sekwencyjną kolekcją.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `BackInsertIterator`  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** collection.h  
  
 **Namespace:** Platform::Collections  
  
---
## <a name="ctor"></a>  Konstruktor BackInsertIterator::BackInsertIterator
Inicjuje nowe wystąpienie klasy `BackInsertIterator` klasy.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
explicit BackInsertIterator(  
   Windows::Foundation::Collections::IVector<T>^ v);  
```  
  
#### <a name="parameters"></a>Parametry  
 `v`  
 IVector\<T > obiektu.  
  
### <a name="remarks"></a>Uwagi  
 A `BackInsertIterator` Wstawia elementy po ostatnim elemencie obiektu określony przez parametr `v`.  
 
## <a name="operator-assign"></a>  BackInsertIterator::operator = — Operator
Dołącza określony obiekt na koniec bieżącego sekwencyjną kolekcją.  
  
## <a name="syntax"></a>Składnia  
  
```    
BackInsertIterator& operator=( const T& t);  
```  
  
#### <a name="parameters"></a>Parametry  
 `t`  
 Obiekt można dołączyć do bieżącej kolekcji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do bieżącego BackInsertIterator.  

## <a name="operator-dereference"></a>  BackInsertIterator::operator * — Operator
Pobiera odwołanie do bieżącego BackInsertIterator.  
  
## <a name="syntax"></a>Składnia  
  
```  
BackInsertIterator& operator*();  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do bieżącego BackInsertIterator.  
  
### <a name="remarks"></a>Uwagi  
 Ten operator zwraca odwołanie do bieżącego BackInsertIterator; Nie można dowolny element w bieżącej kolekcji.  
 
## <a name="operator-increment"></a>  BackInsertIterator::operator ++ — Operator
Zwraca odwołanie do bieżącego BackInsertIterator. Iterator pozostaje niezmieniona.  
  
## <a name="syntax"></a>Składnia  
  
``` 
  
BackInsertIterator& operator++();  
  
BackInsertIterator operator++(int);  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do bieżącego BackInsertIterator.  
  
### <a name="remarks"></a>Uwagi  
 Zgodnie z projektem w pierwszym przykładzie składni wstępnie zwiększa bieżącego BackInsertIterator, a drugi składni zwiększa po bieżącym BackInsertIterator. `int` Typu w drugiej składni wskazuje operację po przyrostu nie operand rzeczywista liczba całkowita.  
  
 Jednak tego operatora faktycznie nie modyfikować BackInsertIterator. Zamiast tego operatora zwraca odwołanie do iteratora zostały zmodyfikowane, bieżący. To jest takie samo zachowanie jako [operator *](#dereference-operator).  
  
  
## <a name="see-also"></a>Zobacz też  
 [Namespace platformy](platform-namespace-c-cx.md)