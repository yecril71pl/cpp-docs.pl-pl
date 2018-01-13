---
title: "single_link_registry — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- single_link_registry
- AGENTS/concurrency::single_link_registry
- AGENTS/concurrency::single_link_registry::single_link_registry
- AGENTS/concurrency::single_link_registry::add
- AGENTS/concurrency::single_link_registry::begin
- AGENTS/concurrency::single_link_registry::contains
- AGENTS/concurrency::single_link_registry::count
- AGENTS/concurrency::single_link_registry::remove
dev_langs: C++
helpviewer_keywords: single_link_registry class
ms.assetid: 09540a4e-c34e-4ff9-af49-21b8612b6ab3
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 11e02e4adb2e2bdb79f275537047199f434a57c2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="singlelinkregistry-class"></a>single_link_registry — Klasa
`single_link_registry` Obiekt jest `network_link_registry` który zarządza tylko jeden blok źródłowa lub docelowa.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class _Block>
class single_link_registry : public network_link_registry<_Block>;
```  
  
#### <a name="parameters"></a>Parametry  
 `_Block`  
 Typ danych bloku są przechowywane w `single_link_registry` obiektu.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[single_link_registry —](#ctor)|Konstruuje `single_link_registry` obiektu.|  
|[~ single_link_registry — destruktor](#dtor)|Niszczy `single_link_registry` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[add](#add)|Dodaje link do `single_link_registry` obiektu. (Przesłania [network_link_registry::add](network-link-registry-class.md#add).)|  
|[Rozpocznij](#begin)|Zwraca pierwszy element w iteratora `single_link_registry` obiektu. (Przesłania [network_link_registry::begin](network-link-registry-class.md#begin).)|  
|[zawiera](#contains)|Wyszukiwanie `single_link_registry` obiektu dla określonego bloku. (Przesłania [network_link_registry::contains](network-link-registry-class.md#contains).)|  
|[Liczba](#count)|Zlicza elementy `single_link_registry` obiektu. (Przesłania [network_link_registry::count](network-link-registry-class.md#count).)|  
|[remove](#remove)|Usuwa link z `single_link_registry` obiektu. (Przesłania [network_link_registry::remove](network-link-registry-class.md#remove).)|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [network_link_registry —](network-link-registry-class.md)  
  
 `single_link_registry`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** agents.h  
  
 **Namespace:** współbieżności  
  
##  <a name="add"></a>Dodaj 

 Dodaje link do `single_link_registry` obiektu.  
  
```
virtual void add(_EType _Link);
```  
  
### <a name="parameters"></a>Parametry  
 `_Link`  
 Wskaźnik do bloku do dodania.  
  
### <a name="remarks"></a>Uwagi  
 Metoda zgłasza [invalid_link_target —](invalid-link-target-class.md) wyjątek, jeśli istnieje już łącza w tym rejestru.  
  
##  <a name="begin"></a>Rozpocznij 

 Zwraca pierwszy element w iteratora `single_link_registry` obiektu.  
  
```
virtual iterator begin();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iteratora adresowania pierwszym elementem w `single_link_registry` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Wskazuje stan końcowy `NULL` łącza.  
  
##  <a name="contains"></a>zawiera 

 Wyszukiwanie `single_link_registry` obiektu dla określonego bloku.  
  
```
virtual bool contains(_EType _Link);
```  
  
### <a name="parameters"></a>Parametry  
 `_Link`  
 Wskaźnik do bloku, który ma zostać wyszukany w `single_link_registry` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli link został znaleziony, `false` inaczej.  
  
##  <a name="count"></a>Liczba 

 Zlicza elementy `single_link_registry` obiektu.  
  
```
virtual size_t count();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów w `single_link_registry` obiektu.  
  
##  <a name="remove"></a>Usuń 

 Usuwa link z `single_link_registry` obiektu.  
  
```
virtual bool remove(_EType _Link);
```  
  
### <a name="parameters"></a>Parametry  
 `_Link`  
 Wskaźnik do bloku, który ma zostać usunięty, jeśli znaleziono.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli łącze zostało odnalezione i usunięte, `false` inaczej.  
  
##  <a name="ctor"></a>single_link_registry — 

 Konstruuje `single_link_registry` obiektu.  
  
```
single_link_registry();
```  
  
##  <a name="dtor"></a>~ single_link_registry — 

 Niszczy `single_link_registry` obiektu.  
  
```
virtual ~single_link_registry();
```  
  
### <a name="remarks"></a>Uwagi  
 Metoda zgłasza [invalid_operation —](invalid-operation-class.md) wyjątek, jeśli jest ona wywoływana przed usunięciem łącza.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [multi_link_registry, klasa](multi-link-registry-class.md)
