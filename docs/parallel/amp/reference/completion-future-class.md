---
title: "completion_future — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- completion_future
- AMPRT/completion_future
- AMPRT/Concurrency::completion_future::completion_future
- AMPRT/Concurrency::completion_future::get
- AMPRT/Concurrency::completion_future::then
- AMPRT/Concurrency::completion_future::to_task
- AMPRT/Concurrency::completion_future::valid
- AMPRT/Concurrency::completion_future::wait
- AMPRT/Concurrency::completion_future::wait_for
- AMPRT/Concurrency::completion_future::wait_until
dev_langs: C++
ms.assetid: 1303c62e-546d-4b02-a578-251ed3fc0b6b
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 40f4c4821a6141e7795f37f5a276a544677ba48b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="completionfuture-class"></a>completion_future — Klasa
Reprezentuje przyszłych odpowiadający C++ AMP operację asynchroniczną.  
  
### <a name="syntax"></a>Składnia  
  
```  
class completion_future;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[completion_future — Konstruktor](#ctor)|Inicjuje nowe wystąpienie klasy `completion_future` klasy.|  
|[~ completion_future — destruktor](#dtor)|Niszczy `completion_future` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Pobierz](#get)|Czeka, aż do zakończenia skojarzonego operację asynchroniczną.|  
|[następnie](#then)|Powiązany obiekt funkcja wywołania zwrotnego do `completion_future` obiektu ma być wykonywana w przypadku skojarzone operację asynchroniczną kończy działanie.|  
|[to_task](#to_task)|Zwraca `task` obiektu odpowiadającego skojarzone operację asynchroniczną.|  
|[Nieprawidłowa](#valid)|Pobiera wartość logiczną wskazującą, czy obiekt jest skojarzony z operacji asynchronicznej.|  
|[oczekiwania](#wait)|Bloki przed zakończeniem skojarzone operacji asynchronicznej.|  
|[wait_for](#wait_for)|Bloki przed zakończeniem operacji asynchronicznych skojarzone lub w czasie określonym przez `_Rel_time` upłynął.|  
|[wait_until](#wait_until)|Blokuje przed zakończeniem operacji asynchronicznych skojarzone lub dopóki bieżąca godzina przekracza wartość określoną przez `_Abs_time`.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Operator std::shared_future\<void >](#operator_shared_future)|Konwertuje niejawnie `completion_future` do obiektu `std::shared_future` obiektu.|  
|[operator =](#operator_eq)|Kopiuje zawartość określonego `completion_future` obiektu do tego.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `completion_future`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** amprt.h  
  
 **Namespace:** współbieżności  


## <a name="ctor"></a>completion_future 

Inicjuje nowe wystąpienie klasy `completion_future` klasy.  
  
### <a name="syntax"></a>Składnia  
  
```  
completion_future();  
  
completion_future(  
    const completion_future& _Other );  
  
completion_future(  
    completion_future&& _Other );  
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `completion_future` Obiekt, aby skopiować lub przenieść.  
  
### <a name="overloads-list"></a>Lista przeciążeń  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`completion_future();`|Inicjuje nowe wystąpienie klasy `completion_future` — klasa|  
|`completion_future(const completion_future& _Other);`|Inicjuje nowe wystąpienie klasy `completion_future` przez skopiowanie konstruktora.|  
|`completion_future(completion_future&& _Other);`|Inicjuje nowe wystąpienie klasy `completion_future` klasy przez przenoszenie konstruktora.|  
  
## <a name="get"></a>Pobierz 

Czeka, aż do zakończenia skojarzonego operację asynchroniczną. Zgłasza wyjątek przechowywanych jedną napotkano podczas operacji asynchronicznej.  
  
### <a name="syntax"></a>Składnia  
  
```  
void get() const;  
```  
  
## <a name="operator_shared_future"></a>std::shared_future — operator<void> 

Konwertuje niejawnie `completion_future` do obiektu `std::shared_future` obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```  
operator std::shared_future<void>() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `std::shared_future` Obiektu.  
  
## <a name="operator_eq"></a>operator = 

Kopiuje zawartość określonego `completion_future` obiektu do tego.  
  
### <a name="syntax"></a>Składnia  
  
```  
completion_future&  operator= (const completion_future& _Other );    
completion_future&  operator= (completion_future&& _Other );  
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 Obiekt do skopiowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do tego `completion_future` obiektu.  
  
## <a name="overloads-list"></a>Lista przeciążeń  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`completion_future& operator=(const completion_future& _Other);`|Kopiuje zawartość określonego `completion_future` obiekt ten element, za pomocą bezpośrednich kopii.|  
|`completion_future& operator=(completion_future&& _Other);`|Kopiuje zawartość określonego `completion_future` obiekt ten element, przy użyciu przypisania przenoszenia.|  
  
## <a name="then"></a>następnie 

Powiązany obiekt funkcja wywołania zwrotnego do `completion_future` obiektu ma być wykonywana w przypadku skojarzone operację asynchroniczną kończy działanie.  
  
### <a name="syntax"></a>Składnia  
  
```  
template <typename _Functor>  
void then(const _Functor & _Func ) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `_Functor`  
 Obiekt wywołania zwrotnego.  
  
 `_Func`  
 Obiekt funkcji wywołania zwrotnego.  
  
## <a name="to_task"></a>to_task 

Zwraca `task` obiektu odpowiadającego skojarzone operację asynchroniczną.  
  
### <a name="syntax"></a>Składnia  
  
```  
concurrency::task<void> to_task() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `task` obiektu odpowiadającego skojarzone operację asynchroniczną.  
  
## <a name="valid"></a>Nieprawidłowa 

Pobiera wartość logiczną wskazującą, czy obiekt jest skojarzony z operacji asynchronicznej.  
  
### <a name="syntax"></a>Składnia  
  
```  
bool valid() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli obiekt jest skojarzony z operacji asynchronicznej; w przeciwnym razie `false`.  
  
## <a name="wait"></a>oczekiwania 

Bloki przed zakończeniem skojarzone operacji asynchronicznej.  
  
### <a name="syntax"></a>Składnia  
  
```  
void wait() const;  
```  
  
## <a name="wait_for"></a>wait_for 

Bloki przed zakończeniem operacji asynchronicznych skojarzone lub czasu określonym przez `_Rel_time` upłynął.  
  
### <a name="syntax"></a>Składnia  
  
```  
template <  
    class _Rep,  
    class _Period  
>  
std::future_status::future_status wait_for(  
    const std::chrono::duration< _Rep, _Period>& _Rel_time ) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `_Rep`  
 Typ arytmetyczny, który reprezentuje liczbę znaczników.  
  
 `_Period`  
 Std::ratio, reprezentującą liczbę sekund, które upłynąć na osi.  
  
 `_Rel_time`  
 Maksymalna ilość czasu oczekiwania na ukończenie tej operacji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca:  
  
-   `std::future_status::deferred`Jeśli skojarzona operacja asynchroniczna nie jest uruchomiona.  
  
-   `std::future_status::ready`Jeśli skojarzona operacja asynchroniczna została zakończona.  
  
-   `std::future_status::timeout`Jeśli określony czas upłynął.  
  
## <a name="wait_until"></a>wait_until 

Blokuje przed zakończeniem operacji asynchronicznych skojarzone lub dopóki bieżąca godzina przekracza wartość określoną przez `_Abs_time`.  
  
### <a name="syntax"></a>Składnia  
  
```  
template <  
    class _Clock,  
    class _Duration  
>  
std::future_status::future_status wait_until(  
    const std::chrono::time_point< _Clock, _Duration>& _Abs_time ) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `_Clock`  
 Zegara, na którym jest mierzony tego punktu w czasie.  
  
 `_Duration`  
 Przedział czasu od chwili uruchomienia `_Clock`firmy epoki, po którym funkcja będzie upłynął limit czasu.  
  
 `_Abs_time`  
 Punkt w czasie, po którym funkcja przekroczy limit czasu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca:  
  
1.  `std::future_status::deferred`Jeśli skojarzona operacja asynchroniczna nie jest uruchomiona.  
  
2.  `std::future_status::ready`Jeśli skojarzona operacja asynchroniczna została zakończona.  
  
3.  `std::future_status::timeout`Jeśli określony okres czasu upłynął.  
  
## <a name="dtor"></a>~ completion_future 

Niszczy `completion_future` obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```  
~completion_future();  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Namespace współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
