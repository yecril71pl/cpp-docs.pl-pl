---
title: Funkcje wewnętrzne _InterlockedIncrement
ms.date: 09/02/2019
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
ms.openlocfilehash: 4dd9ae9ba5454b0afefa332689d94fa3619a07a6
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221981"
---
# <a name="_interlockedincrement-intrinsic-functions"></a>Funkcje wewnętrzne _InterlockedIncrement

**Microsoft Specific**

Zapewnianie wewnętrznej obsługi kompilatora dla funkcji [InterlockedIncrement](/windows/win32/api/winnt/nf-winnt-interlockedincrement) Win32 Windows SDK.

## <a name="syntax"></a>Składnia

```C
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

### <a name="parameters"></a>Parametry

*lpAddend*\
[in. out] Wskaźnik do zmiennej, która ma zostać zwiększona.

## <a name="return-value"></a>Wartość zwracana

Wartość zwracana jest wynikową wartością przyrostową.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|nagłówek|
|---------------|------------------|------------|
|`_InterlockedIncrement`, `_InterlockedIncrement16`|x86, ARM, x64, ARM64|\<intrin.h>|
|`_InterlockedIncrement64`|ARM, x64, ARM64|\<intrin.h>|
|`_InterlockedIncrement_acq`, `_InterlockedIncrement_rel`, `_InterlockedIncrement_nf`, `_InterlockedIncrement16_acq`, `_InterlockedIncrement16_rel`, `_InterlockedIncrement16_nf`, `_InterlockedIncrement64_acq`, `_InterlockedIncrement64_rel`, `_InterlockedIncrement64_nf`|ARM, ARM64|\<intrin.h>|

## <a name="remarks"></a>Uwagi

Istnieją różne różnice `_InterlockedIncrement` , które różnią się w zależności od typów danych, których dotyczą, oraz od tego, czy jest używana specyficzna dla procesora wersja semantyki.

Chociaż funkcja działa na 32-bitowych liczb całkowitych, `_InterlockedIncrement16` działa na 16-bitowych wartościach całkowitych i `_InterlockedIncrement64` działa na 64-bitowych liczb całkowitych. `_InterlockedIncrement`

Na platformach ARM Użyj funkcji wewnętrznych z `_acq` i `_rel` sufiksów, jeśli potrzebujesz uzyskiwania i wydawania semantyki, na przykład na początku i na końcu sekcji krytycznej. Wewnętrzny z `_nf` sufiksem ("No ogrodzeni") nie działa jako bariera pamięci.

Zmienna wskazywana przez `lpAddend` parametr musi być wyrównana do 32-bitowej granicy; w przeciwnym razie ta funkcja kończy się niepowodzeniem w systemach wieloprocesorowych x86 i w systemach innych niż x86. Aby uzyskać więcej informacji, zobacz [align](../cpp/align-cpp.md).

Funkcja Win32 jest zadeklarowana w `Wdm.h` lub `Ntddk.h`.

Te procedury są dostępne tylko jako elementy wewnętrzne.

## <a name="example"></a>Przykład

Aby uzyskać przykład sposobu użycia `_InterlockedIncrement`, zobacz [_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md).

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)\
[Keywords](../cpp/keywords-cpp.md)\
[Konflikty z kompilatorem x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
