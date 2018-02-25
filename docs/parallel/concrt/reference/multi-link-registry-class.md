---
title: "multi_link_registry — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- multi_link_registry
- AGENTS/concurrency::multi_link_registry
- AGENTS/concurrency::multi_link_registry::multi_link_registry
- AGENTS/concurrency::multi_link_registry::add
- AGENTS/concurrency::multi_link_registry::begin
- AGENTS/concurrency::multi_link_registry::contains
- AGENTS/concurrency::multi_link_registry::count
- AGENTS/concurrency::multi_link_registry::remove
- AGENTS/concurrency::multi_link_registry::set_bound
dev_langs:
- C++
helpviewer_keywords:
- multi_link_registry class
ms.assetid: b2aa73a8-e8a6-4255-b117-d07530c328b2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8f87da4852fff0256b5ca55cfd47d839531b8a03
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="multilinkregistry-class"></a>multi_link_registry — Klasa
`multi_link_registry` Obiekt jest `network_link_registry` który zarządza wiele bloków źródła lub wiele bloków docelowej.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class _Block>
class multi_link_registry : public network_link_registry<_Block>;
```  
  
#### <a name="parameters"></a>Parametry  
 `_Block`  
 Typ danych bloku są przechowywane w `multi_link_registry` obiektu.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[multi_link_registry](#ctor)|Konstruuje `multi_link_registry` obiektu.|  
|[~multi_link_registry Destructor](#dtor)|Niszczy `multi_link_registry` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[add](#add)|Dodaje link do `multi_link_registry` obiektu. (Przesłania [network_link_registry::add](network-link-registry-class.md#add).)|  
|[begin](#begin)|Zwraca pierwszy element w iteratora `multi_link_registry` obiektu. (Przesłania [network_link_registry::begin](network-link-registry-class.md#begin).)|  
|[zawiera](#contains)|Wyszukiwanie `multi_link_registry` obiektu dla określonego bloku. (Przesłania [network_link_registry::contains](network-link-registry-class.md#contains).)|  
|[Liczba](#count)|Zlicza elementy `multi_link_registry` obiektu. (Przesłania [network_link_registry::count](network-link-registry-class.md#count).)|  
|[remove](#remove)|Usuwa link z `multi_link_registry` obiektu. (Przesłania [network_link_registry::remove](network-link-registry-class.md#remove).)|  
|[set_bound](#set_bound)|Ustawia górnej granicy liczby łącza `multi_link_registry` obiekt może przechowywać.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [network_link_registry](network-link-registry-class.md)  
  
 `multi_link_registry`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** agents.h  
  
 **Namespace:** współbieżności  
  
##  <a name="add"></a> Dodaj 

 Dodaje link do `multi_link_registry` obiektu.  
  
```
virtual void add(_EType _Link);
```  
  
### <a name="parameters"></a>Parametry  
 `_Link`  
 Wskaźnik do bloku do dodania.  
  
### <a name="remarks"></a>Uwagi  
 Metoda zgłasza [invalid_link_target —](invalid-link-target-class.md) wyjątku czy łącze jest już obecny w rejestrze, czy powiązanej został już ustawiony z `set_bound` funkcji i łącze odwałania został usunięty.  
  
##  <a name="begin"></a> Rozpocznij 

 Zwraca pierwszy element w iteratora `multi_link_registry` obiektu.  
  
```
virtual iterator begin();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iteratora adresowania pierwszym elementem w `multi_link_registry` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Wskazuje stan końcowy `NULL` łącza.  
  
##  <a name="contains">zawiera</a> 

 Wyszukiwanie `multi_link_registry` obiektu dla określonego bloku.  
  
```
virtual bool contains(_EType _Link);
```  
  
### <a name="parameters"></a>Parametry  
 `_Link`  
 Wskaźnik do bloku, który ma zostać wyszukany w `multi_link_registry` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli został określony blok `false` inaczej.  
  
##  <a name="count">Liczba</a> 

 Zlicza elementy `multi_link_registry` obiektu.  
  
```
virtual size_t count();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów w `multi_link_registry` obiektu.  
  
##  <a name="ctor"></a> multi_link_registry 

 Konstruuje `multi_link_registry` obiektu.  
  
```
multi_link_registry();
```  
  
##  <a name="dtor"></a> ~multi_link_registry 

 Niszczy `multi_link_registry` obiektu.  
  
```
virtual ~multi_link_registry();
```  
  
### <a name="remarks"></a>Uwagi  
 Metoda zgłasza [invalid_operation —](invalid-operation-class.md) wyjątek, jeśli metoda wywoływana przed wszystkie linki zostaną usunięte.  
  
##  <a name="remove"></a> Usuń 

 Usuwa link z `multi_link_registry` obiektu.  
  
```
virtual bool remove(_EType _Link);
```  
  
### <a name="parameters"></a>Parametry  
 `_Link`  
 Wskaźnik do bloku, który ma zostać usunięty, jeśli znaleziono.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli łącze zostało odnalezione i usunięte, `false` inaczej.  
  
##  <a name="set_bound"></a> set_bound 

 Ustawia górnej granicy liczby łącza `multi_link_registry` obiekt może przechowywać.  
  
```
void set_bound(size_t _MaxLinks);
```  
  
### <a name="parameters"></a>Parametry  
 `_MaxLinks`  
 Maksymalna liczba łączy, które `multi_link_registry` obiekt może przechowywać.  
  
### <a name="remarks"></a>Uwagi  
 Po ustawieniu powiązanej spowoduje rozłączenie wpis `multi_link_registry` obiektu na przejściu w stan niezmienne gdzie dalsze wywołań `add` zgłosi `invalid_link_target` wyjątku.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [single_link_registry, klasa](single-link-registry-class.md)
