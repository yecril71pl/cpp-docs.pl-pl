---
title: "packaged_task — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- future/std::packaged_task
- future/std::packaged_task::packaged_task
- future/std::packaged_task::get_future
- future/std::packaged_task::make_ready_at_thread_exit
- future/std::packaged_task::reset
- future/std::packaged_task::swap
- future/std::packaged_task::valid
- future/std::packaged_task::operator()
- future/std::packaged_task::operator bool
dev_langs:
- C++
ms.assetid: 0a72cbe3-f22a-4bfe-8e50-dcb268c98780
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
helpviewer_keywords:
- std::packaged_task [C++]
- std::packaged_task [C++], packaged_task
- std::packaged_task [C++], get_future
- std::packaged_task [C++], make_ready_at_thread_exit
- std::packaged_task [C++], reset
- std::packaged_task [C++], swap
- std::packaged_task [C++], valid
ms.workload:
- cplusplus
ms.openlocfilehash: 6ce3db6f4685d8448efd88bf2203d541cc864abd
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="packagedtask-class"></a>packaged_task — Klasa
W tym artykule opisano *asynchroniczne dostawcy* czyli otoka wywołanie jest których sygnatury wywołania `Ty(ArgTypes...)`. Jego *skojarzony stan asynchronicznego* przechowuje kopię jego można wywołać obiektu oprócz potencjalnych wyników.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class>
class packaged_task;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[packaged_task](#packaged_task)|Konstruuje `packaged_task` obiektu.|  
|[packaged_task:: ~ packaged_task — destruktor](#dtorpackaged_task_destructor)|Niszczy `packaged_task` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[get_future](#get_future)|Zwraca [przyszłych](../standard-library/future-class.md) obiektu, który ma taką samą skojarzony stan asynchronicznego.|  
|[make_ready_at_thread_exit](#make_ready_at_thread_exit)|Wywołuje można wywołać obiekt, który jest przechowywany w skojarzony stan asynchroniczne i automatycznie przechowuje zwracanej wartości.|  
|[reset](#reset)|Zastępuje skojarzony stan asynchronicznego.|  
|[swap](#swap)|Zamienia skojarzony stan asynchroniczne z określony obiekt.|  
|[Nieprawidłowa](#valid)|Określa, czy obiekt jest skojarzony stan asynchronicznego.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[packaged_task::operator=](#op_eq)|Przenosi skojarzony stan asynchronicznego od określonego obiektu.|  
|[packaged_task::operator()](#op_call)|Wywołuje można wywołać obiekt, który jest przechowywany w skojarzony stan asynchroniczne, automatycznie przechowuje zwrócona wartość i ustawia stan *gotowe*.|  
|[packaged_task::operator bool](#op_bool)|Określa, czy obiekt jest skojarzony stan asynchronicznego.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<przyszłych >  
  
 **Namespace:** Standard  
  
##  <a name="get_future"></a>  packaged_task::get_future  
 Zwraca obiekt typu `future<Ty>` ma taką samą *skojarzony stan asynchronicznego*.  
  
```
future<Ty> get_future();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `packaged_task` obiekt nie ma skojarzony stan asynchroniczne, ta metoda zgłasza [future_error —](../standard-library/future-error-class.md) mający z kodem błędu `no_state`.  
  
 Jeśli ta metoda została już wywołana dla `packaged_task` asynchroniczne stan skojarzony obiekt, który ma taką samą, metoda wygeneruje `future_error` mający z kodem błędu `future_already_retrieved`.  
  
##  <a name="make_ready_at_thread_exit"></a>  packaged_task::make_ready_at_thread_exit  
 Wywołuje metodę można wywołać obiektu, który jest przechowywany w *skojarzony stan asynchronicznego* i automatycznie przechowuje zwracanej wartości.  
  
```
void make_ready_at_thread_exit(ArgTypes... args);
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `packaged_task` obiekt nie jest skojarzony stan asynchroniczne, ta metoda zgłasza [future_error —](../standard-library/future-error-class.md) mający z kodem błędu `no_state`.  
  
 Jeśli ta metoda lub [make_ready_at_thread_exit](#make_ready_at_thread_exit) została już wywołana dla `packaged_task` asynchroniczne stan skojarzony obiekt, który ma taką samą, metoda wygeneruje `future_error` mający z kodem błędu `promise_already_satisfied`.  
  
 W przeciwnym razie wywołuje ten operator `INVOKE(fn, args..., Ty)`, gdzie *fn* jest można wywołać obiekt, który jest przechowywany w skojarzony stan asynchronicznego. Wartości zwracane jest automatycznie przechowywane jako zwrócony wynik skojarzony stan asynchronicznego.  
  
 Contrast do [packaged_task:: operator()](#op_call), skojarzony stan asynchronicznego nie jest równa `ready` aż po wszystkich wątków lokalnych obiektów w wątku wywołującym zostały zniszczone. Zazwyczaj wątków, które są zablokowane na skojarzony stan asynchroniczne nie są odblokowane, dopóki kończy działanie wątku wywołującym.  
  
##  <a name="op_eq"></a>  packaged_task::operator =  
 Transfery *skojarzony stan asynchronicznego* od określonego obiektu.  
  
```
packaged_task& operator=(packaged_task&& Right);
```  
  
### <a name="parameters"></a>Parametry  
 `Right`  
 A `packaged_task` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `*this`  
  
### <a name="remarks"></a>Uwagi  
 Po wykonaniu operacji `Right` nie ma już skojarzony stan asynchronicznego.  
  
##  <a name="op_call"></a>  packaged_task:: operator()  
 Wywołuje metodę można wywołać obiektu, który jest przechowywany w *skojarzony stan asynchronicznego*, automatycznie przechowuje zwrócona wartość i ustawia stan *gotowe*.  
  
```
void operator()(ArgTypes... args);
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `packaged_task` obiekt nie jest skojarzony stan asynchroniczne, ta metoda zgłasza [future_error —](../standard-library/future-error-class.md) mający z kodem błędu `no_state`.  
  
 Jeśli ta metoda lub [make_ready_at_thread_exit](#make_ready_at_thread_exit) została już wywołana dla `packaged_task` asynchroniczne stan skojarzony obiekt, który ma taką samą, metoda wygeneruje `future_error` mający z kodem błędu `promise_already_satisfied`.  
  
 W przeciwnym razie wywołuje ten operator `INVOKE(fn, args..., Ty)`, gdzie *fn* jest można wywołać obiekt, który jest przechowywany w skojarzony stan asynchronicznego. Wszelkie zwrócona wartość jest przechowywana atomowo jako zwrócony wynik skojarzony stan asynchroniczne, a stan jest ustawiony na gotowe. W związku z tym wszystkie wątków, które są zablokowane na skojarzony stan asynchronicznego stają się odblokowany.  
  
##  <a name="op_bool">packaged_task::operator bool</a>  
 Określa, czy obiekt ma `associated asynchronous state`.  
  
```
operator bool() const noexcept;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli obiekt ma skojarzony stan asynchronicznego; w przeciwnym razie `false`.  
  
##  <a name="packaged_task"></a>  packaged_task::packaged_task — Konstruktor  
 Konstruuje `packaged_task` obiektu.  
  
```
packaged_task() noexcept;
packaged_task(packaged_task&& Right) noexcept;
template <class Fn>
   explicit packaged_task(Fn&& fn);

template <class Fn, class Alloc>
   explicit packaged_task(
      allocator_arg_t, const Alloc& alloc, Fn&& fn);
```  
  
### <a name="parameters"></a>Parametry  
 `Right`  
 A `packaged_task` obiektu.  
  
 `alloc`  
 Program przydzielania pamięci. Aby uzyskać więcej informacji, zobacz [ \<allocators — >](../standard-library/allocators-header.md).  
  
 `fn`  
 Obiekt funkcyjny.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy konstrukcje konstruktora `packaged_task` obiektu, którego nie zdefiniowano *skojarzony stan asynchronicznego*.  
  
 Drugi konstrukcje konstruktora `packaged_task` obiektu i przenosi skojarzony stan asynchroniczne z `Right`. Po wykonaniu operacji `Right` nie ma już skojarzony stan asynchronicznego.  
  
 Trzeci konstrukcje konstruktora `packaged_task` obiekt, który ma kopię `fn` przechowywane w stanie skojarzone asynchronicznego.  
  
 Czwarty konstrukcje konstruktora `packaged_task` obiekt, który ma kopię `fn` przechowywane w stanie skojarzone asynchroniczne i używa `alloc` alokacji pamięci.  
  
##  <a name="dtorpackaged_task_destructor">packaged_task:: ~ packaged_task — destruktor</a>  
 Niszczy `packaged_task` obiektu.  
  
```
~packaged_task();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli *skojarzony stan asynchronicznego* nie jest *gotowe*, magazyny destruktora [future_error —](../standard-library/future-error-class.md) wyjątek, który zawiera kod błędu `broken_promise` jako wynik w skojarzony stan asynchroniczne, a wszelkie wątków, które są zablokowane na skojarzony stan asynchronicznego zostać odblokowany.  
  
##  <a name="reset"></a>  packaged_task::reset  
 Używa nowego *skojarzony stan asynchronicznego* Aby zastąpić istniejącą skojarzony stan asynchronicznego.  
  
```
void reset();
```  
  
### <a name="remarks"></a>Uwagi  
 W efekcie ta metoda jest wykonywana `*this = packaged_task(move(fn))`, gdzie *fn* jest obiekt funkcji, który jest przechowywany w skojarzony stan asynchronicznej dla tego obiektu. W związku z tym stan obiektu jest wyczyszczone, a [get_future](#get_future), [operator()](#op_call), i [make_ready_at_thread_exit](#make_ready_at_thread_exit) można wywołać tak, jakby dla obiekt nowo skonstruowany.  
  
##  <a name="swap"></a>  packaged_task::swap  
 Zamienia skojarzony stan asynchroniczne z określony obiekt.  
  
```
void swap(packaged_task& Right) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Right`  
 A `packaged_task` obiektu.  
  
##  <a name="valid"></a>  packaged_task::valid  
 Określa, czy obiekt ma `associated asynchronous state`.  
  
```
bool valid() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli obiekt ma skojarzony stan asynchronicznego; w przeciwnym razie `false`.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)   
 [\<future>](../standard-library/future.md)



