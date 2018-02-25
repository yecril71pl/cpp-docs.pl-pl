---
title: "static_partitioner — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- static_partitioner
- PPL/concurrency::static_partitioner
- PPL/concurrency::static_partitioner::static_partitioner
dev_langs:
- C++
helpviewer_keywords:
- static_partitioner class
ms.assetid: 2b3dbdf0-6eb9-49f6-8639-03df1d974143
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 20dad961b694042c721f388c9a40e0bf99b9b77d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="staticpartitioner-class"></a>static_partitioner — Klasa
`static_partitioner` Klasa reprezentuje partycjonowania statycznego zakresu iterowane przez `parallel_for`. Obiekt partitioner dzieli zakres na tyle fragmenty są dostępne dla harmonogramu underyling pracowników.  
  
## <a name="syntax"></a>Składnia  
  
```
class static_partitioner;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[static_partitioner](#ctor)|Konstruuje `static_partitioner` obiektu.|  
|[~ static_partitioner — destruktor](#dtor)|Niszczy `static_partitioner` obiektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `static_partitioner`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** ppl.h  
  
 **Namespace:** współbieżności  
  
##  <a name="dtor"></a> ~ static_partitioner — 

 Niszczy `static_partitioner` obiektu.  
  
```
~static_partitioner();
```  
  
##  <a name="ctor"></a> static_partitioner — 

 Konstruuje `static_partitioner` obiektu.  
  
```
static_partitioner();
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności](concurrency-namespace.md)
