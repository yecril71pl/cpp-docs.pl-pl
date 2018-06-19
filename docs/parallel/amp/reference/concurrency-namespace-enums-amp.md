---
title: Typy wyliczeniowe przestrzeń nazw współbieżności (AMP) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- amp/Concurrency::access_type
- amp/Concurrency::queuing_mode
dev_langs:
- C++
ms.assetid: 4c87457e-184f-4992-81ab-ca75e7d524ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a67b5e77b8ab8c52e55dea96e64a3f16a4d70e39
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33695671"
---
# <a name="concurrency-namespace-enums-amp"></a>Typy wyliczeniowe przestrzeń nazw współbieżności (AMP)
|||  
|-|-|  
|[access_type — wyliczenie](#access_type)|[queuing_mode — wyliczenie](#queuing_mode)|  
  
##  <a name="access_type"></a>  access_type — wyliczenie  
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

  
##  <a name="queuing_mode"></a>  queuing_mode — wyliczenie  
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
