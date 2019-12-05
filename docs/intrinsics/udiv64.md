---
title: _udiv64
ms.date: 09/02/2019
f1_keywords:
- _udiv64
helpviewer_keywords:
- _udiv64 intrinsic
ms.openlocfilehash: ddb46f33b0fccc1cedc2a704265b096ba715b506
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857999"
---
# <a name="_udiv64"></a>_udiv64

`_udiv64` wewnętrznie dzieli 64-bitową liczbę całkowitą bez znaku przez 32-bitową liczbę całkowitą bez znaku. Wartość zwracana utrzymuje iloraz, a wewnętrzna Zwraca resztę za pomocą parametru wskaźnika. `_udiv64` to **specyficzny dla firmy Microsoft**.

## <a name="syntax"></a>Składnia

```C
unsigned int _udiv64(
   unsigned __int64 dividend,
   unsigned int divisor,
   unsigned int* remainder
);
```

### <a name="parameters"></a>Parametry

\ *dywidendy*
podczas 64-bitowa liczba całkowita bez znaku do podzielenia.

*dzielnik*\
podczas 32-bitowa liczba całkowita bez znaku do dzielenia przez.

*pozostała*\
określoną 32-bitowa pozostała liczba całkowita bez znaku.

## <a name="return-value"></a>Wartość zwracana

32 bitów ilorazu.

## <a name="remarks"></a>Uwagi

`_udiv64` wewnętrzna dzieli *dzielną* przez *dzielnik*. Przechowuje resztę z 32-bitowej liczby całkowitej bez znaku wskazywanej przez *resztę*i zwraca 32 bitów ilorazu.

`_udiv64` wewnętrzna jest dostępna od wersji Visual Studio 2019 RTM.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|nagłówek|
|---------------|------------------|------------|
|`_udiv64`|x86, x64|\<immintrin.h>|

## <a name="see-also"></a>Zobacz także

[_div64](div64.md) \
[Funkcje wewnętrzne kompilatora](compiler-intrinsics.md)
