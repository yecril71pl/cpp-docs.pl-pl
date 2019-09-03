---
title: _mm_cvtsi64x_ss
ms.date: 09/02/2019
f1_keywords:
- _mm_cvtsi64x_ss
helpviewer_keywords:
- cvtsi2ss instruction
- _mm_cvtsi64x_ss intrinsic
ms.assetid: 01e5d321-c18a-46fd-a6f6-324364514e1f
ms.openlocfilehash: 0e9bacc56f212e804467d1c6e0159a1749235976
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217452"
---
# <a name="_mm_cvtsi64x_ss"></a>_mm_cvtsi64x_ss

**Microsoft Specific**

Generuje rozszerzoną wersję x64 64-bitową liczbę całkowitą do skalarnej wartości zmiennoprzecinkowej o pojedynczej precyzji`cvtsi2ss`().

## <a name="syntax"></a>Składnia

```C
__m128 _mm_cvtsi64x_ss(
   __m128 a,
   __int64 b
);
```

### <a name="parameters"></a>Parametry

*z*\
podczas `__m128` Struktura zawierająca cztery wartości zmiennoprzecinkowe o pojedynczej precyzji.

*b*\
podczas 64-bitowa liczba całkowita do przekonwertowania na wartość zmiennoprzecinkową.

## <a name="return-value"></a>Wartość zwracana

`__m128` Struktura, której pierwsza wartość zmiennoprzecinkowa jest wynikiem konwersji. Pozostałe trzy wartości są kopiowane bez zmian z.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`_mm_cvtsi64x_ss`|X64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Struktura reprezentuje rejestr XMM, więc wewnętrzna umożliwia przeniesienie wartości b z pamięci systemowej do rejestru XMM. `__m128`

Ta procedura jest dostępna tylko jako wewnętrzna.

## <a name="example"></a>Przykład

```cpp
// _mm_cvtsi64x_ss.cpp
// processor: x64

#include <intrin.h>
#include <stdio.h>

#pragma intrinsic(_mm_cvtsi64x_ss)

int main()
{
    __m128 a;
    __int64 b = 54;

    a.m128_f32[0] = 0;
    a.m128_f32[1] = 0;
    a.m128_f32[2] = 0;
    a.m128_f32[3] = 0;
    a = _mm_cvtsi64x_ss(a, b);

    printf_s( "%lf %lf %lf %lf\n",
              a.m128_f32[0], a.m128_f32[1],
              a.m128_f32[2], a.m128_f32[3] );
}
```

```Output
54.000000 0.000000 0.000000 0.000000
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[__m128](../cpp/m128.md)\
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
