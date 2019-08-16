---
title: _InterlockedCompareExchangePointer, funkcje wewnętrzne
ms.date: 11/04/2016
f1_keywords:
- _InterlockedCompareExchangePointer_HLERelease
- _InterlockedCompareExchangePointer_rel
- _InterlockedCompareExchangePointer_acq_cpp
- _InterlockedCompareExchangePointer
- _InterlockedCompareExchangePointer_cpp
- _InterlockedCompareExchangePointer_np
- _InterlockedCompareExchangePointer_rel_cpp
- _InterlockedCompareExchangePointer_HLEAcquire
- _InterlockedCompareExchangePointer_acq
- _InterlockedCompareExchangePointer_nf
helpviewer_keywords:
- InterlockedCompareExchangePointer_acq intrinsic
- _InterlockedCompareExchangePointer_rel intrinsic
- _InterlockedCompareExchangePointer_acq intrinsic
- InterlockedCompareExchangePointer_rel intrinsic
- InterlockedCompareExchangePointer intrinsic
- _InterlockedCompareExchangePointer_HLERelease intrinsic
- _InterlockedCompareExchangePointer_HLEAcquire intrinsic
- _InterlockedCompareExchangePointer intrinsic
- _InterlockedCompareExchangePointer_nf intrinsic
- _InterlockedCompareExchangePointer_np intrinsic
ms.assetid: 97fde59d-2bf9-42aa-a0fe-a5b6befdd44b
ms.openlocfilehash: 7b8ba4fe6224292d0160f859aeb630fc17c2d992
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509430"
---
# <a name="_interlockedcompareexchangepointer-intrinsic-functions"></a>_InterlockedCompareExchangePointer, funkcje wewnętrzne

**Microsoft Specific**

Wykonuje niepodzielną operację, która `Exchange` przechowuje adres `Destination` w `Destination` adresie, `Comparand` Jeśli wartość i adres są równe.

## <a name="syntax"></a>Składnia

```
void * _InterlockedCompareExchangePointer (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
void * _InterlockedCompareExchangePointer_acq (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
void * _InterlockedCompareExchangePointer_HLEAcquire (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
void * _InterlockedCompareExchangePointer_HLERelease (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
void * _InterlockedCompareExchangePointer_nf (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
void * _InterlockedCompareExchangePointer_np (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
long _InterlockedCompareExchangePointer_rel (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
```

#### <a name="parameters"></a>Parametry

*Punktu*<br/>
[in. out] Wskaźnik na wskaźnik do wartości docelowej. Znak jest ignorowany.

*Exchange*<br/>
podczas Wskaźnik programu Exchange. Znak jest ignorowany.

*Argument porównania określony*<br/>
podczas Wskaźnik do porównania z miejscem docelowym. Znak jest ignorowany.

## <a name="return-value"></a>Wartość zwracana

Wartość zwracana jest początkową wartością miejsca docelowego.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|nagłówek|
|---------------|------------------|------------|
|`_InterlockedCompareExchangePointer`|x86, ARM, x64|\<intrin.h>|
|`_InterlockedCompareExchangePointer_acq`, `_InterlockedCompareExchangePointer_nf`, `_InterlockedCompareExchangePointer_rel`|ARM|\<iiintrin.h>|
|`_InterlockedCompareExchangePointer_HLEAcquire`, `_InterlockedCompareExchangePointer_HLERelease`|x86, x64|\<immintrin.h>|

## <a name="remarks"></a>Uwagi

`_InterlockedCompareExchangePointer`wykonuje niepodzielną porównanie `Destination` adresu `Comparand` z adresem. Jeśli adres jest równy `Comparand` adresowi, `Exchange` adres jest przechowywany w adresie określonym przez `Destination`. `Destination` W przeciwnym razie nie jest wykonywana żadna operacja.

`_InterlockedCompareExchangePointer`zapewnia wewnętrzną obsługę kompilatora dla funkcji [InterlockedCompareExchangePointer](/windows-hardware/drivers/ddi/content/wdm/nf-wdm-interlockedcompareexchangepointer) Win32 Windows SDK.

Przykład użycia `_InterlockedCompareExchangePointer`programu można znaleźć w temacie [_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md).

Na platformach ARM Użyj funkcji wewnętrznych z `_acq` i `_rel` sufiksów, jeśli potrzebujesz uzyskiwania i wydawania semantyki, na przykład na początku i na końcu sekcji krytycznej. Elementy wewnętrzne ARM z `_nf` sufiksem ("No ogrodzeni") nie działają jako bariera pamięci.

Elementy wewnętrzne z `_np` sufiksem ("No Fetch") uniemożliwiają wstawienie przez kompilator możliwej operacji pobierania z wyprzedzeniem.

Na platformach firmy Intel, które obsługują instrukcje dotyczące blokowania sprzętowego dla koprocedury (HLE), `_HLEAcquire` wewnętrzne `_HLERelease` z i sufiksy zawierają wskazówkę do procesora, który może przyspieszyć działanie, eliminując krok blokady zapisu sprzętu. Jeśli te elementy wewnętrzne są wywoływane na platformach, które nie obsługują HLE, Wskazówka jest ignorowana.

Te procedury są dostępne tylko jako elementy wewnętrzne.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)