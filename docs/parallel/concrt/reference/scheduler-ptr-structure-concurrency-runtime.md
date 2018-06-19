---
title: Struktura scheduler_ptr | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::get
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::operator bool
dev_langs:
- C++
ms.assetid: e88c84af-c306-476d-aef1-f42a0fa0a80f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 672e4a0dd5f66ab613dde8877915c799d6c4b2f4
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686987"
---
# <a name="schedulerptr-structure"></a>Struktura scheduler_ptr
Reprezentuje wskaźnik do harmonogramu. Ta klasa istnieje umożliwia specyfikację udostępnionego okres istnienia przy użyciu shared_ptr lub zwykłe odwołanie przy użyciu wskaźnika raw.  
  
## <a name="syntax"></a>Składnia  
  
```
struct scheduler_ptr;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[scheduler_ptr::scheduler_ptr](#ctor)|Przeciążone. Tworzy wskaźnik harmonogramu z shared_ptr do harmonogramu|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[scheduler_ptr::get](#get)|Zwraca nieprzetworzoną wskaźnika do harmonogramu|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Operator bool scheduler_ptr::operator](#operator_bool)|Sprawdź, czy wskaźnik harmonogramu jest różna od null|  
|[scheduler_ptr::operator-&gt;](#operator_ptr)|Przypominają wskaźnik|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `scheduler_ptr`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** pplinterface.h  
  
 **Namespace:** współbieżności  
  
##  <a name="get"></a>  scheduler_ptr::Get — metoda  
 Zwraca nieprzetworzoną wskaźnika do harmonogramu  
  
```
scheduler_interface* get() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
##  <a name="operator_bool"></a>  Operator bool scheduler_ptr::operator   
 Sprawdź, czy wskaźnik harmonogramu jest różna od null  
  
"" const; bool() — operator
```  
  
##  <a name="operator_ptr"></a>  scheduler_ptr::operator-&gt;   
 Behave like a pointer  
  
```
scheduler_interface — * — operator -> () const;
```  
  
### Return Value  
  
##  <a name="ctor"></a>  scheduler_ptr::scheduler_ptr Constructor  
 Creates a scheduler pointer from shared_ptr to scheduler  
  
```
jawne scheduler_ptr (std::shared_ptr < scheduler_interface — > Harmonogram);

jawne scheduler_ptr (_In_opt_ pScheduler scheduler_interface — *);
```  
  
### Parameters  
 `scheduler`  
 `pScheduler`  
  
## See Also  
 [concurrency Namespace](concurrency-namespace.md)
