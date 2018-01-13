---
title: "Klasa task_options (współbieżność środowiska wykonawczego) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ppltasks/concurrency::task_options
dev_langs: C++
ms.assetid: f93d146b-70f7-46ec-8c2f-c33b8bb0af69
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 23fe15f95782fc2aead89614143786a845becd62
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="taskoptions-class-concurrency-runtime"></a>Klasa task_options (współbieżność środowiska wykonawczego)
Reprezentuje dozwolonych opcje tworzenia zadania  
  
## <a name="syntax"></a>Składnia  
  
```
class task_options;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[task_options::task_options — Konstruktor (współbieżność środowiska wykonawczego)](#ctor)|Przeciążone. Listy domyślnych opcji tworzenia zadań|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[task_options::get_cancellation_token — metoda (współbieżność środowiska wykonawczego)](#get_cancellation_token)|Zwraca token anulowania|  
|[task_options::get_continuation_context — metoda (współbieżność środowiska wykonawczego)](#get_continuation_context)|Zwraca kontekst kontynuacji|  
|[task_options::get_scheduler — metoda (współbieżność środowiska wykonawczego)](#get_scheduler)|Zwraca harmonogramu|  
|[task_options::has_cancellation_token — metoda (współbieżność środowiska wykonawczego)](#has_cancellation_token)|Wskazuje, czy token anulowania został określony przez użytkownika|  
|[task_options::has_scheduler — metoda (współbieżność środowiska wykonawczego)](#has_scheduler)|Wskazuje, czy n harmonogram został określony przez użytkownika|  
|[task_options::set_cancellation_token — metoda (współbieżność środowiska wykonawczego)](#set_cancellation_token)|Ustawia podany token w opcjach|  
|[task_options::set_continuation_context — metoda (współbieżność środowiska wykonawczego)](#set_continuation_context)|Ustawia kontekst kontynuacji danej opcji|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `task_options`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** ppltasks.h  
  
 **Namespace:** współbieżności  
  
##  <a name="get_cancellation_token"></a>task_options::get_cancellation_token — metoda (współbieżność środowiska wykonawczego)  
 Zwraca token anulowania  
  
```
cancellation_token get_cancellation_token() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
##  <a name="get_continuation_context"></a>task_options::get_continuation_context — metoda (współbieżność środowiska wykonawczego)  
 Zwraca kontekst kontynuacji  
  
```
task_continuation_context get_continuation_context() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
##  <a name="get_scheduler"></a>task_options::get_scheduler — metoda (współbieżność środowiska wykonawczego)  
 Zwraca harmonogramu  
  
```
scheduler_ptr get_scheduler() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
##  <a name="has_cancellation_token"></a>task_options::has_cancellation_token — metoda (współbieżność środowiska wykonawczego)  
 Wskazuje, czy token anulowania został określony przez użytkownika  
  
```
bool has_cancellation_token() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
##  <a name="has_scheduler"></a>task_options::has_scheduler — metoda (współbieżność środowiska wykonawczego)  
 Wskazuje, czy n harmonogram został określony przez użytkownika  
  
```
bool has_scheduler() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
##  <a name="set_cancellation_token"></a>task_options::set_cancellation_token — metoda (współbieżność środowiska wykonawczego)  
 Ustawia podany token w opcjach  
  
```
void set_cancellation_token(cancellation_token _Token);
```  
  
### <a name="parameters"></a>Parametry  
 `_Token`  
  
##  <a name="set_continuation_context"></a>task_options::set_continuation_context — metoda (współbieżność środowiska wykonawczego)  
 Ustawia kontekst kontynuacji danej opcji  
  
```
void set_continuation_context(task_continuation_context _ContinuationContext);
```  
  
### <a name="parameters"></a>Parametry  
 `_ContinuationContext`  
  
##  <a name="ctor"></a>task_options::task_options — Konstruktor (współbieżność środowiska wykonawczego)  
 Listy domyślnych opcji tworzenia zadań  
  
```
task_options();

task_options(
    cancellation_token _Token);

task_options(
    task_continuation_context _ContinuationContext);

task_options(
    cancellation_token _Token,
    task_continuation_context _ContinuationContext);

template<typename _SchedType>
task_options(
    std::shared_ptr<_SchedType> _Scheduler);

task_options(
    scheduler_interface& _Scheduler);

task_options(
    scheduler_ptr _Scheduler);

task_options(
    const task_options& _TaskOptions);
```  
  
### <a name="parameters"></a>Parametry  
 `_SchedType`  
 `_Token`  
 `_ContinuationContext`  
 `_Scheduler`  
 `_TaskOptions`  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności](concurrency-namespace.md)
