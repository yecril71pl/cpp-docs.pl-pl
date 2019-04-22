---
title: _BitScanForward, _BitScanForward64
ms.date: 11/04/2016
f1_keywords:
- _BitScanForward
- _BitScanForward_cpp
- _BitScanForward64_cpp
- _BitScanForward64
helpviewer_keywords:
- _BitScanForward intrinsic
- bsf instruction
- BitScanForward intrinsic
ms.assetid: 405e60fb-0815-42a7-9b02-6fc035122203
ms.openlocfilehash: 8b09aeee485611ddd20d51b4c1e36ec98c03c26e
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59022570"
---
# <a name="bitscanforward-bitscanforward64"></a>_BitScanForward, _BitScanForward64

**Microsoft Specific**

Wyszukaj maskowanie danych z co najmniej znaczący bit (najmniej znaczący BAJT) do najbardziej znaczący bit (BITEM) ustawionego bitu (1).

## <a name="syntax"></a>Składnia

```
unsigned char _BitScanForward(
   unsigned long * Index,
   unsigned long Mask
);
unsigned char _BitScanForward64(
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

0, jeśli maska jest równa zeru; wartość różną od zera w przeciwnym razie.

## <a name="remarks"></a>Uwagi

Jeśli zostanie znaleziony zestaw bitów, pozycja bitu pierwszego ustawionego bitu znaleziono jest zwracany w pierwszym parametrem. Jeśli zostanie znaleziony nie ustawionego bitu, zwracany jest 0; w przeciwnym razie zwracana jest 1.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`_BitScanForward`|x86, ARM, x64|
|`_BitScanForward64`|ARM, x64|

**Plik nagłówkowy** \<intrin.h >

## <a name="example"></a>Przykład

```
// BitScanForward.cpp
// compile with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(_BitScanForward)

int main()
{
   unsigned long mask = 0x1000;
   unsigned long index;
   unsigned char isNonzero;

   cout << "Enter a positive integer as the mask: " << flush;
   cin >> mask;
   isNonzero = _BitScanForward(&index, mask);
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
Mask: 12 Index: 2
```

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)