---
title: "allocator_unbounded — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::allocator_unbounded
- allocators/stdext::allocators::allocator_unbounded
dev_langs: C++
helpviewer_keywords: allocator_unbounded class
ms.assetid: facbaea1-b320-4d99-96da-039b2642f352
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ffd474655599caf3663f33533f0651b1451531a3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="allocatorunbounded-class"></a>allocator_unbounded — Klasa
Opisuje obiekt, który zarządza Alokacja magazynu i zwalnianie obiektów typu `Type` przy użyciu pamięci podręcznej typu [cache_freelist —](../standard-library/cache-freelist-class.md) o długości zarządza [max_unbounded —](../standard-library/max-unbounded-class.md).  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Type>  
class allocator_unbounded;
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Type`|Typ elementów przydzielonej przez program przydzielania.|  
  
## <a name="remarks"></a>Uwagi  
 [Allocator_decl —](../standard-library/allocators-functions.md#allocator_decl) makro przekazuje tę klasę jako `name` parametru w następujących instrukcji:`ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_unbounded), SYNC_DEFAULT, allocator_unbounded);`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<allocators — >  
  
 **Namespace:** stdext —  
  
## <a name="see-also"></a>Zobacz też  
 [\<allocators — >](../standard-library/allocators-header.md)



