---
title: funkcje wewnętrzne _interlockedbittestandset
ms.date: 12/17/2018
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
helpviewer_keywords:
- _interlockedbittestandset intrinsic
- _interlockedbittestandset64 intrinsic
- lock_bts instruction
ms.assetid: b1b7e334-53ea-48cf-ba60-5fa3ef51a1fc
ms.openlocfilehash: 3da533b3cf2ab8f396e4ba284cc0bf921a5c80b5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396792"
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

*a*<br/>
[in] Wskaźnik do pamięci do sprawdzenia.

*b*<br/>
[in] Pozycja bitu do testowania.

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

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)<br/>
[Konflikty z kompilatorem x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)