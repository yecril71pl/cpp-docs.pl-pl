---
title: _BitScanReverse, _BitScanReverse64 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _BitScanReverse64
- _BitScanReverse_cpp
- _BitScanReverse
- _BitScanReverse64_cpp
dev_langs:
- C++
helpviewer_keywords:
- bsr instruction
- _BitScanReverse intrinsic
- BitScanReverse intrinsic
ms.assetid: 2520a207-af8b-4aad-9ae7-831abeadf376
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0867241e983794177cdb53b4bbacd1aadd9b8eba
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436328"
---
# <a name="bitscanreverse-bitscanreverse64"></a>_BitScanReverse, _BitScanReverse64

**Microsoft Specific**

Wyszukiwanie danych maski z najbardziej znaczący bit (BITEM) do najmniej znaczący bit (najmniej znaczący BAJT) ustawionego bitu (1).

## <a name="syntax"></a>Składnia

```
unsigned char _BitScanReverse(
   unsigned long * Index,
   unsigned long Mask
);
unsigned char _BitScanReverse64(
   unsigned long * Index,
   unsigned __int64 Mask
);
```

#### <a name="parameters"></a>Parametry

*Index*<br/>
[out] Pozycja bitu pierwszego ustawionego bitu [1], znaleziono załadowana.

*Maska*<br/>
[in] 32-bitowy lub 64-bitową wartość do wyszukania.

## <a name="return-value"></a>Wartość zwracana

Jeśli wartość różną od zera `Index` było zestawu lub 0, jeśli nie znaleziono żadnych bitów zestawu.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|nagłówek|
|---------------|------------------|------------|
|`_BitScanReverse`|x86, ARM, x64|\<intrin.h>|
|`_BitScanReverse64`|ARM, x64||

## <a name="example"></a>Przykład

```
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

## <a name="input"></a>Dane wejściowe

```
12
```

## <a name="sample-output"></a>Przykładowe dane wyjściowe

```
Enter a positive integer as the mask:
Mask: 12 Index: 3
```

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)