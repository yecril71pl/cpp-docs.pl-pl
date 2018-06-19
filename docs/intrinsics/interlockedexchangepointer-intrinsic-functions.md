---
title: Funkcje wewnętrzne _InterlockedExchangePointer | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _InterlockedExchangePointer_cpp
- _InterlockedExchangePointer_rel
- _InterlockedExchangePointer_nf
- _InterlockedExchangePointer_HLERelease
- _InterlockedExchangePointer_acq
- _InterlockedExchangePointer
- _InterlockedExchangePointer_acq_cpp
- _InterlockedExchangePointer_HLEAcquire
dev_langs:
- C++
helpviewer_keywords:
- _InterlockedExchangePointer_rel intrinsic
- _InterlockedExchangePointer_HLERelease intrinsic
- _InterlockedExchangePointer intrinsic
- _InterlockedExchangePointer_nf intrinsic
- _InterlockedExchangePointer_acq intrinsic
- _InterlockedExchangePointer_HLEAcquire intrinsic
- InterlockedExchangePointer_acq intrinsic
- InterlockedExchangePointer intrinsic
ms.assetid: 0eaca0b0-d79e-406b-892d-b3b462c50bbb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f8482b7d5b21c113001b702e00f406b9a3fcfd9c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334941"
---
# <a name="interlockedexchangepointer-intrinsic-functions"></a>Funkcje wewnętrzne _InterlockedExchangePointer
**Microsoft Specific**  
  
 W trakcie operacji atomic programu exchange, która kopiuje adres przekazany jako drugi argument jako pierwszy i zwraca oryginalnego adresu pierwszy.  
  
## <a name="syntax"></a>Składnia  
  
```  
void * _InterlockedExchangePointer(  
   void * volatile * Target,  
   void * Value  
);   
void * _InterlockedExchangePointer_acq(  
   void * volatile * Target,  
   void * Value  
);   
void * _InterlockedExchangePointer_rel(  
   void * volatile * Target,  
   void * Value  
);   
void * _InterlockedExchangePointer_nf(  
   void * volatile * Target,  
   void * Value  
);   
void * _InterlockedExchangePointer_HLEAcquire(  
   void * volatile * Target,  
   void * Value  
);   
void * _InterlockedExchangePointer_HLERelease(  
   void * volatile * Target,  
   void * Value  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [w, out] `Target`  
 Wskaźnik na wskaźnik do wartości do programu exchange. Funkcja ustawia wartość `Value` i zwraca jego poprzednią wartość.  
  
 [in] `Value`  
 Wartość wymienianych z wartością wskazywana przez `Target`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Funkcja zwraca wartość początkowa wskazywana przez `Target`.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|nagłówek|  
|---------------|------------------|------------|  
|`_InterlockedExchangePointer`|x86, ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h>|  
|`_InterlockedExchangePointer_acq`, `_InterlockedExchangePointer_rel`, `_InterlockedExchangePointer_nf`|ARM|\<intrin.h>|  
|`_InterlockedExchangePointer_HLEAcquire`, `_InterlockedExchangePointer_HLERelease`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] z obsługą HLE|\<immintrin.h>|  
  
 Na x86 architektury, `_InterlockedExchangePointer` jest makrem, który wywołuje `_InterlockedExchange`.  
  
## <a name="remarks"></a>Uwagi  
 W systemie 64-bitowym parametry są 64-bitowej i muszą być wyrównane na granicach 64-bitowy; w przeciwnym razie operacja zakończy się niepowodzeniem. W systemie 32-bitowy parametry są 32-bitowy i muszą być wyrównane na granicach 32-bitowych. Aby uzyskać więcej informacji, zobacz [Dopasuj](../cpp/align-cpp.md).  
  
 Na platformach ARM, użyj funkcji wewnętrznych z `_acq` i `_rel` sufiksy, jeśli należy uzyskać i zwolnij semantyki, takich jak na początku i na końcu sekcji krytycznych. Wewnętrzne z `_nf` sufiks ("nie ogranicznika") nie działa jako bariery pamięci.  
  
 Na platformach firmy Intel, które obsługują instrukcje Elision blokady sprzętu (HLE), funkcje wewnętrzne z `_HLEAcquire` i `_HLERelease` sufiksy obejmują wskazówkę procesora, która umożliwia przyspieszanie wydajności przez wyeliminowanie krok blokady zapisu sprzętu. Jeśli te funkcje wewnętrzne są nazywane na platformach, które nie obsługują HLE, wskazówka zostanie zignorowany.  
  
 Te procedury są dostępne tylko jako funkcje wewnętrzne.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [Konflikty z kompilatorem x86](../build/conflicts-with-the-x86-compiler.md)