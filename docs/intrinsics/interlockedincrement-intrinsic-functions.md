---
title: Funkcje wewnętrzne _interlockedincrement | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _InterlockedIncrement_acq
- _InterlockedIncrement16_rel_cpp
- _InterlockedIncrement16_cpp
- _InterlockedIncrement64_rel
- _InterlockedIncrement_rel
- _InterlockedIncrement64_nf
- _InterlockedIncrement16_acq_cpp
- _InterlockedIncrement_rel_cpp
- _InterlockedIncrement64
- _InterlockedIncrement64_rel_cpp
- _InterlockedIncrement16_nf
- _InterlockedIncrement16_rel
- _InterlockedIncrement16_acq
- _InterlockedIncrement_nf
- _InterlockedIncrement_acq_cpp
- _InterlockedIncrement64_cpp
- _InterlockedIncrement64_acq_cpp
- _InterlockedIncrement
- _InterlockedIncrement_cpp
- _InterlockedIncrement64_acq
- _InterlockedIncrement16
dev_langs:
- C++
helpviewer_keywords:
- _InterlockedIncrement64_rel intrinsic
- _InterlockedIncrement16_rel intrinsic
- InterlockedIncrement64_acq intrinsic
- _InterlockedIncrement16 intrinsic
- _InterlockedIncrement16_acq intrinsic
- _InterlockedIncrement_nf intrinsic
- _InterlockedIncrement_rel intrinsic
- _InterlockedIncrement64_nf intrinsic
- InterlockedIncrement_rel intrinsic
- InterlockedIncrement_acq intrinsic
- _InterlockedIncrement64_acq intrinsic
- _InterlockedIncrement16_nf intrinsic
- _InterlockedIncrement intrinsic
- _InterlockedIncrement64 intrinsic
- InterlockedIncrement64_rel intrinsic
- InterlockedIncrement64 intrinsic
- InterlockedIncrement16 intrinsic
- _InterlockedIncrement_acq intrinsic
- InterlockedIncrement intrinsic
ms.assetid: 37700615-f372-438b-bcef-d76e11839482
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 900200eb1894a4f7065a008aeada9b90e71c6fcd
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42575791"
---
# <a name="interlockedincrement-intrinsic-functions"></a>Funkcje wewnętrzne _interlockedincrement
**Microsoft Specific**  
  
 Zapewnia wsparcie wewnętrznej kompilatora dla zestawu SDK Windows Win32 [InterlockedIncrement](/windows/desktop/api/winbase/nf-winbase-interlockedincrement) funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
long _InterlockedIncrement(  
   long * lpAddend  
);  
long _InterlockedIncrement_acq(  
   long * lpAddend  
);  
long _InterlockedIncrement_rel(  
   long * lpAddend  
);  
long _InterlockedIncrement_nf(  
   long * lpAddend  
);  
short _InterlockedIncrement16(  
   short * lpAddend  
);  
short _InterlockedIncrement16_acq(  
   short * lpAddend  
);  
short _InterlockedIncrement16_rel(  
   short * lpAddend  
);  
short _InterlockedIncrement16_nf (  
   short * lpAddend  
);  
__int64 _InterlockedIncrement64(  
   __int64 * lpAddend  
);  
__int64 _InterlockedIncrement64_acq(  
   __int64 * lpAddend  
);  
__int64 _InterlockedIncrement64_rel(  
   __int64 * lpAddend  
);   
__int64 _InterlockedIncrement64_nf(  
   __int64 * lpAddend  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [out w] `lpAddend`  
 Wskaźnik do zmiennej, aby być zwiększony.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość zwracana jest wartość wynikową zwiększona.  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|nagłówek|  
|---------------|------------------|------------|  
|`_InterlockedIncrement`, `_InterlockedIncrement16`, `_InterlockedIncrement64`|x86, ARM, x64|\<intrin.h>|  
|`_InterlockedIncrement_acq`, `_InterlockedIncrement_rel`, `_InterlockedIncrement_nf`, `_InterlockedIncrement16_acq`, `_InterlockedIncrement16_rel`, `_InterlockedIncrement16_nf`, `_InterlockedIncrement64_acq`, `_InterlockedIncrement64_rel`, `_InterlockedIncrement64_nf`|ARM|\<intrin.h>|  
  
## <a name="remarks"></a>Uwagi  
 Istnieje kilka zmian w `_InterlockedIncrement` różnią się zależnie od typów danych, wymagają one oraz tego, czy uzyskać specyficznych dla procesora lub semantyka wydania jest używany.  
  
 Gdy `_InterlockedIncrement` funkcja działa w 32-bitowych wartości całkowitych, `_InterlockedIncrement16` operuje na wartości 16-bitową liczbę całkowitą i `_InterlockedIncrement64` działa w 64-bitowych wartości całkowitych.  
  
 Na platformach ARM, użyj funkcji wewnętrznych za pomocą `_acq` i `_rel` sufiksy, jeśli potrzebujesz uzyskać i zwolnij semantykę, takich jak na początku i na końcu sekcję krytyczną. Wewnętrzne z `_nf` sufiks ("nie ogranicznika") nie działają jako czynnik blokujący pamięci.  
  
 Zmienna wskazywany przez `lpAddend` parametru musi być wyrównany na granicy 32-bitowy; w przeciwnym razie ta funkcja nie powiedzie się na wieloprocesorowych x86 systemów i systemy innych x86. Aby uzyskać więcej informacji, zobacz [wyrównać](../cpp/align-cpp.md).  
  
 Funkcja Win32 jest zadeklarowana w `Wdm.h` lub `Ntddk.h`.  
  
 Te procedury są dostępne tylko jako funkcje wewnętrzne.  
  
## <a name="example"></a>Przykład  
 Przykład sposobu użycia `_InterlockedIncrement`, zobacz [_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md).  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [Keywords](../cpp/keywords-cpp.md)   
 [Konflikty z kompilatorem x86](../build/conflicts-with-the-x86-compiler.md)