---
title: "Funkcje wewnętrzne _InterlockedAnd | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _InterlockedAnd_rel
- _InterlockedAnd_cpp
- _InterlockedAnd8_nf
- _InterlockedAnd
- _InterlockedAnd_HLERelease
- _InterlockedAnd8_np
- _InterlockedAnd16_rel
- _InterlockedAnd64_np
- _InterlockedAnd_np
- _InterlockedAnd64_HLERelease
- _InterlockedAnd64
- _InterlockedAnd64_nf
- _InterlockedAnd64_HLEAcquire
- _InterlockedAnd16
- _InterlockedAnd16_nf
- _InterlockedAnd8
- _InterlockedAnd_HLEAcquire
- _InterlockedAnd_acq
- _InterlockedAnd16_np
- _InterlockedAnd64_cpp
- _InterlockedAnd64_acq
- _InterlockedAnd16_acq
- _InterlockedAnd8_acq
- _InterlockedAnd64_rel
- _InterlockedAnd_nf
- _InterlockedAnd8_rel
dev_langs: C++
helpviewer_keywords:
- _InterlockedAnd64_np intrinsic
- _InterlockedAnd intrinsic
- _InterlockedAnd64 intrinsic
- _InterlockedAnd8_rel intrinsic
- InterlockedAnd64 intrinsic
- _InterlockedAnd16_np intrinsic
- _InterlockedAnd64_nf intrinsic
- _InterlockedAnd_nf intrinsic
- _InterlockedAnd_np intrinsic
- _InterlockedAnd64_HLERelease intrinsic
- _InterlockedAnd16_rel intrinsic
- _InterlockedAnd_HLERelease intrinsic
- _InterlockedAnd64_acq intrinsic
- _InterlockedAnd16 intrinsic
- _InterlockedAnd8_nf intrinsic
- _InterlockedAnd64_rel intrinsic
- _InterlockedAnd8_np intrinsic
- _InterlockedAnd_rel intrinsic
- InterlockedAnd intrinsic
- _InterlockedAnd8_acq intrinsic
- _InterlockedAnd_acq intrinsic
- _InterlockedAnd64_HLEAcquire intrinsic
- _InterlockedAnd16_acq intrinsic
- _InterlockedAnd16_nf intrinsic
- _InterlockedAnd8 intrinsic
- _InterlockedAnd_HLEAcquire intrinsic
ms.assetid: ad271dc3-42cd-47d0-9f65-30d5cfeb66fc
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 38507a9a2b09c091305478a1e596c8c3485cd754
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="interlockedand-intrinsic-functions"></a>Funkcje wewnętrzne _InterlockedAnd
**Dotyczące firmy Microsoft**  
  
 Używane do wykonywania atomic operacji i na zmienną współużytkowane przez wiele wątków.  
  
## <a name="syntax"></a>Składnia  
  
```  
long _InterlockedAnd(  
   long volatile * value,  
   long mask  
);  
long _InterlockedAnd_acq(  
   long volatile * value,  
   long mask  
);  
long _InterlockedAnd_HLEAcquire(  
   long volatile * value,  
   long mask  
);  
long _InterlockedAnd_HLERelease(  
   long volatile * value,  
   long mask  
);  
long _InterlockedAnd_nf(  
   long volatile * value,  
   long mask  
);  
long _InterlockedAnd_np(  
   long volatile * value,  
   long mask  
);  
long _InterlockedAnd_rel(  
   long volatile * value,  
   long mask  
);  
char _InterlockedAnd8(  
   char volatile * value,  
   char mask  
);  
char _InterlockedAnd8_acq(  
   char volatile * value,  
   char mask  
);  
char _InterlockedAnd8_nf(  
   char volatile * value,  
   char mask  
);  
char _InterlockedAnd8_np(  
   char volatile * value,  
   char mask  
);  
char _InterlockedAnd8_rel(  
   char volatile * value,  
   char mask  
);  
short _InterlockedAnd16(  
   short volatile * value,  
   short mask  
);  
short _InterlockedAnd16_acq(  
   short volatile * value,  
   short mask  
);  
short _InterlockedAnd16_nf(  
   short volatile * value,  
   short mask  
);  
short _InterlockedAnd16_np(  
   short volatile * value,  
   short mask  
);  
short _InterlockedAnd16_rel(  
   short volatile * value,  
   short mask  
);  
__int64 _InterlockedAnd64(  
   __int64 volatile* value,  
   __int64 mask  
);  
__int64 _InterlockedAnd64_acq(  
   __int64 volatile* value,  
   __int64 mask  
);   
__int64 _InterlockedAnd64_HLEAcquire(  
   __int64 volatile* value,  
   __int64 mask  
);  
__int64 _InterlockedAnd64_HLERelease(  
   __int64 volatile* value,  
   __int64 mask  
);  
__int64 _InterlockedAnd64_nf(  
   __int64 volatile* value,  
   __int64 mask  
);  
__int64 _InterlockedAnd64_np(  
   __int64 volatile* value,  
   __int64 mask  
);  
__int64 _InterlockedAnd64_rel(  
   __int64 volatile* value,  
   __int64 mask  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [w, out]`value`  
 Wskaźnik do pierwszego argumentu operacji mają zostać zastąpione przez wynik.  
  
 [in]`mask`  
 Drugi argument operacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Oryginalna wartość pierwszy argument operacji.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|nagłówek|  
|---------------|------------------|------------|  
|`_InterlockedAnd`, `_InterlockedAnd8`, `_InterlockedAnd16`, `_InterlockedAnd64`|x86, ARM,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h >|  
|`_InterlockedAnd_acq`, `_InterlockedAnd_nf`, `_InterlockedAnd_rel`, `_InterlockedAnd8_acq`, `_InterlockedAnd8_nf`, `_InterlockedAnd8_rel`, `_InterlockedAnd16_acq`, `_InterlockedAnd16_nf`, `_InterlockedAnd16_rel`, `_InterlockedAnd64_acq`, `_InterlockedAnd64_nf`, `_InterlockedAnd64_rel`|ARM|\<intrin.h >|  
|`_InterlockedAnd_np`, `_InterlockedAnd8_np`, `_InterlockedAnd16_np`, `_InterlockedAnd64_np`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h >|  
|`_InterlockedAnd_HLEAcquire`, `_InterlockedAnd_HLERelease`, `_InterlockedAnd64_HLEAcquire`, `_InterlockedAnd64_HLERelease`|x86,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<immintrin.h >|  
  
## <a name="remarks"></a>Uwagi  
 Numer nazwy poszczególnych funkcji określa rozmiar bit argumentów.  
  
 Na platformach ARM, użyj funkcji wewnętrznych z `_acq` i `_rel` sufiksy dla semantyki pobierania i zlecenia, takie jak na początku i na końcu sekcji krytycznych. Funkcje wewnętrzne z `_nf` sufiks ("nie ogranicznika") nie działają jako bariery pamięci.  
  
 Funkcje wewnętrzne z `_np` sufiks ("nie pobierania z wyprzedzeniem") uniemożliwiają operacji pobierania z wyprzedzeniem możliwe wstawiane przez kompilator.  
  
 Na platformach firmy Intel, które obsługują instrukcje Elision blokady sprzętu (HLE), funkcje wewnętrzne z `_HLEAcquire` i `_HLERelease` sufiksy obejmują wskazówkę procesora, która umożliwia przyspieszanie wydajności przez wyeliminowanie krok blokady zapisu sprzętu. Jeśli te funkcje wewnętrzne są nazywane na platformach, które nie obsługują HLE, wskazówka zostanie zignorowany.  
  
## <a name="example"></a>Przykład  
  
```  
// InterlockedAnd.cpp  
// Compile with: /Oi  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(_InterlockedAnd)  
  
int main()  
{  
        long data1 = 0xFF00FF00;  
        long data2 = 0x00FFFF00;  
        long retval;  
        retval = _InterlockedAnd(&data1, data2);  
        printf_s("0x%x 0x%x 0x%x", data1, data2, retval);   
}  
```  
  
```Output  
0xff00 0xffff00 0xff00ff00  
```  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [Konflikty z kompilatorem x86](../build/conflicts-with-the-x86-compiler.md)