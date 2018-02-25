---
title: "Funkcje wewnętrzne _interlockedbittestandreset | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- _interlockedbittestandreset_rel
- _interlockedbittestandreset64
- _interlockedbittestandreset64_HLERelease
- _interlockedbittestandreset_HLERelease
- _interlockedbittestandreset_HLEAcquire
- _interlockedbittestandreset_acq
- _interlockedbittestandreset_cpp
- _interlockedbittestandreset_nf
- _interlockedbittestandreset64_cpp
- _interlockedbittestandreset64_HLEAcquire
- _interlockedbittestandreset
dev_langs:
- C++
helpviewer_keywords:
- lock_btr instruction
- _interlockedbittestandreset64 intrinsic
- _interlockedbittestandreset intrinsic
ms.assetid: 9bbb1442-f2e9-4dc2-b0da-97f3de3493b9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 12ade2e7eb61c996300dc4208e45f571a5108a46
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="interlockedbittestandreset-intrinsic-functions"></a>Funkcje wewnętrzne _interlockedbittestandreset
**Microsoft Specific**  
  
 Generuje instrukcja, która ustawia bit `b` adresu `a` od zera i zwraca oryginalną wartość.  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned char _interlockedbittestandreset(  
   long *a,  
   long b  
);  
unsigned char _interlockedbittestandreset_acq(  
   long *a,  
   long b  
);  
unsigned char _interlockedbittestandreset_HLEAcquire(  
   long *a,  
   long b  
);  
unsigned char _interlockedbittestandreset_HLERelease(  
   long *a,  
   long b  
);  
unsigned char _interlockedbittestandreset_nf(  
   long *a,  
   long b  
);  
unsigned char _interlockedbittestandreset_rel(  
   long *a,  
   long b  
);   
unsigned char _interlockedbittestandreset64(  
   __int64 *a,  
   __int64 b  
);   
unsigned char _interlockedbittestandreset64_HLEAcquire(  
   __int64 *a,  
   __int64 b  
);  
unsigned char _interlockedbittestandreset64_HLERelease(  
   __int64 *a,  
   __int64 b  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `a`  
 Wskaźnik do pamięci do sprawdzenia.  
  
 [in] `b`  
 Pozycja bit do testowania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Oryginalnej wartości bitowe w miejscu określonym przez `b`.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|nagłówek|  
|---------------|------------------|------------|  
|`_interlockedbittestandreset`|x86, ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h>|  
|`_interlockedbittestandreset_acq`, `_interlockedbittestandreset_nf`, `_interlockedbittestandreset_rel`|ARM|\<intrin.h>|  
|`_interlockedbittestandreset_HLEAcquire`, `_interlockedbittestandreset_HLERelease`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<immintrin.h>|  
|`_interlockedbittestandreset64`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h>|  
|`_interlockedbittestandreset64_HLEAcquire`, `_interlockedbittestandreset64_HLERelease`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<immintrin.h>|  
  
## <a name="remarks"></a>Uwagi  
 Na x86 i [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] procesorów, te funkcje wewnętrzne użyj `lock btr` instrukcji, która odczytuje i ustawia określony bit zero w niepodzielną operację.  
  
 Na procesorów ARM, użyj funkcji wewnętrznych z `_acq` i `_rel` sufiksy dla semantyki pobierania i zlecenia, takie jak na początku i na końcu sekcji krytycznych. Funkcje wewnętrzne ARM z `_nf` sufiks ("nie ogranicznika") nie działają jako bariery pamięci.  
  
 Na procesorów Intel, które obsługują instrukcje Elision blokady sprzętu (HLE), funkcje wewnętrzne z `_HLEAcquire` i `_HLERelease` sufiksy obejmują wskazówkę procesora, która umożliwia przyspieszanie wydajności przez wyeliminowanie krok blokady zapisu sprzętu. Jeśli te funkcje wewnętrzne są nazywane na procesorów, które nie obsługują HLE, wskazówka zostanie zignorowany.  
  
 Te procedury są dostępne tylko jako funkcje wewnętrzne.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [Konflikty z kompilatorem x86](../build/conflicts-with-the-x86-compiler.md)