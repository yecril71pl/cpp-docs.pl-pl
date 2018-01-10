---
title: _ReadBarrier | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _ReadBarrier
dev_langs: C++
helpviewer_keywords: _ReadBarrier intrinsic
ms.assetid: f9e54a92-61bc-4f55-8195-b8932065a796
caps.latest.revision: "25"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c0ce47629dc26371a896085bf3094f186fd80ee1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="readbarrier"></a>_ReadBarrier  
  
**Dotyczące firmy Microsoft**  
  
 Ogranicza optymalizacje kompilatora, które można zmienić kolejność operacji uzyskiwania dostępu do pamięci dla punktu połączenia.  
  
> [!CAUTION]
>  `_ReadBarrier`, `_WriteBarrier`, I `_ReadWriteBarrier` funkcje wewnętrzne kompilatora i `MemoryBarrier` makra są wszystkie przestarzałe i nie powinna być używana. Do komunikacji między wątku używa mechanizmów takich jak [atomic_thread_fence —](../standard-library/atomic-functions.md#atomic_thread_fence) i [std::atomic\<T >](../standard-library/atomic.md) które są zdefiniowane w [standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md). Dostęp do sprzętu, można użyć [/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) — opcja kompilatora razem z [volatile](../cpp/volatile-cpp.md) — słowo kluczowe.  
  
## <a name="syntax"></a>Składnia  
  
```  
void _ReadBarrier(void);  
```  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`_ReadBarrier`|x86,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 `_ReadBarrier` Wewnętrzne ogranicza optymalizacje kompilatora, które można usunąć lub zmienić kolejność operacji uzyskiwania dostępu do pamięci dla punktu połączenia.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)