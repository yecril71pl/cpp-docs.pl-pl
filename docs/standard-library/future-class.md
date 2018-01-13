---
title: "Klasa przyszłych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- future/std::future
- future/std::future::future
- future/std::future::get
- future/std::future::share
- future/std::future::valid
- future/std::future::wait
- future/std::future::wait_for
- future/std::future::wait_until
dev_langs: C++
ms.assetid: 495e82c3-5341-4e37-87dd-b40107fbdfb6
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
helpviewer_keywords:
- std::future [C++]
- std::future [C++], future
- std::future [C++], get
- std::future [C++], share
- std::future [C++], valid
- std::future [C++], wait
- std::future [C++], wait_for
- std::future [C++], wait_until
ms.workload: cplusplus
ms.openlocfilehash: 1de870da42504494e672cff4272fd230d1346114
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="future-class"></a>future — Klasa
W tym artykule opisano *asynchronicznego obiektu zwracanego*.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Ty>
class future;
```  
  
## <a name="remarks"></a>Uwagi  
 Każdy standard *asynchroniczne dostawcy* zwraca obiekt, którego typ jest instancją tego szablonu. A `future` obiektu zapewnia tylko dostęp do asynchronicznego dostawcy skojarzonego z. Wiele asynchroniczne zwracany obiektów, które są skojarzone z tego samego dostawcy asynchroniczne, należy skopiować `future` do obiektu [shared_future —](../standard-library/shared-future-class.md) obiektu.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[przyszłe](#future)|Konstruuje `future` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[get](#get)|Pobiera wynik, który jest przechowywany w skojarzony stan asynchronicznego.|  
|[Udostępnij](#share)|Konwertuje obiekt na `shared_future`.|  
|[Nieprawidłowa](#valid)|Określa, czy obiekt nie jest pusty.|  
|[oczekiwania](#wait)|Blokuje bieżącego wątku, dopóki skojarzony stan asynchroniczne jest gotowy.|  
|[wait_for](#wait_for)|Bloki do skojarzony stan asynchroniczne jest gotowy lub przed upływem czasu określonego.|  
|[wait_until](#wait_until)|Bloki do skojarzony stan asynchroniczne jest gotowe lub do określonego punktu w czasie.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Future::operator =](#op_eq)|Przenosi skojarzony stan asynchronicznego od określonego obiektu.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<przyszłych >  
  
 **Namespace:** Standard  
  
##  <a name="future"></a>Future::Future — Konstruktor  
 Konstruuje `future` obiektu.  
  
```
future() noexcept;
future(future&& Other) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Other`  
 A `future` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy konstrukcje konstruktora `future` obiekt, który nie ma skojarzonego stan asynchronicznego.  
  
 Drugi konstrukcje konstruktora `future` obiektu i przenosi skojarzony stan asynchroniczne z `Other`. `Other`nie ma już skojarzony stan asynchronicznego.  
  
##  <a name="get"></a>Future::Get  
 Pobiera wynik, który jest przechowywany w skojarzony stan asynchronicznego.  
  
```
Ty get();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli wynik wynosi wyjątek, metoda ponownie zgłasza wyjątek go. W przeciwnym razie wynik zostanie zwrócony.  
  
### <a name="remarks"></a>Uwagi  
 Przed jego pobiera wynik, ta metoda blokuje bieżący wątek aż skojarzony stan asynchronicznego będzie gotowa.  
  
 Dla specjalizacji częściowej `future<Ty&>`, przechowywana wartość jest odwołanie do obiektu, który został przekazany do asynchronicznego dostawcy jako wartość zwracaną.  
  
 Ponieważ przechowywanych wartość nie istnieje dla specjalizacji `future<void>`, metoda zwraca `void`.  
  
 W innych specjalizacje metody przenosi jego wartość zwrotna z wartością przechowywaną. W związku z tym tylko raz wywołać tę metodę.  
  
##  <a name="op_eq"></a>Future::operator =  
 Przenosi skojarzony stan asynchronicznego od określonego obiektu.  
  
```
future& operator=(future&& Right) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Right`  
 A `future` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `*this`  
  
### <a name="remarks"></a>Uwagi  
 Po przesłaniu `Right` nie ma już skojarzony stan asynchronicznego.  
  
##  <a name="share"></a>Future::share  
 Konwertuje obiekt na [shared_future —](../standard-library/shared-future-class.md) obiektu.  
  
```
shared_future<Ty> share();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `shared_future(move(*this))`  
  
##  <a name="valid"></a>Future::valid  
 Określa, czy obiekt jest skojarzony stan asynchronicznego.  
  
```
bool valid() noexcept;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli obiekt ma skojarzony stan asynchronicznego; w przeciwnym razie `false`.  
  
##  <a name="wait"></a>Future::wait  
 Blokuje bieżącego wątku, dopóki nie zostanie skojarzony stan asynchronicznego *gotowe*.  
  
```cpp  
void wait() const;
```  
  
### <a name="remarks"></a>Uwagi  
 Jest skojarzony stan asynchronicznego *gotowe* tylko wtedy, gdy jego dostawcą asynchroniczne przechowywanego wartości zwracanej albo przechowywane Wystąpił wyjątek.  
  
##  <a name="wait_for"></a>Future::wait_for  
 Blokuje bieżącego wątku, dopóki nie zostanie skojarzony stan asynchronicznego *gotowe* lub dopóki nie upłynie określony interwał.  
  
```
template <class Rep, class Period>
future_status wait_for(const chrono::duration<Rep, Period>& Rel_time) const;
```  
  
### <a name="parameters"></a>Parametry  
 `Rel_time`  
 A [chrono::duration](../standard-library/duration-class.md) obiekt, który określa maksymalny czas który bloki wątku.  
  
### <a name="return-value"></a>Wartość zwracana  
 A [future_status —](../standard-library/future-enums.md#future_status) wskazujące przyczynę przekazujących.  
  
### <a name="remarks"></a>Uwagi  
 Skojarzony stan asynchroniczne jest gotowy, tylko wtedy, gdy jego dostawcą asynchroniczne przechowywanego wartości zwracanej albo przechowywane Wystąpił wyjątek.  
  
##  <a name="wait_until"></a>Future::wait_until  
 Blokuje bieżącego wątku, dopóki nie zostanie skojarzony stan asynchronicznego *gotowe* lub po określonym momencie.  
  
```cpp  
template <class Clock, class Duration>
future_status wait_until(const chrono::time_point<Clock, Duration>& Abs_time) const;
```  
  
### <a name="parameters"></a>Parametry  
 `Abs_time`  
 A [chrono::time_point](../standard-library/time-point-class.md) obiektu, który określa czas, po którym można odblokować wątku.  
  
### <a name="return-value"></a>Wartość zwracana  
 A [future_status —](../standard-library/future-enums.md#future_status) wskazujące przyczynę przekazujących.  
  
### <a name="remarks"></a>Uwagi  
 Jest skojarzony stan asynchronicznego *gotowe* tylko wtedy, gdy jego dostawcą asynchroniczne przechowywanego wartości zwracanej albo przechowywane Wystąpił wyjątek.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)   
 [\<przyszłe >](../standard-library/future.md)



