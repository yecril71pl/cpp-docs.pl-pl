---
title: 'Platform::Collections:: inputiterator, klasa | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::InputIterator::InputIterator
dev_langs:
- C++
helpviewer_keywords:
- InputIterator Class
ms.assetid: ef72eea4-32a9-42b9-8119-ce87dbdcd3be
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fbd80f649b27bcb3af720871d6d1378f5fe220c8
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2018
ms.locfileid: "39208487"
---
# <a name="platformcollectionsinputiterator-class"></a>Platform::Collections:: inputiterator, klasa
Zawiera standardowe InputIterator biblioteki szablonu dla kolekcji, pochodzące ze środowiska wykonawczego Windows.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <typename X>  
class InputIterator;  
```  
  
#### <a name="parameters"></a>Parametry  
 `X`  
 Element typename InputIterator szablonu klasy.  
  
### <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Publiczne definicje typów  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`difference_type`|Różnica wskaźników przy obliczaniu (ptrdiff_t —).|  
|`iterator_category`|Do kategorii iteratora danych wejściowych (:: std::input_iterator_tag).|  
|`pointer`|Wskaźnik do `const X`|  
|`reference`|Odwołanie do `const X`|  
|`value_type`|`X` Typename.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[InputIterator::InputIterator](#ctor)|Inicjuje nowe wystąpienie klasy InputIterator.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[InputIterator::operator! = — Operator](#operator-inequality)|Wskazuje, czy bieżący InputIterator nie jest równa określonej InputIterator.|  
|[InputIterator::operator * — Operator](#operator-decrement)|Pobiera odwołanie do elementu określonego przez bieżący InputIterator.|  
|[InputIterator::operator ++ — Operator](#operator-increment)|Zwiększa narastająco InputIterator bieżącego.|  
|[InputIterator::operator == — Operator](#operator-equality)|Wskazuje, czy bieżący InputIterator jest równe określonej InputIterator.|  
|[InputIterator::operator -> — Operator](#operator-arrow)|Pobiera adres elementu przywoływane przez bieżący InputIterator.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `InputIterator`  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** collection.h  
  
 **Namespace:** Platform::Collections  

## <a name="ctor"></a>  Konstruktor InputIterator::InputIterator
Inicjuje nowe wystąpienie klasy InputIterator.  
  
### <a name="syntax"></a>Składnia  
  
```  
InputIterator();  
explicit InputIterator(Windows::Foundation::Collections<X>^ iter);  
```  
  
### <a name="parameters"></a>Parametry  
 `iter`  
 Obiekt iteratora.  
  


## <a name="operator-arrow"></a>  InputIterator::operator -&gt; — Operator
Pobiera adres określony przez InputIterator bieżący element.  
  
### <a name="syntax"></a>Składnia  
  
```  
pointer operator->() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Adres określony przez InputIterator bieżący element.  
  


## <a name="operator-dereference"></a>  InputIterator::operator\* — Operator
Pobiera odwołanie do elementu określonego przez bieżący InputIterator.  
  
### <a name="syntax"></a>Składnia  
  
```  
reference operator*() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Element określony przez bieżący InputIterator.  
  


## <a name="operator-equality"></a>  InputIterator::operator == — Operator
Wskazuje, czy bieżący InputIterator jest równe określonej InputIterator.  
  
### <a name="syntax"></a>Składnia  
  
```  
bool operator== (const InputIterator& other) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 InputIterator innego.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli bieżący InputIterator jest równa `other`; w przeciwnym razie `false`.  
  


## <a name="operator-increment"></a>  InputIterator::operator ++ — Operator
Zwiększa narastająco InputIterator bieżącego.  
  
### <a name="syntax"></a>Składnia  
  
```    
InputIterator& operator++();   
InputIterator operator++(int);  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy składni zwiększa, a następnie zwraca bieżący InputIterator. Składnia drugiego zwraca kopię bieżącego InputIterator i następnie zwiększa InputIterator bieżącego.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy składni InputIterator zwiększa wstępnie InputIterator bieżącego.  
  
 Składnia drugiego zwiększa po bieżącym InputIterator. `int` Typu w drugim składni wskazuje operacji po inkrementacji, nie operandu rzeczywistej liczby całkowitej.  
  


## <a name="operator-inequality"></a>  InputIterator::operator! = — Operator
Wskazuje, czy bieżący InputIterator nie jest równa określonej InputIterator.  
  
### <a name="syntax"></a>Składnia  
  
```  
bool operator!=(const InputIterator& other) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 InputIterator innego.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli bieżący InputIterator nie jest równa `other`; w przeciwnym razie `false`.   

  
## <a name="see-also"></a>Zobacz też  
 [Namespace platformy](platform-namespace-c-cx.md)