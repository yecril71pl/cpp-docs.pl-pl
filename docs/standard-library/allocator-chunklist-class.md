---
title: allocator_chunklist Class | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- allocators/stdext::allocator_chunklist
- allocators/stdext::allocators::allocator_chunklist
dev_langs:
- C++
helpviewer_keywords:
- stdext::allocator_chunklist
- stdext::allocators [C++], allocator_chunklist
ms.assetid: ea72ed0a-dfdb-4c8b-8096-e4baf567b80f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 35cf60a038f193e05afb9afd1a0b8a724076ab0c
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="allocatorchunklist-class"></a>allocator_chunklist — Klasa
Opisuje obiekt, który zarządza Alokacja magazynu i zwalnianie obiektów przy użyciu pamięci podręcznej typu [cache_chunklist —](../standard-library/cache-chunklist-class.md).  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Type>  
class allocator_chunklist;
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Type`|Typ elementów przydzielonej przez program przydzielania.|  
  
## <a name="remarks"></a>Uwagi  
 [Allocator_decl —](../standard-library/allocators-functions.md#allocator_decl) makro przekazuje tę klasę jako `name` parametru w następujących instrukcji: `ALLOCATOR_DECL(CACHE_CHUNKLIST, SYNC_DEFAULT, allocator_chunklist);`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<allocators — >  
  
 **Namespace:** stdext —  
  
## <a name="see-also"></a>Zobacz też  
 [\<allocators>](../standard-library/allocators-header.md)



