---
title: _div64
ms.date: 04/17/2019
f1_keywords:
- _div64
helpviewer_keywords:
- _div64 intrinsic
ms.openlocfilehash: a221cc7cf0655a41873c6777aecd8a9b27131b74
ms.sourcegitcommit: 2ce88de75e7681220ae09a0ab13056f22f357a46
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59983105"
---
# <a name="div64"></a>_div64

`_div64` Wewnętrzne dzieli 64-bitową liczbę całkowitą przez 32-bitową liczbę całkowitą. Wartość zwracana zawiera iloraz, a funkcja zwraca resztę z dzielenia za pomocą parametru wskaźnika. `_div64` jest **specyficzne dla firmy Microsoft**.

## <a name="syntax"></a>Składnia

```C
int _div64(
   __int64 dividend,
   int divisor,
   int* remainder
);
```

### <a name="parameters"></a>Parametry

*dzielna* \
[in] 64-bitową liczbę całkowitą do podzielenia.

*dzielnik.* \
[in] Liczba całkowita 32-bitowych dzielnikiem.

*Pozostała* \
[out] Bity 32-bitową liczbę całkowitą resztę.

## <a name="return-value"></a>Wartość zwracana

32 bity ilorazu.

## <a name="remarks"></a>Uwagi

`_div64` Wewnętrzne dzieli *dzielna* przez *dzielnik*. Przechowuje w 32-bitową liczbę całkowitą, wskazywana przez resztę *resztę*i zwraca 32-bitowy ilorazu.

`_div64` Wewnętrzne są dostępne począwszy od programu Visual Studio 2019 RTM.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|nagłówek|
|---------------|------------------|------------|
|`_div64`|x86, x64|\<immintrin.h>|

## <a name="see-also"></a>Zobacz także

[_udiv64](udiv64.md) \
[Funkcje wewnętrzne kompilatora](compiler-intrinsics.md)
