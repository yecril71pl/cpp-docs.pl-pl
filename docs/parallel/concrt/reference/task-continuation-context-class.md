---
title: task_continuation_context — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- task_continuation_context
- PPLTASKS/concurrency::task_continuation_context
- PPLTASKS/concurrency::task_continuation_context::get_current_winrt_context
- PPLTASKS/concurrency::task_continuation_context::use_arbitrary
- PPLTASKS/concurrency::task_continuation_context::use_current
- PPLTASKS/concurrency::task_continuation_context::use_default
- PPLTASKS/concurrency::task_continuation_context::use_synchronous_execution
dev_langs:
- C++
helpviewer_keywords:
- task_continuation_context class
ms.assetid: 1fb5a76a-3682-45c2-a615-8b6b527741f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 37b218a6db251123513ca155fd491fee7ebabd13
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689184"
---
# <a name="taskcontinuationcontext-class"></a>task_continuation_context — Klasa
`task_continuation_context` Klasa służy do określenia, gdzie chcesz kontynuacji do wykonania. Jest tylko warto użyć tej klasy z aplikacji środowiska wykonawczego systemu Windows. W przypadku aplikacji z systemem innym niż Windows Runtime kontekstu wykonywania kontynuacji zadań jest określone przez środowisko uruchomieniowe i nie można skonfigurować.  
  
## <a name="syntax"></a>Składnia  
  
```
class task_continuation_context : public details::_ContextCallback;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[get_current_winrt_context](#get_current_winrt_context)|Zwraca obiekt kontekstu kontynuacji zadań, która reprezentuje bieżący kontekst wątku winrt.|  
|[use_arbitrary](#use_arbitrary)|Tworzy kontekst kontynuacji zadania, co pozwala wybrać kontekstu wykonywania dla utrzymania środowiska uruchomieniowego.|  
|[use_current](#use_current)|Zwraca obiekt zadania kontynuacji kontekstu reprezentujący bieżącego kontekstu wykonywania.|  
|[use_default](#use_default)|Tworzy domyślny kontekst kontynuacji zadań.|  
|[use_synchronous_execution](#use_synchronous_execution)|Zwraca obiekt kontekstu kontynuacji zadań, który reprezentuje Kontekst wykonywania synchronicznego.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `_ContextCallback`  
  
 `task_continuation_context`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** ppltasks.h  
  
 **Namespace:** współbieżności  

## <a name="get_current_winrt_context"></a> get_current_winrt_context
 Zwraca obiekt kontekstu kontynuacji zadań, która reprezentuje bieżący kontekst wątku WinRT.  
  
## <a name="syntax"></a>Składnia  
  
```  
static task_continuation_context get_current_winrt_context();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Bieżący kontekst wątku środowiska wykonawczego systemu Windows. Zwraca pusty task_continuation_context — Jeśli wywołany z kontekstu obsługi z systemem innym niż Windows.  
  
## <a name="remarks"></a>Uwagi  
 `get_current_winrt_context` Metody przechwytuje kontekst wątku wywołującego środowiska wykonawczego systemu Windows. Zwraca kontekst pustych wywołań obsługi z systemem innym niż Windows.  
  
 Wartość zwrócona przez `get_current_winrt_context` może służyć do wskazywania środowiska uruchomieniowego czy kontynuacji powinien zostać wykonany w modelu typu apartment przechwyconych kontekstu (STA vs MTA), niezależnie od tego, czy zadanie poprzedzających apartamentu pamiętać. Apartamentu pamiętać zadanie jest zadaniem dekoduje środowiska wykonawczego systemu Windows `IAsyncInfo` interfejsu lub zadanie, które są podrzędne w stosunku do takich zadań.  
  
 Ta metoda jest podobna do `use_current` metody, ale jest również dostępny do natywnego kodu C++ bez C + +/ CX rozszerzenia obsługi. Ma ona używana przez zaawansowanych użytkownikom zapisywanie C + +/ CX niezwiązane z żadnym biblioteki kodu macierzystego i wywoływania środowiska wykonawczego systemu Windows. Jeśli nie chcesz dodać tę funkcję, firma Microsoft zaleca `use_current` metodę, która jest dostępna tylko dla C + +/ CX klientów.  
  
  
##  <a name="use_arbitrary"></a> use_arbitrary 

 Tworzy kontekst kontynuacji zadania, co pozwala wybrać kontekstu wykonywania dla utrzymania środowiska uruchomieniowego.  
  
```
static task_continuation_context use_arbitrary();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Kontekst kontynuacji zadania reprezentujący dowolnego lokalizacji.  
  
### <a name="remarks"></a>Uwagi  
 Gdy używany jest ten kontekst kontynuacji kontynuacji będzie wykonywany w kontekście, który wybiera środowiska uruchomieniowego, nawet w przypadku poprzedzających zadań apartamentu pamiętać.  
  
 `use_arbitrary` można wyłączyć domyślne zachowanie dla kontynuacji apartamentu pamiętać zadania utworzone w pozostaje tryb komórek jednowątkowych  
  
 Ta metoda jest dostępna tylko do aplikacji środowiska wykonawczego systemu Windows.  
  
##  <a name="use_current"></a> use_current 

 Zwraca obiekt zadania kontynuacji kontekstu reprezentujący bieżącego kontekstu wykonywania.  
  
```
static task_continuation_context use_current();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżącego kontekstu wykonywania.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda przechwytuje wywołującego kontekstu środowiska uruchomieniowego systemu Windows tak, aby kontynuacje mogą być wykonywane w prawo apartamentu.  
  
 Wartość zwrócona przez `use_current` może służyć do wskazywania środowiska uruchomieniowego kontynuacji mają być wykonywane w kontekście przechwyconych (STA vs MTA) niezależnie od tego, czy zadanie poprzedzających apartamentu pamiętać. Apartamentu pamiętać zadanie jest zadaniem dekoduje środowiska wykonawczego systemu Windows `IAsyncInfo` interfejsu lub zadanie, które są podrzędne w stosunku do takich zadań.  
  
 Ta metoda jest dostępna tylko do aplikacji środowiska wykonawczego systemu Windows.  
  
##  <a name="use_default"></a> use_default 

 Tworzy domyślny kontekst kontynuacji zadań.  
  
```
static task_continuation_context use_default();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Domyślny kontekst kontynuacji.  
  
### <a name="remarks"></a>Uwagi  
 Domyślny kontekst jest używany, w przeciwnym razie Określ kontekstu kontynuacji podczas wywoływania `then` metody. W aplikacji systemu Windows dla systemu Windows 7 i poniżej, a także aplikacjach pulpitu w systemie Windows 8 lub nowszym środowisko uruchomieniowe Określa, gdzie kontynuacje zadania będą wykonywane. Jednak w aplikacji środowiska wykonawczego systemu Windows, domyślny kontekst kontynuacji dla kontynuacji dla zadania pamiętać apartamentu jest apartamencie gdzie `then` jest wywoływana.  
  
 Apartamentu pamiętać zadanie jest zadaniem dekoduje środowiska wykonawczego systemu Windows `IAsyncInfo` interfejsu lub zadanie, które są podrzędne w stosunku do takich zadań. W związku z tym jeśli zaplanowane kontynuacji dla zadania pamiętać typu apartment w STA środowiska wykonawczego systemu Windows, kontynuacji będzie wykonywany w tym pozostaje tryb komórek jednowątkowych  
  
 Kontynuacja z systemem innym niż apartamentu pamiętać zadania będą wykonywane w kontekście, który wybiera środowiska uruchomieniowego.  

## <a name="use_synchronous_execution"></a> task_continuation_context::use_synchronous_execution  
Zwraca obiekt kontekstu kontynuacji zadań, który reprezentuje Kontekst wykonywania synchronicznego.  
  
## <a name="syntax"></a>Składnia  
  
```  
static task_continuation_context use_synchronous_execution();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Kontekst wykonywania synchronicznego.  
  
## <a name="remarks"></a>Uwagi  
 `use_synchronous_execution` Metody wymusza zadania kontynuacji, aby były uruchamiane synchronicznie w kontekście, co powoduje jego poprzedzających zadanie zostało zakończone.  
  
 Poprzedzających zadań została już zakończona, gdy kontynuacji jest dołączony, kontynuacji uruchamiane synchronicznie w kontekście łączący kontynuacji.  
  
 
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności](concurrency-namespace.md)
