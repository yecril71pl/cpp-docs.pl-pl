---
title: single_link_registry — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- single_link_registry
- AGENTS/concurrency::single_link_registry
- AGENTS/concurrency::single_link_registry::single_link_registry
- AGENTS/concurrency::single_link_registry::add
- AGENTS/concurrency::single_link_registry::begin
- AGENTS/concurrency::single_link_registry::contains
- AGENTS/concurrency::single_link_registry::count
- AGENTS/concurrency::single_link_registry::remove
dev_langs:
- C++
helpviewer_keywords:
- single_link_registry class
ms.assetid: 09540a4e-c34e-4ff9-af49-21b8612b6ab3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 60820d2dc6b4fe0ab5c27ad746ee3f922fc39780
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045786"
---
# <a name="singlelinkregistry-class"></a>single_link_registry — Klasa
`single_link_registry` Obiekt jest `network_link_registry` który zarządza tylko jeden blok źródłowym lub docelowym.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class _Block>
class single_link_registry : public network_link_registry<_Block>;
```  
  
#### <a name="parameters"></a>Parametry  
*_Blok*<br/>
Typ danych bloku znajdujących się w `single_link_registry` obiektu.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[single_link_registry](#ctor)|Konstruuje `single_link_registry` obiektu.|  
|[~single_link_registry Destructor](#dtor)|Niszczy `single_link_registry` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[add](#add)|Dodaje link do `single_link_registry` obiektu. (Przesłania [network_link_registry::add —](network-link-registry-class.md#add).)|  
|[begin](#begin)|Zwraca iterator do pierwszego elementu w `single_link_registry` obiektu. (Przesłania [network_link_registry::Begin —](network-link-registry-class.md#begin).)|  
|[zawiera](#contains)|Wyszukiwanie `single_link_registry` obiektu dla określonego bloku. (Przesłania [network_link_registry::CONTAINS —](network-link-registry-class.md#contains).)|  
|[Liczba](#count)|Zlicza liczbę elementów w `single_link_registry` obiektu. (Przesłania [network_link_registry::Count —](network-link-registry-class.md#count).)|  
|[remove](#remove)|Usuwa łącze między `single_link_registry` obiektu. (Przesłania [network_link_registry::REMOVE —](network-link-registry-class.md#remove).)|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [network_link_registry](network-link-registry-class.md)  
  
 `single_link_registry`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** agents.h  
  
 **Namespace:** współbieżności  
  
##  <a name="add"></a> Dodaj 

 Dodaje link do `single_link_registry` obiektu.  
  
```
virtual void add(_EType _Link);
```  
  
### <a name="parameters"></a>Parametry  
*_Link*<br/>
Wskaźnik do bloku, który ma zostać dodana.  
  
### <a name="remarks"></a>Uwagi  
 Metoda zgłasza [invalid_link_target —](invalid-link-target-class.md) wyjątek, jeśli istnieje już link w tego rejestru.  
  
##  <a name="begin"></a> Rozpocznij 

 Zwraca iterator do pierwszego elementu w `single_link_registry` obiektu.  
  
```
virtual iterator begin();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator odnoszący się do pierwszego elementu w `single_link_registry` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Stan zakończenia jest wskazywany przez `NULL` łącza.  
  
##  <a name="contains"></a> zawiera 

 Wyszukiwanie `single_link_registry` obiektu dla określonego bloku.  
  
```
virtual bool contains(_EType _Link);
```  
  
### <a name="parameters"></a>Parametry  
*_Link*<br/>
Wskaźnik do bloku, który ma zostać wyszukany w `single_link_registry` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli link został znaleziony, `false` inaczej.  
  
##  <a name="count"></a> Liczba 

 Zlicza liczbę elementów w `single_link_registry` obiektu.  
  
```
virtual size_t count();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów w `single_link_registry` obiektu.  
  
##  <a name="remove"></a> Usuń 

 Usuwa łącze między `single_link_registry` obiektu.  
  
```
virtual bool remove(_EType _Link);
```  
  
### <a name="parameters"></a>Parametry  
*_Link*<br/>
Wskaźnik do bloku, który ma zostać usunięty, jeśli znaleziono.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli łącze zostało znalezione i usuwane, `false` inaczej.  
  
##  <a name="ctor"></a> single_link_registry — 

 Konstruuje `single_link_registry` obiektu.  
  
```
single_link_registry();
```  
  
##  <a name="dtor"></a> ~single_link_registry 

 Niszczy `single_link_registry` obiektu.  
  
```
virtual ~single_link_registry();
```  
  
### <a name="remarks"></a>Uwagi  
 Metoda zgłasza [invalid_operation](invalid-operation-class.md) wyjątek, jeśli jest wywoływana przed usunięciem łącza.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [multi_link_registry, klasa](multi-link-registry-class.md)
