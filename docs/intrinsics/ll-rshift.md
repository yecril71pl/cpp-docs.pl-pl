---
title: __ll_rshift
ms.date: 09/02/2019
f1_keywords:
- __ll_rshift_cpp
- __ll_rshift
helpviewer_keywords:
- __ll_rshift intrinsic
- ll_rshift intrinsic
ms.assetid: ef13b732-d122-44a0-add9-f5544a2c4ab2
ms.openlocfilehash: 6ae750f1a8825096ee30adb01768d5603ab23a01
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219667"
---
# <a name="__ll_rshift"></a>__ll_rshift

**Specyficzne dla firmy Microsoft**

Przenosi wartość 64-bitową określoną przez pierwszy parametr w prawo przez liczbę bitów określoną przez drugi parametr.

## <a name="syntax"></a>Składnia

```C
__int64 __ll_rshift(
   __int64 Mask,
   int nBit
);
```

### <a name="parameters"></a>Parametry

*Bitowa*\
podczas Wartość 64-bitowa liczba całkowita, która ma zostać przesunięta w prawo.

*nBit*\
podczas Liczba bitów do przesunięcia, modulo 64 w x64 i modulo 32 na x86.

## <a name="return-value"></a>Wartość zwracana

Maska przesunięta przez `nBit` bity.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__ll_rshift`|x86, x64|

**Plik nagłówka**\<intrin.h>

## <a name="remarks"></a>Uwagi

Jeśli drugi parametr jest większy niż 64 na x64 (32 na x86), ta liczba jest pobierana z modulo 64 (32 na x86), aby określić liczbę bitów do przesunięcia. `ll`Prefiks wskazuje, że jest to operacja na **`long long`** , inna nazwa dla **`__int64`** , 64-bitowy typ całkowity ze znakiem.

## <a name="example"></a>Przykład

```cpp
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

```Output
ffffffffffffff00
- 100
fffffffffffffff0
- 10
```

> [!NOTE]
> Jeśli `_ull_rshift` został użyty, MSB wartości z prawej strony byłyby zero, więc żądany wynik nie zostanie uzyskany w przypadku wartości ujemnej.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)\
[__ll_lshift](../intrinsics/ll-lshift.md)\
[__ull_rshift](../intrinsics/ull-rshift.md)
