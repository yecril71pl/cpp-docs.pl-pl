---
title: _udiv128
ms.date: 04/17/2019
f1_keywords:
- _udiv128
helpviewer_keywords:
- _udiv128 intrinsic
ms.openlocfilehash: 0e66bbe978199f47134aa288bdd2bac4eb3e332a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390168"
---
# <a name="udiv128"></a>_udiv128

`_udiv128` Wewnętrzne dzieli 128-bitowej nieoznaczonej liczby całkowitej przez 64-bitowej nieoznaczonej liczby całkowitej. Wartość zwracana zawiera iloraz, a funkcja zwraca resztę z dzielenia za pomocą parametru wskaźnika. `_udiv128` jest **specyficzne dla firmy Microsoft**.

## <a name="syntax"></a>Składnia

```C
unsigned __int64 _udiv128(
   unsigned __int64 highDividend,
   unsigned __int64 lowDividend,
   unsigned __int64 divisor,
   unsigned __int64 *remainder
);
```

### <a name="parameters"></a>Parametry

*highDividend* \
[in] Wysoka 64 bity dzielna.

*lowDividend* \
[in] Niski 64 bity dzielna.

*dzielnik.* \
[in] 64-bitową liczbę całkowitą dzielnikiem.

*Pozostała* \
[out] Bity 64-bitową liczbę całkowitą resztę.

## <a name="return-value"></a>Wartość zwracana

64-bitowy ilorazu.

## <a name="remarks"></a>Uwagi

Przekaż górny 64-bitowy dzielna 128-bitowego w *highDividend*i niższych 64-bitowy w *lowDividend*. Wewnętrzne dzieli tę wartość przez *dzielnik*. Przechowuje w 64-bitowej nieoznaczonej liczby całkowitej wskazywany przez resztę *resztę*i zwraca 64-bitowy ilorazu.

`_udiv128` Wewnętrzne są dostępne począwszy od programu Visual Studio 2019 RTM.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|nagłówek|
|---------------|------------------|------------|
|`_udiv128`|X64|\<immintrin.h>|

## <a name="see-also"></a>Zobacz także

[_div128](div128.md) \
[Funkcje wewnętrzne kompilatora](compiler-intrinsics.md)
