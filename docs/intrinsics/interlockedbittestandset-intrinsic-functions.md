---
title: funkcje wewnętrzne _interlockedbittestandset | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _interlockedbittestandset_cpp
- _interlockedbittestandset_HLEAcquire
- _interlockedbittestandset64
- _interlockedbittestandset
- _interlockedbittestandset_rel
- _interlockedbittestandset64_HLEAcquire
- _interlockedbittestandset_HLERelease
- _interlockedbittestandset_acq
- _interlockedbittestandset_nf
- _interlockedbittestandset64_cpp
- _interlockedbittestandset64_HLERelease
dev_langs:
- C++
helpviewer_keywords:
- _interlockedbittestandset intrinsic
- _interlockedbittestandset64 intrinsic
- lock_bts instruction
ms.assetid: b1b7e334-53ea-48cf-ba60-5fa3ef51a1fc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7b64118753138087bce446a92716c6cb1731c7ea
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465054"
---
# <a name="interlockedbittestandset-intrinsic-functions"></a>funkcje wewnętrzne _interlockedbittestandset
**Microsoft Specific**  
  
 Generowanie instrukcji, która sprawdza, czy bit `b` adresu `a` i zwraca jego bieżąca wartość przed ustawieniem dla niego wartości 1.  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned char _interlockedbittestandset(  
   long *a,  
   long b  
);  
unsigned char _interlockedbittestandset_acq(  
   long *a,  
   long b  
);  
unsigned char _interlockedbittestandset_HLEAcquire(  
   long *a,  
   long b  
);  
unsigned char _interlockedbittestandset_HLERelease(  
   long *a,  
   long b  
);  
unsigned char _interlockedbittestandset_nf(  
   long *a,  
   long b  
);  
unsigned char _interlockedbittestandset_rel(  
   long *a,  
   long b  
);  
unsigned char _interlockedbittestandset64(  
   __int64 *a,  
   __int64 b  
);  
unsigned char _interlockedbittestandset64_HLEAcquire(  
   __int64 *a,  
   __int64 b  
);  
unsigned char _interlockedbittestandset64_HLERelease(  
   __int64 *a,  
   __int64 b  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `a`  
 Wskaźnik do pamięci do sprawdzenia.  
  
 [in] `b`  
 Pozycja bitu do testowania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość bitowa w położeniu `b` przed jest ustawiona.  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|nagłówek|  
|---------------|------------------|------------|  
|`_interlockedbittestandset`|x86, ARM, x64|\<intrin.h>|  
|`_interlockedbittestandset_acq`, `_interlockedbittestandset_nf`, `_interlockedbittestandset_rel`|ARM|\<intrin.h>|  
|`_interlockedbittestandset_HLEAcquire`, `_interlockedbittestandset_HLERelease`|x86, x64|\<immintrin.h>|  
|`_interlockedbittestandset64`|X64|\<intrin.h>|  
|`_interlockedbittestandset64_HLEAcquire`, `_interlockedbittestandset64_HLERelease`|X64|\<immintrin.h>|  
  
## <a name="remarks"></a>Uwagi  
 Na procesorach x86 i x64, użyj funkcji wewnętrznych `lock bts` instrukcji, aby odczytać i ustawić bitu określonego na 1. Operacja jest atomic.  
  
 Na procesorach ARM, użyj funkcji wewnętrznych za pomocą `_acq` i `_rel` sufiksy dla semantyki nabywania i wydania, takie jak na początku i na końcu sekcję krytyczną. Funkcje wewnętrzne ARM przy użyciu `_nf` sufiks ("nie ogranicznika") nie działają jako czynnik blokujący pamięci.  
  
 Na procesorach Intel, obsługujące instrukcje pominięcia blokady sprzętu (HLE), funkcje wewnętrzne z `_HLEAcquire` i `_HLERelease` sufiksy obejmują wskazówkę procesora, który może przyspieszyć wydajność, eliminując krok blokady zapisu w sprzęcie. Jeśli te funkcje wewnętrzne są wywoływane na procesorach, które nie obsługują HLE, wskazówka zostanie zignorowany.  
  
 Te procedury są dostępne tylko jako funkcje wewnętrzne.  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [Konflikty z kompilatorem x86](../build/conflicts-with-the-x86-compiler.md)