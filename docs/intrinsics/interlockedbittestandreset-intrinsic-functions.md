---
title: funkcje wewnętrzne _interlockedbittestandreset
ms.date: 09/02/2019
f1_keywords:
- _interlockedbittestandreset_rel
- _interlockedbittestandreset64
- _interlockedbittestandreset64_acq
- _interlockedbittestandreset64_nf
- _interlockedbittestandreset64_rel
- _interlockedbittestandreset64_HLERelease
- _interlockedbittestandreset_HLERelease
- _interlockedbittestandreset_HLEAcquire
- _interlockedbittestandreset_acq
- _interlockedbittestandreset_cpp
- _interlockedbittestandreset_nf
- _interlockedbittestandreset64_cpp
- _interlockedbittestandreset64_HLEAcquire
- _interlockedbittestandreset
helpviewer_keywords:
- lock_btr instruction
- _interlockedbittestandreset64 intrinsic
- _interlockedbittestandreset intrinsic
ms.assetid: 9bbb1442-f2e9-4dc2-b0da-97f3de3493b9
ms.openlocfilehash: 419d7f800d603a8beca5c8ccb0f9c8f8b3bfcfdb
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222059"
---
# <a name="_interlockedbittestandreset-intrinsic-functions"></a>funkcje wewnętrzne _interlockedbittestandreset

**Microsoft Specific**

Generuje instrukcję, aby ustawić bit `b` adresu `a` na zero i zwrócić oryginalną wartość.

## <a name="syntax"></a>Składnia

```C
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
unsigned char _interlockedbittestandreset64_acq(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandreset64_nf(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandreset64_rel(
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

### <a name="parameters"></a>Parametry

*z*\
podczas Wskaźnik do pamięci do sprawdzenia.

*b*\
podczas Pozycja bitu do przetestowania.

## <a name="return-value"></a>Wartość zwracana

Oryginalna wartość bitu na pozycji określonej przez `b`.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|nagłówek|
|---------------|------------------|------------|
|`_interlockedbittestandreset`|x86, ARM, x64, ARM64|\<intrin.h>|
|`_interlockedbittestandreset_acq`, `_interlockedbittestandreset_nf`, `_interlockedbittestandreset_rel`|ARM, ARM64|\<intrin.h>|
|`_interlockedbittestandreset64_acq`, `_interlockedbittestandreset64_nf`, `_interlockedbittestandreset64_rel`|ARM64|\<intrin.h>|
|`_interlockedbittestandreset_HLEAcquire`, `_interlockedbittestandreset_HLERelease`|x86, x64|\<immintrin.h>|
|`_interlockedbittestandreset64`|x64, ARM64|\<intrin.h>|
|`_interlockedbittestandreset64_HLEAcquire`, `_interlockedbittestandreset64_HLERelease`|X64|\<immintrin.h>|

## <a name="remarks"></a>Uwagi

W przypadku procesorów x86 i x64 te funkcje wewnętrzne wykorzystują `lock btr` instrukcję, która odczytuje i ustawia określony bit na zero w operacji niepodzielnej.

W przypadku procesorów ARM Użyj wewnętrznych z `_acq` i `_rel` sufiksów dla semantyki pozyskiwania i wydawania, na przykład na początku i na końcu sekcji krytycznej. Elementy wewnętrzne ARM z `_nf` sufiksem ("No ogrodzeni") nie działają jako bariera pamięci.

W przypadku procesorów firmy Intel, które obsługują instrukcje dotyczące blokowania sprzętowego dla koprocedury (HLE) `_HLEAcquire` , `_HLERelease` wewnętrzne z i sufiksy zawierają wskazówkę procesora, która może przyspieszyć działanie, eliminując krok blokady zapisu sprzętu. Jeśli te elementy wewnętrzne są wywoływane na procesorach, które nie obsługują HLE, Wskazówka jest ignorowana.

Te procedury są dostępne tylko jako elementy wewnętrzne.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)\
[Konflikty z kompilatorem x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
