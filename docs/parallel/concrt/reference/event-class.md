---
title: "Event — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- event
- CONCRT/concurrency::event
- CONCRT/concurrency::event::reset
- CONCRT/concurrency::event::set
- CONCRT/concurrency::event::wait
- CONCRT/concurrency::event::wait_for_multiple
- CONCRT/concurrency::event::timeout_infinite
dev_langs:
- C++
helpviewer_keywords:
- event class
ms.assetid: fba35a53-6568-4bfa-9aaf-07c0928cf73d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c2301e06554d99529c7d4e4e5215208dc4265970
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="event-class"></a>event — Klasa
Zdarzenie resetowania ręcznego, która jawnie rozpoznaje współbieżności środowiska wykonawczego.  
  
## <a name="syntax"></a>Składnia  
  
```
class event;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[~ event — destruktor](#dtor)|Niszczy zdarzenia.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[reset](#reset)|Resetuje zdarzenia do stanu sygnalizowane.|  
|[set](#set)|Sygnalizuje zdarzenia.|  
|[oczekiwania](#wait)|Czeka na zdarzenie sygnalizuje stają się.|  
|[wait_for_multiple](#wait_for_multiple)|Czeka na wiele zdarzeń stać się sygnalizowane.|  
  
### <a name="public-constants"></a>Publiczny — stałe  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[timeout_infinite](#timeout_infinite)|Wartość wskazująca, której oczekiwania nigdy nie ma limitu czasu.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [struktury danych synchronizacji](../../../parallel/concrt/synchronization-data-structures.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `event`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrt.h  
  
 **Namespace:** współbieżności  
  
##  <a name="ctor"></a> Zdarzenia 

 Tworzy nowe zdarzenie.  
  
```
_CRTIMP event();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="dtor"></a> ~ zdarzeń 

 Niszczy zdarzenia.  
  
```
~event();
```  
  
### <a name="remarks"></a>Uwagi  
 Oczekuje się, że nie istnieją nie wątków oczekujących na zdarzenie, gdy działa destruktor. Stosowanie zdarzenia destruct z wątków, które nadal oczekuje na nim powoduje niezdefiniowane zachowanie.  
  
##  <a name="reset"></a> Resetowanie 

 Resetuje zdarzenia do stanu sygnalizowane.  
  
```
void reset();
```  
  
##  <a name="set"></a> zestaw 

 Sygnalizuje zdarzenia.  
  
```
void set();
```  
  
### <a name="remarks"></a>Uwagi  
 Sygnalizowanie zdarzenie może spowodować dowolnej liczby kontekstów oczekiwanie na zdarzenia stają się do uruchomienia.  
  
##  <a name="timeout_infinite"></a> timeout_infinite 

 Wartość wskazująca, której oczekiwania nigdy nie ma limitu czasu.  
  
```
static const unsigned int timeout_infinite = COOPERATIVE_TIMEOUT_INFINITE;
```  
  
##  <a name="wait">oczekiwania</a> 

 Czeka na zdarzenie sygnalizuje stają się.  
  
```
size_t wait(unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```  
  
### <a name="parameters"></a>Parametry  
 `_Timeout`  
 Wskazuje wyrażony w milisekundach czas, zanim upłynie limit czasu oczekiwania. Wartość `COOPERATIVE_TIMEOUT_INFINITE` oznacza brak limitu czasu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli czas oczekiwania zostały spełnione, wartość `0` zwrócony, a w przeciwnym razie wartość `COOPERATIVE_WAIT_TIMEOUT` wskazująca, że czas oczekiwania upłynął limit czasu bez zdarzenia sygnalizuje staje się.  
  
> [!IMPORTANT]
>  Nie należy wywoływać w aplikacji Windows platformy Uniwersalnej `wait` na ASTA wątku, ponieważ to wywołanie można zablokować bieżącego wątku i może spowodować, że aplikacja przestanie odpowiadać.  
  
##  <a name="wait_for_multiple"></a> wait_for_multiple 

 Czeka na wiele zdarzeń stać się sygnalizowane.  
  
```
static size_t __cdecl wait_for_multiple(
    _In_reads_(count) event** _PPEvents,
    size_t count,
    bool _FWaitAll,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```  
  
### <a name="parameters"></a>Parametry  
 `_PPEvents`  
 Tablica zdarzeń oczekiwania. Liczba zdarzeń w tablicy jest określane przez `count` parametru.  
  
 `count`  
 Liczba zdarzeń w podanym w tablicy `_PPEvents` parametru.  
  
 `_FWaitAll`  
 Jeśli ustawiono wartość `true`, parametr określa, że wszystkie zdarzenia w tablicy podane w `_PPEvents` parametru musi się sygnalizowane w celu spełnienia czas oczekiwania. Jeśli ustawiono wartość `false`, określa, że wszystkie zdarzenia w tablicy podane w `_PPEvents` parametru staje się sygnalizowane będą spełniały warunki czas oczekiwania.  
  
 `_Timeout`  
 Wskazuje wyrażony w milisekundach czas, zanim upłynie limit czasu oczekiwania. Wartość `COOPERATIVE_TIMEOUT_INFINITE` oznacza brak limitu czasu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli czas oczekiwania zostały spełnione, indeks w tablicy dostarczane w `_PPEvents` parametr, który spełnia warunek oczekiwania; w przeciwnym razie wartość `COOPERATIVE_WAIT_TIMEOUT` wskazująca, że czas oczekiwania upłynął limit czasu bez warunek jest spełniony.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli parametr `_FWaitAll` jest ustawiona na wartość `true` wskaż, czy wszystkie zdarzenia musi stają się informowany spełniają oczekiwania, indeks zwracane przez funkcję niesie nie specjalne znaczenie niż fakt, że nie jest wartością `COOPERATIVE_WAIT_TIMEOUT`.  
  
> [!IMPORTANT]
>  Nie należy wywoływać w aplikacji Windows platformy Uniwersalnej `wait_for_multiple` na ASTA wątku, ponieważ to wywołanie można zablokować bieżącego wątku i może spowodować, że aplikacja przestanie odpowiadać.  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności](concurrency-namespace.md)
