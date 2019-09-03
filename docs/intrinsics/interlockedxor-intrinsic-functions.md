---
title: Funkcje wewnętrzne _InterlockedXor
ms.date: 09/02/2019
f1_keywords:
- _InterlockedXor_nf
- _InterlockedXor_np
- _InterlockedXor64_HLERelease
- _InterlockedXor8_acq
- _InterlockedXor64_acq
- _InterlockedXor64_rel
- _InterlockedXor64_nf
- _InterlockedXor_acq
- _InterlockedXor16
- _InterlockedXor64_np
- _InterlockedXor64
- _InterlockedXor_HLEAcquire
- _InterlockedXor_HLERelease
- _InterlockedXor_cpp
- _InterlockedXor16_rel
- _InterlockedXor8_rel
- _InterlockedXor8
- _InterlockedXor64_HLEAcquire
- _InterlockedXor16_nf
- _InterlockedXor16_acq
- _InterlockedXor16_np
- _InterlockedXor8_fn
- _InterlockedXor8_np
- _InterlockedXor64_cpp
- _InterlockedXor_rel
- _InterlockedXor
helpviewer_keywords:
- InterlockedXor intrinsic
- _InterlockedXor64 intrinsic
- InterlockedXor64 intrinsic
- _InterlockedXor intrinsic
ms.assetid: faef1796-cb5a-4430-b1e2-9d5eaf9b4a91
ms.openlocfilehash: 22cb9edd5fa4ffd8ffae7363ab07dc48f519fff0
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221907"
---
# <a name="_interlockedxor-intrinsic-functions"></a>Funkcje wewnętrzne _InterlockedXor

**Microsoft Specific**

Wykonaj niepodzielną, niezależną lub (XOR) operację na zmiennej udostępnionej przez wiele wątków.

## <a name="syntax"></a>Składnia

```C
long _InterlockedXor(
   long volatile * Value,
   long Mask
);
long _InterlockedXor_acq(
   long volatile * Value,
   long Mask
);
long _InterlockedXor_HLEAcquire(
   long volatile * Value,
   long Mask
);
long _InterlockedXor_HLERelease(
   long volatile * Value,
   long Mask
);
long _InterlockedXor_nf(
   long volatile * Value,
   long Mask
);
long _InterlockedXor_np(
   long volatile * Value,
   long Mask
);
long _InterlockedXor_rel(
   long volatile * Value,
   long Mask
);
char _InterlockedXor8(
   char volatile * Value,
   char Mask
);
char _InterlockedXor8_acq(
   char volatile * Value,
   char Mask
);
char _InterlockedXor8_nf(
   char volatile * Value,
   char Mask
);
char _InterlockedXor8_np(
   char volatile * Value,
   char Mask
);
char _InterlockedXor8_rel(
   char volatile * Value,
   char Mask
);
short _InterlockedXor16(
   short volatile * Value,
   short Mask
);
short _InterlockedXor16_acq(
   short volatile * Value,
   short Mask
);
short _InterlockedXor16_nf (
   short volatile * Value,
   short Mask
);
short _InterlockedXor16_np (
   short volatile * Value,
   short Mask
);
short _InterlockedXor16_rel(
   short volatile * Value,
   short Mask
);
__int64 _InterlockedXor64(
   __int64 volatile * Value,
   __int64 Mask
);
__int64 _InterlockedXor64_acq(
   __int64 volatile * Value,
   __int64 Mask
);
__int64 _InterlockedXor64_HLEAcquire(
   __int64 volatile * Value,
   __int64 Mask
);
__int64 _InterlockedXor64_HLERelease(
   __int64 volatile * Value,
   __int64 Mask
);
__int64 _InterlockedXor64_nf(
   __int64 volatile * Value,
   __int64 Mask
);
__int64 _InterlockedXor64_np(
   __int64 volatile * Value,
   __int64 Mask
);
__int64 _InterlockedXor64_rel(
   __int64 volatile * Value,
   __int64 Mask
);
```

### <a name="parameters"></a>Parametry

*Wartościami*\
[in. out] Wskaźnik do pierwszego operandu, który ma zostać zastąpiony przez wynik.

*Bitowa*\
podczas Drugi operand.

## <a name="return-value"></a>Wartość zwracana

Oryginalna wartość pierwszego operandu.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|nagłówek|
|---------------|------------------|------------|
|`_InterlockedXor`, `_InterlockedXor8`, `_InterlockedXor16`|x86, ARM, x64, ARM64|\<intrin.h>|
|`_InterlockedXor64`|ARM, x64, ARM64|\<intrin.h>|
|`_InterlockedXor_acq`, `_InterlockedXor_nf`, `_InterlockedXor_rel`, `_InterlockedXor8_acq`, `_InterlockedXor8_nf`, `_InterlockedXor8_rel`, `_InterlockedXor16_acq`, `_InterlockedXor16_nf`, `_InterlockedXor16_rel`, `_InterlockedXor64_acq`, `_InterlockedXor64_nf`, `_InterlockedXor64_rel`,|ARM, ARM64|\<intrin.h>|
|`_InterlockedXor_np`, `_InterlockedXor8_np`, `_InterlockedXor16_np`, `_InterlockedXor64_np`|X64|\<intrin.h>|
|`_InterlockedXor_HLEAcquire`, `_InterlockedXor_HLERelease`|x86, x64|\<immintrin.h>|
|`_InterlockedXor64_HLEAcquire`, `_InterlockedXor64_HLERelease`|X64|\<immintrin.h>|

## <a name="remarks"></a>Uwagi

Liczba w nazwie każdej funkcji określa rozmiar bitowy argumentów.

Na platformach ARM Użyj funkcji wewnętrznych z `_acq` i `_rel` sufiksów, jeśli potrzebujesz uzyskiwania i wydawania semantyki, na przykład na początku i na końcu sekcji krytycznej. Elementy wewnętrzne ARM z `_nf` sufiksem ("No ogrodzeni") nie działają jako bariera pamięci.

Elementy wewnętrzne z `_np` sufiksem ("No Fetch") uniemożliwiają wstawienie przez kompilator możliwej operacji pobierania z wyprzedzeniem.

Na platformach firmy Intel, które obsługują instrukcje dotyczące blokowania sprzętowego dla koprocedury (HLE), `_HLEAcquire` wewnętrzne `_HLERelease` z i sufiksy zawierają wskazówkę do procesora, który może przyspieszyć działanie, eliminując krok blokady zapisu sprzętu. Jeśli te elementy wewnętrzne są wywoływane na platformach, które nie obsługują HLE, Wskazówka jest ignorowana.

## <a name="example"></a>Przykład

```cpp
// _InterLockedXor.cpp
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_InterlockedXor)

int main()
{
        long data1 = 0xFF00FF00;
        long data2 = 0x00FFFF00;
        long retval;
        retval = _InterlockedXor(&data1, data2);
        printf_s("0x%x 0x%x 0x%x", data1, data2, retval);
}
```

```Output
0xffff0000 0xffff00 0xff00ff00
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)\
[Konflikty z kompilatorem x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
