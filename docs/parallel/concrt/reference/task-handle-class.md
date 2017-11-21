---
title: "task_handle — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- task_handle
- PPL/concurrency::task_handle
- PPL/concurrency::task_handle::task_handle
dev_langs: C++
helpviewer_keywords: task_handle class
ms.assetid: 74a34b15-708b-4231-a509-947874292b13
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 358d217a131ec3e282775604619f1ff265baf490
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="taskhandle-class"></a>task_handle — Klasa
`task_handle` Klasa reprezentuje element indywidualnej pracy równoległych. Hermetyzuje zgodnie z instrukcjami i dane wymagane do wykonywania pracy.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<
    typename _Function  
>  
class task_handle : public ::Concurrency::details::_UnrealizedChore;  
```  
  
#### <a name="parameters"></a>Parametry  
 `_Function`  
 Typ obiektu funkcja, która będzie wywołana na wykonanie pracy reprezentowany przez `task_handle` obiektu.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[task_handle —](#ctor)|Tworzy nową `task_handle` obiektu. Pracy zadanie jest wykonywane przez wywoływanie funkcji określonej jako parametr do konstruktora.|  
|[~ task_handle — destruktor](#dtor)|Niszczy `task_handle` obiektu.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Operator()](#task_handle__operator_call)|Operator wywołania funkcji środowiska uruchomieniowego wywołuje do wykonywania pracy dojścia zadań.|  
  
## <a name="remarks"></a>Uwagi  
 `task_handle`obiekty mogą być używane w połączeniu z `structured_task_group` lub więcej ogólny `task_group` obiektu próba dekompozycji pracy do zadań równoległych. Aby uzyskać więcej informacji, zobacz [równoległość zadań](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
 Należy pamiętać, że twórca `task_handle` obiektu jest odpowiedzialny za konserwację okres istnienia utworzony `task_handle` obiektu, dopóki nie jest wymagany przez współbieżności środowiska wykonawczego. Zazwyczaj oznacza to, że `task_handle` obiekt nie należy destruct aż do otrzymania `wait` lub `run_and_wait` metody `task_group` lub `structured_task_group` , do którego jest Zakolejkowane została wywołana.  
  
 `task_handle`obiekty są zazwyczaj używane w połączeniu z wyrażenia lambda w języku C++. Ponieważ nie znasz true typu lambda, [make_task —](concurrency-namespace-functions.md#make_task) funkcji jest zwykle używane do tworzenia `task_handle` obiektu.  
  
 Środowisko uruchomieniowe tworzy kopię funkcja pracy, który jest przekazywany do `task_handle` obiektu. W związku z tym wszelkie zmiany stanu, które występują w funkcji obiekt przekazywany do `task_handle` obiektu nie będą widoczne w kopii tego obiektu funkcji.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `task_handle`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** ppl.h  
  
 **Namespace:** współbieżności  
  
##  <a name="task_handle__operator_call"></a>Operator() 

 Operator wywołania funkcji środowiska uruchomieniowego wywołuje do wykonywania pracy dojścia zadań.  
  
```  
void operator()() const;

 
```  
  
##  <a name="task_handle__ctor"></a>task_handle — 

 Tworzy nową `task_handle` obiektu. Pracy zadanie jest wykonywane przez wywoływanie funkcji określonej jako parametr do konstruktora.  
  
```  
task_handle(const _Function& _Func);
```  
  
### <a name="parameters"></a>Parametry  
 `_Func`  
 Funkcji, które będą wywoływane w celu wykonywania pracy reprezentowany przez `task_handle` obiektu. Może to być obiekt lambda, wskaźnika do funkcji, lub dowolnego obiektu, która obsługuje wersję operator wywołania funkcji z podpisem `void operator()()`.  
  
### <a name="remarks"></a>Uwagi  
 Środowisko uruchomieniowe tworzy kopię funkcja pracy, który jest przekazywany do konstruktora. W związku z tym wszelkie zmiany stanu, które występują w funkcji obiekt przekazywany do `task_handle` obiektu nie będą widoczne w kopii tego obiektu funkcji.  
  
##  <a name="dtor"></a>~ task_handle — 

 Niszczy `task_handle` obiektu.  
  
```  
~task_handle();
```  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [task_group — klasa](task-group-class.md)   
 [structured_task_group — klasa](structured-task-group-class.md)
