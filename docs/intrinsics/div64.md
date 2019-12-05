---
title: _div64
ms.date: 09/02/2019
f1_keywords:
- _div64
helpviewer_keywords:
- _div64 intrinsic
ms.openlocfilehash: 59c5eae66f9e93cb88f9512e405376f2ef5f1ceb
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74858025"
---
# <a name="_div64"></a>_div64

`_div64` wewnętrznie dzieli 64-bitową liczbę całkowitą przez 32-bitową liczbę całkowitą. Wartość zwracana utrzymuje iloraz, a wewnętrzna Zwraca resztę za pomocą parametru wskaźnika. `_div64` to **specyficzny dla firmy Microsoft**.

## <a name="syntax"></a>Składnia

```C
int _div64(
   __int64 dividend,
   int divisor,
   int* remainder
);
```

### <a name="parameters"></a>Parametry

 \ *dywidendy*
podczas 64-bitowa liczba całkowita do podzielenia.

*dzielnik* \
podczas 32-bitowa liczba całkowita do podzielenia przez.

*pozostała* \
określoną 32-bitowe całkowite bity reszty.

## <a name="return-value"></a>Wartość zwracana

32 bitów ilorazu.

## <a name="remarks"></a>Uwagi

`_div64` wewnętrzna dzieli *dzielną* przez *dzielnik*. Przechowuje resztę z 32-bitowej liczby całkowitej wskazywanej przez *resztę*i zwraca 32 bitów ilorazu.

`_div64` wewnętrzna jest dostępna od wersji Visual Studio 2019 RTM.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|nagłówek|
|---------------|------------------|------------|
|`_div64`|x86, x64|\<immintrin.h>|

## <a name="see-also"></a>Zobacz także

[_udiv64](udiv64.md) \
[Funkcje wewnętrzne kompilatora](compiler-intrinsics.md)
