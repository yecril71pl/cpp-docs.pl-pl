---
title: _umul128
ms.date: 11/04/2016
f1_keywords:
- __umul128
helpviewer_keywords:
- __umul128 intrinsic
ms.assetid: 13684df3-3ac7-467c-b258-a0e93bc490b5
ms.openlocfilehash: 94f26a6baeb4d3440d7f16af298b9880b91860f2
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220494"
---
# <a name="umul128"></a>_umul128

**Microsoft Specific**

Mnoży dwie 64-bitowych liczb całkowitych bez znaku przekazany jako pierwsze dwa argumenty i umieszcza wysokiej 64-bitowy produktu w 64-bitowej nieoznaczonej liczby całkowitej wskazywany przez `HighProduct` i zwraca niski 64-bitowy produkt.

## <a name="syntax"></a>Składnia

```
unsigned __int64 _umul128(
   unsigned __int64 Multiplier,
   unsigned __int64 Multiplicand,
   unsigned __int64 *HighProduct
);
```

#### <a name="parameters"></a>Parametry

*Mnożnik*<br/>
[in] Pierwsza liczba całkowita 64-bitowego do pomnożenia.

*Którą mnożona jest mnożna*<br/>
[in] Drugi 64-bitową liczbę całkowitą do pomnożenia.

*HighProduct*<br/>
[out] Wysoka 64 bity produktu.

## <a name="return-value"></a>Wartość zwracana

Niski 64 bity produktu.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|nagłówek|
|---------------|------------------|------------|
|`_umul128`|X64|\<intrin.h>|

## <a name="example"></a>Przykład

```
// umul128.c
// processor: x64

#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_umul128)

int main()
{
    unsigned __int64 a = 0x0fffffffffffffffI64;
    unsigned __int64 b = 0xf0000000I64;
    unsigned __int64 c, d;

    d = _umul128(a, b, &c);

    printf_s("%#I64x * %#I64x = %#I64x%I64x\n", a, b, c, d);
}
```

```Output
0xfffffffffffffff * 0xf0000000 = 0xeffffffffffffff10000000
```

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
