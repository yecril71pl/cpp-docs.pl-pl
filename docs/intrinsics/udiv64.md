---
title: _udiv64
ms.date: 04/17/2019
f1_keywords:
- _udiv64
helpviewer_keywords:
- _udiv64 intrinsic
ms.openlocfilehash: 73a29b180eeda49a9a25e9e568d25c7563234fad
ms.sourcegitcommit: 2ce88de75e7681220ae09a0ab13056f22f357a46
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59983114"
---
# <a name="udiv64"></a>_udiv64

`_udiv64` Wewnętrzne dzieli 64-bitowej nieoznaczonej liczby całkowitej przez 32-bitowa liczba całkowita bez znaku. Wartość zwracana zawiera iloraz, a funkcja zwraca resztę z dzielenia za pomocą parametru wskaźnika. `_udiv64` jest **specyficzne dla firmy Microsoft**.

## <a name="syntax"></a>Składnia

```C
unsigned int _udiv64(
   unsigned __int64 dividend,
   unsigned int divisor,
   unsigned int* remainder
);
```

### <a name="parameters"></a>Parametry

*dzielna*<br/>
[in] 64-bitowej nieoznaczonej liczby całkowitej do podzielenia.

*divisor*<br/>
[in] 32-bitowa liczba całkowita bez znaku dzielnikiem.

*Pozostała*<br/>
[out] Resztę 32-bitowej nieoznaczonej liczby całkowitej.

## <a name="return-value"></a>Wartość zwracana

32 bity ilorazu.

## <a name="remarks"></a>Uwagi

`_udiv64` Wewnętrzne dzieli *dzielna* przez *dzielnik*. Przechowuje w 32-bitowa liczba całkowita bez znaku wskazywany przez resztę *resztę*i zwraca 32-bitowy ilorazu.

`_udiv64` Wewnętrzne są dostępne począwszy od programu Visual Studio 2019 RTM.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|nagłówek|
|---------------|------------------|------------|
|`_udiv64`|x86, x64|\<immintrin.h>|

## <a name="see-also"></a>Zobacz także

[_div64](div64.md) \
[Funkcje wewnętrzne kompilatora](compiler-intrinsics.md)
