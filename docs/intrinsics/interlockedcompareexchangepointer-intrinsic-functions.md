---
title: Funkcje wewnętrzne _interlockedcompareexchangepointer | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 18f26f9ac0cd00758d1259ac368b2408a7a2e8cf
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43214624"
---
# <a name="interlockedcompareexchangepointer-intrinsic-functions"></a>Funkcje wewnętrzne _interlockedcompareexchangepointer
**Microsoft Specific**  
  
 Wykonuje operacją niepodzielną, która przechowuje `Exchange` adresem `Destination` adres, jeśli `Comparand` i `Destination` adres są takie same.  
  
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
 [out w] `Destination`  
 Wskaźnik do wskaźnika do wartości docelowej. Znak jest ignorowany.  
  
 [in] `Exchange`  
 Wskaźnik do programu Exchange. Znak jest ignorowany.  
  
 [in] `Comparand`  
 Wskaźnik do porównania do miejsca docelowego. Znak jest ignorowany.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość zwracana jest wartość początkowa miejsca docelowego.  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|nagłówek|  
|---------------|------------------|------------|  
|`_InterlockedCompareExchangePointer`|x86, ARM, x64|\<intrin.h>|  
|`_InterlockedCompareExchangePointer_acq`, `_InterlockedCompareExchangePointer_nf`, `_InterlockedCompareExchangePointer_rel`|ARM|\<iiintrin.h>|  
|`_InterlockedCompareExchangePointer_HLEAcquire`, `_InterlockedCompareExchangePointer_HLERelease`|x86, x64|\<immintrin.h>|  
  
## <a name="remarks"></a>Uwagi  
 `_InterlockedCompareExchangePointer` Wykonuje porównanie atomowe `Destination` spełnić za pomocą `Comparand` adresu. Jeśli `Destination` adresów jest równa `Comparand` adresu `Exchange` adres jest przechowywany w adresem określonym przez `Destination`. W przeciwnym razie odbywa się żadna operacja.  
  
 `_InterlockedCompareExchangePointer` zapewnia wsparcie wewnętrznej kompilatora dla zestawu SDK Windows Win32 [_InterlockedCompareExchangePointer](https://msdn.microsoft.com/library/ff547863.aspx) funkcji.  
  
 Na przykład sposobu użycia `_InterlockedCompareExchangePointer`, zobacz [_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md).  
  
 Na platformach ARM, użyj funkcji wewnętrznych za pomocą `_acq` i `_rel` sufiksy, jeśli potrzebujesz uzyskać i zwolnij semantykę, takich jak na początku i na końcu sekcję krytyczną. Funkcje wewnętrzne ARM, za pomocą `_nf` sufiks ("nie ogranicznika") nie działają jako czynnik blokujący pamięci.  
  
 Funkcje wewnętrzne z `_np` sufiks ("nie pobieranie z wyprzedzeniem") uniemożliwić operacji możliwe pobieranie z wyprzedzeniem wstawiane przez kompilator.  
  
 Na platformach firmy Intel, obsługujące instrukcje pominięcia blokady sprzętu (HLE), funkcje wewnętrzne z `_HLEAcquire` i `_HLERelease` sufiksy obejmują wskazówkę procesora, który może przyspieszyć wydajność, eliminując krok blokady zapisu w sprzęcie. Jeśli te funkcje wewnętrzne są wywoływane na platformach, które nie obsługują HLE, wskazówka zostanie zignorowany.  
  
 Te procedury są dostępne tylko jako funkcje wewnętrzne.  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)