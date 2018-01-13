---
title: "Schedulerpolicy — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SchedulerPolicy
- concrt/concurrency::SchedulerPolicy
- concrt/concurrency::SchedulerPolicy::SchedulerPolicy
- concrt/concurrency::SchedulerPolicy::GetPolicyValue
- concrt/concurrency::SchedulerPolicy::SetConcurrencyLimits
- concrt/concurrency::SchedulerPolicy::SetPolicyValue
dev_langs: C++
helpviewer_keywords: SchedulerPolicy class
ms.assetid: bcebf51a-65f8-45a3-809b-d1ff93527dc4
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7ce629f81d952a274a86aafba71da126c65946f5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="schedulerpolicy-class"></a>SchedulerPolicy — Klasa
`SchedulerPolicy` Klasa zawiera zbiór pary klucz wartość, po jednej dla każdego elementu zasad, które określają zachowanie wystąpienia harmonogramu.  
  
## <a name="syntax"></a>Składnia  
  
```
class SchedulerPolicy;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Schedulerpolicy —](#ctor)|Przeciążone. Tworzy nową zasadę harmonogramu i wypełnia wartości [zasad kluczy](concurrency-namespace-enums.md) obsługiwane przez współbieżność środowiska wykonawczego planiści i Menedżera zasobów.|  
|[~ SchedulerPolicy — destruktor](#dtor)|Niszczy zasad harmonogramu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[GetPolicyValue](#getpolicyvalue)|Pobiera wartość klucza zasad podana jako `key` parametru.|  
|[SetConcurrencyLimits](#setconcurrencylimits)|Ustawia jednocześnie `MinConcurrency` i `MaxConcurrency` zasad na `SchedulerPolicy` obiektu.|  
|[SetPolicyValue](#setpolicyvalue)|Ustawia wartość klucza zasad podana jako `key` parametrów i zwraca stara wartość.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[operator =](#operator_eq)|Przypisuje zasad harmonogramu z innego zasad harmonogramu.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat zasad, które mogą być kontrolowane za pomocą `SchedulerPolicy` , zobacz [policyelementkey —](concurrency-namespace-enums.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `SchedulerPolicy`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrt.h, concrtrm.h  
  
 **Namespace:** współbieżności  
  
##  <a name="getpolicyvalue"></a>GetPolicyValue 

 Pobiera wartość klucza zasad podana jako `key` parametru.  
  
```
unsigned int GetPolicyValue(PolicyElementKey key) const;
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klucz zasad można pobrać wartości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli klucz określony przez `key` parametr jest obsługiwany, rzutować wartości zasad dla klucza `unsigned int`.  
  
### <a name="remarks"></a>Uwagi  
 Metoda zgłosi [invalid_scheduler_policy_key —](invalid-scheduler-policy-key-class.md) klucza nieprawidłowe zasady.  
  
##  <a name="operator_eq"></a>operator = 

 Przypisuje zasad harmonogramu z innego zasad harmonogramu.  
  
```
SchedulerPolicy& operator= (const SchedulerPolicy& _RhsPolicy);
```  
  
### <a name="parameters"></a>Parametry  
 `_RhsPolicy`  
 Zasady można przypisać do tych zasad.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do zasad harmonogramu.  
  
### <a name="remarks"></a>Uwagi  
 Często najwygodniejsza sposób definiowania nowych zasad harmonogramu polega na skopiowaniu istniejących zasad i modyfikować za pomocą `SetPolicyValue` lub `SetConcurrencyLimits` metody.  
  
##  <a name="ctor"></a>Schedulerpolicy — 

 Tworzy nową zasadę harmonogramu i wypełnia wartości [zasad kluczy](concurrency-namespace-enums.md) obsługiwane przez współbieżność środowiska wykonawczego planiści i Menedżera zasobów.  
  
```
SchedulerPolicy();

SchedulerPolicy(
    size_t _PolicyKeyCount,
 ...);

SchedulerPolicy(
    const SchedulerPolicy& _SrcPolicy);
```  
  
### <a name="parameters"></a>Parametry  
 `_PolicyKeyCount`  
 Poniżej pary klucz/wartość liczby `_PolicyKeyCount` parametru.  
  
 `_SrcPolicy`  
 Zasady źródłowe do skopiowania.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy Konstruktor tworzy nowe zasady harmonogramu, gdzie wszystkie zasady zostaną zainicjowane do wartości domyślnych.  
  
 Drugi Konstruktor tworzy nową zasadę harmonogram używany styl parametru o nazwie inicjowania. Wartości po `_PolicyKeyCount` parametru jako pary klucz wartość. Dowolny klawisz zasad, która nie jest określana w tym konstruktorze będzie mieć wartość domyślną. Ten konstruktor może zgłaszać wyjątki [invalid_scheduler_policy_key —](invalid-scheduler-policy-key-class.md), [invalid_scheduler_policy_value —](invalid-scheduler-policy-value-class.md) lub [invalid_scheduler_policy_thread_specification —](invalid-scheduler-policy-thread-specification-class.md).  
  
 Trzeci Konstruktor jest Konstruktor kopiujący. Często najwygodniejsza sposób definiowania nowych zasad harmonogramu polega na skopiowaniu istniejących zasad i modyfikować za pomocą `SetPolicyValue` lub `SetConcurrencyLimits` metody.  
  
##  <a name="dtor"></a>~ Schedulerpolicy — 

 Niszczy zasad harmonogramu.  
  
```
~SchedulerPolicy();
```  
  
##  <a name="setconcurrencylimits"></a>SetConcurrencyLimits 

 Ustawia jednocześnie `MinConcurrency` i `MaxConcurrency` zasad na `SchedulerPolicy` obiektu.  
  
```
void SetConcurrencyLimits(
    unsigned int _MinConcurrency,
    unsigned int _MaxConcurrency = MaxExecutionResources);
```  
  
### <a name="parameters"></a>Parametry  
 `_MinConcurrency`  
 Wartość `MinConcurrency` klucza zasad.  
  
 `_MaxConcurrency`  
 Wartość `MaxConcurrency` klucza zasad.  
  
### <a name="remarks"></a>Uwagi  
 Metoda zgłosi [invalid_scheduler_policy_thread_specification —](invalid-scheduler-policy-thread-specification-class.md) Jeśli wartość określona dla `MinConcurrency` zasad jest większy niż określony dla `MaxConcurrency` zasad.  
  
 Metoda może również zgłosić [invalid_scheduler_policy_value —](invalid-scheduler-policy-value-class.md) inne nieprawidłowe wartości.  
  
##  <a name="setpolicyvalue"></a>SetPolicyValue 

 Ustawia wartość klucza zasad podana jako `key` parametrów i zwraca stara wartość.  
  
```
unsigned int SetPolicyValue(
    PolicyElementKey key,
    unsigned int value);
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klucz zasady można ustawić wartości.  
  
 `value`  
 Wartość do ustawienia klucza zasad.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli klucz określony przez `key` parametr jest obsługiwany, stara wartość zasad dla klucza rzutować `unsigned int`.  
  
### <a name="remarks"></a>Uwagi  
 Metoda zgłosi [invalid_scheduler_policy_key —](invalid-scheduler-policy-key-class.md) dla klucza nieprawidłowe zasady lub dowolny klawisz zasad, którego wartość nie może ustawić `SetPolicyValue` metody.  
  
 Metoda zgłosi [invalid_scheduler_policy_value —](invalid-scheduler-policy-value-class.md) dla wartości, która nie jest obsługiwana dla klucza określonego przez `key` parametru.  
  
 Należy pamiętać, że ta metoda nie może ustawić `MinConcurrency` lub `MaxConcurrency` zasad. Aby ustawić te wartości, należy użyć [SetConcurrencyLimits](#setconcurrencylimits) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [Policyelementkey —](concurrency-namespace-enums.md)   
 [Currentscheduler — klasa](currentscheduler-class.md)   
 [Klasa harmonogramu](scheduler-class.md)   
 [Harmonogram zadań](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)



