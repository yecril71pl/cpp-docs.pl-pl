---
title: _WriteBarrier | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- _WriteBarrier
dev_langs:
- C++
helpviewer_keywords:
- WriteBarrier intrinsic
- _WriteBarrier intrinsic
ms.assetid: a5ffdad9-0ca1-4eb7-b2f3-0f092c4bf4b5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fda8963e89086a2b1655b7dbe3d3b95aca24a7df
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="writebarrier"></a>_WriteBarrier
**Microsoft Specific**  
  
 Ogranicza optymalizacje kompilatora, które można zmienić kolejność operacji uzyskiwania dostępu do pamięci dla punktu połączenia.  
  
> [!CAUTION]
>  `_ReadBarrier`, `_WriteBarrier`, I `_ReadWriteBarrier` funkcje wewnętrzne kompilatora i `MemoryBarrier` makra są wszystkie przestarzałe i nie powinna być używana. Do komunikacji między wątku używa mechanizmów takich jak [atomic_thread_fence —](../standard-library/atomic-functions.md#atomic_thread_fence) i [std::atomic\<T >](../standard-library/atomic.md), które są zdefiniowane w [standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md). Dostęp do sprzętu, można użyć [/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) — opcja kompilatora razem z [volatile](../cpp/volatile-cpp.md) — słowo kluczowe.  
  
## <a name="syntax"></a>Składnia  
  
```  
void _WriteBarrier(void);  
```  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`_WriteBarrier`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 `_WriteBarrier` Wewnętrzne ogranicza optymalizacje kompilatora, które można usunąć lub zmienić kolejność operacji uzyskiwania dostępu do pamięci dla punktu połączenia.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_ReadBarrier](../intrinsics/readbarrier.md)   
 [_ReadWriteBarrier](../intrinsics/readwritebarrier.md)   
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)