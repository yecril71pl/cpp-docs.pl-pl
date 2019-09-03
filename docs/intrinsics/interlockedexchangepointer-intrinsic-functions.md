---
title: Funkcje wewnętrzne _InterlockedExchangePointer
ms.date: 09/02/2019
f1_keywords:
- _InterlockedExchangePointer_cpp
- _InterlockedExchangePointer_rel
- _InterlockedExchangePointer_nf
- _InterlockedExchangePointer_HLERelease
- _InterlockedExchangePointer_acq
- _InterlockedExchangePointer
- _InterlockedExchangePointer_acq_cpp
- _InterlockedExchangePointer_HLEAcquire
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
ms.openlocfilehash: 1402dcf5279658c1364b59a324d988129bc841d8
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217630"
---
# <a name="_interlockedexchangepointer-intrinsic-functions"></a>Funkcje wewnętrzne _InterlockedExchangePointer

**Microsoft Specific**

Wykonuje niepodzielną operację wymiany, która kopiuje adres przekazaną jako drugi argument do pierwszego argumentu i zwraca oryginalny adres pierwszego.

## <a name="syntax"></a>Składnia

```C
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

### <a name="parameters"></a>Parametry

*Obiektów*\
[in. out] Wskaźnik na wskaźnik do wartości do wymiany. Funkcja ustawia wartość na *wartość* i zwraca jej poprzednią wartość.

*Wartościami*\
podczas Wartość, która ma być wymieniana z wartością wskazywaną przez *element docelowy*.

## <a name="return-value"></a>Wartość zwracana

Funkcja zwraca początkową wartość wskazywaną przez *element docelowy*.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|nagłówek|
|---------------|------------------|------------|
|`_InterlockedExchangePointer`|x86, ARM, x64, ARM64|\<intrin.h>|
|`_InterlockedExchangePointer_acq`, `_InterlockedExchangePointer_rel`, `_InterlockedExchangePointer_nf`|ARM, ARM64|\<intrin.h>|
|`_InterlockedExchangePointer_HLEAcquire`, `_InterlockedExchangePointer_HLERelease`|X64|\<immintrin.h>|

W architekturze `_InterlockedExchangePointer` x86 jest makrem wywołującym `_InterlockedExchange`.

## <a name="remarks"></a>Uwagi

W systemie 64-bitowym parametry mają 64 bity i muszą być wyrównane na granicach 64-bitowych. W przeciwnym razie funkcja kończy się niepowodzeniem. W systemie 32-bitowym parametry mają 32 bity i muszą być wyrównane na granicach 32-bitowych. Aby uzyskać więcej informacji, zobacz [align](../cpp/align-cpp.md).

Na platformach ARM Użyj funkcji wewnętrznych z `_acq` i `_rel` sufiksów, jeśli potrzebujesz uzyskiwania i wydawania semantyki, na przykład na początku i na końcu sekcji krytycznej. Wewnętrzny z `_nf` sufiksem ("No ogrodzeni") nie działa jako bariera pamięci.

Na platformach firmy Intel, które obsługują instrukcje dotyczące blokowania sprzętowego dla koprocedury (HLE), `_HLEAcquire` wewnętrzne `_HLERelease` z i sufiksy zawierają wskazówkę do procesora, który może przyspieszyć działanie, eliminując krok blokady zapisu sprzętu. Jeśli te elementy wewnętrzne są wywoływane na platformach, które nie obsługują HLE, Wskazówka jest ignorowana.

Te procedury są dostępne tylko jako elementy wewnętrzne.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)\
[Konflikty z kompilatorem x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
