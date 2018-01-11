---
title: "Funkcje wewnętrzne _InterlockedExchange | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _InterlockedExchange_rel
- _InterlockedExchange8_nf
- _InterlockedExchange_acq_cpp
- _InterlockedExchange_nf
- _InterlockedExchange64_nf
- _InterlockedExchange_HLEAcquire
- _InterlockedExchange_cpp
- _InterlockedExchange64_acq_cpp
- _InterlockedExchange64_acq
- _InterlockedExchange64_HLERelease
- _InterlockedExchange8_acq
- _InterlockedExchange16_acq
- _InterlockedExchange
- _InterlockedExchange64_HLEAcquire
- _InterlockedExchange8
- _InterlockedExchange64_rel
- _InterlockedExchange_acq
- _InterlockedExchange16
- _InterlockedExchange16_rel
- _InterlockedExchange16_nf
- _InterlockedExchange64
- _InterlockedExchange_HLERelease
- _InterlockedExchange64_cpp
- _InterlockedExchange8_rel
dev_langs: C++
helpviewer_keywords:
- _InterlockedExchange8
- _InterlockedExchange64 intrinsic
- _InterlockedExchange_acq intrinsic
- InterlockedExchange64 intrinsic
- _InterlockedExchange64_acq intrinsic
- InterlockedExchange64_acq intrinsic
- _InterlockedExchange16_acq
- _InterlockedExchange8_acq
- _InterlockedExchange16
- _InterlockedExchange8_rel
- InterlockedExchange_acq intrinsic
- InterlockedExchange intrinsic
- _InterlockedExchange16_rel
- _InterlockedExchange16_nf
- _InterlockedExchange intrinsic
- _InterlockedExchange8_nf
ms.assetid: be2f232a-6301-462a-a92b-fcdeb8b0f209
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9541b3b3099d7ef088b80552410e77baec2370f1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="interlockedexchange-intrinsic-functions"></a>Funkcje wewnętrzne _InterlockedExchange
**Dotyczące firmy Microsoft**  
  
 Generuje atomic instrukcjami, aby ustawić określoną wartość.  
  
## <a name="syntax"></a>Składnia  
  
```  
long _InterlockedExchange(  
   long volatile * Target,  
   long Value  
);  
long _InterlockedExchange_acq(  
   long volatile * Target,  
   long Value  
);  
long _InterlockedExchange_HLEAcquire(  
   long volatile * Target,  
   long Value  
);  
long _InterlockedExchange_HLERelease(  
   long volatile * Target,  
   long Value  
);  
long _InterlockedExchange_nf(  
   long volatile * Target,  
   long Value  
);  
long _InterlockedExchange_rel(  
   long volatile * Target,  
   long Value  
);  
char _InterlockedExchange8(  
   char volatile * Target,  
   char Value  
);  
char _InterlockedExchange8_acq(  
   char volatile * Target,  
   char Value  
);  
char _InterlockedExchange8_nf(  
   char volatile * Target,  
   char Value  
);  
char _InterlockedExchange8_rel(  
   char volatile * Target,  
   char Value  
);  
short _InterlockedExchange16(  
   short volatile * Target,  
   short Value  
);  
short _InterlockedExchange16_acq(  
   short volatile * Target,  
   short Value  
);  
short _InterlockedExchange16_nf(  
   short volatile * Target,  
   short Value  
);  
short _InterlockedExchange16_rel(  
   short volatile * Target,  
   short Value  
);  
__int64 _InterlockedExchange64(  
   __int64 volatile * Target,  
   __int64 Value  
);  
__int64 _InterlockedExchange64_acq(  
   __int64 volatile * Target,  
   __int64 Value  
);  
__int64 _InterlockedExchange64_HLEAcquire(  
   __int64 volatile * Target,  
   __int64 Value  
);  
__int64 _InterlockedExchange64_HLERelease(  
   __int64 volatile * Target,  
   __int64 Value  
);  
__int64 _InterlockedExchange64_nf(  
   __int64 volatile * Target,  
   __int64 Value  
);  
__int64 _InterlockedExchange64_rel(  
   __int64 volatile * Target,  
   __int64 Value  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [w, out]`Target`  
 Wskaźnik do wartości, aby wymienić. Funkcja ta zmienna ustawia `Value` i zwraca jego poprzedniej wartości.  
  
 [in]`Value`  
 Wartość wymienianych z wartością wskazywana przez `Target`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość początkowa wskazywana przez `Target`.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|nagłówek|  
|---------------|------------------|------------|  
|`_InterlockedExchange`, `_InterlockedExchange8`, `_InterlockedExchange16`, `_InterlockedExchange64`|x86, ARM,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h >|  
|`_InterlockedExchange_acq`, `_InterlockedExchange_nf`, `_InterlockedExchange_rel`, `_InterlockedExchange8_acq`, `_InterlockedExchange8_nf`, `_InterlockedExchange8_rel`, `_InterlockedExchange16_acq`, `_InterlockedExchange16_nf`, `_InterlockedExchange16_rel`, `_InterlockedExchange64_acq`, `_InterlockedExchange64_nf`, `_InterlockedExchange64_rel`,|ARM|\<intrin.h >|  
|`_InterlockedExchange_HLEAcquire`, `_InterlockedExchange_HLERelease`, `_InterlockedExchange64_HLEAcquire`, `_InterlockedExchange64_HLERelease`|x86,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<immintrin.h >|  
  
## <a name="remarks"></a>Uwagi  
 `_InterlockedExchange`zapewnia obsługę wewnętrznych kompilatora dla środowiska Win32 [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)] [InterlockedExchange](http://msdn.microsoft.com/library/ms683590.aspx) funkcji.  
  
 Istnieje kilka zmian na `_InterlockedExchange` który różnić w zależności od typów danych, wymagają one i czy uzyskać specyficznych dla procesora lub Wydaj semantykę jest używany.  
  
 Podczas `_InterlockedExchange` funkcja działa na 32-bitowych liczb całkowitych, `_InterlockedExchange8` działa na wartości 8-bitową liczbę całkowitą `_InterlockedExchange16` działa na wartości 16-bitową liczbę całkowitą i `_InterlockedExchange64` działa na 64-bitowych liczb całkowitych.  
  
 Na platformach ARM, użyj funkcji wewnętrznych z `_acq` i `_rel` sufiksy dla semantyki pobierania i zlecenia, takie jak na początku i na końcu sekcji krytycznych. Funkcje wewnętrzne z `_nf` sufiks ("nie ogranicznika") nie działają jako bariery pamięci.  
  
 Na platformach firmy Intel, które obsługują instrukcje Elision blokady sprzętu (HLE), funkcje wewnętrzne z `_HLEAcquire` i `_HLERelease` sufiksy obejmują wskazówkę procesora, która umożliwia przyspieszanie wydajności przez wyeliminowanie krok blokady zapisu sprzętu. Jeśli te funkcje wewnętrzne są nazywane na platformach, które nie obsługują HLE, wskazówka zostanie zignorowany.  
  
 Te procedury są dostępne tylko jako funkcje wewnętrzne.  
  
## <a name="example"></a>Przykład  
 Przykładowe zastosowania `_InterlockedExchange`, zobacz [_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md).  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)   
 [Konflikty z kompilatorem x86](../build/conflicts-with-the-x86-compiler.md)