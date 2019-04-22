---
title: __mulh
ms.date: 11/04/2016
f1_keywords:
- __mulh
helpviewer_keywords:
- __mulh intrinsic
ms.assetid: cd2ab093-9ef6-404d-ac34-0bee033882f3
ms.openlocfilehash: 122d7ff28a01c0b95c16c6a0f4cd20e883744d2e
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59034160"
---
# <a name="mulh"></a>__mulh

**Microsoft Specific**

Zwraca wysokiej 64-bitowy iloczyn dwóch liczb całkowitych ze znakiem 64-bitowych.

## <a name="syntax"></a>Składnia

```
__int64 __mulh(
   __int64 a,
   __int64 b
);
```

#### <a name="parameters"></a>Parametry

*a*<br/>
[in] Pierwszy numer do pomnożenia.

*b*<br/>
[in] Druga liczba do pomnożenia.

## <a name="return-value"></a>Wartość zwracana

Wysoka 64 bity 128-bitowego wynik mnożenia.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__mulh`|X64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Ta procedura jest dostępna wyłącznie jako wewnętrzna.

## <a name="example"></a>Przykład

```
// mulh.cpp
// processor: x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic (__mulh)

int main()
{
    __int64 a = 0x0fffffffffffffffI64;
    __int64 b = 0xf0000000I64;

    __int64 result = __mulh(a, b); // the high 64 bits
    __int64 result2 = a * b; // the low 64 bits

    printf_s(" %#I64x * %#I64x = %#I64x%I64x\n",
             a, b, result, result2);
}
```

```Output
0xfffffffffffffff * 0xf0000000 = 0xeffffffffffffff10000000
```

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)