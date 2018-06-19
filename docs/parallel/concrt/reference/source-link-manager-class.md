---
title: source_link_manager — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- source_link_manager
- AGENTS/concurrency::source_link_manager
- AGENTS/concurrency::source_link_manager::source_link_manager
- AGENTS/concurrency::source_link_manager::add
- AGENTS/concurrency::source_link_manager::begin
- AGENTS/concurrency::source_link_manager::contains
- AGENTS/concurrency::source_link_manager::count
- AGENTS/concurrency::source_link_manager::reference
- AGENTS/concurrency::source_link_manager::register_target_block
- AGENTS/concurrency::source_link_manager::release
- AGENTS/concurrency::source_link_manager::remove
- AGENTS/concurrency::source_link_manager::set_bound
dev_langs:
- C++
helpviewer_keywords:
- source_link_manager class
ms.assetid: 287487cf-e0fe-4c35-aa3c-24f081d1ddae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f8e17626fc870242c97a9ad66a77e5e3b77b1ed1
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691290"
---
# <a name="sourcelinkmanager-class"></a>source_link_manager — Klasa
`source_link_manager` Obiektu zarządza komunikatów łączy sieciowych bloku do `ISource` bloków.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class _LinkRegistry>
class source_link_manager;
```  
  
#### <a name="parameters"></a>Parametry  
 `_LinkRegistry`  
 Rejestr łącze sieci.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`const_pointer`|Typ, który dostarcza wskaźnik do `const` element `source_link_manager` obiektu.|  
|`const_reference`|Typ, który zawiera odwołanie do `const` element przechowywane w `source_link_manager` obiektu za odczytywanie i wykonywanie operacji na stałe.|  
|`iterator`|Typ, który udostępnia iteratora, które mogą odczytywać lub modyfikować dowolny element w `source_link_manager` obiektu.|  
|`type`|Typ rejestru łącze zarządzany przez `source_link_manager` obiektu.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[source_link_manager](#ctor)|Konstruuje `source_link_manager` obiektu.|  
|[~source_link_manager Destructor](#dtor)|Niszczy `source_link_manager` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[add](#add)|Dodaje link do źródła `source_link_manager` obiektu.|  
|[begin](#begin)|Zwraca pierwszy element w iteratora `source_link_manager` obiektu.|  
|[zawiera](#contains)|Wyszukiwanie `network_link_registry` w ramach tego `source_link_manager` obiektu dla określonego bloku.|  
|[Liczba](#count)|Zlicza połączonego bloków w `source_link_manager` obiektu.|  
|[Odwołanie](#reference)|Uzyskuje odwołania na `source_link_manager` obiektu.|  
|[register_target_block](#register_target_block)|Rejestruje blok docelowy przechowujący to `source_link_manager` obiektu.|  
|[Zlecenia](#release)|Zwalnia odwołania na `source_link_manager` obiektu.|  
|[remove](#remove)|Usuwa link z `source_link_manager` obiektu.|  
|[set_bound](#set_bound)|Ustawia maksymalną liczbę łączy źródła, które mogą zostać dodane do tego `source_link_manager` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Obecnie bloki źródła są zliczane odwołania. Ta opcja jest włączona otoka `network_link_registry` obiekt, który umożliwia równoczesny dostęp do łącza i zapewnia możliwość odwołania łącza za pomocą wywołania zwrotne. Bloki komunikatów ( `target_block`s lub `propagator_block`s) powinny używać tej klasy dla łączy ich źródła.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `source_link_manager`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** agents.h  
  
 **Namespace:** współbieżności  
  
##  <a name="add"></a> Dodaj 

 Dodaje link do źródła `source_link_manager` obiektu.  
  
```
void add(_EType _Link);
```  
  
### <a name="parameters"></a>Parametry  
 `_Link`  
 Wskaźnik do bloku do dodania.  
  
##  <a name="begin"></a> Rozpocznij 

 Zwraca pierwszy element w iteratora `source_link_manager` obiektu.  
  
```
iterator begin();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iteratora adresowania pierwszym elementem w `source_link_manager` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Wskazuje stan końcowy iteratora `NULL` łącza.  
  
##  <a name="contains"></a> zawiera 

 Wyszukiwanie `network_link_registry` w ramach tego `source_link_manager` obiektu dla określonego bloku.  
  
```
bool contains(_EType _Link);
```  
  
### <a name="parameters"></a>Parametry  
 `_Link`  
 Wskaźnik do bloku, który ma zostać wyszukany w `source_link_manager` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli został określony blok `false` inaczej.  
  
##  <a name="count"></a> Liczba 

 Zlicza połączonego bloków w `source_link_manager` obiektu.  
  
```
size_t count();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba połączonych bloków w `source_link_manager` obiektu.  
  
##  <a name="reference"></a> Odwołanie 

 Uzyskuje odwołania na `source_link_manager` obiektu.  
  
```
void reference();
```  
  
##  <a name="register_target_block"></a> register_target_block 

 Rejestruje blok docelowy przechowujący to `source_link_manager` obiektu.  
  
```
void register_target_block(_Inout_ ITarget<typename _Block::source_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Blok docelowy przechowujący to `source_link_manager` obiektu.  
  
##  <a name="release"></a> Zlecenia 

 Zwalnia odwołania na `source_link_manager` obiektu.  
  
```
void release();
```  
  
##  <a name="remove"></a> Usuń 

 Usuwa link z `source_link_manager` obiektu.  
  
```
bool remove(_EType _Link);
```  
  
### <a name="parameters"></a>Parametry  
 `_Link`  
 Wskaźnik do bloku, który ma zostać usunięty, jeśli znaleziono.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli łącze zostało odnalezione i usunięte, `false` inaczej.  
  
##  <a name="set_bound"></a> set_bound 

 Ustawia maksymalną liczbę łączy źródła, które mogą zostać dodane do tego `source_link_manager` obiektu.  
  
```
void set_bound(size_t _MaxLinks);
```  
  
### <a name="parameters"></a>Parametry  
 `_MaxLinks`  
 Maksymalna liczba łącza.  
  
##  <a name="ctor"></a> source_link_manager 

 Konstruuje `source_link_manager` obiektu.  
  
```
source_link_manager();
```  
  
##  <a name="dtor"></a> ~source_link_manager 

 Niszczy `source_link_manager` obiektu.  
  
```
~source_link_manager();
```  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [single_link_registry — klasa](single-link-registry-class.md)   
 [multi_link_registry, klasa](multi-link-registry-class.md)
