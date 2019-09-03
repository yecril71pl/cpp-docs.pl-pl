---
title: _BitScanReverse, _BitScanReverse64
ms.date: 09/02/2019
f1_keywords:
- _BitScanReverse64
- _BitScanReverse_cpp
- _BitScanReverse
- _BitScanReverse64_cpp
helpviewer_keywords:
- bsr instruction
- _BitScanReverse intrinsic
- BitScanReverse intrinsic
ms.assetid: 2520a207-af8b-4aad-9ae7-831abeadf376
ms.openlocfilehash: 848c153967e5581f08f1d499a28ab282ee2602df
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216947"
---
# <a name="_bitscanreverse-_bitscanreverse64"></a>_BitScanReverse, _BitScanReverse64

**Microsoft Specific**

Przeszukaj dane maski z najbardziej znaczącego bitu (MSB) na najmniej znaczący bit (LSB) dla zestawu bitów (1).

## <a name="syntax"></a>Składnia

```C
unsigned char _BitScanReverse(
   unsigned long * Index,
   unsigned long Mask
);
unsigned char _BitScanReverse64(
   unsigned long * Index,
   unsigned __int64 Mask
);
```

### <a name="parameters"></a>Parametry

*Indeks*\
określoną Załadowano z pozycją bitową pierwszego zestawu bit (1).

*Bitowa*\
podczas Wartość 32-bitowa lub 64-bitowa do wyszukania.

## <a name="return-value"></a>Wartość zwracana

Wartość różna od `Index` zera, jeśli została ustawiona, lub wartość 0, jeśli nie znaleziono żadnego zestawu bitów.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|nagłówek|
|---------------|------------------|------------|
|`_BitScanReverse`|x86, ARM, x64, ARM64|\<intrin.h>|
|`_BitScanReverse64`|ARM64, x64|\<intrin.h>|

## <a name="example"></a>Przykład

```cpp
// BitScanReverse.cpp
// compile with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(_BitScanReverse)

int main()
{
   unsigned long mask = 0x1000;
   unsigned long index;
   unsigned char isNonzero;

   cout << "Enter a positive integer as the mask: " << flush;
   cin >> mask;
   isNonzero = _BitScanReverse(&index, mask);
   if (isNonzero)
   {
      cout << "Mask: " << mask << " Index: " << index << endl;
   }
   else
   {
      cout << "No set bits found.  Mask is zero." << endl;
   }
}
```

```Input
12
```

```Output
Enter a positive integer as the mask:
Mask: 12 Index: 3
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
