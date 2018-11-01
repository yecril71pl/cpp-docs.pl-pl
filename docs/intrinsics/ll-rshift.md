---
title: __ll_rshift
ms.date: 11/04/2016
f1_keywords:
- __ll_rshift_cpp
- __ll_rshift
helpviewer_keywords:
- __ll_rshift intrinsic
- ll_rshift intrinsic
ms.assetid: ef13b732-d122-44a0-add9-f5544a2c4ab2
ms.openlocfilehash: 9c486921e41732ef7736ca5b62b44a86010dcf83
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50621875"
---
# <a name="llrshift"></a>__ll_rshift

**Microsoft Specific**

Przenosi wartość 64-bitową, określonym przez pierwszy parametr w prawo o liczbę bitów określoną w drugim parametrze.

## <a name="syntax"></a>Składnia

```
__int64 __ll_rshift(
   __int64 Mask,
   int nBit
);
```

#### <a name="parameters"></a>Parametry

*Maska*<br/>
[in] Wartość 64-bitową liczbę całkowitą na przesunięcie w prawo.

*nBit*<br/>
[in] Liczba bitów, aby przenieść modulo 64 na x64 i modulo 32 na x86.

## <a name="return-value"></a>Wartość zwracana

Maska przesunięte `nBit` usługi bits.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__ll_rshift`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Jeśli drugi parametr jest większa niż 64 na numer jest pobierany modulo 64 (32 na x86), aby określić liczbę bitów, aby przenieść x64 (32 na x86). `ll` Prefiks wskazuje, że jest operacją na `long long`, inną nazwę `__int64`, typ całkowity ze znakiem 64-bitowych.

## <a name="example"></a>Przykład

```
// ll_rshift.cpp
// compile with: /EHsc
// processor: x86, x64
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(__ll_rshift)

int main()
{
   __int64 Mask = - 0x100;
   int nBit = 4;
   cout << hex << Mask << endl;
   cout << " - " << (- Mask) << endl;
   Mask = __ll_rshift(Mask, nBit);
   cout << hex << Mask << endl;
   cout << " - " << (- Mask) << endl;
}
```

## <a name="output"></a>Dane wyjściowe

```
ffffffffffffff00
- 100
fffffffffffffff0
- 10
```

**Uwaga** Jeśli `_ull_rshift` było używane, BITEM wartość przesunięte w prawo byłby zero, dzięki czemu oczekiwany wynik może nie zostały uzyskane w przypadku wartości ujemnej.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)<br/>
[__ll_lshift](../intrinsics/ll-lshift.md)<br/>
[__ull_rshift](../intrinsics/ull-rshift.md)