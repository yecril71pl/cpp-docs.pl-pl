---
title: "condition_variable — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- condition_variable/std::condition
- condition_variable/std::condition_variable::condition_variable
- condition_variable/std::condition_variable::native_handle
- condition_variable/std::condition_variable::notify_all
- condition_variable/std::condition_variable::notify_one
- condition_variable/std::condition_variable::wait
- condition_variable/std::condition_variable::wait_for
- condition_variable/std::condition_variable::wait_until
dev_langs: C++
ms.assetid: 80b1295c-b73d-4d46-b664-6e183f2eec1b
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
helpviewer_keywords:
- std::condition
- std::condition_variable::condition_variable
- std::condition_variable::native_handle
- std::condition_variable::notify_all
- std::condition_variable::notify_one
- std::condition_variable::wait
- std::condition_variable::wait_for
- std::condition_variable::wait_until
ms.workload: cplusplus
ms.openlocfilehash: 3b51ec2810ddb982d53c3073bdf860b26100859d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="conditionvariable-class"></a>condition_variable — Klasa
Użyj `condition_variable` klasy oczekiwania na zdarzenie, gdy masz `mutex` typu `unique_lock<mutex>`. Obiekty tego typu może mieć lepszą wydajność niż obiekty typu [condition_variable_any — < unique_lock\<obiektu mutex >>](../standard-library/condition-variable-any-class.md).  
  
## <a name="syntax"></a>Składnia  
  
```
class condition_variable;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[condition_variable —](#condition_variable)|Konstruuje `condition_variable` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[native_handle](#native_handle)|Zwraca typ implementacji reprezentujący dojście condition_variable —.|  
|[notify_all](#notify_all)|Odblokowuje wszystkie wątki, które oczekują na `condition_variable` obiektu.|  
|[notify_one](#notify_one)|Jeden z wątków, które oczekują na odblokowuje `condition_variable` obiektu.|  
|[oczekiwania](#wait)|Blokuje wątku.|  
|[wait_for](#wait_for)|Blokuje wątku i ustawia przedział czasu, po którym odblokowuje wątku.|  
|[wait_until](#wait_until)|Blokuje wątku i ustawia maksymalną punktu w czasie, w którym odblokowuje wątku.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<condition_variable — >  
  
 **Namespace:** Standard  
  
##  <a name="condition_variable"></a>condition_variable::condition_variable — Konstruktor  
 Konstruuje `condition_variable` obiektu.  
  
```
condition_variable();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli nie ma wystarczającej ilości pamięci jest dostępny, zgłasza konstruktora [system_error —](../standard-library/system-error-class.md) obiektu, który ma `not_enough_memory` kod błędu. Jeśli nie można utworzyć obiektu, ponieważ innego zasobu nie jest dostępna, zgłasza konstruktora `system_error` obiektu, który ma `resource_unavailable_try_again` kod błędu.  
  
##  <a name="native_handle"></a>condition_variable::native_handle  
 Zwraca typ konkretnej implementacji, który reprezentuje dojście condition_variable —.  
  
```
native_handle_type native_handle();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `native_handle_type`nie zdefiniowano jako wskaźnik do struktur danych wewnętrznych współbieżność środowiska wykonawczego.  
  
##  <a name="notify_all"></a>condition_variable::notify_all  
 Odblokowuje wszystkie wątki, które oczekują na `condition_variable` obiektu.  
  
```
void notify_all() noexcept;
```  
  
##  <a name="notify_one"></a>condition_variable::notify_one  
 Jeden z wątków, które oczekują na odblokowuje `condition_variable` obiektu.  
  
```
void notify_one() noexcept;
```  
  
##  <a name="wait"></a>condition_variable::wait  
 Blokuje wątku.  
  
```
void wait(unique_lock<mutex>& Lck);

template <class Predicate>
void wait(unique_lock<mutex>& Lck, Predicate Pred);
```  
  
### <a name="parameters"></a>Parametry  
 `Lck`  
 A [unique_lock\<obiektu mutex >](../standard-library/unique-lock-class.md) obiektu.  
  
 `Pred`  
 Dowolne wyrażenie zwracające `true` lub `false`.  
  
### <a name="remarks"></a>Uwagi  
 Pierwsza metoda blokuje do `condition_variable` obiektu zostanie zasygnalizowane przez wywołanie do [notify_one](#notify_one) lub [notify_all](#notify_all). On również wybudzania spuriously.  
  
 Druga metoda wykonuje w efekcie następujący kod.  
  
```cpp  
while(!Pred())
    wait(Lck);
```    
  
##  <a name="wait_for"></a>condition_variable::wait_for  
 Blokuje wątku i ustawia przedział czasu, po którym odblokowuje wątku.  
  
```
template <class Rep, class Period>
cv_status wait_for(
    unique_lock<mutex>& Lck,
    const chrono::duration<Rep, Period>& Rel_time);

template <class Rep, class Period, class Predicate>
bool wait_for(
    unique_lock<mutex>& Lck,
    const chrono::duration<Rep, Period>& Rel_time, 
    Predicate Pred);
```  
  
### <a name="parameters"></a>Parametry  
 `Lck`  
 A [unique_lock\<obiektu mutex >](../standard-library/unique-lock-class.md) obiektu.  
  
 `Rel_time`  
 A `chrono::duration` obiekt, który określa ilość czasu przed wątku zostanie wznowiona.  
  
 `Pred`  
 Dowolne wyrażenie zwracające `true` lub `false`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwsza metoda zwraca `cv_status::timeout` jeśli kończy czas oczekiwania, kiedy `Rel_time` upłynął. W przeciwnym razie metoda zwraca `cv_status::no_timeout`.  
  
 Druga metoda zwraca wartość `Pred`.  
  
### <a name="remarks"></a>Uwagi  
 Pierwsza metoda blokuje do `condition_variable` obiektu zostanie zasygnalizowane przez wywołanie do [notify_one](#notify_one) lub [notify_all](#notify_all) lub do czasu przedział czasu `Rel_time` upłynął. On również wybudzania spuriously.  
  
 Druga metoda wykonuje w efekcie następujący kod.  
  
```cpp  
while(!Pred())
    if(wait_for(Lck, Rel_time) == cv_status::timeout)
    return Pred();

return true;
```  
  
##  <a name="wait_until"></a>condition_variable::wait_until  
 Blokuje wątku i ustawia maksymalną punktu w czasie, w którym odblokowuje wątku.  
  
```
template <class Clock, class Duration>
cv_status wait_until(
    unique_lock<mutex>& Lck,
    const chrono::time_point<Clock, Duration>& Abs_time);

template <class Clock, class Duration, class Predicate>
bool wait_until(
    unique_lock<mutex>& Lck,
    const chrono::time_point<Clock, Duration>& Abs_time, 
    Predicate Pred);

cv_status wait_until(
    unique_lock<mutex>& Lck,
    const xtime* Abs_time);

template <class Predicate>
bool wait_until(
    unique_lock<mutex>& Lck,
    const xtime* Abs_time, 
    Predicate Pred);
```  
  
### <a name="parameters"></a>Parametry  
 `Lck`  
 A [unique_lock\<obiektu mutex >](../standard-library/unique-lock-class.md) obiektu.  
  
 `Abs_time`  
 A [chrono::time_point](../standard-library/time-point-class.md) obiektu.  
  
 `Pred`  
 Dowolne wyrażenie zwracające `true` lub `false`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Metody zwracające `cv_status` typ zwracany `cv_status::timeout` jeśli kończy czas oczekiwania, kiedy `Abs_time` upływa. W przeciwnym razie zwracany metody `cv_status::no_timeout`.  
  
 Metody zwracające `bool` zwrócić wartość `Pred`.  
  
### <a name="remarks"></a>Uwagi  
 Pierwsza metoda blokuje do `condition_variable` obiektu zostanie zasygnalizowane przez wywołanie do [notify_one](#notify_one) lub [notify_all](#notify_all) lub do czasu `Abs_time`. On również wybudzania spuriously.  
  
 W efekcie druga metoda wykonuje następujący kod  
  
```cpp  
while(!Pred())
    if(wait_until(Lck, Abs_time) == cv_status::timeout)
    return Pred();

return true;
```  
  
 Metody trzeci i czwarty używać wskaźnika do obiektu typu `xtime` zastąpić `chrono::time_point` obiektu. `xtime` Obiektu określa maksymalną ilość czasu oczekiwania na sygnał.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)   
 [<condition_variable>](../standard-library/condition-variable.md)



