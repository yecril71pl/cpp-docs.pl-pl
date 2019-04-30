---
title: __ull_rshift
ms.date: 11/04/2016
f1_keywords:
- __ull_rshift
helpviewer_keywords:
- ull_rshift intrinsic
- __ull_rshift intrinsic
ms.assetid: b7ff5254-3540-4e6e-b57c-a6c4beb7dca2
ms.openlocfilehash: 5d62ec1526aff595c14a53e9eca43a7a3118c8fa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390129"
---
# <a name="ullrshift"></a>__ull_rshift

**Microsoft Specific**

na x64 przesuwa wartość 64-bitową, określonym przez pierwszy parametr w prawo o liczbę bitów określoną w drugim parametrze.

## <a name="syntax"></a>Składnia

```
unsigned __int64 __ull_rshift(
   unsigned __int64 mask, 
   int nBit
);
```

#### <a name="parameters"></a>Parametry

*Maska*<br/>
[in] Wartość 64-bitową liczbę całkowitą na przesunięcie w prawo.

*nBit*<br/>
[in] Liczba bitów, aby przenieść modulo 32 na x86 i modulo 64 na x64.

## <a name="return-value"></a>Wartość zwracana

Maska przesunięte `nBit` usługi bits.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__ull_rshift`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Jeśli drugi parametr jest większa niż 31 na numer jest pobierany modulo 32 (64 na x64), aby określić liczbę bitów, aby przenieść x86 (63 na x64). `ull` w nazwie wskazuje `unsigned long long (unsigned __int64)`.

## <a name="example"></a>Przykład

```
// ull_rshift.cpp
// compile with: /EHsc
// processor: x86, x64
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(__ull_rshift)

int main()
{
   unsigned __int64 mask = 0x100;
   int nBit = 8;
   mask = __ull_rshift(mask, nBit);
   cout << hex << mask << endl;
}
```

## <a name="output"></a>Dane wyjściowe

```
1
```

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[__ll_lshift](../intrinsics/ll-lshift.md)<br/>
[__ll_rshift](../intrinsics/ll-rshift.md)<br/>
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)