---
title: auto_partitioner — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- auto_partitioner
- PPL/concurrency::auto_partitioner
- PPL/concurrency::auto_partitioner::auto_partitioner
dev_langs:
- C++
helpviewer_keywords:
- auto_partitioner class
ms.assetid: 7cc08e5d-20b4-47a4-b4b5-c214a78f5a9e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 05232aa954a9ded7d2ab3a26ae4e1524610c3d04
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="autopartitioner-class"></a>auto_partitioner — Klasa
`auto_partitioner` Klasa reprezentuje domyślną metodą `parallel_for`, `parallel_for_each` i `parallel_transform` służy do zakresu ich wykonuje iterację na partycji. Ta metoda partycjonowania employes kradzież równoważenia obciążenia w zakresie jak również na — iteracyjne anulowania.  
  
## <a name="syntax"></a>Składnia  
  
```
class auto_partitioner;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[auto_partitioner](#ctor)|Konstruuje `auto_partitioner` obiektu.|  
|[~ auto_partitioner — destruktor](#dtor)|Niszczy `auto_partitioner` obiektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `auto_partitioner`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** ppl.h  
  
 **Namespace:** współbieżności  
  
##  <a name="dtor"></a> ~ auto_partitioner — 

 Niszczy `auto_partitioner` obiektu.  
  
```
~auto_partitioner();
```  
  
##  <a name="ctor"></a> auto_partitioner — 

 Konstruuje `auto_partitioner` obiektu.  
  
```
auto_partitioner();
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności](concurrency-namespace.md)
