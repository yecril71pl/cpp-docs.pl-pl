---
title: _Readbarrier — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _ReadBarrier
dev_langs:
- C++
helpviewer_keywords:
- _ReadBarrier intrinsic
ms.assetid: f9e54a92-61bc-4f55-8195-b8932065a796
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e46b64b47aa2f47d5b63aea1231a5f8e8bb274ac
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42464550"
---
# <a name="readbarrier"></a>_ReadBarrier  
  
**Microsoft Specific**  
  
 Ogranicza optymalizacje kompilatora, które można zmieniać kolejność operacji dostępu do pamięci poprzez punkt wywołania.  
  
> [!CAUTION]
>  `_ReadBarrier`, `_WriteBarrier`, I `_ReadWriteBarrier` funkcje wewnętrzne kompilatora i `MemoryBarrier` makra są przestarzałe i nie powinna być używana. Do komunikacji między wątku, użyj mechanizmów takich jak [atomic_thread_fence —](../standard-library/atomic-functions.md#atomic_thread_fence) i [std::atomic\<T >](../standard-library/atomic.md) które są definiowane w [standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md). W przypadku dostępu do sprzętu, użyj [/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) — opcja kompilatora wraz z [volatile](../cpp/volatile-cpp.md) — słowo kluczowe.  
  
## <a name="syntax"></a>Składnia  
  
```  
void _ReadBarrier(void);  
```  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`_ReadBarrier`|x86, x64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 `_ReadBarrier` Wewnętrzne ogranicza optymalizacje kompilatora, które mogą usuwać lub zmieniać kolejność operacji dostępu do pamięci poprzez punkt wywołania.  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)