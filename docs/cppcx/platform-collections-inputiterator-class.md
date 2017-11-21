---
title: Klasa platform::Collections::InputIterator | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: COLLECTION/Platform::Collections::InputIterator::InputIterator
dev_langs: C++
helpviewer_keywords: InputIterator Class
ms.assetid: ef72eea4-32a9-42b9-8119-ce87dbdcd3be
caps.latest.revision: "4"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 15dd1d6ece1af3d561801c497b87f7be4f7d5397
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="platformcollectionsinputiterator-class"></a>Klasa platform::Collections::InputIterator
Zawiera standardowe InputIterator biblioteki szablonu kolekcje pochodzące z środowiska uruchomieniowego systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <typename X>  
class InputIterator;  
```  
  
#### <a name="parameters"></a>Parametry  
 `X`  
 Właściwość typename klasy InputIterator szablonu.  
  
### <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`difference_type`|Różnica wskaźników (ptrdiff_t —).|  
|`iterator_category`|Kategoria iteratora wejściowych (:: std::input_iterator_tag).|  
|`pointer`|Wskaźnik do`const X`|  
|`reference`|Odwołanie do`const X`|  
|`value_type`|`X` Typename.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[InputIterator::InputIterator](#ctor)|Inicjuje nowe wystąpienie klasy InputIterator.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[InputIterator::operator! = — Operator](#operator-inequality)|Wskazuje, czy bieżący InputIterator nie jest równa określonej InputIterator.|  
|[InputIterator::operator * — Operator](#operator-decrement)|Pobiera odwołanie do określonego przez InputIterator bieżącego elementu.|  
|[InputIterator::operator ++ — Operator](#operator-increment)|Zwiększa InputIterator bieżącej.|  
|[InputIterator::operator == — Operator](#operator-equality)|Wskazuje, czy bieżący InputIterator jest równa określonej InputIterator.|  
|[InputIterator::operator -> — Operator](#operator-arrow)|Pobiera adres odwołuje się InputIterator bieżącego elementu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `InputIterator`  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** collection.h  
  
 **Namespace:** Platform::Collections  

## <a name="ctor"></a>Konstruktor InputIterator::InputIterator
Inicjuje nowe wystąpienie klasy InputIterator.  
  
### <a name="syntax"></a>Składnia  
  
```  
InputIterator();  
explicit InputIterator(Windows::Foundation::Collections<X>^ iter);  
```  
  
### <a name="parameters"></a>Parametry  
 `iter`  
 Obiekt iteratora.  
  


## <a name="operator-arrow"></a>InputIterator::operator —&gt; — Operator
Pobiera adres określony przez InputIterator bieżącego elementu.  
  
### <a name="syntax"></a>Składnia  
  
```  
pointer operator->() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Adres określony przez InputIterator bieżący element.  
  


## <a name="operator-dereference"></a>InputIterator::operator * — Operator
Pobiera odwołanie do określonego przez InputIterator bieżącego elementu.  
  
### <a name="syntax"></a>Składnia  
  
```  
reference operator*() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Element określony przez bieżący InputIterator.  
  


## <a name="operator-equality"></a>InputIterator::operator == — Operator
Wskazuje, czy bieżący InputIterator jest równa określonej InputIterator.  
  
### <a name="syntax"></a>Składnia  
  
```  
bool operator== (const InputIterator& other) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 Inny InputIterator.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli bieżący InputIterator jest równa `other`; w przeciwnym razie `false`.  
  


## <a name="operator-increment"></a>InputIterator::operator ++ — Operator
Zwiększa InputIterator bieżącej.  
  
### <a name="syntax"></a>Składnia  
  
```    
InputIterator& operator++();   
InputIterator operator++(int);  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy składni zwiększa, a następnie zwraca bieżące InputIterator. Drugi składni zwraca kopię bieżącego InputIterator i następnie zwiększa InputIterator bieżącej.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy składni InputIterator zwiększa wstępnie InputIterator bieżącej.  
  
 Drugi składni zwiększa po bieżącym InputIterator. `int` Typu w drugiej składni wskazuje operację po przyrostu nie operand rzeczywista liczba całkowita.  
  


## <a name="operator-inequality"></a>InputIterator::operator! = — Operator
Wskazuje, czy bieżący InputIterator nie jest równa określonej InputIterator.  
  
### <a name="syntax"></a>Składnia  
  
```  
bool operator!=(const InputIterator& other) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 Inny InputIterator.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli bieżący InputIterator nie jest równa `other`; w przeciwnym razie `false`.   

  
## <a name="see-also"></a>Zobacz też  
 [Namespace platformy](platform-namespace-c-cx.md)