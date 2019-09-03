---
title: _div64
ms.date: 09/02/2019
f1_keywords:
- _div64
helpviewer_keywords:
- _div64 intrinsic
ms.openlocfilehash: 1d05c5d6e25540a5de1b2f8231697c9a738759ce
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216766"
---
# <a name="_div64"></a>_div64

`_div64` Wewnętrznie dzieli 64-bitową liczbę całkowitą przez 32-bitową liczbę całkowitą. Wartość zwracana utrzymuje iloraz, a wewnętrzna Zwraca resztę za pomocą parametru wskaźnika. `_div64`jest **specyficzny dla firmy Microsoft**.

## <a name="syntax"></a>Składnia

```C
int _div64(
   __int64 dividend,
   int divisor,
   int* remainder
);
```

### <a name="parameters"></a>Parametry

*płacone* \
podczas 64-bitowa liczba całkowita do podzielenia.

*dzielnik* \
podczas 32-bitowa liczba całkowita do podzielenia przez.

*pozostałej części* \
określoną 32-bitowe całkowite bity reszty.

## <a name="return-value"></a>Wartość zwracana

32 bitów ilorazu.

## <a name="remarks"></a>Uwagi

Wewnętrznie dzieli *dzielną* przez *dzielnik.* `_div64` Przechowuje resztę z 32-bitowej liczby całkowitej wskazywanej przez *resztę*i zwraca 32 bitów ilorazu.

Funkcja `_div64` wewnętrzna jest dostępna od wersji Visual Studio 2019 RTM.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|nagłówek|
|---------------|------------------|------------|
|`_div64`|x86, x64|\<immintrin.h>|

## <a name="see-also"></a>Zobacz także

[_udiv64](udiv64.md) \
[Funkcje wewnętrzne kompilatora](compiler-intrinsics.md)
