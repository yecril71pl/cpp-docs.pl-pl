---
title: _udiv64
ms.date: 09/02/2019
f1_keywords:
- _udiv64
helpviewer_keywords:
- _udiv64 intrinsic
ms.openlocfilehash: 6dabbc94260ef578eb1a58a1b289b4a4654decdd
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219682"
---
# <a name="_udiv64"></a>_udiv64

`_udiv64` Wewnętrznie dzieli 64-bitową liczbę całkowitą bez znaku przez 32-bitową liczbę całkowitą bez znaku. Wartość zwracana utrzymuje iloraz, a wewnętrzna Zwraca resztę za pomocą parametru wskaźnika. `_udiv64`jest **specyficzny dla firmy Microsoft**.

## <a name="syntax"></a>Składnia

```C
unsigned int _udiv64(
   unsigned __int64 dividend,
   unsigned int divisor,
   unsigned int* remainder
);
```

### <a name="parameters"></a>Parametry

*płacone*\
podczas 64-bitowa liczba całkowita bez znaku do podzielenia.

*dzielnik*\
podczas 32-bitowa liczba całkowita bez znaku do dzielenia przez.

*pozostałej części*\
określoną 32-bitowa pozostała liczba całkowita bez znaku.

## <a name="return-value"></a>Wartość zwracana

32 bitów ilorazu.

## <a name="remarks"></a>Uwagi

Wewnętrznie dzieli *dzielną* przez *dzielnik.* `_udiv64` Przechowuje resztę z 32-bitowej liczby całkowitej bez znaku wskazywanej przez *resztę*i zwraca 32 bitów ilorazu.

Funkcja `_udiv64` wewnętrzna jest dostępna od wersji Visual Studio 2019 RTM.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|nagłówek|
|---------------|------------------|------------|
|`_udiv64`|x86, x64|\<immintrin.h>|

## <a name="see-also"></a>Zobacz także

[_div64](div64.md) \
[Funkcje wewnętrzne kompilatora](compiler-intrinsics.md)
