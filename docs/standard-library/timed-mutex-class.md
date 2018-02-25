---
title: "timed_mutex — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- mutex/std::timed_mutex
- mutex/std::timed_mutex::timed_mutex
- mutex/std::timed_mutex::lock
- mutex/std::timed_mutex::try_lock
- mutex/std::timed_mutex::try_lock_for
- mutex/std::timed_mutex::try_lock_until
- mutex/std::timed_mutex::unlock
dev_langs:
- C++
ms.assetid: cd198081-6f38-447a-9dba-e06dfbfafe59
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
helpviewer_keywords:
- std::timed_mutex [C++]
- std::timed_mutex [C++], timed_mutex
- std::timed_mutex [C++], lock
- std::timed_mutex [C++], try_lock
- std::timed_mutex [C++], try_lock_for
- std::timed_mutex [C++], try_lock_until
- std::timed_mutex [C++], unlock
ms.workload:
- cplusplus
ms.openlocfilehash: ec0d34d83d19185730216af6ca9280fa14246214
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="timedmutex-class"></a>timed_mutex — Klasa
Reprezentuje *upłynął typu obiektu mutex*. Obiekty tego typu są używane do wymuszania wzajemne wykluczenie przez ograniczony czas blokowania w programie.  
  
## <a name="syntax"></a>Składnia  
  
```
class timed_mutex;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[timed_mutex](#timed_mutex)|Konstruuje `timed_mutex` obiekt, który nie jest zablokowany.|  
|[timed_mutex:: ~ timed_mutex — destruktor](#dtortimed_mutex_destructor)|Zwalnia wszystkie zasoby, które są używane przez `timed_mutex` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[lock](#lock)|Wątek wywołujący blokuje, dopóki wątek uzyskuje prawo własności do `mutex`.|  
|[try_lock](#try_lock)|Próbuje uzyskać prawo własności `mutex` bez blokowania.|  
|[try_lock_for](#try_lock_for)|Próbuje uzyskać prawo własności `mutex` określony interwał czasu.|  
|[try_lock_until](#try_lock_until)|Próbuje uzyskać prawo własności `mutex` dopiero po określonym czasie.|  
|[unlock](#unlock)|Zwalnia własność `mutex`.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<obiektu mutex >  
  
 **Namespace:** Standard  
  
##  <a name="lock"></a>  timed_mutex::Lock
 Wątek wywołujący blokuje, dopóki wątek uzyskuje prawo własności do `mutex`.  
  
```cpp  
void lock();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wątek wywołujący już właścicielem `mutex`, zachowanie jest niezdefiniowany.  
  
##  <a name="timed_mutex"></a>  timed_mutex::timed_mutex — Konstruktor  
 Konstruuje `timed_mutex` obiekt, który nie jest zablokowany.  
  
```cpp  
timed_mutex();
```  
  
##  <a name="dtortimed_mutex_destructor">timed_mutex:: ~ timed_mutex — destruktor</a>  
 Zwalnia wszystkie zasoby, które są używane przez `mutex` obiektu.  
  
```cpp  
~timed_mutex();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli obiekt jest zablokowany, po uruchomieniu destruktor, zachowanie jest niezdefiniowany.  
  
##  <a name="try_lock"></a>  timed_mutex::try_lock
 Próbuje uzyskać prawo własności `mutex` bez blokowania.  
  
```cpp  
bool try_lock();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli metoda pomyślnie uzyskuje prawo własności `mutex`; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wątek wywołujący już właścicielem `mutex`, zachowanie jest niezdefiniowany.  
  
##  <a name="try_lock_for"></a>  timed_mutex::try_lock_for
 Próbuje uzyskać prawo własności `mutex` bez blokowania.  
  
```cpp  
template <class Rep, class Period>
bool try_lock_for(const chrono::duration<Rep, Period>& Rel_time);
```  
  
### <a name="parameters"></a>Parametry  
 `Rel_time`  
 A [chrono::duration](../standard-library/duration-class.md) obiekt, który określa maksymalną ilość czasu, który próbuje uzyskać prawo własności do metody `mutex`.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli metoda pomyślnie uzyskuje prawo własności `mutex`; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wątek wywołujący już właścicielem `mutex`, zachowanie jest niezdefiniowany.  
  
##  <a name="try_lock_until"></a>  timed_mutex::try_lock_until
 Próbuje uzyskać prawo własności `mutex` bez blokowania.  
  
```cpp  
template <class Clock, class Duration>
bool try_lock_for(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```  
  
### <a name="parameters"></a>Parametry  
 `Abs_time`  
 Punktu w czasie, który określa próg, po upływie którego metoda nie jest już próbuje uzyskać prawo własności do `mutex`.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli metoda pomyślnie uzyskuje prawo własności `mutex`; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wątek wywołujący już właścicielem `mutex`, zachowanie jest niezdefiniowany.  
  
##  <a name="unlock"></a>  timed_mutex::Unlock
 Zwalnia własność `mutex`.  
  
```cpp  
void unlock();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wątek wywołujący nie jest właścicielem `mutex`, zachowanie jest niezdefiniowany.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex>](../standard-library/mutex.md)



