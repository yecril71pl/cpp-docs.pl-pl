---
title: __ll_lshift
ms.date: 11/04/2016
f1_keywords:
- __ll_lshift_cpp
- __ll_lshift
helpviewer_keywords:
- ll_lshift intrinsic
- __ll_lshift intrinsic
ms.assetid: fe98f733-426d-44b3-8f24-5d0d6d44bd94
ms.openlocfilehash: 5a91ce5db46b19be570f8d48a584a2caeabcc163
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59024468"
---
# <a name="lllshift"></a>__ll_lshift

**Microsoft Specific**

Przesuwa podana wartość 64-bitowego w lewo przez określoną liczbę bitów.

## <a name="syntax"></a>Składnia

```
unsigned __int64 __ll_lshift(
   unsigned __int64 Mask,
   int nBit
);
```

#### <a name="parameters"></a>Parametry

*Maska*<br/>
[in] Wartość 64-bitową liczbę całkowitą na przesunięcie w lewo.

*nBit*<br/>
[in] Liczba bitów, aby przesunąć.

## <a name="return-value"></a>Wartość zwracana

Maska przesunięte w lewo przez `nBit` usługi bits.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__ll_lshift`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Jeśli kompilujesz program za pomocą architektury 64-bitowym i `nBit` jest większy niż 63, jest liczbą bitów, aby przenieść `nBit` modulo 64. Jeśli kompilujesz program za pomocą architektury 32-bitowej i `nBit` jest większy niż 31, jest liczbą bitów, aby przenieść `nBit` modulo 32.

`ll` Nazwa wskazuje, że jest operacją na `long long` (`__int64`).

## <a name="example"></a>Przykład

```
// ll_lshift.cpp
// compile with: /EHsc
// processor: x86, x64
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(__ll_lshift)

int main()
{
   unsigned __int64 Mask = 0x100;
   int nBit = 8;
   Mask = __ll_lshift(Mask, nBit);
   cout << hex << Mask << endl;
}
```

## <a name="output"></a>Dane wyjściowe

```
10000
```

**Uwaga** nie ma wersji bez znaku operacji przesunięcia w lewo. Jest to spowodowane `__ll_lshift` już korzysta z parametrem wejściowym bez znaku. W odróżnieniu od przesunięcia w prawo jest ma zależności logowania dla przesunięcia w lewo, ponieważ najmniej znaczący bit w wyniku jest zawsze równa zero, niezależnie od tego, znak wartości przesunięte.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[__ll_rshift](../intrinsics/ll-rshift.md)<br/>
[__ull_rshift](../intrinsics/ull-rshift.md)<br/>
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)