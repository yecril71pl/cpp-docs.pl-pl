---
title: Funkcje wewnętrzne _interlockedexchangepointer
ms.date: 11/04/2016
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
ms.openlocfilehash: 7599d4221d7dbd0e08585b51982e839aa267a011
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512102"
---
# <a name="interlockedexchangepointer-intrinsic-functions"></a>Funkcje wewnętrzne _interlockedexchangepointer

**Microsoft Specific**

W trakcie operacji niepodzielnych programu exchange, skopiowanie adresu przekazanego jako drugi argument do pierwszego, która zwraca oryginalny adres pierwszego.

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

*Docelowy*<br/>
[out w] Wskaźnik do wskaźnika do wartości do programu exchange. Funkcja ustawia wartość `Value` i zwraca jego poprzednią wartość.

*Wartość*<br/>
[in] Wartość wymienianych z wartością wskazywany przez `Target`.

## <a name="return-value"></a>Wartość zwracana

Funkcja zwraca wartość początkową wskazywany przez `Target`.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|nagłówek|
|---------------|------------------|------------|
|`_InterlockedExchangePointer`|x86, ARM, x64|\<intrin.h>|
|`_InterlockedExchangePointer_acq`, `_InterlockedExchangePointer_rel`, `_InterlockedExchangePointer_nf`|ARM|\<intrin.h>|
|`_InterlockedExchangePointer_HLEAcquire`, `_InterlockedExchangePointer_HLERelease`|x64 z obsługą HLE|\<immintrin.h>|

Na x86 architektury, `_InterlockedExchangePointer` to makro, które wywołuje `_InterlockedExchange`.

## <a name="remarks"></a>Uwagi

W systemie 64-bitowych parametry są 64-bitowy i muszą być wyrównane na granicach 64-bitowy; w przeciwnym razie operacja zakończy się niepowodzeniem. W systemie 32-bitowych parametry są 32-bitowy i muszą być wyrównane na granicach 32-bitowych. Aby uzyskać więcej informacji, zobacz [wyrównać](../cpp/align-cpp.md).

Na platformach ARM, użyj funkcji wewnętrznych za pomocą `_acq` i `_rel` sufiksy, jeśli potrzebujesz uzyskać i zwolnij semantykę, takich jak na początku i na końcu sekcję krytyczną. Wewnętrzne z `_nf` sufiks ("nie ogranicznika") nie działają jako czynnik blokujący pamięci.

Na platformach firmy Intel, obsługujące instrukcje pominięcia blokady sprzętu (HLE), funkcje wewnętrzne z `_HLEAcquire` i `_HLERelease` sufiksy obejmują wskazówkę procesora, który może przyspieszyć wydajność, eliminując krok blokady zapisu w sprzęcie. Jeśli te funkcje wewnętrzne są wywoływane na platformach, które nie obsługują HLE, wskazówka zostanie zignorowany.

Te procedury są dostępne tylko jako funkcje wewnętrzne.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)<br/>
[Konflikty z kompilatorem x86](../build/conflicts-with-the-x86-compiler.md)