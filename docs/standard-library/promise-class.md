---
title: "Promise — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- future/std::promise
- future/std::promise::promise
- future/std::promise::get_future
- future/std::promise::set_exception
- future/std::promise::set_exception_at_thread_exit
- future/std::promise::set_value
- future/std::promise::set_value_at_thread_exit
- future/std::promise::swap
dev_langs:
- C++
ms.assetid: 2931558c-d94a-4ba1-ac4f-20bf7b6e23f9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
helpviewer_keywords:
- std::promise [C++]
- std::promise [C++], promise
- std::promise [C++], get_future
- std::promise [C++], set_exception
- std::promise [C++], set_exception_at_thread_exit
- std::promise [C++], set_value
- std::promise [C++], set_value_at_thread_exit
- std::promise [C++], swap
ms.workload:
- cplusplus
ms.openlocfilehash: 6673483beb2552ba1b3a11b76d65e9be484c2a39
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="promise-class"></a>promise — Klasa
W tym artykule opisano *asynchroniczne dostawcy*.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Ty>
class promise;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Promise](#promise)|Konstruuje `promise` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[get_future](#get_future)|Zwraca [przyszłych](../standard-library/future-class.md) skojarzone z tym promise.|  
|[set_exception](#set_exception)|Automatycznie ustawia wynik promise tego wskazująca Wystąpił wyjątek.|  
|[set_exception_at_thread_exit](#set_exception_at_thread_exit)|Automatycznie ustawia wynik promise tego wskazująca wyjątek i dostarcza powiadomienie, które zostały zniszczone tylko obiekty po wszystkich wątków lokalnych w bieżącym wątku (zazwyczaj w chwili zakończenia wątku).|  
|[set_value](#set_value)|Automatycznie ustawia wynik promise tego wskazująca wartość.|  
|[set_value_at_thread_exit](#set_value_at_thread_exit)|Automatycznie ustawia wynik tego obietnicę w celu wskazuje wartość, a zapewnia powiadomienie, które zostały zniszczone tylko obiekty po wszystkich wątków lokalnych w bieżącym wątku (zazwyczaj w chwili zakończenia wątku).|  
|[swap](#swap)|Wymiana *skojarzony stan asynchronicznego* z tym promise z obiekt promise określony.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Promise::operator =](#op_eq)|Przypisanie udostępniony stan tego obiektu promise.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `promise`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<przyszłych >  
  
 **Namespace:** Standard  
  
##  <a name="get_future"></a>  Promise::get_future  
 Zwraca [przyszłych](../standard-library/future-class.md) obiektu, który ma taką samą *skojarzony stan asynchronicznego* jako tego promise.  
  
```
future<Ty> get_future();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli obiekt promise jest pusty, ta metoda zgłasza [future_error —](../standard-library/future-error-class.md) mający [error_code —](../standard-library/error-code-class.md) z `no_state`.  
  
 Jeśli ta metoda została już wywołana dla obiekt promise, który ma tego samego skojarzony stan asynchroniczne, metoda wygeneruje `future_error` mający `error_code` z `future_already_retrieved`.  
  
##  <a name="op_eq">Promise::operator =</a>  
 Transfery *skojarzony stan asynchronicznego* z określonej `promise` obiektu.  
  
```
promise& operator=(promise&& Other) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Other`  
 A `promise` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `*this`  
  
### <a name="remarks"></a>Uwagi  
 Ten operator przenosi skojarzony stan asynchroniczne z `Other`. Po przesłaniu `Other` jest *pusty*.  
  
##  <a name="promise"></a>  Promise::Promise — Konstruktor  
 Konstruuje `promise` obiektu.  
  
```
promise();
template <class Alloc>
promise(allocator_arg_t, const Alloc& Al);
promise(promise&& Other) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Al`  
 Program przydzielania pamięci. Zobacz [ \<allocators — >](../standard-library/allocators-header.md) Aby uzyskać więcej informacji.  
  
 `Other`  
 A `promise` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy konstrukcje konstruktora *pusty* `promise` obiektu.  
  
 Drugi Konstruktor tworzy pustą `promise` obiektu i używa `Al` alokacji pamięci.  
  
 Trzeci konstrukcje konstruktora `promise` obiektu i przenosi skojarzony stan asynchroniczne z `Other`i pozostawienie `Other` puste.  
  
##  <a name="set_exception"></a>  Promise::set_exception  
 Automatycznie przechowuje Wystąpił wyjątek w wyniku tego `promise` obiektu i zestawy *skojarzony stan asynchronicznego* do *gotowe*.  
  
```
void set_exception(exception_ptr Exc);
```  
  
### <a name="parameters"></a>Parametry  
 `Exc`  
 [Exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) przechowywanej przez tę metodę w wyniku wyjątku.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `promise` obiekt nie ma żadnych skojarzony stan asynchroniczne, ta metoda zgłasza [future_error —](../standard-library/future-error-class.md) mający z kodem błędu `no_state`.  
  
 Jeśli `set_exception`, [set_exception_at_thread_exit](#set_exception_at_thread_exit), [set_value](#set_value), lub [set_value_at_thread_exit](#set_value_at_thread_exit) została już wywołana dla `promise` obiekt, który ma takie same skojarzony stan asynchroniczne, ta metoda zgłasza `future_error` mający z kodem błędu `promise_already_satisfied`.  
  
 W wyniku tej metody wszelkie wątków, które są zablokowane na skojarzony stan asynchronicznego stają się odblokowany.  
  
##  <a name="set_exception_at_thread_exit"></a>  Promise::set_exception_at_thread_exit  
 Automatycznie ustawia wynik `promise` wskaż wyjątek, dostarczanie powiadomienia tylko po wszystkich wątków lokalnych obiektów w bieżącym wątku został zlikwidowany (zazwyczaj w chwili zakończenia wątku).  
  
```
void set_exception_at_thread_exit(exception_ptr Exc);
```  
  
### <a name="parameters"></a>Parametry  
 `Exc`  
 [Exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) przechowywanej przez tę metodę w wyniku wyjątku.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli nie ma obiektu promise *skojarzony stan asynchronicznego*, ta metoda zgłasza [future_error —](../standard-library/future-error-class.md) mający z kodem błędu `no_state`.  
  
 Jeśli [set_exception](#set_exception), `set_exception_at_thread_exit`, [set_value](#set_value), lub [set_value_at_thread_exit](#set_value_at_thread_exit) została już wywołana dla `promise` obiektu, który ma taką samą skojarzony stan asynchroniczne, ta metoda zgłasza `future_error` mający z kodem błędu `promise_already_satisfied`.  
  
 Contrast do [set_exception](#set_exception), ta metoda nie ustawia skojarzony stan asynchronicznego Aby przygotować aż po wszystkich wątków lokalnych obiektów w bieżącym wątku zostały zniszczone. Zazwyczaj wątków, które są zablokowane na skojarzony stan asynchroniczne nie są odblokowane, dopóki opuszcza bieżącego wątku.  
  
##  <a name="set_value"></a>  Promise::set_value  
 Automatycznie zapisuje wartość jako wynik `promise` obiektu i zestawy *skojarzony stan asynchronicznego* do *gotowe*.  
  
```
void promise::set_value(const Ty& Val);
void promise::set_value(Ty&& Val);
void promise<Ty&>::set_value(Ty& Val);
void promise<void>::set_value();
```  
  
### <a name="parameters"></a>Parametry  
 `Val`  
 Wartość, które mają być przechowywane w wyniku.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `promise` obiekt nie ma żadnych skojarzony stan asynchroniczne, ta metoda zgłasza [future_error —](../standard-library/future-error-class.md) mający z kodem błędu `no_state`.  
  
 Jeśli [set_exception](#set_exception), [set_exception_at_thread_exit](#set_exception_at_thread_exit), `set_value`, lub [set_value_at_thread_exit](#set_value_at_thread_exit) została już wywołana dla `promise` obiektu który ma tego samego skojarzony stan asynchroniczne, ta metoda zgłasza `future_error` mający z kodem błędu `promise_already_satisfied`.  
  
 W wyniku tej metody wszelkie wątków, które są zablokowane na skojarzony stan asynchronicznego stają się odblokowany.  
  
 Pierwsza metoda również zgłoszenie wyjątku zgłoszonego podczas `Val` jest kopiowana do skojarzony stan asynchronicznego. W takiej sytuacji skojarzony stan asynchronicznego nie jest ustawiona na gotowe.  
  
 Druga metoda również zgłoszenie wyjątku zgłoszonego podczas `Val` jest przenoszony do skojarzony stan asynchronicznego. W takiej sytuacji skojarzony stan asynchronicznego nie jest ustawiona na gotowe.  
  
 Dla specjalizacji częściowej `promise<Ty&>`, przechowywana wartość skutkuje to odwołanie do `Val`.  
  
 Dla specjalizacji `promise<void>`, nie ma żadnej przechowywanej wartości.  
  
##  <a name="set_value_at_thread_exit"></a>  Promise::set_value_at_thread_exit  
 Automatycznie zapisuje wartość jako wynik `promise` obiektu.  
  
```
void promise::set_value_at_thread_exit(const Ty& Val);
void promise::set_value_at_thread_exit(Ty&& Val);
void promise<Ty&>::set_value_at_thread_exit(Ty& Val);
void promise<void>::set_value_at_thread_exit();
```  
  
### <a name="parameters"></a>Parametry  
 `Val`  
 Wartość, które mają być przechowywane w wyniku.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli nie ma obiektu promise *skojarzony stan asynchronicznego*, ta metoda zgłasza [future_error —](../standard-library/future-error-class.md) mający z kodem błędu `no_state`.  
  
 Jeśli [set_exception](#set_exception), [set_exception_at_thread_exit](#set_exception_at_thread_exit), [set_value](#set_value), lub `set_value_at_thread_exit` została już wywołana dla `promise` obiektu, który ma taką samą skojarzony stan asynchroniczne, ta metoda zgłasza `future_error` mający z kodem błędu `promise_already_satisfied`.  
  
 Contrast do `set_value`, skojarzony stan asynchronicznego nie ustawiono gotowe do momentu po wszystkich wątków lokalnych obiektów w bieżącym wątku zostały zniszczone. Zazwyczaj wątków, które są zablokowane na skojarzony stan asynchroniczne nie są odblokowane, dopóki opuszcza bieżącego wątku.  
  
 Pierwsza metoda również zgłoszenie wyjątku zgłoszonego podczas `Val` jest kopiowana do skojarzony stan asynchronicznego.  
  
 Druga metoda również zgłoszenie wyjątku zgłoszonego podczas `Val` jest przenoszony do skojarzony stan asynchronicznego.  
  
 Dla specjalizacji częściowej `promise<Ty&>`, przechowywana wartość jest odwołaniem do `Val`.  
  
 Dla specjalizacji `promise<void>`, nie ma żadnej przechowywanej wartości.  
  
##  <a name="swap"></a>  Promise::swap  
 Wymiana *skojarzony stan asynchronicznego* tego obiektu promise określony obiekt.  
  
```
void swap(promise& Other) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Other`  
 A `promise` obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)




 

