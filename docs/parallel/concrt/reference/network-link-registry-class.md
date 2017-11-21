---
title: "network_link_registry — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- network_link_registry
- AGENTS/concurrency::network_link_registry
- AGENTS/concurrency::network_link_registry::add
- AGENTS/concurrency::network_link_registry::begin
- AGENTS/concurrency::network_link_registry::contains
- AGENTS/concurrency::network_link_registry::count
- AGENTS/concurrency::network_link_registry::remove
dev_langs: C++
helpviewer_keywords: network_link_registry class
ms.assetid: 3e7b4097-09f1-4252-964e-b15b8f7f7fc6
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 348964eb2f9b17a00188dd3a2589ce0711767e64
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="networklinkregistry-class"></a>network_link_registry — Klasa
`network_link_registry` Abstrakcyjna klasa podstawowa zarządza łącza między bloki źródłowe i docelowe.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class _Block>
class network_link_registry;
```  
  
#### <a name="parameters"></a>Parametry  
 `_Block`  
 Typ danych bloku są przechowywane w `network_link_registry`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`const_pointer`|Typ, który dostarcza wskaźnik do `const` element `network_link_registry` obiektu.|  
|`const_reference`|Typ, który zawiera odwołanie do `const` element przechowywane w `network_link_registry` obiektu za odczytywanie i wykonywanie operacji na stałe.|  
|`iterator`|Typ, który udostępnia iteratora, które mogą odczytywać lub modyfikować dowolny element w `network_link_registry` obiektu.|  
|`type`|Typ reprezentujący typ bloku, przechowywane w `network_link_registry` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Dodaj](#add)|W przypadku przesłonięcia w klasie pochodnej, dodaje łącze do `network_link_registry` obiektu.|  
|[Rozpocznij](#begin)|W przypadku przesłonięcia w klasie pochodnej zwraca iteratora do pierwszego elementu w `network_link_registry` obiektu.|  
|[zawiera](#contains)|W przypadku przesłonięcia w klasie pochodnej, wyszukuje `network_link_registry` obiektu dla określonego bloku.|  
|[Liczba](#count)|W przypadku przesłonięcia w klasie pochodnej zwraca liczbę elementów w `network_link_registry` obiektu.|  
|[Usuń](#remove)|W przypadku przesłonięcia w klasie pochodnej usuwa określony blok z `network_link_registry` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 `network link registry` Nie jest bezpieczne dla współbieżny dostęp.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `network_link_registry`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** agents.h  
  
 **Namespace:** współbieżności  
  
##  <a name="add"></a>Dodaj 

 W przypadku przesłonięcia w klasie pochodnej, dodaje łącze do `network_link_registry` obiektu.  
  
```
virtual void add(_EType _Link) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_Link`  
 Wskaźnik do bloku do dodania.  
  
##  <a name="begin"></a>Rozpocznij 

 W przypadku przesłonięcia w klasie pochodnej zwraca iteratora do pierwszego elementu w `network_link_registry` obiektu.  
  
```
virtual iterator begin() = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iteratora adresowania pierwszym elementem w `network_link_registry` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Wskazuje stan końcowy iteratora `NULL` łącza.  
  
##  <a name="contains"></a>zawiera 

 W przypadku przesłonięcia w klasie pochodnej, wyszukuje `network_link_registry` obiektu dla określonego bloku.  
  
```
virtual bool contains(_EType _Link) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_Link`  
 Wskaźnik do bloku, który jest przeszukiwany dla w `network_link_registry` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli znaleziono bloku, `false` inaczej.  
  
##  <a name="count"></a>Liczba 

 W przypadku przesłonięcia w klasie pochodnej zwraca liczbę elementów w `network_link_registry` obiektu.  
  
```
virtual size_t count() = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów w `network_link_registry` obiektu.  
  
##  <a name="remove"></a>Usuń 

 W przypadku przesłonięcia w klasie pochodnej usuwa określony blok z `network_link_registry` obiektu.  
  
```
virtual bool remove(_EType _Link) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_Link`  
 Wskaźnik do bloku, który ma zostać usunięty, jeśli znaleziono.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli łącze zostało odnalezione i usunięte, `false` inaczej.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [single_link_registry — klasa](single-link-registry-class.md)   
 [multi_link_registry — klasa](multi-link-registry-class.md)
