---
title: "Typy wyliczeniowe przestrzeń nazw współbieżności (AMP) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp/Concurrency::access_type
- amp/Concurrency::queuing_mode
dev_langs: C++
ms.assetid: 4c87457e-184f-4992-81ab-ca75e7d524ab
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8979ab026d5bf6aef9d0dd8677bf2ec47a8c6142
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="concurrency-namespace-enums-amp"></a>Typy wyliczeniowe przestrzeń nazw współbieżności (AMP)
|||  
|-|-|  
|[access_type — wyliczenie](#access_type)|[queuing_mode — wyliczenie](#queuing_mode)|  
  
##  <a name="access_type"></a>access_type — wyliczenie  
 Typ wyliczeniowy używany do określenia różnych typów dostępu do danych.  
  
```  
enum access_type;  
```  
### <a name="values"></a>Wartości  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`access_type_auto`|Automatycznie Wybierz najlepsze `access_type` dla akceleratora.|  
|`access_type_none`|W wersji dedykowanej. Alokacja jest dostępny tylko na akceleratora, a nie na Procesor.|  
|`access_type_read`|Udostępnione. Alokacja jest dostępny z akceleratora i jest możliwy do odczytu na Procesor.|  
|`access_type_read_write`|Udostępnione. Alokacja jest dostępny z akceleratora i jest dostępny do zapisu na Procesorze.|  
|`access_type_write`|Udostępnione. Alokacja jest dostępny z akceleratora i elementy readable i writable procesora.|  

  
##  <a name="queuing_mode"></a>queuing_mode — wyliczenie  
 Określa kolejkowania tryby, które są obsługiwane na akceleratora.  
  
```  
enum queuing_mode;  
``` 
### <a name="values"></a>Wartości  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`queuing_mode_immediate`|Kolejkowanie tryb, który określa, że jakaś polecenia, na przykład [parallel_for_each — funkcja (C++ AMP)](concurrency-namespace-functions-amp.md#parallel_for_each), są wysyłane do odpowiedniego urządzenia akceleratora, jak tylko zostaną zwrócone do obiektu wywołującego.|  
|`queuing_mode_automatic`|Kolejkowanie tryb, który określa, czy polecenia być umieszczone w kolejce w kolejce polecenia, który odpowiada [accelerator_view](accelerator-view-class.md) obiektu. Polecenia są wysyłane do urządzenia podczas [accelerator_view::flush](accelerator-view-class.md#flush) jest wywoływana.|   
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
