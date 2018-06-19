---
title: affinity_partitioner — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- affinity_partitioner
- PPL/concurrency::affinity_partitioner
- PPL/concurrency::affinity_partitioner::affinity_partitioner
dev_langs:
- C++
helpviewer_keywords:
- affinity_partitioner class
ms.assetid: 31bf7bb1-bd01-491c-9760-d9d60edfccad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2242346bda717117e2b43ba108d86fd2a77a3b58
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691134"
---
# <a name="affinitypartitioner-class"></a>affinity_partitioner — Klasa
`affinity_partitioner` Klasy jest podobna do `static_partitioner` klasy, ale zwiększa koligacji pamięci podręcznej przez siebie mapowania podzakresów na wątków roboczych. Go znacznie zwiększyć wydajność podczas pętli jest ponowne wykonanie przez ten sam zestaw danych i danych mieści się w pamięci podręcznej. Należy pamiętać, że takie same `affinity_partitioner` obiektu musi być używany z kolejnych iteracji pętli równoległej wykonywanym dla określonego zestawu danych, do korzystania z danych lokalizacji.  
  
## <a name="syntax"></a>Składnia  
  
```
class affinity_partitioner;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[affinity_partitioner](#ctor)|Konstruuje `affinity_partitioner` obiektu.|  
|[~ affinity_partitioner — destruktor](#dtor)|Niszczy `affinity_partitioner` obiektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `affinity_partitioner`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** ppl.h  
  
 **Namespace:** współbieżności  
  
##  <a name="dtor"></a> ~ affinity_partitioner — 

 Niszczy `affinity_partitioner` obiektu.  
  
```
~affinity_partitioner();
```  
  
##  <a name="ctor"></a> affinity_partitioner — 

 Konstruuje `affinity_partitioner` obiektu.  
  
```
affinity_partitioner();
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności](concurrency-namespace.md)
