---
title: "Dispatchstate — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DispatchState
- CONCRTRM/concurrency::DispatchState
- CONCRTRM/concurrency::DispatchState::DispatchState::DispatchState
- CONCRTRM/concurrency::DispatchState::DispatchState::m_dispatchStateSize
- CONCRTRM/concurrency::DispatchState::DispatchState::m_fIsPreviousContextAsynchronouslyBlocked
- CONCRTRM/concurrency::DispatchState::DispatchState::m_reserved
dev_langs: C++
helpviewer_keywords: DispatchState structure
ms.assetid: 8c52546e-1650-48a0-985f-7e4a0fc26a90
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d58fc12aa31c9d6a72acac6287a425044d42777c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="dispatchstate-structure"></a>DispatchState — Struktura
`DispatchState` Struktury jest używana do przesyłania stanu, tak aby `IExecutionContext::Dispatch` metody. Zawiera opis sytuacji, w którym `Dispatch` jest wywoływana metoda `IExecutionContext` interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```
struct DispatchState;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Dispatchstate::dispatchstate —](#ctor)|Tworzy nową `DispatchState` obiektu.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Dispatchstate::m_dispatchstatesize —](#m_dispatchstatesize)|Rozmiar tej struktury, która jest używana do przechowywania wersji.|  
|[Dispatchstate::m_fispreviouscontextasynchronouslyblocked —](#m_fispreviouscontextasynchronouslyblocked)|Informuje, czy przeszedł w tym kontekście `Dispatch` metody, ponieważ poprzedni kontekst asynchronicznie zablokowany. To jest używane tylko w kontekście harmonogramu UMS i ma ustawioną wartość `0` dla wszystkich innych kontekstach wykonywania.|  
|[Dispatchstate::m_reserved —](#m_reserved)|Bity zarezerwowane dla przyszłego informacji przekazywanie.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `DispatchState`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrtrm.h  
  
 **Namespace:** współbieżności  
  
##  <a name="ctor"></a>Dispatchstate::dispatchstate — Konstruktor  
 Tworzy nową `DispatchState` obiektu.  
  
```
DispatchState();
```  
  
##  <a name="m_dispatchstatesize"></a>Dispatchstate::m_dispatchstatesize — członek danych  
 Rozmiar tej struktury, która jest używana do przechowywania wersji.  
  
```
unsigned long m_dispatchStateSize;
```  
  
##  <a name="m_fispreviouscontextasynchronouslyblocked"></a>Dispatchstate::m_fispreviouscontextasynchronouslyblocked — członek danych  
 Informuje, czy przeszedł w tym kontekście `Dispatch` metody, ponieważ poprzedni kontekst asynchronicznie zablokowany. To jest używane tylko w kontekście harmonogramu UMS i ma ustawioną wartość `0` dla wszystkich innych kontekstach wykonywania.  
  
```
unsigned int m_fIsPreviousContextAsynchronouslyBlocked : 1;
```  
  
##  <a name="m_reserved"></a>Dispatchstate::m_reserved — członek danych  
 Bity zarezerwowane dla przyszłego informacji przekazywanie.  
  
```
unsigned int m_reserved : 31;
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności](concurrency-namespace.md)
