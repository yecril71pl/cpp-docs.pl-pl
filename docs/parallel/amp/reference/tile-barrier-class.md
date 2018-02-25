---
title: "tile_barrier — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- tile_barrier
- AMP/tile_barrier
- AMP/Concurrency::tile_barrier::tile_barrier::tile_barrier
- AMP/Concurrency::tile_barrier::tile_barrier::wait
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_all_memory_fence
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_global_memory_fence
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_tile_static_memory_fence
dev_langs:
- C++
helpviewer_keywords:
- tile_barrier class
ms.assetid: b4ccdccb-0032-4e11-b7bd-dc9d43445dee
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e7d868b4bd677d207590de6449e3d5643001e857
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="tilebarrier-class"></a>tile_barrier — Klasa
Synchronizuje wykonywanie wątków, które są uruchomione w grupie wątku (kafelka) przy użyciu `wait` metody. Tylko środowiska uruchomieniowego można utworzyć wystąpienia tej klasy.  
  
### <a name="syntax"></a>Składnia 
  
```  
class tile_barrier;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[tile_barrier Constructor](#ctor)|Inicjuje nowe wystąpienie klasy `tile_barrier` klasy.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[oczekiwania](#wait)|Powoduje, że wszystkie wątki w grupie wątku (kafelka) można zatrzymać wykonywania, dopóki wszystkie wątki na kafelku zakończyły oczekiwania.|  
|[wait_with_all_memory_fence](#wait_with_all_memory_fence)|Wykonanie bloki wszystkie wątki na kafelku ukończenie wszystkich uzyskuje dostęp do pamięci i wszystkie wątki na kafelku osiągnęły tego wywołania.|  
|[wait_with_global_memory_fence](#wait_with_global_memory_fence)|Wykonanie bloki wszystkie wątki na kafelku, dopóki nie zostały ukończone wszystkie uzyskuje dostęp do pamięci globalnej i wszystkie wątki na kafelku osiągnięto tego wywołania.|  
|[wait_with_tile_static_memory_fence](#wait_with_tile_static_memory_fence)|Blokuje wykonywanie wszystkie wątki na kafelku, aż wszystkie `tile_static` uzyskuje dostęp do pamięci zostały ukończone i wszystkie wątki na kafelku osiągnięto tego wywołania.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `tile_barrier`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** amp.h  
  
 **Namespace:** współbieżności  

## <a name="tile_barrier__ctor"></a>  tile_barrier — Konstruktor  
 Inicjuje nowe wystąpienie klasy przez skopiowanie istniejącej.  
  
### <a name="syntax"></a>Składnia 
  
```  
tile_barrier(  
    const tile_barrier& _Other ) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `tile_barrier` Obiektu do skopiowania.  

## <a name="wait">oczekiwania</a> 
Powoduje, że wszystkie wątki w grupie wątku (kafelka), można zatrzymać wykonywania, dopóki wszystkie wątki na kafelku zakończyły oczekiwania.  
  
### <a name="syntax"></a>Składnia 
  
```  
void wait() const restrict(amp);  
```    

## <a name="wait_with_all_memory_fence"></a>  wait_with_all_memory_fence —   
Wykonanie bloki wszystkie wątki na kafelku, dopóki wszystkie wątki na kafelku osiągnięto tego wywołania. Dzięki temu wszystkie uzyskuje dostęp do pamięci są widoczne dla innych wątków na kafelku wątku czy zostały wykonane w kolejności program.  
  
### <a name="syntax"></a>Składnia 
  
```  
void wait_with_all_memory_fence() const restrict(amp);  
```  
  

## <a name="wait_with_global_memory_fence"></a>  wait_with_global_memory_fence —   
Wykonanie bloki wszystkie wątki na kafelku, dopóki wszystkie wątki na kafelku osiągnięto tego wywołania. Dzięki temu wszystkie uzyskuje dostęp do pamięci globalnej są widoczne dla innych wątków na kafelku wątku czy zostały wykonane w kolejności program.  
  
### <a name="syntax"></a>Składnia 
  
```  
void wait_with_global_memory_fence() const  restrict(amp);  
```

## <a name="wait_with_tile_static_memory_fence"></a>  wait_with_tile_static_memory_fence —   
Wykonanie bloki wszystkie wątki na kafelku, dopóki wszystkie wątki na kafelku osiągnięto tego wywołania. Gwarantuje to, że `tile_static` pamięci dostępu są widoczne dla innych wątków na kafelku wątku i zostały wykonane w kolejności program.  
  
### <a name="syntax"></a>Składnia 
  
```  
void wait_with_tile_static_memory_fence() const restrict(amp);  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
