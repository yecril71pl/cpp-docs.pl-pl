---
title: "task_completion_event — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- task_completion_event
- PPLTASKS/concurrency::task_completion_event
- PPLTASKS/concurrency::task_completion_event::task_completion_event
- PPLTASKS/concurrency::task_completion_event::set
- PPLTASKS/concurrency::task_completion_event::set_exception
dev_langs: C++
helpviewer_keywords: task_completion_event class
ms.assetid: fb19ed98-f245-48dc-9ba5-487ba879b28a
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 78c5cb9bdd1da0876abacda48000a914c884d25a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="taskcompletionevent-class"></a>task_completion_event — Klasa
`task_completion_event` Klasa umożliwia opóźnienie wykonania zadania, dopóki spełniony jest warunek lub uruchomić zadanie w odpowiedzi na zdarzenie zewnętrzne.  
  
## <a name="syntax"></a>Składnia  
  
```
template<typename _ResultType>
class task_completion_event;

template<>
class task_completion_event<void>;
```  
  
#### <a name="parameters"></a>Parametry  
 `_ResultType`  
 Typ wyniku `task_completion_event` klasy.  
  
 `T`  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[task_completion_event —](#ctor)|Konstruuje `task_completion_event` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[zestaw](#set)|Przeciążone. Ustawia zdarzenie ukończenia zadania.|  
|[set_exception](#set_exception)|Przeciążone. Propaguje wyjątek, aby wszystkie zadania skojarzone z tym zdarzeniem.|  
  
## <a name="remarks"></a>Uwagi  
 Należy użyć zadania utworzone na podstawie zdarzenie ukończenia zadania podczas danego scenariusza należy utworzyć zadanie, które zostanie ukończona, a tym samym jego kontynuacje zaplanowane do wykonania w pewnym momencie w przyszłości. `task_completion_event` Musi mieć taki sam typ jak zadań możesz utworzyć i wywołanie metody set zdarzenie ukończenia zadania o wartości tego typu będą spowodować zakończenie zadania skojarzone i podaj tę wartość, w związku z tym do jego kontynuacje.  
  
 Jeśli nigdy nie zostanie zasygnalizowane zdarzenie ukończenia zadania, gdy jest on niszczone zostaną anulowane wszystkie zadania utworzone na podstawie jego.  
  
 `task_completion_event`zachowuje się jak wskaźnika inteligentnego i powinien zostać przekazany przez wartość.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `task_completion_event`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** ppltasks.h  
  
 **Namespace:** współbieżności  
  
##  <a name="set"></a>zestaw 

 Ustawia zdarzenie ukończenia zadania.  
  
```
bool set(_ResultType _Result) const ;

bool set() const ;
```  
  
### <a name="parameters"></a>Parametry  
 `_Result`  
 Wynik można ustawić tego zdarzenia z.  
  
### <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `true` czy było pomyślne podczas ustawiania zdarzenia. Zwraca `false` Jeśli zdarzenie jest już ustawiony.  
  
### <a name="remarks"></a>Uwagi  
 Obecności wielu lub równoczesnych wywołań `set`, pierwsze wywołanie powiedzie się i jego wynik (jeśli istnieje), które będą przechowywane w zdarzenie ukończenia zadania. Pozostałe zestawy są ignorowane, a metoda zwróci wartość false. Jeśli zdarzenie ukończenia zadania, wszystkie zadania utworzone na podstawie zdarzeń natychmiast zostanie ukończona, czy jego kontynuacje, jeśli istnieje, zostanie zaplanowane. Zadanie ukończenia obiektów, które mają `_ResultType` innych niż `void` przekazuje wartość do ich kontynuacje.  
  
##  <a name="set_exception"></a>set_exception 

 Propaguje wyjątek, aby wszystkie zadania skojarzone z tym zdarzeniem.  
  
```
template<typename _E>
__declspec(noinline) bool set_exception(_E _Except) const;

__declspec(noinline) bool set_exception(std::exception_ptr _ExceptionPtr) const ;
```  
  
### <a name="parameters"></a>Parametry  
 `_E`  
 `_Except`  
 `_ExceptionPtr`  
  
### <a name="return-value"></a>Wartość zwracana  
  
##  <a name="ctor"></a>task_completion_event — 

 Konstruuje `task_completion_event` obiektu.  
  
```
task_completion_event();
```  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)
