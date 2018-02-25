---
title: "simple_partitioner — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- simple_partitioner
- PPL/concurrency::simple_partitioner
- PPL/concurrency::simple_partitioner::simple_partitioner
dev_langs:
- C++
helpviewer_keywords:
- simple_partitioner class
ms.assetid: d7e997af-54d1-43f5-abe0-def72df6edb3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2cc4b4b92e3ad6324b3f25862c81892fde8f2c1f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="simplepartitioner-class"></a>simple_partitioner — Klasa
`simple_partitioner` Klasa reprezentuje partycjonowania statycznego zakresu iterowane przez `parallel_for`. Obiekt partitioner dzieli zakres fragmentów tak, aby każdy fragment jest co najmniej liczby iteracji określony przez rozmiar fragmentu.  
  
## <a name="syntax"></a>Składnia  
  
```
class simple_partitioner;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[simple_partitioner](#ctor)|Konstruuje `simple_partitioner` obiektu.|  
|[~ simple_partitioner — destruktor](#dtor)|Niszczy `simple_partitioner` obiektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `simple_partitioner`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** ppl.h  
  
 **Namespace:** współbieżności  
  
##  <a name="dtor"></a> ~ simple_partitioner — 

 Niszczy `simple_partitioner` obiektu.  
  
```
~simple_partitioner();
```  
  
##  <a name="ctor"></a> simple_partitioner — 

 Konstruuje `simple_partitioner` obiektu.  
  
```
explicit simple_partitioner(_Size_type _Chunk_size);
```  
  
### <a name="parameters"></a>Parametry  
 `_Chunk_size`  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności](concurrency-namespace.md)
