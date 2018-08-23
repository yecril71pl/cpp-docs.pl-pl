---
title: _Writebarrier — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _WriteBarrier
dev_langs:
- C++
helpviewer_keywords:
- WriteBarrier intrinsic
- _WriteBarrier intrinsic
ms.assetid: a5ffdad9-0ca1-4eb7-b2f3-0f092c4bf4b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 89b1f9c04d9ac4e4cb1892b0abfed9ddcd59717e
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465049"
---
# <a name="writebarrier"></a>_WriteBarrier
**Microsoft Specific**  
  
 Ogranicza optymalizacje kompilatora, które można zmieniać kolejność operacji dostępu do pamięci poprzez punkt wywołania.  
  
> [!CAUTION]
>  `_ReadBarrier`, `_WriteBarrier`, I `_ReadWriteBarrier` funkcje wewnętrzne kompilatora i `MemoryBarrier` makra są przestarzałe i nie powinna być używana. Do komunikacji między wątku, użyj mechanizmów takich jak [atomic_thread_fence —](../standard-library/atomic-functions.md#atomic_thread_fence) i [std::atomic\<T >](../standard-library/atomic.md), które są określone w [standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md). W przypadku dostępu do sprzętu, użyj [/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) — opcja kompilatora wraz z [volatile](../cpp/volatile-cpp.md) — słowo kluczowe.  
  
## <a name="syntax"></a>Składnia  
  
```  
void _WriteBarrier(void);  
```  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`_WriteBarrier`|x86, x64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 `_WriteBarrier` Wewnętrzne ogranicza optymalizacje kompilatora, które mogą usuwać lub zmieniać kolejność operacji dostępu do pamięci poprzez punkt wywołania.  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_ReadBarrier](../intrinsics/readbarrier.md)   
 [_ReadWriteBarrier](../intrinsics/readwritebarrier.md)   
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)