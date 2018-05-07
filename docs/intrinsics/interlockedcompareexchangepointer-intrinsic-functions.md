---
title: Funkcje wewnętrzne _InterlockedCompareExchangePointer | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _InterlockedCompareExchangePointer_HLERelease
- _InterlockedCompareExchangePointer_rel
- _InterlockedCompareExchangePointer_acq_cpp
- _InterlockedCompareExchangePointer
- _InterlockedCompareExchangePointer_cpp
- _InterlockedCompareExchangePointer_np
- _InterlockedCompareExchangePointer_rel_cpp
- _InterlockedCompareExchangePointer_HLEAcquire
- _InterlockedCompareExchangePointer_acq
- _InterlockedCompareExchangePointer_nf
dev_langs:
- C++
helpviewer_keywords:
- InterlockedCompareExchangePointer_acq intrinsic
- _InterlockedCompareExchangePointer_rel intrinsic
- _InterlockedCompareExchangePointer_acq intrinsic
- InterlockedCompareExchangePointer_rel intrinsic
- InterlockedCompareExchangePointer intrinsic
- _InterlockedCompareExchangePointer_HLERelease intrinsic
- _InterlockedCompareExchangePointer_HLEAcquire intrinsic
- _InterlockedCompareExchangePointer intrinsic
- _InterlockedCompareExchangePointer_nf intrinsic
- _InterlockedCompareExchangePointer_np intrinsic
ms.assetid: 97fde59d-2bf9-42aa-a0fe-a5b6befdd44b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6c8e7a31c5377d71eaad96fddc7d93215ed3abb4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="interlockedcompareexchangepointer-intrinsic-functions"></a>Funkcje wewnętrzne _InterlockedCompareExchangePointer
**Microsoft Specific**  
  
 Wykonuje operację atomic, która przechowuje `Exchange` adresów w `Destination` adres, jeśli `Comparand` i `Destination` adresu są takie same.  
  
## <a name="syntax"></a>Składnia  
  
```  
void * _InterlockedCompareExchangePointer (  
   void * volatile * Destination,  
   void * Exchange,  
   void * Comparand  
);  
void * _InterlockedCompareExchangePointer_acq (  
   void * volatile * Destination,  
   void * Exchange,  
   void * Comparand  
);  
void * _InterlockedCompareExchangePointer_HLEAcquire (  
   void * volatile * Destination,  
   void * Exchange,  
   void * Comparand  
);  
void * _InterlockedCompareExchangePointer_HLERelease (  
   void * volatile * Destination,  
   void * Exchange,  
   void * Comparand  
);  
void * _InterlockedCompareExchangePointer_nf (  
   void * volatile * Destination,  
   void * Exchange,  
   void * Comparand  
);  
void * _InterlockedCompareExchangePointer_np (  
   void * volatile * Destination,  
   void * Exchange,  
   void * Comparand  
);  
long _InterlockedCompareExchangePointer_rel (  
   void * volatile * Destination,  
   void * Exchange,  
   void * Comparand  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [w, out] `Destination`  
 Wskaźnik na wskaźnik do wartości docelowej. Znak jest ignorowana.  
  
 [in] `Exchange`  
 Wskaźnik programu Exchange. Znak jest ignorowana.  
  
 [in] `Comparand`  
 Wskaźnik do porównania do miejsca docelowego. Znak jest ignorowana.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość zwracana jest wartość początkowa miejsca docelowego.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|nagłówek|  
|---------------|------------------|------------|  
|`_InterlockedCompareExchangePointer`|x86, ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h>|  
|`_InterlockedCompareExchangePointer_acq`, `_InterlockedCompareExchangePointer_nf`, `_InterlockedCompareExchangePointer_rel`|ARM|\<iiintrin.h>|  
|`_InterlockedCompareExchangePointer_HLEAcquire`, `_InterlockedCompareExchangePointer_HLERelease`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<immintrin.h>|  
  
## <a name="remarks"></a>Uwagi  
 `_InterlockedCompareExchangePointer` przeprowadza porównanie atomic `Destination` adresów z `Comparand` adres. Jeśli `Destination` adres jest taki sam `Comparand` adres `Exchange` adres jest przechowywany w adresem określonym przez `Destination`. W przeciwnym razie operacja nie jest wykonywana.  
  
 `_InterlockedCompareExchangePointer` zapewnia obsługę wewnętrznych kompilatora dla środowiska Win32 [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)] [_InterlockedCompareExchangePointer](http://msdn.microsoft.com/library/ff547863.aspx) funkcji.  
  
 Na przykład można użyć `_InterlockedCompareExchangePointer`, zobacz [_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md).  
  
 Na platformach ARM, użyj funkcji wewnętrznych z `_acq` i `_rel` sufiksy, jeśli należy uzyskać i zwolnij semantyki, takich jak na początku i na końcu sekcji krytycznych. Funkcje wewnętrzne ARM z `_nf` sufiks ("nie ogranicznika") nie działają jako bariery pamięci.  
  
 Funkcje wewnętrzne z `_np` sufiks ("nie pobierania z wyprzedzeniem") uniemożliwiają operacji pobierania z wyprzedzeniem możliwe wstawiane przez kompilator.  
  
 Na platformach firmy Intel, które obsługują instrukcje Elision blokady sprzętu (HLE), funkcje wewnętrzne z `_HLEAcquire` i `_HLERelease` sufiksy obejmują wskazówkę procesora, która umożliwia przyspieszanie wydajności przez wyeliminowanie krok blokady zapisu sprzętu. Jeśli te funkcje wewnętrzne są nazywane na platformach, które nie obsługują HLE, wskazówka zostanie zignorowany.  
  
 Te procedury są dostępne tylko jako funkcje wewnętrzne.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)